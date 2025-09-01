## Metadata

A powerful feature of using **glTF** is its ability to embed metadata. This metadata comes in various forms and can support several practical use cases:

- **Ellipsoids** can be included to define where Ambient Occlusion (AO) applies to vegetation in **Scene Viewer**.
- **Animation tracks** can be embedded directly into the glTF to drive dynamic behavior or interactions.
- **Custom properties** can be used to store useful information about an object, such as species type, building usage, or other semantic data.

As our pipeline evolves, we may give artists the ability to embed base metadata and load all LODs together, simplifying asset setup and supporting more intelligent rendering.

---

## glTF Tool

A significant part of our QA work involves testing LODs for consistency before models are promoted to webstyles. Automation helps free up time to focus on visual improvements and fidelity.

[David Koerner](mailto:dkoerner@esri.com) has developed a robust set of Python command-line scripts that assist in automating many of these glTF-related tasks.

<div style="text-align: center;">
  <img src="../../images/gif1.gif" style="width: 90%;" />
</div>

The example above shows a tree model that has been processed by the glTF Tool, which automatically packs all LODs into a single glTF asset. The tool supports a broader range of functionality also.

Further documentation and scripts can be found here:  
[Prototype Webstyle Publishing – Build Scripts](https://devtopia.esri.com/davi9752/prototype-webstyle-publishing/tree/main/build-scripts)
