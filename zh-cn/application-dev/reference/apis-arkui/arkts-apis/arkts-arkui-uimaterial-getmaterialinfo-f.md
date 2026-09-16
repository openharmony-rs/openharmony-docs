# getMaterialInfo

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## getMaterialInfo

```TypeScript
function getMaterialInfo(): MaterialInfo
```

获取当前应用的材质配置信息。在需要根据材质使能状态决定组件是否开启或关闭沉浸式系统材质效果时，可调用此方法获取配置信息。返回的配置信息来自应用在[module.json5](../../../quick-start/module-configuration-file.md)中配置的metadata。只有在entry类型的module中配置的metadata才会生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md) | 返回当前应用的材质配置信息，包含材质使能状态和材质类型。 |
