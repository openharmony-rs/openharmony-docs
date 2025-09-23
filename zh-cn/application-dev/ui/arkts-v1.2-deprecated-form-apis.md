# 表单类组件

## Slider（滑动条组件）

以下接口在ArkTS-Dyn中已标记为废弃，并在ArkTS-Sta中不再支持。

### minLabel

ArkTS-Dyn接口声明：[minLabel(value: string)](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#minlabeldeprecated)

替代的ArkTS-Sta接口声明：[min?: number](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions对象说明)

### maxLabel

ArkTS-Dyn接口声明：[maxLabel(value: string)](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#maxlabeldeprecated)

替代的ArkTS-Sta接口声明：[max?: number](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions对象说明)



ArkTS-Dyn

```ts
Slider({value: 50}).minLabel('0').maxLabel('100')
```

ArkTS-Sta

```ts
Slider({value: 50, min: 0, max: 100})
```