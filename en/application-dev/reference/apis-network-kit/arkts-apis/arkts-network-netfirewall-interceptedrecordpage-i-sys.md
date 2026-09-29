# InterceptedRecordPage (System API)

```TypeScript
interface InterceptedRecordPage
```

Intercepted record page information.

**Since:** 14

<!--Device-netFirewall-interface InterceptedRecordPage--><!--Device-netFirewall-interface InterceptedRecordPage-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## data

```TypeScript
data: Array<InterceptedRecord>
```

Page data: all records displayed on this page.

**Type:** Array&lt;[InterceptedRecord](arkts-network-netfirewall-interceptedrecord-i-sys.md)&gt;

**Since:** 14

<!--Device-InterceptedRecordPage-data: Array<InterceptedRecord>--><!--Device-InterceptedRecordPage-data: Array<InterceptedRecord>-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## page

```TypeScript
page: number
```

Current page number: indicates the page number of this query.

**Type:** number

**Since:** 14

<!--Device-InterceptedRecordPage-page: int--><!--Device-InterceptedRecordPage-page: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## pageSize

```TypeScript
pageSize: number
```

Page size: maximum number of records on a page for this query.

**Type:** number

**Since:** 14

<!--Device-InterceptedRecordPage-pageSize: int--><!--Device-InterceptedRecordPage-pageSize: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## totalPage

```TypeScript
totalPage: number
```

Total pages: total number of pages.

**Type:** number

**Since:** 14

<!--Device-InterceptedRecordPage-totalPage: int--><!--Device-InterceptedRecordPage-totalPage: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.
