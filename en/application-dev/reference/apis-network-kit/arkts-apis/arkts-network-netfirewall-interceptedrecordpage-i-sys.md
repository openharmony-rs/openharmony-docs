# InterceptedRecordPage (System API)

Intercepted record page information.

**Since:** 14

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

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## page

```TypeScript
page: number
```

Current page number: indicates the page number of this query.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## pageSize

```TypeScript
pageSize: number
```

Page size: maximum number of records on a page for this query.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.

## totalPage

```TypeScript
totalPage: number
```

Total pages: total number of pages.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**System API:** This is a system API.
