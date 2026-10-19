# @ohos.net.policy (Network Policy Management) (System API)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=3186fe26194e8e3bb50c26df22fad33d7d33dcfd translatedAt=2026-09-23T02:18:27.988Z pushedAt=2026-09-24T06:00:14.208Z -->

The **policy** module provides APIs for managing network policies, through which you can control and manage the data volume used.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This page contains only the system APIs of this module. For details about the public APIs, see [@ohos.net.policy (Network Policy Management)](js-apis-net-policy.md).

## Modules to Import

```ts
import { policy } from '@kit.NetworkKit';
```

## policy.setBackgroundAllowed

setBackgroundAllowed(isAllowed: boolean, callback: AsyncCallback\<void>): void

Sets whether background applications are allowed to access the network. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                | Mandatory| Description                                                        |
| --------- | -------------------- | ---- | ------------------------------------------------------------ |
| isAllowed | boolean              | Yes  | Whether background applications are allowed to use mobile data. The value **true** indicates that background applications are allowed to use mobile data, and the value **false** indicates the opposite.                                    |
| callback  | AsyncCallback\<void\> | Yes   | Callback function. On success, **err** is **undefined**. On failure, returns error code and error information. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.setBackgroundAllowed(true, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.setBackgroundAllowed

setBackgroundAllowed(isAllowed: boolean): Promise\<void>

Sets whether background applications are allowed to access the network. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type   | Mandatory| Description                    |
| --------- | ------- | ---- | ------------------------ |
| isAllowed | boolean | Yes  | Whether background applications are allowed to use mobile data. The value **true** indicates that background applications are allowed to use mobile data, and the value **false** indicates the opposite.|

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.setBackgroundAllowed(true).then(() => {
  console.info("setBackgroundAllowed success");
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.isBackgroundAllowed

isBackgroundAllowed(callback: AsyncCallback\<boolean>): void

Obtains whether the current application is allowed to access the network in the background. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                            |
| -------- | ----------------------- | ---- | ---------------------------------------------------------------- |
| callback | AsyncCallback\<boolean> | Yes | Callback invoked to return the result. The value true indicates that the background policy is allowed, and an error code and error information are returned on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.isBackgroundAllowed((error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
 console.info(JSON.stringify(data));
});
```

## policy.isBackgroundAllowed

isBackgroundAllowed(): Promise\<boolean>

Obtains whether the current application is allowed to access the network in the background. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type             | Description                                                                                |
| ----------------- | ------------------------------------------------------------------------------------ |
| Promise\<boolean> | Promise object. Returns true if the background policy is allowed; returns false otherwise. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .isBackgroundAllowed()
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.setPolicyByUid

setPolicyByUid(uid: number, policy: NetUidPolicy, callback: AsyncCallback\<void>): void

Sets the policy for whether the application with the corresponding UID can access the metered network. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                           | Mandatory| Description                                          |
| -------- | ------------------------------- | ---- | ---------------------------------------------- |
| uid      | number                          | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range.                                |
| policy   | [NetUidPolicy](#netuidpolicy) | Yes  | Network access policy for the application.                                |
| callback | AsyncCallback\<void>            | Yes   | Callback function. Returns an empty value on success, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.setPolicyByUid(11111, policy.NetUidPolicy.NET_POLICY_NONE, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.setPolicyByUid

setPolicyByUid(uid: number, policy: NetUidPolicy): Promise\<void>

Sets whether the application with the corresponding UID can access the metering network. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type                           | Mandatory| Description          |
| ------ | ------------------------------- | ---- | -------------- |
| uid    | number                          | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range. |
| policy | [NetUidPolicy](#netuidpolicy) | Yes  | Network access policy for the application.|

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .setPolicyByUid(11111, policy.NetUidPolicy.NET_POLICY_NONE)
  .then(() => {
    console.info('setPolicyByUid success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getPolicyByUid

getPolicyByUid(uid: number, callback: AsyncCallback\<NetUidPolicy>): void

Obtains the network access policy by app UID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                           | Mandatory| Description                                                    |
| -------- | ----------------------------------------------- | ---- | -------------------------------------------------------- |
| uid      | number                                          | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range.                                           |
| callback | AsyncCallback\<[NetUidPolicy](#netuidpolicy)> | Yes   | Callback function. Returns the policy result on success, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getPolicyByUid(11111, (error: BusinessError, data: policy.NetUidPolicy) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.getPolicyByUid

getPolicyByUid(uid: number): Promise\<NetUidPolicy>

Obtains the network access policy by app UID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
|uid   | number | Yes   | Unique identifier of the app. The value is a positive integer within the range of int32_t. |

**Return value**

| Type                                     | Description                                                     |
| ----------------------------------------- | --------------------------------------------------------- |
| Promise\<[NetUidPolicy](#netuidpolicy)> | Promise object used to return the policy retrieval result. Returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getPolicyByUid(11111)
  .then((data: policy.NetUidPolicy) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getUidsByPolicy

getUidsByPolicy(policy: NetUidPolicy, callback: AsyncCallback\<Array\<number>>): void

Obtains all UIDs that match the policy. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                           | Mandatory| Description                                                       |
| -------- | ------------------------------- | ---- | ----------------------------------------------------------- |
| policy   | [NetUidPolicy](#netuidpolicy) | Yes  | Network policy for the application.                                 |
| callback | AsyncCallback\<Array\<number>>  | Yes   | Callback function. Returns the application's UID array on success, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getUidsByPolicy(11111, (error: BusinessError, data: number[]) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.getUidsByPolicy

getUidsByPolicy(policy: NetUidPolicy): Promise\<Array\<number>>

Obtains all UIDs that match the policy. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type                           | Mandatory| Description                      |
| ------ | ------------------------------- | ---- | -------------------------- |
| policy | [NetUidPolicy](#netuidpolicy) | Yes | Policy of the application on the metered network. |

**Return value**

| Type                    | Description                                                        |
| ------------------------ | ------------------------------------------------------------ |
| Promise\<Array\<number>> | Promise object used to return the UID array of the application. Returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getUidsByPolicy(11111)
  .then((data: object) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getNetQuotaPolicies

getNetQuotaPolicies(callback: AsyncCallback\<Array\<NetQuotaPolicy>>): void

Obtains the metering network policy. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                       | Mandatory| Description                    |
| -------- | ----------------------------------------------------------- | ---- | ------------------------ |
| callback | AsyncCallback\<Array\<[NetQuotaPolicy](#netquotapolicy)>> | Yes  | Callback used to return the result.  .|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getNetQuotaPolicies((error: BusinessError, data: policy.NetQuotaPolicy[]) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.getNetQuotaPolicies

getNetQuotaPolicies(): Promise\<Array\<NetQuotaPolicy>>

Obtains the metering network policy. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                                                 | Description                         |
| ----------------------------------------------------- | ----------------------------- |
| Promise\<Array\<[NetQuotaPolicy](#netquotapolicy)>> | Promise that returns the set result. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getNetQuotaPolicies()
  .then((data: policy.NetQuotaPolicy[]) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.setNetQuotaPolicies

setNetQuotaPolicies(quotaPolicies: Array\<NetQuotaPolicy>, callback: AsyncCallback\<void>): void

Sets the metered network policy. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name       | Type                                       | Mandatory| Description                                          |
| ------------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| quotaPolicies | Array\<[NetQuotaPolicy](#netquotapolicy)> | Yes  | Defines the quota policy for the specified network.                                  |
| callback      | AsyncCallback\<void>                        | Yes   | Callback function. Returns empty on success, and returns the error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netQuotaPolicyList: Array<policy.NetQuotaPolicy> = [];
let netQuotaPolicy: policy.NetQuotaPolicy = {
  networkMatchRule: {
    netType: connection.NetBearType.BEARER_CELLULAR,
    identity: '',
    simId: '1'
  },
  quotaPolicy: {
    periodDuration: 'M1',
    warningBytes: 40000,
    limitBytes: 50000,
    metered: true,
    limitAction: policy.LimitAction.LIMIT_ACTION_NONE
  }
}
netQuotaPolicyList.push(netQuotaPolicy);

policy.setNetQuotaPolicies(netQuotaPolicyList, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.setNetQuotaPolicies

setNetQuotaPolicies(quotaPolicies: Array\<NetQuotaPolicy>): Promise\<void>

Sets the metered network policy. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name       | Type                                       | Mandatory| Description        |
| ------------- | ------------------------------------------- | ---- | ------------ |
| quotaPolicies | Array\<[NetQuotaPolicy](#netquotapolicy)> | Yes  | Defines the quota policy for the specified network.|

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netQuotaPolicyList: Array<policy.NetQuotaPolicy> = [];
let netQuotaPolicy: policy.NetQuotaPolicy = {
  networkMatchRule: {
    netType: connection.NetBearType.BEARER_CELLULAR,
    identity: '',
    simId: '1'
  },
  quotaPolicy: {
    periodDuration: 'M1',
    warningBytes: 40000,
    limitBytes: 50000,
    metered: true,
    limitAction: policy.LimitAction.LIMIT_ACTION_NONE
  }
}
netQuotaPolicyList.push(netQuotaPolicy);

policy
  .setNetQuotaPolicies(netQuotaPolicyList)
  .then(() => {
    console.info('setNetQuotaPolicies success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.isUidNetAllowed

isUidNetAllowed(uid: number, isMetered: boolean, callback: AsyncCallback\<boolean>): void

Checks whether the application specified by a given UID can access a metered or non-metered network. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                   | Mandatory| Description                                                     |
| --------- | ----------------------- | ---- | --------------------------------------------------------- |
|uid      | number                  | Yes   | Unique identifier of the app. The value range is a positive integer within the range of int32_t.                                           |
| isMetered | boolean                 | Yes  | Whether the network is a metered network. The value **true** indicates that the network is a metered network, and the value **false** indicates the opposite.                                           |
| callback  | AsyncCallback\<boolean> | Yes   | Callback function. Returns **true** to indicate that this uid can access the corresponding metered network. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.isUidNetAllowed(11111, true, (error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.isUidNetAllowed

isUidNetAllowed(uid: number, isMetered: boolean): Promise\<boolean>

Checks whether the corresponding UID can access the metered or non-metered network. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type   | Mandatory| Description          |
| --------- | ------- | ---- | -------------- |
|uid      | number  | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range. |
| isMetered | boolean | Yes  | Whether the network is a metered network. The value **true** indicates that the network is a metered network, and the value **false** indicates the opposite.|

**Return value**

| Type             | Description                         |
| ----------------- | ----------------------------- |
| Promise\<boolean> | Promise object. Returns **true** if this **uid** can access the metered or non-metered network; returns **false** otherwise. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .isUidNetAllowed(11111, true)
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.isUidNetAllowed

isUidNetAllowed(uid: number, iface: string, callback: AsyncCallback\<boolean>): void

Obtains whether the network of the specified iface can be accessed by the corresponding UID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
|uid     | number                  | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range.                                               |
|iface   | string                  | Yes   | Name of the corresponding network.                                              |
| callback | AsyncCallback\<boolean> | Yes   | Callback function. Returning **true** indicates that this uid can access the network corresponding to the iface. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.isUidNetAllowed(11111, 'wlan0', (error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.isUidNetAllowed

isUidNetAllowed(uid: number, iface: string): Promise\<boolean>

Obtains whether the network of the specified iface can be accessed by the corresponding UID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| uid    | number | Yes   | Unique identifier of the app. The value is a positive integer within the range of int32_t. |
| iface  | string | Yes  | Name of the target network.|

**Return value**

| Type             | Description                                                   |
| ----------------- | ------------------------------------------------------- |
| Promise\<boolean> | Promise object. The value **true** indicates that the corresponding UID can access the network of the specified iface; the value **false** indicates that it cannot. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .isUidNetAllowed(11111, 'wlan0')
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.setDeviceIdleTrustlist

setDeviceIdleTrustlist(uids: Array\<number>, isAllowed: boolean, callback: AsyncCallback\<void>): void

Sets whether multiple UIDs are on the trustlist of the sleep firewall. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                          | Mandatory| Description                                          |
| --------- | ------------------------------ | ---- | ---------------------------------------------- |
| uids      | Array\<number\>                 | Yes   | Unique identifier of the application.                                 |
| isAllowed | boolean                        | Yes  | Whether to add the application to the trustlist. The value **true** means to add the application to the trustlist, and the value **false** means the opposite.                                |
| callback  | AsyncCallback\<void\> | Yes   | Callback function. Returns no value on success, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.setDeviceIdleTrustlist([11111, 22222], true, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.setDeviceIdleTrustlist

setDeviceIdleTrustlist(uids: Array\<number>, isAllowed: boolean): Promise\<void>

Sets whether multiple UIDs are on the trustlist of the sleep firewall. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type          | Mandatory| Description          |
| --------- | -------------- | ---- | -------------- |
| uids      | Array\<number> | Yes   | Unique identifier of the app. |
| isAllowed | boolean        | Yes  | Whether to add the application to the trustlist. The value **true** means to add the application to the trustlist, and the value **false** means the opposite.|

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.setDeviceIdleTrustlist([11111, 22222], true).then(() => {
    console.info('setDeviceIdleTrustlist success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getDeviceIdleTrustlist

getDeviceIdleTrustlist(callback: AsyncCallback\<Array\<number>>): void

Obtains the UIDs contained in the sleep mode trustlist. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                          | Mandatory| Description                    |
| -------- | ------------------------------ | ---- | ------------------------ |
| callback | AsyncCallback\<Array\<number>> | Yes  | Callback used to return the result.  .|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getDeviceIdleTrustlist((error: BusinessError, data: number[]) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.getDeviceIdleTrustlist

getDeviceIdleTrustlist(): Promise\<Array\<number>>

Obtains the UIDs contained in the sleep mode trustlist. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                    | Description                         |
| ------------------------ | ----------------------------- |
| Promise\<Array\<number>> | Promise that returns the set result. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getDeviceIdleTrustlist().then((data: number[]) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.getBackgroundPolicyByUid

getBackgroundPolicyByUid(uid: number, callback: AsyncCallback\<NetBackgroundPolicy>): void

Obtains whether the specified UID can access the background network. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                         | Mandatory| Description                    |
| -------- | ------------------------------------------------------------- | ---- | ------------------------ |
| uid      | number                                                        | Yes   | Unique identifier of the app. The value is a positive integer within the range of int32_t.           |
| callback | AsyncCallback\<[NetBackgroundPolicy](#netbackgroundpolicy)> | Yes  | Callback used to return the result.  .|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getBackgroundPolicyByUid(11111, (error: BusinessError, data: policy.NetBackgroundPolicy) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.getBackgroundPolicyByUid

getBackgroundPolicyByUid(uid: number): Promise\<NetBackgroundPolicy>

Obtains whether the specified UID can access the background network. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| uid    | number | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range. |

**Return value**

| Type                                                   | Description                         |
| ------------------------------------------------------- | ----------------------------- |
| Promise\<[NetBackgroundPolicy](#netbackgroundpolicy)> | Promise that returns the set result. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getBackgroundPolicyByUid(11111)
  .then((data: policy.NetBackgroundPolicy) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.resetPolicies

resetPolicies(simId: string, callback: AsyncCallback\<void>): void

Resets the cellular network, background network policy, firewall policy, and application-specific policy corresponding to the specified SIM card ID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                          |
| -------- | -------------------- | ---- | ---------------------------------------------- |
| simId    | string               | Yes   | SIM card ID.                                      |
| callback | AsyncCallback\<void\> | Yes   | Callback function. Returns no value on success, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.resetPolicies('1', (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.resetPolicies

resetPolicies(simId: string): Promise\<void>

Resets the cellular network, background network policy, firewall policy, and application-specific policies corresponding to the SIM card ID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description     |
| ------ | ------ | ---- | --------- |
| simId  | string | Yes   | SIM card ID. |

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .resetPolicies('1')
  .then(() => {
    console.info('resetPolicies success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.updateRemindPolicy

updateRemindPolicy(netType: NetBearType, simId: string, remindType: RemindType, callback: AsyncCallback\<void>): void

Updates a reminder policy. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name    | Type                                                | Mandatory| Description                                          |
| ---------- | ---------------------------------------------------- | ---- | ---------------------------------------------- |
| netType    | [NetBearType](js-apis-net-connection.md#netbeartype) | Yes  | Network type.                                      |
| simId      | string                                               | Yes   | SIM card ID.                                      |
| remindType | [RemindType](#remindtype)                          | Yes  | Enumerates the reminder types.                                      |
| callback   | AsyncCallback\<void>                                 | Yes   | Callback function. Returns on success with no value, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

policy.updateRemindPolicy(
  connection.NetBearType.BEARER_CELLULAR,
  '1',
  policy.RemindType.REMIND_TYPE_WARNING,
  (error: BusinessError) => {
    console.error(JSON.stringify(error));
  }
);
```

## policy.updateRemindPolicy

updateRemindPolicy(netType: NetBearType, simId: string, remindType: RemindType): Promise\<void>

Updates a reminder policy. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name    | Type                                                | Mandatory| Description     |
| ---------- | ---------------------------------------------------- | ---- | --------- |
| netType    | [NetBearType](js-apis-net-connection.md#netbeartype) | Yes  | Network type. |
| simId      | string                                               | Yes   | SIM card ID. |
| remindType | [RemindType](#remindtype)                          | Yes  | Enumerates the reminder types. |

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .updateRemindPolicy(
    connection.NetBearType.BEARER_CELLULAR,
    '1',
    policy.RemindType.REMIND_TYPE_WARNING
  )
  .then(() => {
    console.info('updateRemindPolicy success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.setPowerSaveTrustlist

setPowerSaveTrustlist(uids: Array\<number>, isAllowed: boolean, callback: AsyncCallback\<void>): void

Sets whether the app with the specified UID is in the trustlist of the power saving firewall. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type                          | Mandatory| Description                                          |
| --------- | ------------------------------ | ---- | ---------------------------------------------- |
| uids      | Array\<number\>                 | Yes   | Unique identifier of the application.                                |
| isAllowed | boolean                        | Yes  | Whether to add the application to the trustlist. The value **true** means to add the application to the trustlist, and the value **false** means the opposite.                                |
| callback  | AsyncCallback\<void\> | Yes   | Callback function. Returns no value on success, and returns an error code and error information on failure. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.setPowerSaveTrustlist([11111, 22222], true, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

## policy.setPowerSaveTrustlist

setPowerSaveTrustlist(uids: Array\<number>, isAllowed: boolean): Promise\<void>

Sets whether the app with the specified UID is in the trustlist of the power saving firewall. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name   | Type          | Mandatory| Description          |
| --------- | -------------- | ---- | -------------- |
| uids      | Array\<number> | Yes   | Unique identifier of the app. |
| isAllowed | boolean        | Yes  | Whether to add the application to the trustlist. The value **true** means to add the application to the trustlist, and the value **false** means the opposite.|

**Return value**

| Type          | Description                                                             |
| -------------- | ----------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .setPowerSaveTrustlist([11111, 22222], true)
  .then(() => {
    console.info('setPowerSaveTrustlist success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getPowerSaveTrustlist

getPowerSaveTrustlist(callback: AsyncCallback\<Array\<number>>): void

Obtains the UID array contained in the power save mode trustlist. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                          | Mandatory| Description                    |
| -------- | ------------------------------ | ---- | ------------------------ |
| callback | AsyncCallback\<Array\<number>> | Yes  | Callback used to return the result.  .|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy.getPowerSaveTrustlist((error: BusinessError, data: number[]) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```

## policy.getPowerSaveTrustlist

getPowerSaveTrustlist(): Promise\<Array\<number>>

Obtains the UID array contained in the sleep mode trustlist. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                    | Description                         |
| ------------------------ | ----------------------------- |
| Promise\<Array\<number>> | Promise that returns the set result. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getPowerSaveTrustlist()
  .then((data: number[]) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.setNetworkAccessPolicy<sup>12+</sup>

setNetworkAccessPolicy(uid: number, policy: NetworkAccessPolicy, isReconfirmed?: boolean): Promise\<void>

Sets the policy on whether the application with the specified UID can access the network. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name        | Type                                          | Mandatory| Description                                                                         |
| ------------- | ---------------------------------------------- | ---- | ---------------------------------------------------------------------------- |
| uid           | number                                         | Yes   | Unique identifier of the app. The value range is a positive integer within the int32_t range.                                                                |
| policy        | [NetworkAccessPolicy](#networkaccesspolicy12)  | Yes  | Network policy.                                                                     |
| isReconfirmed | boolean                                        | No  | Whether reconfirmation is required. The value **true** indicates that reconfirmation is not required and no dialog box is displayed. The value **false** indicates that reconfirmation is required and a dialog box is displayed when the application accesses the network. The default value is **false**. |

**Return value**

| Type          | Description                                                         |
| -------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accessPolicy: policy.NetworkAccessPolicy = {
  allowWiFi: false,
  allowCellular: true,
}
policy
  .setNetworkAccessPolicy(11111, accessPolicy)
  .then(() => {
    console.info('setNetworkAccessPolicy success');
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getNetworkAccessPolicy<sup>12+</sup>

getNetworkAccessPolicy(uid: number): Promise\<NetworkAccessPolicy>

Obtains the network access policy of the application with the specified UID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| uid    | number | Yes   | Unique identifier of the app. The value range is a positive integer within the range of int32_t. |

**Return value**

| Type                                                   | Description                         |
| ------------------------------------------------------- | ----------------------------- |
| Promise\<[NetworkAccessPolicy](#networkaccesspolicy12)> | Promise that returns the set result. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getNetworkAccessPolicy(11111)
  .then((data: policy.NetworkAccessPolicy) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy.getNetworkAccessPolicy<sup>12+</sup>

getNetworkAccessPolicy(): Promise\<UidNetworkAccessPolicy>

Obtains the network access policy information of all applications under the current user. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Return value**

| Type                                                         | Description                       |
| ------------------------------------------------------------- | --------------------------- |
| Promise\<[UidNetworkAccessPolicy](#uidnetworkaccesspolicy12)> | Promise that returns the set result. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .getNetworkAccessPolicy()
  .then((data: policy.UidNetworkAccessPolicy) => {
    let keyMap: Map<string, object> = new Map<string, object>(Object.entries(data));
    let uid:number = 0;
    let allowWiFi: string = "";
    let allowCellular: string = "";

    keyMap.forEach((value:object, key:string) => {
      let valueMap: Map<string, string> = new Map<string, string>(Object.entries(value));
      uid = Number.parseInt(key);
      valueMap.forEach((value:string, key:string)=>{
        if (key == "allowWiFi") {
          allowWiFi = value;
        }
        if (key == "allowCellular") {
          allowCellular = value;
        }
      })
    })
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

## policy

Represents the handle to a network policy.

### on('netUidPolicyChange')

on(type: 'netUidPolicyChange', callback: Callback\<NetUidPolicyInfo\>): void

Registers the callback for network policy changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                               | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------------- | ---- | -------------------------------------- |
| type     | string                                                              | Yes  | Event type.<br/> The value **netUidPolicyChange** indicates a policy change event.                 |
| callback | Callback\<[NetUidPolicyInfo](#netuidpolicyinfo11)> | Yes | Callback invoked when the network policy changes. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

interface Data {
  uid: number,
  policy: policy.NetUidPolicy
}

try {
  policy.on('netUidPolicyChange', (data: Data) => {
    console.info('on netUidPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netUidPolicyChange error: ' + JSON.stringify(err));
}
```

### off('netUidPolicyChange')

off(type: 'netUidPolicyChange', callback?: Callback\<NetUidPolicyInfo\>): void

Unsubscribes from network policy changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                               | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------------- | ---- | -------------------------------------- |
| type     | string                                                              | Yes  | Event type. The value **netUidPolicyChange** indicates a policy change event.              |
| callback | Callback\<[NetUidPolicyInfo](#netuidpolicyinfo11)> | No   | Callback for the network policy change event. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

interface Data {
  uid: number,
  policy: policy.NetUidPolicy
}

try {
  policy.on('netUidPolicyChange', (data: Data) => {
    console.info('on netUidPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netUidPolicyChange error: ' + JSON.stringify(err));
}

try {
  policy.off('netUidPolicyChange', (data: Data) => {
    console.info('off netUidPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('off netUidPolicyChange error: ' + JSON.stringify(err));
}
```

### on('netUidRuleChange')

on(type: 'netUidRuleChange', callback: Callback\<NetUidRuleInfo\>): void

Registers the callback for rule changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                         | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------- | ---- | -------------------------------------- |
| type     | string                                                        | Yes  | Event type.<br/> The value **netUidRuleChange** indicates a rule change event.                   |
| callback | Callback\<[NetUidRuleInfo](#netuidruleinfo11)> | Yes | Callback function. Callback invoked when the registered rule changes. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

interface Data {
  uid: number,
  rule: policy.NetUidRule
}

try {
  policy.on('netUidRuleChange', (data: Data) => {
    console.info('on netUidRuleChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netUidRuleChange error: ' + JSON.stringify(err));
}
```

### off('netUidRuleChange')

off(type: 'netUidRuleChange', callback?: Callback\<NetUidRuleInfo\>): void

Unregisters the callback for rule changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                         | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------- | ---- | -------------------------------------- |
| type     | string                                                        | Yes  | Event type. The value **netUidRuleChange** indicates a rule change event.                   |
| callback | Callback\<[NetUidRuleInfo](#netuidruleinfo11)> | No | Callback function. Callback invoked when the rule changes. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

interface Data {
  uid: number,
  rule: policy.NetUidRule
}

try {
  policy.on('netUidRuleChange', (data: Data) => {
    console.info('on netUidRuleChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netUidRuleChange error: ' + JSON.stringify(err));
}

try {
  policy.off('netUidRuleChange', (data: Data) => {
    console.info('off netUidRuleChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('off netUidRuleChange error: ' + JSON.stringify(err));
}
```

### on('netMeteredIfacesChange')

on(type: 'netMeteredIfacesChange', callback: Callback\<Array\<string>>): void

Registers the callback for metered iface changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                     |
| -------- | ------------------------- | ---- | ----------------------------------------- |
| type     | string                    | Yes  | Event type.<br/> The value **netMeteredIfacesChange** indicates a metered **iface** change event.                |
| callback | Callback\<Array\<string>> | Yes | Callback invoked when the metered iface changes. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

try {
  policy.on('netMeteredIfacesChange', (data: string[]) => {
    console.info('on netMeteredIfacesChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netMeteredIfacesChange error: ' + JSON.stringify(err));
}
```

### off('netMeteredIfacesChange')

off(type: 'netMeteredIfacesChange', callback?: Callback\<Array\<string>>): void

Unregisters the callback for metered iface changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                     |
| -------- | ------------------------- | ---- | ----------------------------------------- |
| type     | string                    | Yes  | Event type. The value **netMeteredIfacesChange** indicates a metered **iface** change event.                |
| callback | Callback\<Array\<string>> | No | Callback invoked when the metered iface changes. |

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

try {
  policy.on('netMeteredIfacesChange', (data: string[]) => {
    console.info('on netMeteredIfacesChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netMeteredIfacesChange error: ' + JSON.stringify(err));
}

try {
  policy.off('netMeteredIfacesChange', (data: string[]) => {
    console.info('off netMeteredIfacesChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('off netMeteredIfacesChange error: ' + JSON.stringify(err));
}
```

### on('netQuotaPolicyChange')

on(type: 'netQuotaPolicyChange', callback: Callback\<Array\<NetQuotaPolicy>>): void

Registers a callback for metered network policy changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                  | Mandatory| Description                                      |
| -------- | ------------------------------------------------------ | ---- | ------------------------------------------ |
| type     | string                                                 | Yes  | Event type.<br/> The value **netQuotaPolicyChange** indicates a network quota policy change event.                |
| callback | Callback\<Array\<[NetQuotaPolicy](#netquotapolicy)>> | Yes  | Callback used to return the result. It is called when the registered network quota policy changes.|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

interface Data {
  uid: number,
  policy: policy.NetUidPolicy
}

try {
  policy.on('netQuotaPolicyChange', (data: policy.NetQuotaPolicy[]) => {
    console.info('on netQuotaPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netQuotaPolicyChange error: ' + JSON.stringify(err));
}
```

### off('netQuotaPolicyChange')

off(type: 'netQuotaPolicyChange', callback?: Callback\<Array\<NetQuotaPolicy>>): void

Unregisters the callback for metered network policy changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type                                                  | Mandatory| Description                                      |
| -------- | ------------------------------------------------------ | ---- | ------------------------------------------ |
| type     | string                                                 | Yes  | Event type. The value **netQuotaPolicyChange** indicates a network quota policy change event.                |
| callback | Callback\<Array\<[NetQuotaPolicy](#netquotapolicy)>> | No  | Callback used to return the result. It is called when the registered network quota policy changes.|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

try {
  policy.on('netQuotaPolicyChange', (data: Array<policy.NetQuotaPolicy>) => {
    console.info('on netQuotaPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netQuotaPolicyChange error: ' + JSON.stringify(err));
}

try {
  policy.off('netQuotaPolicyChange', (data: Array<policy.NetQuotaPolicy>) => {
    console.info('off netQuotaPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('off netQuotaPolicyChange error: ' + JSON.stringify(err));
}
```

### on('netBackgroundPolicyChange')

on(type: 'netBackgroundPolicyChange', callback: Callback\<boolean>): void

Registers a callback for background network policy changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type              | Mandatory| Description                                      |
| -------- | ------------------ | ---- | ------------------------------------------ |
| type     | string             | Yes  | Event type.<br/> The value **netBackgroundPolicyChange** indicates a background network policy change event.                |
| callback | Callback\<boolean> | Yes  | Callback used to return the result. It is called when the registered background network policy changes.|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

try {
  policy.on('netBackgroundPolicyChange', (data: boolean) => {
    console.info('on netBackgroundPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netBackgroundPolicyChange error: ' + JSON.stringify(err));
}
```

### off('netBackgroundPolicyChange')

off(type: 'netBackgroundPolicyChange', callback?: Callback\<boolean>): void

Unregisters the callback for background network policy changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.MANAGE_NET_STRATEGY

**System capability**: SystemCapability.Communication.NetManager.Core

**Parameters**

| Name  | Type              | Mandatory| Description                                      |
| -------- | ------------------ | ---- | ------------------------------------------ |
| type     | string             | Yes  | Event type. The value **netBackgroundPolicyChange** indicates a background network policy change event.                |
| callback | Callback\<boolean> | No  | Callback used to return the result. It is called when the registered background network policy changes.|

**Error codes**

For details about the error codes, see [Policy Management Error Codes](errorcode-net-policy.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2100001   | Invalid parameter value.                     |
| 2100002   | Failed to connect to the service.            |
| 2100003   | System internal error.                       |

**Example**

```ts
import { policy } from '@kit.NetworkKit';

try {
  policy.on('netBackgroundPolicyChange', (data: boolean) => {
    console.info('on netBackgroundPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('on netBackgroundPolicyChange error: ' + JSON.stringify(err));
}

try {
  policy.off('netBackgroundPolicyChange', (data: boolean) => {
    console.info('off netBackgroundPolicyChange data: ' + JSON.stringify(data));
  });
} catch(err) {
  console.error('off netBackgroundPolicyChange error: ' + JSON.stringify(err));
}
```

## NetBackgroundPolicy

Enumerates the background network policies.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                           | Value | Description                                      |
| ------------------------------- | --- | ------------------------------------------ |
| NET_BACKGROUND_POLICY_NONE      | 0   | No background network policy is specified. This is the default value.                                  |
| NET_BACKGROUND_POLICY_ENABLE    | 1   | The application can use the metered network in the background. |
| NET_BACKGROUND_POLICY_DISABLE   | 2   | The application cannot use the metered network in the background. |
| NET_BACKGROUND_POLICY_TRUSTLIST | 3   | Only applications on the trustlist are allowed to access metered networks when they are running in the background.|

## NetQuotaPolicy

Defines the quota policy for the specified network.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name            | Type                                   | Read-Only|Optional| Description                            |
| ---------------- | --------------------------------------- | ---- | ----|---------------------------- |
| networkMatchRule | [NetworkMatchRule](#networkmatchrule) | No  |No|Network for which the quota policy is set.|
| quotaPolicy      | [QuotaPolicy](#quotapolicy)           | No | No|Network quota policy.              |

## NetworkMatchRule

Defines the network for which the quota policy is set.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name    | Type                                                | Read-Only|Optional| Description                                                                        |
| -------- | ---------------------------------------------------- | ---- | ------|---------------------------------------------------------------------- |
| netType  | [NetBearType](js-apis-net-connection.md#netbeartype) | No  |No|Network type.                                                                  |
| simId    | string                                               | No    |No |Identifier value of the SIM card in the metered cellular network.<br>Not used for Ethernet and Wi-Fi networks.                     |
| identity | string                                               | No   |No |Used together with simId in the metered cellular network.<br>Used independently for Ethernet and Wi-Fi networks.<br>Used to mark the type. |

## QuotaPolicy

Defines the network quota policy.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name             | Type                           | Read-Only|Optional| Description                                                 |
| ----------------- |-------------------------------| ---- |----|-------------------------------------------------|
| periodDuration    | string                        | No  |No|Metering period for the quota limit. **D1**, **M1**, and **Y1** indicate one day, one month, and one year, respectively. If the specified metering period is exceeded, the quota is not limited.|
| warningBytes      | number                        | No  |No|Data volume threshold for generating an alarm.                                         |
| limitBytes        | number                        | No  |No|Data volume quota.                                           |
| metered           | boolean                       | No  |No|Whether the network is a metered network. The value **true** indicates that the network is a metered network, and the value **false** indicates the opposite.                                        |
| limitAction       | [LimitAction](#limitaction) | No  | No|Action to take when the data volume quota is reached.                                        |
| lastWarningRemind | number                        | No  |Yes|Last time when an alarm was generated. Default value: **-1**.                                 |
| lastLimitRemind   | number                        | No  |Yes|Last time when the quota was exhausted. Default value: **-1**.                                     |

## LimitAction

Enumerates the actions that can be taken when the data volume quota is reached.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                        | Value | Description                              |
| ---------------------------- | --- | ---------------------------------- |
| LIMIT_ACTION_NONE            | -1  | No action is taken. This is the default value.                          |
| LIMIT_ACTION_ACCESS_DISABLED | 0   | Internet access is disabled.|
| LIMIT_ACTION_ALERT_ONLY      | 1   | An alarm is generated when the quota limit is reached.|

## NetUidRule

Enumerates the metered network rules.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                             | Value    | Description                |
| --------------------------------- | ------ | -------------------- |
| NET_RULE_NONE                     | 0      | Default rule.            |
| NET_RULE_ALLOW_METERED_FOREGROUND | 1 << 0 | Applications running in the foreground are allowed to access a metered network.|
| NET_RULE_ALLOW_METERED            | 1 << 1 | Applications are allowed to access a metered network.    |
| NET_RULE_REJECT_METERED           | 1 << 2 | Applications are not allowed to access a metered network.    |
| NET_RULE_ALLOW_ALL                | 1 << 5 | Applications are allowed to access all networks (metered or non-metered).   |
| NET_RULE_REJECT_ALL               | 1 << 6 | Applications are not allowed to access any networks (metered or non-metered).    |

## NetUidRuleInfo<sup>11+</sup>

Defines a unique network ID.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name             | Type                          | Read-Only|Optional| Description                                     |
| ----------------- | ----------------------------- | ---- | ------|----------------------------------- |
| uid               | number                        | No  |No|Traffic alarm threshold. The default value is **DATA_USAGE_UNKNOWN**.|
| rule              | [NetUidRule](#netuidrule)   | No |No|Rule that specifies whether the application specified by a given UID is allowed to access a metered or non-metered network.    |

## NetUidPolicyInfo<sup>11+</sup>

Defines the network policy information for an application.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name             | Type                           | Read-Only|Optional| Description                                   |
| ----------------- | ------------------------------- | ---- | ----|---------------------------------- |
| uid               | number                          | No  |No|Traffic alarm threshold. The default value is **DATA_USAGE_UNKNOWN**.|
| policy            | [NetUidPolicy](#netuidpolicy) | No  | No|Policy that specifies whether the application specified by a given UID is allowed to access the network when running in the background.   |

## RemindType

Enumerates the reminder types.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name               | Value | Description    |
| ------------------- | --- | -------- |
| REMIND_TYPE_WARNING | 1   | Warning.|
| REMIND_TYPE_LIMIT   | 2   | Limit.|

## NetUidPolicy

Enumerates network access policies for the application.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name                                | Value    | Description                      |
| ------------------------------------ | ------ | -------------------------- |
| NET_POLICY_NONE                      | 0      | Default network policy.              |
| NET_POLICY_ALLOW_METERED_BACKGROUND  | 1 << 0 | Background applications are allowed to access a metered network.|
| NET_POLICY_REJECT_METERED_BACKGROUND | 1 << 1 | Applications running in the background are not allowed to access a metered network.|

## NetworkAccessPolicy<sup>12+</sup>

Network access policy.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name             | Type      | Read-Only| Optional|Description                         |
| ----------------- | --------- | ---- | ------|----------------------- |
| allowWiFi         | boolean   | No   |Yes |Whether to allow the application to access the Wi-Fi network. The value true means allowed, and false means not allowed. |
| allowCellular     | boolean   | No |Yes|Whether the application is allowed to access the cellular network. The value **true** indicates that the application is allowed to access the cellular network, and the value **false** indicates the opposite.|
| alwaysAllowWiFi<sup>18+</sup>    | boolean   | No  |Yes |Whether to allow the application to always access the Wi-Fi network. The value true means allowed, and false means not allowed. |
| alwaysAllowCellular<sup>18+</sup>  | boolean   | No |Yes|Whether the application is always allowed to access the cellular network. The value **true** indicates that the application is always allowed to access the cellular network, and the value **false** indicates the opposite.|

## UidNetworkAccessPolicy<sup>12+</sup>

Defines the network policy for an application with the specified UID.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Core

| Name      | Type                                                        | Read-Only|Optional|Description                |
| --------- | -----------------------------------------------------------  | ---- | ---|---------------- |
| [uid: string] | [NetworkAccessPolicy](#networkaccesspolicy12) | No  |No|Network policy. The data type is key-value pair.     |