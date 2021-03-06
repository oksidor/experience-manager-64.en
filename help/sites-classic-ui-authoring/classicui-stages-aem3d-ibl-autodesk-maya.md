---
title: Setting up an IBL stage with Autodesk Maya and Mental Ray
seo-title: Setting up an IBL stage with Autodesk Maya and Mental Ray
description: Learn how to set up an IBL stage with Autodesk Maya and Mental Ray.
seo-description: Learn how to set up an IBL stage with Autodesk Maya and Mental Ray.
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
---

# Setting up an IBL stage with Autodesk Maya and Mental Ray{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. In Maya, create a new, empty scene.  

1. Create a (temporary) reference to a representative model. Doing so helps to facilitate evaluating lighting, setting up cameras, and configuring the renderer.
1. Set up image-based lighting.

    1. In Render Settings, select **[!UICONTROL Render Using: mental ray]**, and open the **[!UICONTROL Scene]** tab.
    1. Open the **[!UICONTROL Environment]** accordion, then click **[!UICONTROL Create Image Based Lighting]**.
    1. Click the box icon that has a right arrow on the left side of the box to select the IBL node `mentalRayIblShape1`, then exit the [!UICONTROL Render Settings].
    1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.

    1. Set the [!UICONTROL Scale] of the node to make the environment sphere significantly larger than the largest 3D object to be shown with this stage (for example, `10000,10000,10000`).
    1. Select the `AdobeIblShape` node and configure it as follows:

        * **[!UICONTROL Mapping]** - Spherical
        * **[!UICONTROL Type]** - Image File
        * **[!UICONTROL Emit Light]** - true

    1. Attach the desired 32-bit TIFF image to the `AdobeIbl` node.

1. Setup the ground plane.

    * Create a suitable plane to use as ground plane and size it to reasonably fit within the IBL sphere, passing through the coordinate origin.
    * Attach a **[!UICONTROL Use Background]** material to the ground plane and name it `AdobeUseBackground` and attach it to the ground plane object.

1. (Optional) Create and configure cameras.

   Have the cameras "look" toward the center of the scene where the asset will be inserted. Be sure you set the cameras to renderable.

1. Set up rendering with Mental Ray.

   Configure the [!UICONTROL Render Settings] with the following suggestions.

    * **[!UICONTROL Common]** tab 

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

    * **[!UICONTROL Quality]** tab

        * **[!UICONTROL Overall quality]** - `0.5` or less
        * **[!UICONTROL Indirect Diffuse (GI) Mode]** - `Final Gather`
        * **[!UICONTROL Filter Size]** - `2.0`, `2.0`

    * Render the scene at the typical image sizes that you expect to use. If necessary, refine the lights, Render settings, or both to achieve the results you want. 

      Be aware that rendering with Mental Ray, using image-based lighting, is very slow and CPU-intensive. Adobe recommends that you configure the lowest quality settings that are still capable of producing the desired render quality.

1. Remove the reference that you created in step 2.  

1. Save the scene, then exit Autodesk Maya.  

1. Upload the scene and the IBL PTIFF into AEM and wait for upload processing to complete.

   See [Uploading Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).

1. Resolve any file dependencies.

   See [Resolving file dependencies](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md).

   AEM 3D may not be able to detect the IBL image configured in the stage. In such situations, you must resolve the missing dependencies manually. You can assign the same previously uploaded IBL PTIFF image for each of the missing dependencies. Or, you can assign different images to further control the IBL effects. After resolving the dependencies, be sure you tap **Save** to initiate reprocessing.

1. Open Asset Properties in AEM. Set Title to a suitable string that will appear in the Stage Selector drop-down list. Verify that **[!UICONTROL Class]** is set to **[!UICONTROL 3D Stage]**. Save and exit.  

1. Open a 3D asset, select the new stage, and verify that it previews and renders as expected.

