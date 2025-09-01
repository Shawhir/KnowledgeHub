# Coordinate system

- The axis is **lefthand y-up**. The direction of the positive z-axis is the forward facing direction of the asset. Examples:
  

<div style="text-align: center;">
  <img src="../../images/image46.jpg" style="width: 33%;" />
</div>

- It should be noted that any models that are were made before this manifesto have a negative z-axis.  Prior, it has been noticed that the glTF appears to by default create positive z-axis positions and it looks like we decided to flip the model 180 degrees (likely in the Pro exporter).  Going forward – it would be more consistent to have directions all using the glTF default.  This would mean changing the Webstyles authoring  for legacy versions to flip them back 180.  This will be taken into consideration.

- Origin of the coordinate system is at the most likely rotation pivot of the model.  The general rule for determining the origin is to place it in center on single connection point to the ground – namely the trunk.

- If your asset has more than one connection point, centre it between the connection points but keep y at 0 (bottom center of the asset).

- This will help with controlling the rotation of assets, especially when randomly rotating many assets at the same time for a more natural looking setting and to mitigate asset trunks from clashing or entering into buildings.

# Application Differences and Coordinate systems

<div style="text-align: center;">
  <img src="../../images/image47.jpg" style="width: 75%;" />
</div>

Most 3D file exchange formats use a Y-Up coordinate system by default. These include

- OBJ
- VRML
- FBX
- GLTF
- Collada
- USD

- Some modern formats, such as FBX and USD, offer explicit options to define the coordinate system. However, not all applications can read or write these settings from the file.  Our import systems are designed to handle coordinate system differences and adapt to the application's coordinate system automatically.

## Potential Issues
Problems may arise when end-users create OBJ or GLTF files in a Z-Up system. Applications might interpret these as Y-Up and transform them into their native coordinate system, potentially causing unexpected results.

##Best Practices
To mitigate these challenges
- End-users should be aware of the coordinate system used by their creation tools and target applications.
- Applications should clearly communicate their native coordinate system and any transformations applied during import/export.
- When possible, use file formats that explicitly define the coordinate system.
- Always test the imported 3D models in the target application to ensure correct orientation.

