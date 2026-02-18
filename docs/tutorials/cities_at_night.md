# Cities at Night

![](../../images/image71.png){width="100%"}


Cities at Night is a living demo that shows how Emissions and the newly added Glow effect can be used as tools to help clients tell stories in their 3D scenes. The demo shows how the Glow tool can be successfully used with Emission from different points of view, showing how we can successfully depict simple graphical information abstractly through the Birds Eye View and the Busline, or explore a mood-driven experience in Street View through its look and feel.

---

## Use Cases & Target Audiences

| Sector | Application |
|---|---|
| **Urban Planning & Architecture** | Light pollution studies, streetlighting design, safety analysis, event planning |
| **Real Estate & Development** | Night renders showing buildings lit in urban context; marketing assets for high-end clients |
| **Smart Cities & IoT** | Emissive intensity mapped to live data: energy consumption, sensors, infrastructure status |
| **Telecoms** | Signal strength and network coverage visualised spatially across a night cityscape |
| **Defense & Security** | Visibility analysis, surveillance coverage, lighting gaps across critical infrastructure |
| **Tourism & City Marketing** | Promotional night-time visualisations: waterfront districts, festivals, lighting schemes |
| **Esri Marketing & Sales** | Conference-ready demo content that is visually striking beyond typical GIS output |

> **The main takeaway:** this demo proves Web can produce something emotionally compelling, not just analytically useful, opening doors to customers who wouldn't typically look at Esri for traditional GIS reasons.

---

## Pipeline Overview

This post mortem explores the pipelines involved to make these visuals successful. For clarity, they are broken down into two sections, **Birds Eye View** and **Street View**, as their approaches, though linked, were done very differently.

---

## Birds Eye View

Using CityEngine's GetMapData, a small area of parcels around Brooklyn and Manhattan was used to make the urban skyline. The night scene needed a style that is simple and lower poly but shows off the city skyline appropriately. It was decided to go for something graphically similar to a skyline without swamping the user with detail. All surface elements were removed except for simple emissive texture maps to represent windows, longer and shorter, darker and brighter, with a view to randomise these on the facades in CGA.

### CGA Rule

```cga
/**
 * File:    White_LOD1_Height_OSM.cga
 * Purpose: Extrude to calculated height and apply emissive window materials.
 */

// ------------------------------
// 1. Attributes & Height Model
// ------------------------------

@Hidden
attr height = NaN
@Hidden
attr building__levels = NaN

attr groundfloor_height = 2
attr topfloor_height = 2
attr tile_width         = 2
attr biglvl = 2

const NaN  = ln(-1)
const NULL = "\ue000"

@Hidden
attr stringMats = filesSearch("Materials/Lights/Box2/*.cgamat")
attr stringMats2 = filesSearch("Materials/Lights/Long_Rect2/*.cgamat")

// Flags: Check if OSM data provides height/levels
hasHeight         = !isNull(height)
hasBuildingLevels = !isNull(building__levels)

// Calculate Levels
@Hidden
attr Levels =
    case hasBuildingLevels:
        building__levels
    case hasHeight && height > 0:
        max(1, rint(height / 3.0))
    else:
        2

// Calculate Floor Height
@Hidden
attr Floor_Ht =
    case hasHeight && hasBuildingLevels && building__levels > 0:
        max(2, height / building__levels)
    else:
        3.0

// Calculate Eave Height (Total Building Height)
@Hidden
attr Eave_Ht =
    case hasHeight && height > 0:
        height
    else:
        Levels * Floor_Ht


// ------------------------------
// 2. Start Rule
// ------------------------------

@StartRule
@InPolygon
Generate -->
    extrude(Eave_Ht)
    Building


// ------------------------------
// 3. Building Assembly
// ------------------------------

Building -->
    comp(f) { front : Frontfacade | side : Sidefacade | top: Roof }

Frontfacade -->
    case isnan(building__levels):
        setupProjection(0, scope.xy, 30, ~1)
        projectUV(0)
        setMaterial(readMaterial("Materials/Lights/GF.cgamat"))
        split(y) { groundfloor_height : Groundfloor
             |    { ~(biglvl): Window}*
             | ~(topfloor_height / 1) : Groundfloor }
    else :
        split(y) { groundfloor_height : Groundfloor
             |    { ~(biglvl): Window}*
             | ~(topfloor_height * 2) : Groundfloor }

Sidefacade -->
    case isnan(building__levels):
        setupProjection(0, scope.xy, 30, ~1)
        projectUV(0)
        setMaterial(readMaterial("Materials/Lights/GF.cgamat"))
        split(y) { groundfloor_height : Groundfloor
             |    { ~(biglvl): Window}*
             | ~(topfloor_height / 2) : Groundfloor}
    else :
        split(y) { groundfloor_height : Groundfloor
             |    { ~(biglvl): Window}*
             | ~(topfloor_height * 2) : Groundfloor}

Roof -->
    cleanupGeometry(all, 0)
    RoofTop

Groundfloor -->
    setMaterial(readMaterial("Materials/Lights/GF.cgamat"))


// ------------------------------
// 4. Window Randomisation
// ------------------------------

Window -->
    30% :
        setupProjection(0, scope.xy, 100, ~6)
        projectUV(0)
        setMaterial(readMaterial(stringMats[rint(rand(0, size(stringMats) - 1))]))
        translateUV(0, rand(-10, 10), 0)

    30% :
        setupProjection(0, scope.xy, 100, ~6)
        projectUV(0)
        setMaterial(readMaterial(stringMats[rint(rand(0, size(stringMats) - 1))]))
        translateUV(0, rand(-5, 5), 0)

    else :
        setupProjection(0, scope.xy, 100, ~6)
        projectUV(0)
        setMaterial(readMaterial(stringMats2[rint(rand(0, size(stringMats2) - 1))]))
        translateUV(0, rand(-10, 10), 0)

RoofTop -->
    cleanupGeometry(all, 0)
    setMaterial(readMaterial("Materials/Lights/RT.cgamat"))
```

