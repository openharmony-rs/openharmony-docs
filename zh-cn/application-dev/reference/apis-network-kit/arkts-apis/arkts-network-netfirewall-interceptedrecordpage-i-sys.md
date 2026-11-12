# InterceptedRecordPage（系统接口）

```TypeScript
interface InterceptedRecordPage
```

拦截记录分页信息结构。

**起始版本：** 14

<!--Device-netFirewall-interface InterceptedRecordPage--><!--Device-netFirewall-interface InterceptedRecordPage-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## data

```TypeScript
data: Array<InterceptedRecord>
```

页面数据。

**类型：** Array&lt;[InterceptedRecord](arkts-network-netfirewall-interceptedrecord-i-sys.md)&gt;

**起始版本：** 14

<!--Device-InterceptedRecordPage-data: Array<InterceptedRecord>--><!--Device-InterceptedRecordPage-data: Array<InterceptedRecord>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## page

```TypeScript
page: number
```

当前页码。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecordPage-page: int--><!--Device-InterceptedRecordPage-page: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## pageSize

```TypeScript
pageSize: number
```

页面大小。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecordPage-pageSize: int--><!--Device-InterceptedRecordPage-pageSize: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## totalPage

```TypeScript
totalPage: number
```

总页数。

**类型：** number

**起始版本：** 14

<!--Device-InterceptedRecordPage-totalPage: int--><!--Device-InterceptedRecordPage-totalPage: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。
