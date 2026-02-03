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

More tutorials will be added over time (e.g. basic Blender→glTF export, SpeedTree QA workflows, Flexi Textures authoring, etc.).
