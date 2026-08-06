# ImmersiveMaterial

沉浸式材质类，继承自[Material]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。 沉浸式材质根据设备算力有分档表现，设备算力的高、中、低档由设备厂商决定，定义在系统配置文件中。在高档和中档算力设备上，影响材质层滤镜效果和阴影 [shadow]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_效果。在低档算力设备上，影响背景色 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、边框 颜色[borderColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、边框宽度[borderWidth]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、阴影 [shadow]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_效果。且同一材质的效果，会受到设置应用中沉浸光感配置项的影响，不同强弱程度的沉浸光感配置 下，材质的参数和效果存在差异。

**继承/实现关系：** ImmersiveMaterial extends [Material](arkts-na-uimaterial-material-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-uiMaterial-export class ImmersiveMaterial extends Material--><!--Device-uiMaterial-export class ImmersiveMaterial extends Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: ImmersiveOptions)
```

ImmersiveMaterial的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImmersiveMaterial-constructor(options?: ImmersiveOptions)--><!--Device-ImmersiveMaterial-constructor(options?: ImmersiveOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 系统材质配置选项，包括材质样式、材质层赋色等。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值参考ImmersiveOptions接口各参数的默认值，即{style:ImmersiveStyle.REGULAR, materialColor:Color.Transparent, colorInvert:false, applyShadow:true, interactive:false, lightEffect:undefined}。 |

