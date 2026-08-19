# XComponentParameters

定义XComponent的具体配置参数，支持Native侧触发XComponent生命周期回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface XComponentParameters--><!--Device-unnamed-export declare interface XComponentParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: XComponentController
```

给组件绑定一个控制器，通过控制器调用组件方法，仅类型为SURFACE或TEXTURE时有效。

**类型：** [XComponentController](arkts-na-xcomponent-xcomponentcontroller-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentParameters-controller?: XComponentController--><!--Device-XComponentParameters-controller?: XComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string
```

组件的唯一标识，支持最大的字符串长度128。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentParameters-id: string--><!--Device-XComponentParameters-id: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nativeXComponentHandler

```TypeScript
nativeXComponentHandler: Callback<NativeXComponentPointer>
```

用于处理NativeXComponent实例的回调。

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[NativeXComponentPointer](arkts-na-nativexcomponentpointer-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentParameters-nativeXComponentHandler: Callback<NativeXComponentPointer>--><!--Device-XComponentParameters-nativeXComponentHandler: Callback<NativeXComponentPointer>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

用于指定XComponent组件类型。

**类型：** [XComponentType](../../apis-arkui/arkts-apis/arkts-arkui-xcomponenttype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentParameters-type: XComponentType--><!--Device-XComponentParameters-type: XComponentType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

