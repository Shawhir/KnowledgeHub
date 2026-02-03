

# Level Of Detail (LOD)

- As we build vegetation – it is good to flag some points so to know how to approach the building of specific objects and how much detail should be added.

- As you are building Assets it’s good to reflect that these are classified into 4 different complexities: extreme simple, simple, standard, and complex.  

- Each of these complexities will be provided at 4 different levels of details, in separate gltf files:
	- LOD3: high resolution
	- LOD2: medium resolution
	- LOD1: low resolution
	- LOD0: imposter / billboards
	- These LODs will have different tri counts depending on complexity. 

<div style="text-align: center;">
  <img src="../../images/image14.jpeg" style="width: 100%;" />
</div>

### Use Case Considerations

Esri products are an ecosystem and our assets are used in different ways throughout.  We have to consider the importance of our assets running in Web Mobile and Desktop (Weakest) to Unreal (Strongest).

Generally, the vegetation is seen from a distance, think birds eye view so this shifts the importance to well made LOD0 and LOD1 models with low tri counts and compromised, low resolution textures.  These models are only displayed as small to tiny assets, so we remove the unnecessary detail.

However we cannot underplay the importance of LOD2 and LOD3.  They have an importance on representing vegetation on street level, something used cross product but has a growing importance.  These are a stronger representation of the Vegetation but need cut off points in regards to what maps are used on them and how much detail we display.

So, Primary Importance is given to the Crown and Secondary importance to the Trunk.  Granted users may want to parse the data to show only the Trunk (think dead version of the tree or Winter scenes) so a trunk has to represent it's species.




### Asset Vegetation Complexity Analysis

To initially understand the suggested complexity of each  asset, specifically for vegetation, look at the Tri Breakdown Guide and compare the color to the Vegetation Asset Type Chart.  Currently this works as an educated guess from the previous Realistic Tree Assets to choose the tri count for each tree type.  Flowering and Fruiting are included as a suggestion.

<div style="text-align: center;">
  <img src="../../images/image48.jpg" style="width: 100%;" />
</div>

Complexity is based on visual detail and tri count targets. Simple trees have minimal foliage detail, Standard trees have moderate detail, and Complex trees have dense foliage, multiple materials, or intricate geometry.

<div style="text-align: center;">
  <img src="../../images/image49.jpg" style="width: 100%;" />
</div>

Colors represent the recommended complexity for each vegetation type in different seasonal states or growth stages.

Note: Discretion is advised when determining tree complexity. If the desired visual quality can be achieved with fewer polygons, it is recommended to do so. Lower complexity not only optimizes memory usage but also improves overall performance and user experience.


### Vegetation Categories – Asset Guidance (System-Focused)

The following guidance applies specifically to the vegetation categories used in our asset library.
Each category differs structurally and therefore requires different LOD, tri distribution, and visual priorities.

Primary rule across all categories:
- Crown readability comes first. Trunk fidelity is secondary but must remain species-recognisable.

#### Broadleaf Trees

<div style="text-align: center;">
  <img src="../../images/image60.jpg" style="width: 100%;" />
</div>


Examples: Frangular alnus, Juglans regia, Salix alba, Quercus spp., Acer spp.

##### What are the characteristics of a Broadleaf:

- Flowering trees with complex, irregular crowns

- Branching structure varies heavily by species

- Leaves are broad and visually dominant

##### What visually matters most:

- Crown volume and silhouette

- Leaf mass distribution (not individual leaves at distance)

- Species-specific trunk character (especially for winter / dead states)

##### LOD priorities

<div style="text-align: center;">
  <img src="../../images/image61.jpg" style="width: 100%;" />
</div>


##### Tri distribution

- Majority of tris in the crown

- Minimal trunk tris, but:

	-- Correct taper

	-- Recognisable bark breakup for species identity

#### Conifer Trees

<div style="text-align: center;">
  <img src="../../images/image62.jpg" style="width: 100%;" />
</div>

Examples
Abies alba, Picea abies, Pinus sylvestris, Sequoia spp.

##### What are the characteristics of a Conifer:

- Gymnosperms with strong vertical hierarchy

