# XComponentAttribute

定义XComponent属性。

**继承/实现关系：** XComponentAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface XComponentAttribute extends CommonMethod--><!--Device-unnamed-export declare interface XComponentAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableTransparentLayer

```TypeScript
default enableTransparentLayer(enabled: boolean | undefined): this
```

当背景颜色设置半透明的XComponent需要开启独立图层（即将该组件的内容置于单独的合成图层上进行渲染， 以避免半透明区域与下方内容混合时出现渲染异常）时，使用本接口。 使用本接口，并不代表一定会被设置为独立图层。出于硬件规格（如硬件不支持独立图层进行硬件合成）、 软件规格（如独立图层与带有模糊效果的UI组件相交）等原因，将导致半透明XComponent无法设置为独立图层。 **说明：** 仅type为SURFACE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentAttribute-default enableTransparentLayer(enabled: boolean | undefined): this--><!--Device-XComponentAttribute-default enableTransparentLayer(enabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 是否开启组件背景半透明状态下的独立图层。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：开启独立图层；false：关闭独立图层。设置为true时，由于硬件规格或软件规格等原因，可能无法实际生效。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