### How the Rule Works

**Height Calculation**
The rule reads OSM attributes (`height` and `building__levels`) to determine how tall to make each building. Fallback logic defaults to 2 levels at 3m each if neither attribute is present. This is what gives the Brooklyn/Manhattan parcels their varied skyline heights rather than a uniform result.

**Building Assembly**
The footprint is extruded to the calculated height and split into front facades, side facades, and roof. Both facade types follow the same vertical structure: a ground floor strip, a repeating middle window band, and a top floor strip.

**Window Randomisation**
Each window band face uses a three-way probabilistic split. 30% receives a material from the `Box2` folder, 30% receives another random `Box2` material with a tighter UV translation range, and the remaining 40% receives a material from the `Long_Rect2` folder. The `translateUV` calls shift the texture randomly on each face so the emissive window pattern lands at different positions, preventing tiling repetition across the facade.

**Materials**
`GF.cgamat` is applied to ground floors, a dark non-emissive material. The window materials in `Box2` and `Long_Rect2` are the emissive textures carrying the light. `RT.cgamat` handles the roof.

### Performance Considerations

A balance was struck between poly count and emissive texture coverage. By keeping individual texture file sizes to 550KB, instancing them, and using every third floor as the split unit, enough variation was introduced to make the city feel organic at an acceptable performance cost. The window textures could potentially be reduced further. A range of window colours is also possible but should be used sparingly, as additional colour variants mean additional texture files that can accumulate quickly.

---

## Resolving Z-Fighting in CityEngine

![](../../images/image70.png){width="100%"}

A problem that appeared downstream, not visible during initial authoring, was z-fighting across a substantial number of buildings. This was caused by shapes containing more than one overlapping element. For a clean, minimal look, all inner shapes needed to be removed.

This was handled using a Python script run directly inside CityEngine.

### Python Cleanup Script

```python
from scripting import *

ce = CE()

shapes = ce.getObjectsFrom(ce.selection, ce.isShape)
if not shapes:
    print("No shapes selected.")
    raise SystemExit

newShapes = ce.separateFaces(shapes)

toDelete = [s for s in newShapes if not ce.getName(s).endswith("_0")]

if toDelete:
    ce.delete(toDelete)

kept = len(newShapes) - len(toDelete)
print("Done. Kept: %d | Deleted: %d" % (kept, len(toDelete)))
```

### How the Script Works

The script separates each selected shape into its component faces. The largest base shape, the building foundation, consistently receives a suffix of `_0`. All other faces are collected into a single `toDelete` list and removed in one batched call.

Batching the deletions is significantly faster than deleting each shape individually. Every `ce.delete()` call carries overhead as CityEngine updates its scene graph. A single call passing the full list pays that overhead once regardless of whether 5 or 5000 shapes are being removed. The fix fully resolved the z-fighting issue across the scene.