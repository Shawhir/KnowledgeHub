# Texture Files
- The texture files that work with the assets to give the best version
  of them are all part of the PBR, MetallicRoughness workflow.

- PBR strives to mimic the flow of light on objects in the real world;
  giving a more realistic impression of the digital asset.

- A general heuristic is to blend map types together where possible – so
  to be less resource intensive.

Since the previous assets were built with Standard shaders here is a
quick run through of naming conventions with **some further detail on
Colormap/Opacitymaps and MetallicRoughness/
MetallicRoughnessOcclusionmaps:**

### Colormap/ Opacitymap

- Colormap/opacitymap for pbrMetallicRoughness.baseColorTexture (RGB or
  RGBA)

<div style="text-align: center;">
  <img src="../images/image28.png" style="width: 75%;" />
</div>
  
- Color Maps can be used with or without Opacity Maps. If Color Maps do not use Opacity maps then
  jpgs will work best for saving disk space.

- If Color Maps use Opacity Maps then the alpha is combined into the RGB
  layer directly or as a mask. This would be saved as a 32 bit png.

<div style="text-align: center;">
  <img src="../images/image29.png" style="width: 75%;" />
</div>

---

## Normalmap

- Normal maps simulate surface detail without extra geometry, using RGB to encode direction (X = R, Y = G, Z = B).

<div style="text-align: center;">
  <img src="../images/image42.png" style="width: 75%;" />
</div>

- Above you can see the left normal - correctly using OpenGL compared to the Right and inverted normal, that uses DirectX.

<div style="text-align: center;">

<table>
  <thead>
    <tr>
      <th>Convention</th>
      <th>Y (Green) Direction</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>OpenGL</strong></td>
      <td>Up (+Y)</td>
    </tr>
    <tr>
      <td><strong>DirectX</strong></td>
      <td>Down (–Y)</td>
    </tr>
  </tbody>
</table>

</div>

We use **OpenGL** as our standard because it's compatible with **glTF**, **WebGL**, and most of our tools. It also avoids extra shader logic for those tools.

## Normalmap Best Practices

- **Stick to OpenGL format** — flip the green channel if converting from DirectX.
- **Compression-sensitive** — Normal maps are sensitive to JPEG compression, especially on the web. Flat areas (like cladding) should remain a **single color** to avoid banding.
- **Dithering** — Subtle noise can reduce banding but must be **visually checked** per product.
- **Use strategically** — Cladding often benefits from minimal normals. Organic surfaces (e.g. pebbles) can gain more realism from detailed normals.
- Unreal uses DirectX normals by default. This will be rechecked again soon and updated accordingly.

---

## MetallicRoughness

- (Optional) Metallic roughness map for
  pbrMetallicRoughness.metallicRoughnessTexture


- MetallicRoughness maps affect how reflection values work along with the accompanying
  Colormap Color value (RGB). This is used to mimic real world reflections on metallic, plastic or any surface in-between.

  <div style="text-align: center;">
  <img src="../images/image31.png" style="width: 75%;" />
</div>

- Above you can see a round table with a simple color, a MetallicRoughness
  texture with a high metallic value and ranging and patterned roughness texture which contributes to the anisotropic surface.

  <div style="text-align: center;">
  <img src="../images/image32.png" style="width: 75%;" />
</div>

- The wooden table above shows the blend between a more complicated
  Colormap and MetallicRoughness texture with a mixed Roughness value
  and little Metallic value.

- When creating maps for Metallic, Roughness or (if required) Occlusion
  – they tend to be packed together in the same image but using separate
  RGB channels.

- This is very useful for saving on texture space when loading an asset
  for use. For example: below you can see the RGB channels used to
  depict the Occlusion, Metallic and Roughness. Each channel portrays
  their color in grayscale before blending them together as one large
  RGB.

  <div style="text-align: center;">
  <img src="../images/image33.png" style="width: 75%;" />
</div>

  <div style="text-align: center;">
  <img src="../images/image35.png" style="width: 75%;" />
