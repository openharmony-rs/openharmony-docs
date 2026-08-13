# RenderingContextSettings

用来配置CanvasRenderingContext2D对象的参数，包括是否开启抗锯齿。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class RenderingContextSettings--><!--Device-unnamed-export declare class RenderingContextSettings-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(antialias?: boolean)
```

构造CanvasRenderingContext2D对象，支持配置开启抗锯齿。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderingContextSettings-constructor(antialias?: boolean)--><!--Device-RenderingContextSettings-constructor(antialias?: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| antialias | boolean | 否 | 表明canvas是否开启抗锯齿。&lt;br&gt;异常值undefined按默认值处理。 &lt;br&gt;false：表示不开启抗锯齿功能，true：表示开启抗锯齿。&lt;br&gt;默认值：false |

