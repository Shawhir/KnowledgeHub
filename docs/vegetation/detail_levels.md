

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

### Tri Counts

- Do keep in mind that the complexities of tri counts for each LOD may change depending on the type of asset it is.  For example – organic vegetation trees would have different LOD tri values in comparison to Transportation vehicles.  Use these values as a heuristic to approximate with and build with less where possible

- Triangle counts should count triangles, not polygons as polygons equal 2 or more tris and will give a misleading and underestimated count – meaning that the tri count would be higher than anticipated.

<div style="text-align: center;">
  <img src="../../images/image19.png" style="width: 75%;" />
</div>