- Central leader with layered branch whorls

- Needle or scale foliage forms continuous masses

##### What visually matters most:

- Overall conical / columnar silhouette

- Layered crown depth

- Trunk readability at mid to close range

##### LOD priorities

<div style="text-align: center;">
  <img src="../../images/image63.jpg" style="width: 100%;" />
</div>


##### Tri distribution

- Crown remains primary

- Low Tri Count on Crown Leaves when required.

- Trunk slightly more important than broadleaf trunks

- Bark detail should remain restrained

#### Shrubs / Small Woody Plants

<div style="text-align: center;">
  <img src="../../images/image64.jpg" style="width: 100%;" />
</div>


Examples
Buxus Sempervirens, Rhododendron Tsutsuji, RhamnusAlaternus

##### What are the characteristics of a Shrub:

- Woody plants without a dominant trunk

- Multiple stems from the base

- Crown begins near ground level

##### What visually matters most:

- Overall mass and footprint

- Ground contact and base density

- Species-typical bushiness

##### LOD priorities

<div style="text-align: center;">
  <img src="../../images/image65.jpg" style="width: 100%;" />
</div>

##### Tri distribution

- Mostly crown/mass

- Minimal stem geometry

- Do not over-model internal structure

### Palms

<div style="text-align: center;">
  <img src="../../images/image66.jpg" style="width: 100%;" />
</div>

Examples
Cocos nucifera, Phoenix dactylifera, Washingtonia spp.

##### What are the characteristics of a Palm:

- Monocots (not true woody trees)

- Unbranched trunk

- Crown consists entirely of fronds

##### What matters most

- Frond shape and orientation

- Clear crown silhouette

- Correct trunk proportions (constant diameter)

##### LOD priorities

<div style="text-align: center;">
  <img src="../../images/image67.jpg" style="width: 100%;" />
</div>

##### Tri distribution

- Almost all tris in the leaves

- Trunk extremely cheap

- Fruits optional, only if visually significant

### Succulents / SXerophytes

<div style="text-align: center;">
  <img src="../../images/image68.jpg" style="width: 100%;" />
</div>

Examples
Agave spp., Opuntia spp., Yucca spp., Carnegiea spp.

##### What are the characteristics of a Succulent:

- Water-storage plants

- Often mistaken for trees but do not follow tree logic

- Growth is mass-based, not branch-based

##### What visually matters most:

- Primary form and volume

- Surface silhouette

- Material response (normal + roughness)

##### LOD priorities

<div style="text-align: center;">
  <img src="../../images/image69.jpg" style="width: 100%;" />
</div>


##### Tri distribution

- Even distribution across main body

- No internal structure


### Cross-Category Rules (Important)

- LOD0 and LOD1 are the most important LODs for Esri products

- Interior detail is almost always wasted

- If a species reads correctly with fewer triangles:

	- Use fewer triangles

- Hair, fuzz, fibers, and micro-geometry:

	- Hero assets only (LOD4 / special cases)

##### Why this matters

- Our vegetation assets must:

	- Work across Web, Mobile, Desktop, and Unreal

	- Scale visually from bird’s-eye to street-level

	- Remain procedurally manageable and performant

- These categories exist because they require different assumptions.
- Treating them the same leads to:

	- Wasted tris

	- Broken LODs

	- Poor visual consistency across products



Note: Discretion is advised when determining tree complexity. If the desired visual quality can be achieved with fewer polygons, it is recommended to do so. Lower complexity not only optimizes memory usage but also improves overall performance and user experience.
Anything with hair etc should be kept for LOD4/Hero as there is a place for this.




### Tri Counts

- Do keep in mind that the complexities of tri counts for each LOD may change depending on the type of asset it is.  For example – organic vegetation trees would have different LOD tri values in comparison to Transportation vehicles.  Use these values as a heuristic to approximate with and build with less where possible

- Triangle counts should count triangles, not polygons as polygons equal 2 or more tris and will give a misleading and underestimated count – meaning that the tri count would be higher than anticipated.

<div style="text-align: center;">
  <img src="../../images/image19.png" style="width: 75%;" />
</div>