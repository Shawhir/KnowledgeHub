# Texture Sizing Guide



Textures are generally split into two General groups, patterned materials and organic materials.  Each must be approached differently by the creator who aims to effectively balance quality and performance.  


Patterned Materials
Ironically these can hide the tiling easier compared to organic objects due to repetition.  It is the subtle change of texture in each repeating object that adds to the realism and at the same time hides the tiling.  Look for breaks if the colors are too contrasting inside one object. 

<div style="text-align: center;">

&nbsp; <img src="../../images/image58.jpg" style="width: 100%;" />

</div>
 
o	Color: 2048px
o	Normal: 1024px
o	MetallicRoughness: 512px
o	Consider if normals or MR can be scaled up to a smaller but not singular area, like in the image above – note the number of objects for NRM and MR being different than Color.
o	They can be scaled differently to color to improve quality on the Normal and MR channels while keeping overall size down.

Organic Materials
Due to the randomness in organic materials and the limitations for material creation in CE, their tiling can be harder to hide.  This is mitigated by creating a larger tilable texture in any 3D DCC, up to 5 - 10m to minimise tiling. Minimising the color variation that is used on the texture works too, the fewer colors used, the easier the tiling is to hide.  How-ever, the most obvious and perhaps most overlooked part of tiling problems on organic shape is a cut in the seamlessness.  If the patches of grass, wood grain or rock size, pebble color etc. don't match when blending with the other side – then this can break the frail illusion that we are already working within.

<div style="text-align: center;">

&nbsp; <img src="../../images/image59.jpg" style="width: 100%;" />

</div>

 
o	Color: 2048px
o	Normal: 1024px
o	MetallicRoughness: 512px
o	Note: These cannot be as easily scaled to repeat with their normals and MR texture maps – obvious repetition in organic shapes normal maps show up too easily.  How-ever, minimising detail in their MR texture or using a roughness factor can work if the rocks are clean, smooth, or not a lot of detail is being shown. I do advise that if MR can be used as a texture to hint at some more detail – then it should be used.




<div style="text-align: center;">

&nbsp; <img src="../../images/image59.jpg" style="width: 100%;" />

</div>





In some circumstances – the heuristic may not need to be so rigid if the same quality can be gained for less (using a roughness factor value instead of roughnessmap).  This will overall mean preparing for  better performance on the most limited devices used whilst being forward facing to improvements in memory management and rendering.  



