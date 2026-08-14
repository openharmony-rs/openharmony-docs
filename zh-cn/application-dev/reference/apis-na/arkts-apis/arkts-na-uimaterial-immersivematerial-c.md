# ImmersiveMaterial

沉浸式材质类，继承自[Material](arkts-na-uimaterial-materialtype-e.md#MaterialType（系统接口）)。 沉浸式材质根据设备算力有分档表现，设备算力的高、中、低档由设备厂商决定，定义在系统配置文件中。在高档和中档算力设备上，影响材质层滤镜效果和阴影 shadow效果。在低档算力设备上，影响背景色 [backgroundColor](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框 颜色borderColor、边框宽度borderWidth、阴影 shadow效果。且同一材质的效果，会受到设置应用中沉浸光感配置项的影响，不同强弱程度的沉浸光感配置 下，材质的参数和效果存在差异。

**继承/实现关系：** ImmersiveMaterial extends [Material](arkts-na-uimaterial-material-c-sys.md#Material（系统接口）)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-uiMaterial-export class ImmersiveMaterial--><!--Device-uiMaterial-export class ImmersiveMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: ImmersiveOptions)
```

ImmersiveMaterial的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImmersiveMaterial-constructor(options?: ImmersiveOptions)--><!--Device-ImmersiveMaterial-constructor(options?: ImmersiveOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ImmersiveOptions](arkts-na-uimaterial-immersiveoptions-i.md) | 否 | 系统材质配置选项，包括材质样式、材质层赋色等。&lt;br/&gt;默认值参考ImmersiveOptions接口各参数的默认值，即{style: ImmersiveStyle.REGULAR, materialColor:Color.Transparent, colorInvert:false, applyShadow:true, interactive: false, lightEffect:undefined}。 |

