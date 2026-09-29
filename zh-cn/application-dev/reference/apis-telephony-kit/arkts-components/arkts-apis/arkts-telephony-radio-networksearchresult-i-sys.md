# NetworkSearchResult（系统接口）

```TypeScript
export interface NetworkSearchResult
```

Obtains the network search results.

**起始版本：** 6

<!--Device-radio-export interface NetworkSearchResult--><!--Device-radio-export interface NetworkSearchResult-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isNetworkSearchSuccess

```TypeScript
isNetworkSearchSuccess: boolean
```

Indicates whether the network search was successful.

**类型：** boolean

**起始版本：** 6

<!--Device-NetworkSearchResult-isNetworkSearchSuccess: boolean--><!--Device-NetworkSearchResult-isNetworkSearchSuccess: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## networkSearchResult

```TypeScript
networkSearchResult: Array<NetworkInformation>
```

Obtains the network search results.

**类型：** Array&lt;[NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md)&gt;

**起始版本：** 6

<!--Device-NetworkSearchResult-networkSearchResult: Array<NetworkInformation>--><!--Device-NetworkSearchResult-networkSearchResult: Array<NetworkInformation>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
