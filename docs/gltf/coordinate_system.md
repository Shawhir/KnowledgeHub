# Coordinate system

- The axis is **lefthand y-up**. If the asset has a clear forward (e.g. cars, people, park
  benches), it should be facing in the direction of the positive z-axis.
  Examples:

<div style="text-align: center;">
  <img src="../../images/image11.jpg" style="width: 75%;" />
</div>

- It should be noted that any models that are were made before this
  manifesto have a negative z-axis. Prior, it has been noticed that the
  glTF appears to by default create positive z-axis positions and it
  looks like we decided to flip the model 180 degrees (likely in the Pro
  exporter). Going forward – it would be more consistent to have
  directions all using the glTF default. This would mean changing the
  Webstyles authoring for legacy versions to flip them back 180. This
  will be taken into consideration.

- Origin of the coordinate system is at the most likely rotation pivot
  of the model. Here are some general rules for determining the origin:

  - posts/poles: center on single connection point to ground (e.g. sign
  posts / street lamps)

  - ground vehicles: center of mass projected to the ground (e.g. bottom
  center for car or land vehicle)

  - air vehicles on ground: center of mass projected to the ground (should
  be the same rotation pivot as model in air)

  - air vehicles in air: center of mass

  - water vehicles: y=0 is on waterline, center of mass projected to
  waterline

  - locators: location that it points to (e.g. push pins)

  - other: center on most likely rotation pivot of the model, then project
    to the ground

      - Example: planters: center on pot

      - Example: bus stops: center on bounding box

      - Example: antennas: center on support structure that touches the ground
