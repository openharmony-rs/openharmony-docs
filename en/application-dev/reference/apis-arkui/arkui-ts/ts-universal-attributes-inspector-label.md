# Node Inspector Label
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f5d9043d98f8fa50422028dea8cff4f34b773b75 translatedAt=2026-09-01T12:41:35.135Z -->

Sets an inspector label for a component node. The label, as a custom identifier of the node, is displayed in the Inspector component tree of DevEco Studio, helping you distinguish nodes of the same type, quickly locate components during debugging, and improve development and analysis efficiency.

**Since**: 26.0.0

## inspectorLabel

inspectorLabel(label: string | undefined): T

Sets the inspector label of a component. If not set, the component inspector label defaults to an empty string. If this API is called multiple times for the same component, the later label overwrites the previous one.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type      | Required | Description                       |
| ------ | -------- | -----|---------------------- |
| label  | string \| undefined  |  Yes  | Inspector label of the component. It must be unique within the entire application so that nodes can be accurately located and distinguished during debugging. When this API is called multiple times on the same component, the label set later overwrites the previous one. Passing undefined clears the inspector label. The inspector label is an empty string by default. |

**Return value**

| Type | Description |
| -------- | -------- |
| T | Current component, which can be used for chain calls. |

**Example**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(20)
        .inspectorLabel('TEXT')
        .onClick(() => {
          console.info(`Text is clicked`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```