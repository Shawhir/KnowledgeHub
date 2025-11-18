# Directory Overview

For our standards to work, a strong directory structure is needed. Additional Materials, stakeholder clarity and benefits to users were considered for accessibility and scalability.

We categorize the Materials into Groups.  For instance the folder Architectural will have Materials that are related to buildings (Walls, Roofing).  These are split into Sub Materials/SMs (Brick, Concrete, Slate Tiles).



Each SM will hold .cgamat(s) and generally a Textures folder.  This holds all the image files that are referenced by the .cgamat.  This cgamat is what we apply to planes or 3D assets to display the related Standard or PBR Shader.



The visual guide can be better understood with the following legend:



* &nbsp;	Blue underlined - Material Folders
* &nbsp;	Orange underlined - Sub Materials / SMs.
* &nbsp;	Red box - .cgamats and Texture Folders
* &nbsp;	Green box - Textures



Use the diagram below to understand the hierarchy.



<div style="text-align: center;">

&nbsp; <img src="../../images/image54.jpg" style="width: 100%;" />

</div>





The directory holds a \*\*Source\*\* folder for each SM.  As each SM was built differently than others, they have different Sub Folder Structures.  Each Source Folder will hold a \*\*Textures\_4096\*\* for quick access to higher quality textures.  The Source Folder is not accessible to the user and is hidden when pushed to Devtopia.



<div style="text-align: center;">

  <img src="../../images/image55.jpg" style="width: 100%;" />

</div>



