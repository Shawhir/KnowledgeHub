
# Materials and Textures 

### General Overview
This Spec generalises the 3D models appearances, so after, each category
(vegetation, transportation, etc) will get their own additional
specification. So for now use this as an overall guide.

- Material names follow \<base_name\>, plus suffixes as described in the
  section **“Asset Structure”.**

- Do not use real logos or branding on any model

- All map types will use same UV Set.

- Texture maps are optional maps which can be further specified as
  necessary by category.

- Each asset can have at maximum one color texture map

  - Filename: \<base_name\>\_\_Color.jpg **or .png if it contains an
    alpha.**

  - If the model is uni-colored, the color should be set via material
    and no color texture map should be present.

  - If present, this texture map should be referenced in the material
    (which will be further specified by category)

  - File format:

    - If transparency is needed: PNG. Use lossy PNG techniques (e.g.
      <https://pngquant.org/>) to reduce file size appropriately

    - Otherwise: JPEG, 85% quality

- Don’t apply any color profiles - SRGB color space

- Leave adequate spacing between texture patches in order to not clash
  with texture wrap or mipmapping effects.

- Fill nearest color in also in transparent pixels i.e.:


<div style="text-align: center;">
  <img src="../images/image20.png" style="width: 80%;" />
</div>


- We will use PBR materials, specifically the MetallicRoughness
  workflow. Broken down into each category the following sections can
  make up the material through textures, factors and RGB values :

  - ### Color and Opacity
    - ***color, colormap, opacity, opacitymap:***
    - ***pbrMetallicRoughness.baseColorFactor (RGB or RGBA components)
    and/or pbrMetallicRoughness.baseColorTexture (RGB or RGBA
    components)***

  - ### Alpha Mode
    - ***(optional) opacitymap.mode, opacitymap.cutoff:***
    - ***alpha Mode***
    - ***alphaCutoff if alphaMode=mask***

  - ### Metallic
    - ***metallic, metallicmap:***
    - ***pbrMetallicRoughness.metallicFactor and/or
    pbrMetallicRoughness.metallicRoughnessTexture (B channel)***

  - ### Roughness
    - ***roughness, roughness map:***
    - ***pbrMetallicRoughness.roughnessFactor and/or
    pbrMetallicRoughness.metallicRoughnessTexture (G channel)***

  - ### Occlusion
    - ***(optional) occlusionmap***
    - ***pbrMetallicRoughness.metallicRoughnessTexture (R channel)***

  - ### Normal
    - ***(optional) normalmap :***
    - ***normalTexture***

  - ### Emission
    - ***(optional) emissive, emissive map***
    - ***emmisiveFactor and/or emissiveTexture***
