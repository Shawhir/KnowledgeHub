

# File Format

## Core Format: glTF (.glb / .gltf)

- Format is `.glb`. Additionally, the original Maya/Max files for each asset at each separate LOD level — if required — will be delivered.  
- The provision of an `.obj` of each asset is also required for interchange and archiving.

- For `.glb` files — there should be **no references to external files** (all textures, buffers etc. must be within the same `.glb` file).

- The `.glb` supports only **triangle geometries** with normals and (if needed) UV coordinates.

- **Center of all objects** is at origin (0/0/0 coordinate system).

- The vertices of a triangle should appear in **counter-clockwise order** when looked at from the front (i.e. CCW order according to this definition:  
  [http://cmichel.io/understanding-front-faces-winding-order-and-normals/](http://cmichel.io/understanding-front-faces-winding-order-and-normals/)).

- **Units** = metres.

- No **base64 binary encoding**.

- The `.glb` uses the **MS LOD extension** of the glTF format.  
  This same requirement is true for online usage where we also use the MS LOD extension.

- **Precision** of vertices and normals is `0.001` and of UV coordinates is `0.0001`, e.g.:

    `v -0.179 28.935 -1.636`  
    `vt 0.125 0.781`  
    `vn -0.9999 -0.0153 0`

    instead of:

    `v -0.179175 28.93456 -1.63585`  
    `vt 0.125 0.78125`  
    `vn -0.999883 -0.0153269 -1.11061e-015`

---

## Supported 3D Model Formats in ArcGIS Workflow

Besides glTF (.glb), ArcGIS and CityEngine workflows also support importing and exporting the following 3D formats:

| Format | Use Cases | Notes / Constraints |
|--------|-----------|---------------------|
| `.glb` / `.gltf` | Primary delivery format (web, CE, SceneViewer) | PBR, self-contained, MSFT LOD |
| `.obj` | Interchange, source format, archiving | Triangulated, no animation, simple material |
| `.fbx` | Source format for animated / rigged assets, Unreal workflows | Often used for Hero assets, supports animation |
| `.dae` (COLLADA) | Legacy CE workflows, interchange | XML-based, fragile, used less today |
| `.usd` | Advanced pipeline integration (future-facing) | High-end VFX, versioning, layering |
| `.3ds` | Legacy format, limited support | Used mainly in older model libraries |
| `.flt` (OpenFlight) | GIS simulation | Specialized use only |
| `.wrl` (VRML, GeoVRML) | Legacy GIS workflows | Rarely used today |

---

## Format Recommendations

- **Primary output format**: `.glb`
- **Source format (complex assets)**: `.fbx` or `.obj`
- **Legacy or special use**: `.dae`, `.usd`, `.flt`, `.wrl`, `.3ds`

---

## Notes

- Imported formats must be converted to **Multipatch** or **3D Object Feature Class** for use in ArcGIS Pro.
- Only `.glb` fully supports **advanced materials**, **LOD switching**, and **modern web visualization**.
- For further details on file formats see: [3D Models](https://doc.arcgis.com/en/3d/workflows/content/3d-models.htm).

