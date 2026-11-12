# getTrafficStatsByUid (System API)

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getTrafficStatsByUid

```TypeScript
function getTrafficStatsByUid(uidInfo: UidInfo, callback: AsyncCallback<NetStatsInfo>): void
```

Obtains the historical traffic information of the specified application. This API uses an asynchronous callback to return the result. Based on the application UID, network interface, and time range specified in **uidInfo**, the system reads the transmitted and received bytes and packets of the application in the corresponding period from the statistics database and returns them through the callback. If the application has no traffic records in the specified period, all-zero statistics are returned.

**Since:** 10

**Required permissions:** ohos.permission.GET_NETWORK_STATS

<!--Device-statistics-function getTrafficStatsByUid(uidInfo: UidInfo, callback: AsyncCallback<NetStatsInfo>): void--><!--Device-statistics-function getTrafficStatsByUid(uidInfo: UidInfo, callback: AsyncCallback<NetStatsInfo>): void-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uidInfo | [UidInfo](arkts-network-statistics-uidinfo-i-sys.md) | Yes | Application information. For details, see [UidInfo](arkts-network-statistics-uidinfo-i-sys.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md)&gt; | Yes | Callback used to return the application historical traffic information. If the operation is successful, **err** is **undefined** and **data** is the obtained application historical traffic information. Otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2103017](../errorcode-net-statistics.md#2103017-failed-to-read-the-database) | Failed to read the database. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let uidInfo: statistics.UidInfo = {
  uid: 20010037,
  ifaceInfo: {
    iface: '',
    startTime: 1,
    endTime: 3,
  }
}

statistics.getTrafficStatsByUid(
  uidInfo,
  (error: BusinessError, statsInfo: statistics.NetStatsInfo) => {
    if (error) {
      console.error(JSON.stringify(error));
      return;
    };
    console.info(
      "getTrafficStatsByUid bytes of received = " +
      JSON.stringify(statsInfo.rxBytes)
    );
    console.info(
      "getTrafficStatsByUid bytes of sent = " +
      JSON.stringify(statsInfo.txBytes)
    );
    console.info(
      "getTrafficStatsByUid packets of received = " +
      JSON.stringify(statsInfo.rxPackets)
    );
    console.info(
      "getTrafficStatsByUid packets of sent = " +
      JSON.stringify(statsInfo.txPackets)
    );
  }
);
```

<!--DelEnd-->


## getTrafficStatsByUid

```TypeScript
function getTrafficStatsByUid(uidInfo: UidInfo): Promise<NetStatsInfo>
```

Obtains the historical traffic information of the specified application. This API uses a promise to return the result. Based on the application UID, network interface, and time range specified in **uidInfo**, the system reads the transmitted and received bytes and packet counts of the application within the corresponding period from the statistics database and returns them in a promise. If the application has no traffic records within the specified period, all-zero statistics are returned.

**Since:** 10

**Required permissions:** ohos.permission.GET_NETWORK_STATS

<!--Device-statistics-function getTrafficStatsByUid(uidInfo: UidInfo): Promise<NetStatsInfo>--><!--Device-statistics-function getTrafficStatsByUid(uidInfo: UidInfo): Promise<NetStatsInfo>-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uidInfo | [UidInfo](arkts-network-statistics-uidinfo-i-sys.md) | Yes | Application information. For details, see [UidInfo](arkts-network-statistics-uidinfo-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetStatsInfo](arkts-network-statistics-netstatsinfo-i.md)&gt; | Promise used to return the application historical traffic information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2103017](../errorcode-net-statistics.md#2103017-failed-to-read-the-database) | Failed to read the database. |

<!--Del-->
**Examples**

```TypeScript
import { statistics } from '@kit.NetworkKit';

let uidInfo: statistics.UidInfo = {
  uid: 20010037,
  ifaceInfo: {
    iface: '',
    startTime: 1,
    endTime: 3,
  }
}

statistics.getTrafficStatsByUid(uidInfo).then((statsInfo: statistics.NetStatsInfo) => {
  console.info("getTrafficStatsByUid bytes of received = " + JSON.stringify(statsInfo.rxBytes));
  console.info("getTrafficStatsByUid bytes of sent = " + JSON.stringify(statsInfo.txBytes));
  console.info("getTrafficStatsByUid packets of received = " + JSON.stringify(statsInfo.rxPackets));
  console.info("getTrafficStatsByUid packets of sent = " + JSON.stringify(statsInfo.txPackets));
})
```

<!--DelEnd-->
