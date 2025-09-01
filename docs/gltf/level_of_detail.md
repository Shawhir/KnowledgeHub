

# Level Of Detail (LOD)

As many projects using the ESRI software tend to use numerous amounts of
meshes, it is important that we use LODs to improve it’s performance on
many systems by reducing demand on the workload of the system. Each LOD
lowers polygon counts whose details aren't visible at a given distance.
This keeps performance on many systems running smoothly. LODs can be
also incorporated to give lower texture map sizes and/or less intensive
shaders depending on the LOD version that are being used.

### Different map sizes for each LOD

- For each LOD it should be noted that different map sizes and different
  accumulation of maps will be used.

- A rule of thumb is – the less detail a model has – the smaller the
  maps on its shader will be.

- This again comes down to the balance of quality over resources - where
  we smartly allocate different map sizes to the shaders’ assets in the
  scene so our FPS ultimately stays as smooth and as user friendly as
  possible.

- **The only exception to this rule is the ColorOpacity Map for LOD0
  which will be bigger than the LOD1. This will be explained further
  below.**

- All texture sizes must be powers of 2 (i.e. 64, 128, 256, 512,
  1024, 2048) and Squared unless further specified by category

- A good safety capture for all maps is to prepare them as a bigger size
  and keep that file saved. They can always be downsized afterwards.
  **4096 x 4096 is recommended as a back up and to future prepare the
  glb assets.**

### **ColorOpacity Map Size**

- LOD0: 512x512

- LOD1: 256x256

- LOD2: 512x512

- LOD3: 2048x2048

### **MetallicRoughness Map Size**

- This in general is smaller than the colormap, as a rule of thumb it
  can be half the size.

### **Normalmap Map Size**

- This in general stays the same size as the colormap.

### **Emissivemap Map Size**

- This in general is smaller than colormap, as a rule of thumb it can be
  half the size but it’s worth testing it out at a quarter of the
  colormap’s size if the emission has a lack of detail.


<div style="text-align: center;">
  <img src="../../images/image39.png" style="width: 60%;" />
</div>

### **LOD 0 Map Sizes**

- This map is a little special compared to the larger LODS. **LOD 0
  works as a billboard, meaning the object is made up of a collection of
  planes that capture the image of that viewpoint of the model.**

- This tends to be used at a further distance so the detail isn’t ever
  as defined as something up close.

- However it is worth noting why the LOD 0 UV dimensions are higher than
  LOD1. LOD 1 can have the luxury of reusing texture islands on an asset
  (for example a specific branch on a UV map can be used many times).

- LOD 0 has to take an entire (or substantial) picture of the object,
  taking up more space on the texture map. This means a smaller UV
  dimension can be for the LOD 1 but a larger UV tends to be required
  for the LOD 0 to look presentable.

