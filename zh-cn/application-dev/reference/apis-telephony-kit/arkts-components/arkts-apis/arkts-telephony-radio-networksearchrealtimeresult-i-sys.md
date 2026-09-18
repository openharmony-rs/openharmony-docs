# NetworkSearchRealTimeResult（系统接口）

表示手动网络扫描的结果

**起始版本：** 23

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isFinish

```TypeScript
isFinish: boolean
```

指示网络搜索是否已停止

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## networkInfos

```TypeScript
networkInfos: Array<NetworkInformation>
```

网络搜索结果

**类型：** Array&lt;[NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md)&gt;

**起始版本：** 23

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
