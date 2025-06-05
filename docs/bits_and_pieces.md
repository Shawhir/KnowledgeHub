

INDEX

*A collection of all the useful but potentially out of scope details for
the artists, developers and anyone else involved in the creation of the
glbs.*

# Legacy Material and Model Notes:

The notes on this section raises a few other points on Legacy meshes
that you may or may not know but I think are worth bringing up. .

- Their mesh and material names sometimes use different cap cases than
  what has been used in the Furniture models. I think this has appears
  elsewhere also (perhaps with a bunch of tree types) and there may be
  confusion over this inconsistency. This has been mentioned before and
  is best tackling as we go.

- Although materials are separate in these models – they don’t appear to
  have accessibly separate and relatable groups (though I’ve only looked
  at the glbs – so perhaps they were compressed in some way). If we
  wanted to animate something – like the wheels of a car – these will
  need separated and their pivots appropriately set up.

- I believe if Ankara ever finds themselves updating these older models
  (from Standard to PBR) – it could be worth reviewing each Webstyle
  type appropriately and finding suitable naming conventions for each
  group and material.

- If we were to go back and correct assets, we would need to decide as
  to how much we would want to break down a particular asset. For
  example we could break a car into the following (Chasis, Body/Main,
  Windows, Plastic Frames, Tyres, Metals, Textures). This would give
  much more control over appearances of assets – creating a potentially
  more realistic world. However do we want to do this?

# CE Directory Naming 

This section feels specific to Furniture Rules, but I thought it best to
keep it in here in the case there is some benefit or brings up something
useful that I cannot see.

When creating the directory for CE – it is best noted that full file
paths are indeed still limited to ~256 characters on Windows 10. So to
alleviate the chances of a file from being unreadable – we want to
minimise the amount of characters in a glTFs entire address.

What we suggest is to be as sparing as possible with words – using each
folder to direct the path to the next folder – but trying to minimise
repetition of words along the way.

The flow in CE follows the following address rule: **Users \> User
Address \> Documents \> CityEngine \> Workspace Name \> Project Name \>
Assets \> Directory Name \> Directory Group Name \> Directory Sub Group
\> Directory**

We can minimize the character count in the directory name folder name
and it’s children. Short folder names are important but keep them
descriptive and to the point. Classify them. However we try not to
repeat words.

C:\Users\user001\Documents\CityEngine\Zurich_Office\Example_Esri_Zurich_Office\assets\Furniture\Lighting\Desk_Lamp\Herman_Miller\_\_Holly_Flute_Personal_Light\_\_Herman_Miller.glb

Furniture has it’s own set of rules so the file names were quite
descriptive. Within furniture some elements are generic and follow the
same flow. What we need to ask is does this rule for file structures
change per Directory type?

It would make sense to me that it would – trees aren’t made by a brand
or provided by a particular company in this context – so this additional
information would be a waste of time.

However if we were using Furniture, actual car brands, branded material
types or outdoor elements – perhaps this is where it is useful.

Buildings, outdoor stationary or anything considered generic and hasn’t
got it’s image owned by a company will tend to have a shorter address.
But we have to consider – if only one object in a directory has a
licensed object – and it’s name is treated appropriately – then it’s
name type would potentially have an effect on the other names on the
directory.

**So each directory has to hold less than 256 characters in its entire
address**

**Branded groups like furniture tend to have longer addresses**

**Generic groups tend to have shorter addresses – and there appears to
be more of these directory types.**

**For consistency these addresses could have the same flow as their
counterparts in the repository.**

# Product Use

This section is a quick review to give an understanding of how the glbs
are/ could be used throughout different products in ESRI.

# SceneViewer

- Sceneviewer tends to be the tool that uses the glbs to their full
  potential.

- Ellipsoids within the metadata tend to be used to to create realtime
  AO. -VEGETATION

- Camera distances are included to switch between LODs.

- This could / will likely be used in future for animations – whether on
  dynamic shaders or using transforms on different meshes within the
  model.

- The PBR Textures and upgraded Models will be most noticed here.

# CityEngine

- CityEngine uses the models primarily within their Procedural Rules by
  accessing them using their addresses in the file structure. Think of
  it as simply using a library model within a scene.

- No metadata from the glTF model will be currently used.

# Unreal

- GLBS aren’t generally used in Unreal. Before Unreal 4.7, the glbs that
  came out of CE didn’t tend to port correctly and gave the right
  normals.

- The older glb models in the ESRI.lib weren’t of a decent quality for
  Unreal.

- Datasmith is what tends to be used to port visual data from CE to
  Unreal. It tends to work easier and hold more information.

- However now that glbs can port across properly the models may be used
  for mid ground or background models. This is due to the new glbs being
  PBR and having a higher quality to them.

- Models that are used for close up in Unreal (Hero models) tend to come
  from the Unreal market place or are a more high quality bespoke model,
  treated with its own material.
