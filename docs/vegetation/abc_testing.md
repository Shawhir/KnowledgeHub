# ABC Testing

<div style="text-align: center;">
  <img src="../../images/image74.jpg" style="width: 100%;" />
</div>

---

## Why Consistency Matters

Consistency is key, and keeping that consistency in place between Esri's ecosystem of Webstyles is key to their adoptability by clients. In other words, we are held by the constraint of the dimensions of other digital assets.

This means Quality Assurance has to be taken into account, and if it is done incrementally, it can help mitigate further headaches near the end of a project. The best way we currently have for testing this out is through ABC Testing of the different Webstyles inside their ecosystem of assets. This we will evolve in time.

---

## AB Testing in CityEngine

<div style="text-align: center;">
  <img src="../../images/image73.jpg" style="width: 100%;" />
</div>

AB testing can be successfully carried out in CityEngine, where it is procedurally simpler to use a CGA rule to show the Ankara Vegetation style in comparison to other vegetation style types. Watch the video below to go through the setup and how to run the CGA file to find the appropriate trees.

Here we are looking for close consistency to the other styles. Length, breadth, and height overall should be 20 percent or less compared to the other style silhouettes. The objective is to provide clients with a clean and enjoyable experience should they decide to update or change to other tree styles, regardless of where they are in their project pipeline.

The `ABTesting.cga` rule allows you to compare all styles of a singular species in alignment, by scrolling and selecting the trees available.

Here is a python script that converts the vegetation gltfs to glbs and outputs them to the same output folder, this may be useful for packing all the assets into one place.

---

## BC Testing

BC Testing in this instance involves taking the tree assets produced by the `ABTesting.cga` rule and exporting it from CityEngine to Web and Unreal using automated scripts. The purpose here is to validate the SpeedTree assets across CityEngine, Web, and Unreal at multiple distances to ensure consistent silhouette, scale, and performance.

For LODs validation, we are in tandem setting up a Web test, aiming to get as close to finished product setup as possible. More information to come.

As we progress, updates may be provided that can be run inside CityEngine to give you a snapshot of each of the tree groups, altogether or in batches. Beyond this we will consider testing whether some unit testing and AI can be set up to do anything beneficial for the more tedious but necessary QA work.

---

## QA Automation Tools

To support the BC Testing workflow, we have a dedicated repo that automates the setup for cross-platform QA testing environments. Rather than manually configuring CityEngine exports, local servers, and Unreal projects each time, which can take hours, this toolset handles it in minutes. It includes automated export scripts, a local server for browser-based GLB review, and pre-configured Unreal project files, so you can focus on evaluating the assets rather than wrangling the setup.

:octicons-repo-16: **[QA_Automation_Tools_Setup](https://devtopia.esri.com/mar11366/QA_Automation_Tools_Setup)**: Clone the repo and follow the README to get started.