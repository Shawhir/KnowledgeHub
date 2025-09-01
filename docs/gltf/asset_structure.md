# Asset Structure

## Overview

- A rule of thumb at ESRI is to **build our assets as economically as possible**. These models are used in many different products – from the intensive Unreal to the more frugal Web products, so it is best to build assets that are workable for all our products. We have built an Ubershader **where all the materials of all assets** are combined into one. For this Ubershader to work the models will be built within constraints.

  - All Models will have clean and unwrapped/clear UV mapping and **only one texture (atlas) per channel (Color, MetallicRoughness, Normal)**. Where possible – it is best to pack all required textures for each separate geometry together. This will help in lowering resource intensity while giving enough flexibility in the creation of appropriate materials to give a high visual fidelity to the model.


![](../../images/image1.jpeg){width="100%"}

- All files belonging to an asset are named the same as the asset, usually suffixed by the LOD and other properties listed in this document. Every word in a file name starts with a capital. Between the model name and the description (LOD) there should be two underscores.


- Example: `Fire Hydrant` ->  
  `Fire_Hydrant__LOD1.glb`,  
  `Fire_Hydrant_Color__LOD1.jpg`,  
  `Fire_Hydrant_Normal__LOD1.jpg`,  
  `Fire_Hydrant_MetallicRoughness__LOD1.jpg`, etc.

- Asset name + LOD suffix (“Fire_Hydrant__LOD1”) is referred to by `<base_name>` in this document.


- **Each asset is placed in a separate directory which will include all LOD’s. See section “Directory structure example”.**


- Assets consist of as few separate geometries/materials as possible. The only reasons for more than one single geometry/material are the following:

## Double-Sided Materials

- **If the asset contains faces that need to be visible from both sides, those faces should be in a separate group and material**

  - Examples: the sail in **“Sailboat_Sails_Up”**, or the window/screen in **“Motorboat”**

  - Counter-example: car windows do not need to be in this group, because we won’t have interior viewpoints

  - The material which belongs to this group should have a suffix **“_doublesided”**

  - If all faces of the asset are visible from both sides, only one group and material is needed, and the material should have the **“_doublesided”** suffix

![](../../images/image5.jpg){width="100%"}

## Fixed Color Materials

- If the term **“Colorable”** is noted in an asset creation list beside a model, it specifies which parts of the asset should be using the main material. All the asset parts that do not fall into that description should use a separate group and material.

  - Background: this split will be used to re-color one part of the model (e.g. the car body) while leaving other parts in the original color (e.g. the car wheels).

  - The additional material should have a suffix **“_fixedcolor”** which stops the color changing.


- Model **“Ford_Fusion”** should consist of two geometries and materials:
  - The first group contains the car body, and its material is called **“Ford_Fusion”**
  - The second group contains wheels, windows, lamps, antenna, license plates, grille and mirrors. Its material is called **“Ford_Fusion_fixedcolor”**


- Model **“Mailbox”** should consist of two groups and materials:
  - The first group contains the box and flag, and its material is called **“Mailbox”**
  - The second group contains the post. Its material is called **“Mailbox_fixedcolor”**

![](../../images/image7.jpg){width="100%"}

## Colorable: All

- If **“Colorable”** reads **“All”**, then no additional geometries/materials should be created. A good example of this is the **Fire Hydrant**.

## Combined: Double-Sided + FixedColor

- Combinations of the two previous categories are possible. In this case, the **“_doublesided”** suffix should precede the **“_fixedcolor”** suffix.

- Model **“Eurocopter_H125_Flying”** should consist of three geometries and materials:

  - First geometry: helicopter body → **“Eurocopter_H125_Flying”**

  - Second geometry: windows, wheels, engine interior → **“Eurocopter_H125_Flying_fixedcolor”**

  - Rotor blade (visible from both sides + not recolored) → **“Eurocopter_H125_Flying_doublesided_fixedcolor”**

![](../../images/image8.jpg){width="100%"}

**Material Name**: Eurocopter_H125_Flying_doublesided_fixedcolor  
**Material Name**: Eurocopter_H125_Flying  
**Material Name**: Eurocopter_H125_Flying_fixedcolor


- Model **“Sailboat_Sails_Up”** should consist of three geometries and materials:

  - First geometry: boat body → **“Sailboat_Sails_Up”**

  - Second geometry: masts and deck → **“Sailboat_Sails_Up_fixedcolor”**

  - Sail: visible from both sides → **“Sailboat_Sails_Up_doublesided”**

![](../../images/image9.jpg){width="100%"}

**Material Name**: Sailboat_Sails_Up_doublesided  
**Material Name**: Sailboat_Sails_Up_fixedcolor  
**Material Name**: Sailboat_Sails_Up

## Merged Versions

- Assets which contain more than one geometry/material are delivered in two versions:

  - One with multiple geometries/materials
  - One where all geometries are merged into a minimal amount of usable and editable geometries

- The merged version is placed in a subfolder called **Merged**, which contains a copy of all needed resources (does not reference the parent folder). See section “Directory structure example”.

![](../../images/image10.jpg){width="100%"}

## Mesh and Material Name Consistency

- **An asset’s mesh and its representative material should have the same name.**

**Mesh Name**: Bulb__Emission  
**Material Name**: Bulb__Emission  

**Mesh Name**: Shade_Inner__Metal_Simple  
**Material Name**: Shade_Inner__Metal_Simple  

**Mesh Name**: Cable__Plastic_Simple  
**Material Name**: Cable__Plastic_Simple  

**Mesh Name**: Main__Metal_Simple  
**Material Name**: Main__Metal_Simple

## Future Naming Considerations

In the future there will be consideration to include double spacing and appropriate capitalization for suffixes like **‘_fixedcolor’** and **‘_doublesided’**: They would become **‘__FixedColor’** and **‘__DoubleSided’** in newer models. Legacy models will retain their original naming conventions.
