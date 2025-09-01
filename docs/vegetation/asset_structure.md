# Asset Structure

## Overview

- A rule of thumb at ESRI is to **build our assets as economically as possible**. These models are used in many different products – from the intensive Unreal to the more frugal Web products, so it is best to build assets that are workable for all our products. We have built an Ubershader **where all the materials of all assets** are combined into one. For this Ubershader to work the models will be built within constraints.

  - All Models will have clean and unwrapped/clear UV mapping  and only one texture (atlas) per channel (Color, Alpha, MetallicRoughness, Normal).  Where possible – it is best to pack all required textures for each separate geometry together.  For example:  All leaves are under the same Object name “Crown” and the branches and trunk are under the name “Trunk”.  This will help in lowering resource intensity while giving a enough flexibility in the creation of appropriate materials to give a high visual fidelity to the model.


![](../../images/image43.png){width="100%"}

- All files belonging to an asset are named the same as the asset, usually suffixed by the LOD and other properties listed in this document.  Every word in a file name starts with a capital.
Between the model name and the description (LOD) there should be two underscores.


- Example: `Samanea_Saman` → `Samanea_Saman.glb`<br>
  `Samanea_Saman__LOD1.glb`<br>
  `Samanea_Saman_Color__LOD1.jpg`<br>
  `Samanea_Saman_Normal__LOD1.jpg`<br>
  `Samanea_Saman_Alpha__LOD1.jpg`

- Asset name + LOD suffix (“Samanea_Saman__LOD1” in the above example) is referred to by`<base_name>` in this document.


- **Each asset is placed in a separate directory which will include all LOD’s. See section “Directory structure example”.**


- Assets consist of as few separate geometries/materials as possible. The only reasons for more than one single geometry/material are the following:

## Flowers and Fruit

- **If there is a consideration to have fruits or flowers contained in the assets alongside the leaves**
  - Examples: a tree with fruits in “Samanea_Saman_Adult_Summer_Fruits”.

![](../../images/image44.png){width="100%"}


## Double-Sided Materials

- **For when the asset geometry is made up of leaves or the crown**

  - The material which belongs to this group should have a suffix **“_doublesided”**

  - If all faces of the asset are visible from both sides, only one group and material is needed, and the material should have the "_doublesided" suffix

  - Crown can act as the “Colorable” element of the model and therefore be the main material.  This separation could allow the leaves and only the leaves to be colored, potentially affecting it for the seasons.  This would not affect the trunk.

  - All others assets that make up the tree that do not fall into that description should use a separate group or material e.g. Fruits, Flowers.





- **For when the asset geometry is the branch and the trunk**:

  - Background: this split will be used to re-color one part of the model (e.g. the crown) while leaving other parts in the original color (e.g. the trunk).

  - The additional material should have a suffix “_fixedcolor” which stops the color changing.

  - Example: Tree model “Hopea_Odorata” should consist of two geometries and materials.

  	- The first group contains the tree leaves, and its material is called “Crown_doublesided”

	- The second group contains branches and trunk. Its material is called “Trunk_fixedcolor”.

	- May need to consider fruit in this if we decide to go this route.

![](../../images/image45.png){width="100%"}

- As it stands, Tree Assets which contain more than two geometries/materials are delivered in two versions, one with multiple geometries/materials, but placed into their respective layers and one where all geometries are merged into a minimal amount of usable and editable geometries. The second (merged) version of the asset is placed in a subfolder called Merged, which contains a copy of all needed resources (does not reference the parent folder). See section “Directory structure example”.

- An assets’ mesh and its representative material should have the same name. 

- In the future there will be consideration to include the double spacing and appropriate Caps here for labels like ‘_fixedcolor’ and ‘_doublesided’ so they become ‘__FixedColor’ and ‘_DoubleSided’ for each newer model where applicable – with legacy models keeping their original naming conventions.  