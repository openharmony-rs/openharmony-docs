# XComponent

定义XComponent组件。


## XComponent

```TypeScript
XComponent(value: { id: string; type: string; libraryname?: string; controller?: XComponentController })
```

构造参数

**起始版本：** 8

**废弃版本：** 12

**替代接口：** <!--SUBSTITUTE_API-->(value:<!--/SUBSTITUTE_API-->

<!--Device-XComponentInterface-(value: { id: string; type: string; libraryname?: string; controller?: XComponentController }): XComponentAttribute--><!--Device-XComponentInterface-(value: { id: string; type: string; libraryname?: string; controller?: XComponentController }): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { id: string; type: string; libraryname?: string; controller?: XComponentController } | 是 | 表示XComponent的选项。  |

## XComponent

```TypeScript
XComponent(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController })
```

构造参数

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentInterface-(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController }): XComponentAttribute--><!--Device-XComponentInterface-(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController }): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController } | 是 | 表示XComponent的选项。  |

## XComponent

```TypeScript
XComponent(options: XComponentOptions)
```

构造参数

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentInterface-(options: XComponentOptions): XComponentAttribute--><!--Device-XComponentInterface-(options: XComponentOptions): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [XComponentOptions](arkts-arkui-xcomponentoptions-i.md) | 是 | 表示XComponent的选项。  |

## XComponent

```TypeScript
XComponent(params: NativeXComponentParameters)
```

构造参数

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentInterface-(params: NativeXComponentParameters): XComponentAttribute--><!--Device-XComponentInterface-(params: NativeXComponentParameters): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [NativeXComponentParameters](arkts-arkui-nativexcomponentparameters-i.md) | 是 | 表示用于native开发的XComponent构造参数。  |

## 汇总

- [NativeXComponentParameters](arkts-arkui-xcomponent-nativexcomponentparameters-i.md)
- [SurfaceConfig](arkts-arkui-xcomponent-surfaceconfig-i.md)
- [SurfaceRect](arkts-arkui-xcomponent-surfacerect-i.md)
- [SurfaceRotationOptions](arkts-arkui-xcomponent-surfacerotationoptions-i.md)
- [XComponentOptions](arkts-arkui-xcomponent-xcomponentoptions-i.md)
- [OnNativeLoadCallback](arkts-arkui-xcomponent-onnativeloadcallback-t.md)
- [HdrType](arkts-arkui-xcomponent-hdrtype-e.md)
