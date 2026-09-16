# isImmersiveMaterialSupported

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## isImmersiveMaterialSupported

```TypeScript
function isImmersiveMaterialSupported(): boolean
```

判断当前设备是否支持沉浸式系统材质[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)。在开发需要沉浸式材质效果的功能时，可先调用此方法判断设备是否支持，以决定是否为组件设置沉浸式材质。该配置项由设备定义，不可修改。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持ImmersiveMaterial。true表示当前设备支持ImmersiveMaterial，false表示不支持。 |
