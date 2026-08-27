# InterceptedRecordPage（系统接口）

拦截记录分页信息。

**起始版本：** 14

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

**类型：** Array&lt;[InterceptedRecord](arkts-network-netfirewall-interceptedrecord-i-sys.md)&gt;

**起始版本：** 14

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## page

```TypeScript
page: number
```

Current page number: indicates the page number of this query.

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## pageSize

```TypeScript
pageSize: number
```

Page size: maximum number of records on a page for this query.

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

## totalPage

```TypeScript
totalPage: number
```

Total pages: total number of pages.

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。
