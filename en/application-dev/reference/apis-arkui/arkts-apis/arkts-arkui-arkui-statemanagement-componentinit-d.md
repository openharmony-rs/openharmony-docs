# @ComponentInit

```TypeScript
export declare const ComponentInit: MethodDecorator
```

The function decorated by **\@ComponentInit** is executed when the initialization of a custom component is about to complete, and is triggered before **\@ComponentAppear**. You can register lifecycle listeners and modify state variables at this time. The difference from **\@ComponentAppear** is that **\@ComponentInit** focuses on preparation operations in the initialization phase (such as listener registration), while **\@ComponentAppear** focuses on state changes before the component is about to be displayed. The two can be used together to respectively assume the responsibilities of initialization and pre-display.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-export declare const ComponentInit: MethodDecorator--><!--Device-unnamed-export declare const ComponentInit: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
