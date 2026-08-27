# isNearLinkSupported

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## isNearLinkSupported

```TypeScript
function isNearLinkSupported(): boolean
```

查询当前设备是否支持星闪服务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前设备是否支持星闪。返回true：设备支持星闪。返回false：设备不支持星闪。 |
