

# Detail levels

### Overview

- As we build models – it is good to flag some points so to know how to
  approach the building of specific objects and how much detail should
  be added.

- It should be known that models will only be looked at from the outside
  so most of the time they won’t be needed to be built – this should
  help with keeping tri counts lower. Model interiors (e.g. car
  dashboards) should only be modelled to the extent in which they are
  relevant to the outer appearance (e.g. can it be seen through a
  transparent glass) and distance (e.g. the further away the model is –
  the less detail is need for the interior and exterior of the model).

- As you are building Assets it’s good to reflect that these are
  classified into 4 different complexities: ***extreme simple*,
  *simple*, *standard*, and *complex*.**

- Each of these complexities will be provided at 4 different levels of
  details, in separate gltf files:

    - LOD3: high resolution

    - LOD2: medium resolution

    - LOD1: low resolution

    - LOD0: imposter / billboards

  	These LODs will have different tri counts depending on complexity.

<div style="text-align: center;">
  <img src="../../images/image14.jpeg" style="width: 100%;" />
</div>

## Extreme Simple
<div style="text-align: center;">
  <img src="../../images/image15.png" style="width: 75%;" />
</div>


- Extreme Simple assets are suited to models like road signs and speed limits that are made up of basic shapes. These objects are made up to 500 tris maximum.


<div style="text-align: center;">
  
<table>
  <thead>
    <tr>
      <th></th>
      <th>LOD3</th>
      <th>LOD2</th>
      <th>LOD1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Extreme Simple Tri Count</strong></td>
      <td>500</td>
      <td>100</td>
      <td>40</td>
    </tr>
  </tbody>
</table>

</div>

## Simple


<div style="text-align: center;">
  <img src="../../images/image16.png" style="width: 75%;" />
</div>

- Simple assets are suited to static models in an outdoor settings –
  from simple but organically shaped rocks, trashcans or benches up to
  more complicated traffic lights, bus shelters or decorative potted
  plants . These objects are made from 500 tris to 1500 tris maximum.



<div style="text-align: center;">
<table>
  <thead>
    <tr>
      <th></th>
      <th>LOD3</th>
      <th>LOD2</th>
      <th>LOD1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Simple Tri Count</strong></td>
      <td>1500</td>
      <td>300</td>
      <td>50</td>
    </tr>
  </tbody>
</table>

</div>


## Standard

<div style="text-align: center;">
  <img src="../../images/image17.png" style="width: 75%;" />
</div>

- Standard assets overall are cars, boats, helicopters and bikes. They are approximately 1500 tris to 3000 tris maximum.

<div style="text-align: center;">
<table>
  <thead>
    <tr>
      <th></th>
      <th>LOD3</th>
      <th>LOD2</th>
      <th>LOD1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Standard Tri Count</strong></td>
      <td>3000</td>
      <td>600</td>
      <td>100</td>
    </tr>
  </tbody>
</table>

</div>


## Complex

<div style="text-align: center;">
  <img src="../../images/image18.png" style="width: 75%;" />
</div>

- Complex assets are vehiclesthat have a lot additional pieces that cannot be faked easily with normals or colours. Think of diggers, trucks and cranes. They are approximately 3000 tris to 4500 tris maximum.


<div style="text-align: center;">
<table>
  <thead>
    <tr>
      <th></th>
      <th>LOD3</th>
      <th>LOD2</th>
      <th>LOD1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Complex Tri Count</strong></td>
      <td>4500</td>
      <td>900</td>
      <td>150</td>
    </tr>
  </tbody>
</table>

</div>

- Do keep in mind that the complexities of tri counts for each LOD may
  change depending on the type of asset it is. For example – **organic
  vegetation trees would have different LOD tri values in comparison to
  Transportation vehicles**. Use these values as a heuristic to
  approximate with and build with less where possible.

<div style="text-align: center;">
  <img src="../../images/image19.png" style="width: 75%;" />
</div>


 - *Triangle counts should count triangles**, not polygons as polygons equal 2 or more tris and will give a misleading and under estimated count – meaning that the tri count would be higher than anticipated.

- These models will currently not be animated.

- When making a particular LOD of an asset do keep in mind as mentioned
  in the asset Structure section that each LOD has its own glb. Later
  the LOD glbs will be imported into one file and saved together.
