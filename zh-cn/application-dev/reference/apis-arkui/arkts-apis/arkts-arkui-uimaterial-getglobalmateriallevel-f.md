# getGlobalMaterialLevel

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## getGlobalMaterialLevel

```TypeScript
function getGlobalMaterialLevel(): MaterialLevel
```

获取全局材质等级，与设备算力相关。在需要根据设备算力等级选择不同材质效果实现方式时，可调用此方法获取材质等级。该配置项由设备定义，不可修改。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MaterialLevel](arkts-arkui-uimaterial-materiallevel-e.md) | 返回设备的材质等级，表示设备算力档次，不同等级对应沉浸式材质在当前设备上的不同渲染效果级别。 |
