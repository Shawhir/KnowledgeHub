

# Material and Group names 

## New Models

To give the user access so to change groups and their corresponding
materials, their names are initially matching so to be easier to access
and if desired, to edit. Excluding the inclusion of an “\_\_LODx” in the
group or material name, a double underscore is used so to easily parse
the name and access it’s material type through code or .cga rule. In
this instance “Crown__doublesided” – which can be set up to give users
access to a this material in its own library – **potentially to reside
in ESRI Lib.**

We have different examples below to indicate as to how this would work
depending on how many groups an asset has:

If an asset has only one group, it is named with the keyword
**Complete** unless it is part of a key asset type **(like Seating or
Tables):**

   > “Rock **Asset**",  
   > “Rock **Group Name**” -\> Complete_Stone,  
   > “Rock **Material Name**” -\> Complete_Stone


![](../../images/image50.jpg){width="100%"}

If an asset has more than one group, its’ keywords are broken down to Crown for the leaves and/or flowers and Trunk for the main trunk and branches. 

Main Example:

> “Khaya_Sengalensis **Asset**",  
> “Khaya_Sengalensis **Group** One Name" -\> Crown__ doublesided,  
> “Khaya_Sengalensis **Material** One Name" -\> Crown__ doublesided,  
> “Khaya_Sengalensis **Group** Two Name" -\> Trunk__fixedcolor,  
> “Khaya_Sengalensis **Material** Two Name" -\> Trunk__fixedcolor


![](../../images/image51.jpg){width="100%"}

**We can place an asset with three groups in here if needed – such as a tree with fruits or seeds – to explain this addition if we decide to include it.

NEED TO CONSIDER BILLBOARD NAMING HERE:  If texture is changed for one LOD it must be changed for all of them. Call them Imposter
**:

![](../../images/image52.jpg){width="100%"}


## Legacy Models

As the approach of the suggested pipeline is to improve on what has came before, here is a quick analysis of the realistic vegetation Webstyles.

- The trees here are look quite uniform and hold a decent consistency between their LODs 
- These trees do not look so good close up due to textures trying to condense so much visual data into such a small size. 
- A positive is the realistic trees look great and full mid ground and far away – suggesting a healthy crown
- The normals and planes are large and noticeable from a distance.  This could look better
- Their measurements for tris, file size and textures are all small and in turn work well on all devices.
- Realistic leaves have a lot of empty space, this could be used better
- They are set up with invisible bleeds so they do not dissappear in SV
- The larger textures have more detail but at a small size so close ups are not great.
- The trunk could of been at least reused as a separate texture

![](../../images/image53.jpg){width="100%"}
