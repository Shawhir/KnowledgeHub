# Tutorials

This section collects practical, step-by-step workflows that apply the standards
and conventions described elsewhere in the **3D Visual Standards Hub**.

---

## Available Tutorials

### 1. Blender Scene Cleanup (Pompeii Reconstruction → Web-Ready glb)

**Goal:**  
Take a heavy reconstruction scene in Blender (e.g. a Pompeii temple), clean it up,
and reduce the file size so that it runs smoothly in **JSAPI / Web Scene Viewer**
and remains compatible with Esri’s glTF standards.

**What you’ll learn:**

- How to spot and fix **z-fighting** and duplicated geometry  
- How to use a simple **Python script** to shrink all textures to a target resolution  
- How to add and tune **Decimate** modifiers safely  
- How to clean up hierarchy, set a correct **pivot at world origin**, and export a **glb**

→ [Open the tutorial](blender_scene_cleanup.md)

---

### 2. Cities at Night (OSM Data → Stylised Night Cityscape → Web Scene)

**Goal:**  
Take OSM parcel data for a real urban area, generate a stylised low-poly night cityscape in CityEngine using procedural CGA rules and emissive materials, and publish it as a performant Web Scene using the Glow effect.

**What you'll learn:**

- How to structure a CGA rule to drive building height from OSM attributes with fallback logic  
- How to use probabilistic material assignment and UV randomisation to break facade repetition  
- How to identify and resolve z-fighting caused by overlapping shapes using Python scripting in CE  
- How to balance emissive texture file size against visual quality for Web performance  
- How the Glow effect can be applied meaningfully across different viewing scales  

→ [Open the tutorial](cities_at_night.md)

---

More tutorials will be added over time (e.g. basic Blender→glTF export, SpeedTree QA workflows, Flexi Textures authoring, etc.).