</div>

  <div style="text-align: center;">
  <img src="../images/image37.png" style="width: 75%;" />
</div>


- The final example shows MetallicRoughness and Occlusion textures
  working together from one map.

- Do note how Occlusion is used above as an example – where it is
  darkened on the R channel – that part appears more subdued.

---

## **Occlusion (Beta)**

<img src="../images/image38.jpeg" style="width:6.26806in;height:3.52569in"
alt="C4D: Optimize Ambient Occlusion Renders in Cinema 4D - Toolfarm" />

- Ambient occlusion (AO) is a shading and rendering technique that can
  be baked onto a UV Map or used as a post processing technique (SSAO).

- It is used to calculate how exposed each point in a scene is to
  ambient lighting; meaning – tight corners are darker and more open
  areas are lighter.

- You can see in the example above the effect of AO around the window
  frames, doorframes and where the buildings touch the street. This
  example is also excellent in displaying how AO can be used by blending
  with Colormaps to ground objects more solidly in an environment.

- Although AO tends not to be used in our models and may not be
  obligatory for our glTF examples as our AO can be calculated in
  real-time using a technique like SSAO – it is good to be aware of its
  existence and how it can be used should it become a solution to a
  problem.

---

## Colormap/ Opacitymap Naming

- \*Name\*\_Color\_\_LOD\*Number\*.jpg for color only

- \*Name\*\_ColorOpacity\_\_LOD\*Number\*.png for color which contains transparency

## **MetallicRoughness / Occlusion Naming (Optional)**

- \*Name\*\_ MetallicRoughness\_\_LOD\*Number\*.jpg

- \*Name\*\_ MetallicRoughnessOcclusion\_\_LOD\*Number\*.jpg for
  MetallicRoughness which contains Occlusion in it’s R channel

## **Normal Naming (Optional)**

- \*Name\*\_ Normal\_\_LOD\*Number\*.jpg

## **Emissive Naming (Optional)**

- \*Name\*\_ Emissive\_\_LOD\*Number\*.jpg

---

## **BasisU Compression**

To ensure the best balance of **visual fidelity**, **performance**, and **cross-platform compatibility**, we are standardizing on **Basis Universal (BasisU)** for texture compression.
BasisU compression should only be performed **as the final step** in the pipeline — **after all texture editing and QA is complete**.  
Source textures (PNG / JPG) must always be preserved for future edits.

---

## Why BasisU?

- **Universal GPU support** → BasisU can be transcoded at runtime to native GPU formats (BCn, ASTC, ETC), ensuring broad compatibility across **WebGL**, **Scene Viewer**, **mobile**, **desktop**, and **Unreal**.
- **Drastically reduced file sizes** → enabling **faster loading** and **lower memory usage** in large-scale 3D scenes.
- **Modern standard** → Scene Viewer, glTF, and industry tools increasingly support **BasisU → KTX2** pipeline.
- **Supports LOD workflows** → compressed textures remain efficient even across multiple LODs and variants.

---

## Current Tools

[David Koerner](mailto:dkoerner@esri.com) has developed a robust **glTF Tool** (Python command-line scripts) that automates:

- **Packing of all LODs** into a single glTF asset
- **Preparation for BasisU compression**  

Tool reference: [Prototype Webstyle Publishing – Build Scripts](https://devtopia.esri.com/davi9752/prototype-webstyle-publishing/tree/main/build-scripts)

---

## Pipeline Guidance

- Artists deliver **standard PBR textures** (Color, MetallicRoughness, Normal, Emissive) in **PNG / JPG** at required LOD sizes.
- QA and visual review occur using **uncompressed textures**.
- **BasisU compression is applied last**, using validated settings per product.
- Current target: **BasisU → KTX2** pipeline, optimized for Scene Viewer and other Esri 3D clients.

---

As adoption progresses, **detailed settings** (e.g. BasisU UASTC vs BasisLZ, quality tuning per texture type) will be documented here to ensure **consistent high quality** across the entire 3D product stack.
