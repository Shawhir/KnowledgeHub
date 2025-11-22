So this is a WIP Tutorial going through the steps of how to do a Clean up of a large scene in Blender.  The intention is to give you enough tools to lower the size of the file so it can work on the JSAPI but with consideration for our Esri products too.

## Tutorial Video



<iframe width="800" height="450"
        src="https://www.youtube.com/embed/wrus5ezlJ_E"
        title="Blender Cleanup Tutorial"
        frameborder="0"
        allowfullscreen>
</iframe>


## Quick Tips for Scene Control

Lets start with some quick tips to help to give better control over the scene.

### Frame Selected

First, one of the best tools for navigation is the **Frame Selected** tool.  
It can be found in:

**View > Frame Selected**

This will focus the area you currently have selected.  
For this WIP demo, the menu method is used instead of shortcuts.

### Enable Statistics Overlay

In **Viewport > Overlays**, you will find a useful option called **Statistics**.  
Toggling it on gives you access to mesh counts and other useful data.

### Scene Collection Overview

On the right-hand side, you will find **Scene Collection**.  
Sometimes the objects here will be grouped, sometimes not.

In this project:

- `Container > Reconstruction` holds mostly the Temple  
- `Container > Objects` holds 10 separate assets used to populate the temple  

When one of these containers is hidden, the **triangle counts drop** accordingly.  
For this tutorial, we will focus on **Reconstruction** and keep **Objects** hidden.

### Sub-Objects and Data Structure

As seen in this project, **Reconstruction** contains many sub-objects used to make up the Temple.  
This is useful for controlling the data cleanly - better than having everything packed into one single mesh.

---
## Identifying and Removing Z-Fighting

As I move the viewport, especially with some slight rotation, you will see flickering on the surfaces of the model. These are the areas of interest and should be taken care of. On a model like this, where there isn't a consistent and recognizable flickering problem, I would recommend doing the following two steps:

### 1. Hide Clean Submeshes

Remove clean submeshes incrementally if they are not flickering:

- Select the mesh  
- Press **H** to hide it  
- Press **Alt + H** to unhide all if you hide the wrong mesh  

### 2. Delete Duplicate Surfaces

Delete one of the surfaces that are showing signs of duplication:

- Select the mesh  
- Press **Delete**  
- If the remaining surface is no longer flickering, hide it  

Use **Ctrl + Z** to undo actions if needed.  
Keep an eye on **Scene Collection** and continue hiding or deleting until all issues have been observed.

### Orphaned LOD Tiers

In this scene, it appears there are duplicates or orphaned LOD tiers that are not z-fighting because they are slightly offset. Go through each sub-asset, hiding as you go and treating the process like a game - seeing how many you can safely delete.

### Verify Before Continuing

Press **Alt + H** to unhide all objects.  
Switch back to **Viewport Shading Mode > Material Preview**.

You should see **no visual difference**, but already have a **lower triangle count**.

---

## Reducing File Size: Texture Shrinking

Now the biggest culprit for file sizes are **textures**. This scene has a substantial number of them, but if handled properly, they can drastically reduce overall file size.

Here we will use a script to shrink all textures to **1K resolution**.

### Texture Shrink Script (Paste in Scripting > New)

```python
import bpy

TARGET = 1024  # set your desired resolution

for img in bpy.data.images:
    if img.size[0] == 0 or img.size[1] == 0:
        continue  # skip weird ones

    print("Resizing:", img.name, img.size[:])
    img.scale(TARGET, TARGET)  # force to TARGET x TARGET
    img.pack()                 # embed the smaller version into the .blend
```


## Decimation for Further File Size Reduction

Look at the difference in file size now. Now you could technically stop here for now, but since file size can be a real bottleneck in our products, we will take this further by introducing you to a modifier called **Decimate**.

Select all of the meshes, go back to **Scripting** and add the following script.

### Decimate Modifier Script

```python
import bpy

for obj in bpy.context.selected_objects:
    if obj.type == 'MESH':
        mod = obj.modifiers.new(name="Decimate", type='DECIMATE')
        mod.ratio = 0.5   # set your decimation strength here
```

This adds the Decimate Modifier on Collapse Mode, the default setting and with a strength of 0.5 we cut the mesh size down to half. Lets look at this in a little more detail.

Lets focus on the curtain for a moment, you will see that the decimation does not necessarily break the uvmap if the tri count is in a sweet spot. Consider tweaking the value as well so the model topology looks appropriate. Special note has to be given to the walls, they should have the Decimation turned off otherwise the uv map will break the texture display. Spend your time going through each of these at this point.

## Applying the Modifier

After this the Modifier needs to be applied, otherwise the data for the original will carry through to the glb. Applying the modifier collapses it.

Here is a quick script to run on all the selected meshes.

```python
import bpy

for obj in bpy.context.selected_objects:
    bpy.context.view_layer.objects.active = obj
    for mod in obj.modifiers:
        bpy.ops.object.modifier_apply(modifier=mod.name)
```

Some of the modifiers are not applied in this instance due to them not being unique. You notice them in Scene Collection having a wrench symbol beside the Mesh. Go to the mesh itself and apply the modifier for each by hand.

## Final Cleanup and Combining Meshes

Now you are soon there. The next step is to:

1. Select all meshes  
2. Press **CTRL + J** to combine them  

This makes it easy to control the pivot point.  
Delete any empty nodes in Scene Collection you don’t need and name your mesh names into something more appropriate.

## Setting the Pivot

Selecting the combined mesh:

1. Press **Shift + S > Cursor to World Origin**  
2. Then **Object > Set Origin > Origin to 3D Cursor**  

This will set the pivot at **0,0,0** in world space.

## Exporting the glb

Now final step, export this out as a **glb**.

- Include **Selected Objects**  
- Deselect any unused export factors  
- Change material images to **JPEG** to help lower file size  

You should now see a bigger difference in file size - down to around **25 MB**.

## Final Check

Finally checking the file on the Web, it works well enough without having to do more work on it.

