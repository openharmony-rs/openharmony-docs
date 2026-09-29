# ImageAnalyzerController

```TypeScript
declare class ImageAnalyzerController
```

Defines the image AI analysis controller. You can bind this object to a supported component and call the methods it provides through the controller.

**Since:** 12

<!--Device-unnamed-declare class ImageAnalyzerController--><!--Device-unnamed-declare class ImageAnalyzerController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create an **ImageAnalyzerController** instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAnalyzerController-constructor()--><!--Device-ImageAnalyzerController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getImageAnalyzerSupportTypes

```TypeScript
getImageAnalyzerSupportTypes(): ImageAnalyzerType[]
```

Obtains the image AI analysis types supported by the component to which this controller is bound. Before calling this method, bind the controller to a component through the **aiController** attribute of components such as **Image** and **ImageAnimator**. Otherwise, an empty array is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAnalyzerController-getImageAnalyzerSupportTypes(): ImageAnalyzerType[]--><!--Device-ImageAnalyzerController-getImageAnalyzerSupportTypes(): ImageAnalyzerType[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ImageAnalyzerType](arkts-arkui-imageanalyzertype-e.md)[] | AI analysis type supported by the corresponding component. |
