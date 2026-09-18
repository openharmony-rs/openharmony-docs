# isRangingSupported

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## isRangingSupported

```TypeScript
function isRangingSupported(): boolean
```

判断本端设备是否支持测距特性。

建议在调用本模块其他接口前先调用此接口检查设备是否支持测距特性，避免因不支持而导致功能异常。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持测距功能。true表示支持，false表示不支持。 |
