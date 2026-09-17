# isPartnerAgentSupported

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## isPartnerAgentSupported

```TypeScript
function isPartnerAgentSupported(): boolean
```

判断本机设备是否支持外设互通功能，若该接口返回值是false，该文件内的其他接口均无法使用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持外设互通功能。true表示支持外设互通功能，false表示不支持外设互通功能。 |
