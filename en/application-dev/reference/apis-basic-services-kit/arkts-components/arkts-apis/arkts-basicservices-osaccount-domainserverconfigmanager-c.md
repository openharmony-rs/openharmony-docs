# DomainServerConfigManager

Provides APIs for domain server configuration and management.

**Since:** 18

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## addServerConfig

```TypeScript
static addServerConfig(parameters: Record<string, Object>): Promise<DomainServerConfig>
```

Adds domain server configuration. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameters | Record&lt;string, Object&gt; | Yes | Domain server configuration parameters, which are used to configure the connection information of the domain server. The parameters include the server address and port number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md)&gt; | Promise used to return the configuration of the newly added domain server. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid server config parameters. |
| 12300211 | Server unreachable. |
| 12300213 | Server config already exists. |
| 12300215 | The number of server config reaches the upper limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let configParams: Record<string, Object> = {
  'uri': 'test.example.com',
  'port': 100
};
osAccount.DomainServerConfigManager.addServerConfig(configParams).then((
  serverConfig: osAccount.DomainServerConfig) => {
  console.info('add server configuration successfully, the return config: ' + JSON.stringify(serverConfig));
}).catch((err: BusinessError) => {
  console.error(`add server configuration failed, code is ${err.code}, message is ${err.message}`);
});
```

## getAccountServerConfig

```TypeScript
static getAccountServerConfig(domainAccountInfo: DomainAccountInfo): Promise<DomainServerConfig>
```

Obtains the server configuration of a domain account. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Information of the domain account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md)&gt; | Promise used to return the domain server configuration of the account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountInfo: osAccount.DomainAccountInfo = {
  'accountName': 'demoName',
  'domain': 'demoDomain'
};
osAccount.DomainServerConfigManager.getAccountServerConfig(accountInfo).then((
  serverConfig: osAccount.DomainServerConfig) => {
  console.info('get account server configuration successfully, the return config: ' + JSON.stringify(serverConfig));
}).catch((err: BusinessError) => {
  console.error(`add server configuration failed, code is ${err.code}, message is ${err.message}`);
});
```

## getAllServerConfigs

```TypeScript
static getAllServerConfigs(): Promise<Array<DomainServerConfig>>
```

Obtains the configurations of all domain servers. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md)&gt;&gt; | Promise used to return the domain server configuration obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let configParams: Record<string, Object> = {
  'uri': 'test.example.com',
  'port': 100
};
osAccount.DomainServerConfigManager.addServerConfig(configParams).then((
  serverConfig: osAccount.DomainServerConfig) => {
  console.info('add domain server configuration successfully, the added config: ' + JSON.stringify(serverConfig));
  osAccount.DomainServerConfigManager.getAllServerConfigs().then((data: Array<osAccount.DomainServerConfig>) => {
    console.info('get all domain server configuration successfully, return config: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`get all domain server configuration failed, code is ${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`add server configuration failed, code is ${err.code}, message is ${err.message}`);
});
```

## getServerConfig

```TypeScript
static getServerConfig(configId: string): Promise<DomainServerConfig>
```

Obtains the domain server configuration. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configId | string | Yes | Server configuration ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md)&gt; | Promise used to return the domain server configuration obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| 12300212 | Server config not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let configParams: Record<string, Object> = {
  'uri': 'test.example.com',
  'port': 100
};
osAccount.DomainServerConfigManager.addServerConfig(configParams).then((
  serverConfig: osAccount.DomainServerConfig) => {
  console.info('add domain server configuration successfully, the added config: ' + JSON.stringify(serverConfig));
  osAccount.DomainServerConfigManager.getServerConfig(serverConfig.id).then((data: osAccount.DomainServerConfig) => {
    console.info('get domain server configuration successfully, return config: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`get domain server configuration failed, code is ${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`add server configuration failed, code is ${err.code}, message is ${err.message}`);
});
```

## removeServerConfig

```TypeScript
static removeServerConfig(configId: string): Promise<void>
```

Removes domain server configuration. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configId | string | Yes | Server configuration ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| 12300212 | Server config not found. |
| 12300214 | Server config has been associated with an account. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let configParams: Record<string, Object> = {
  'uri': 'test.example.com',
  'port': 100
};
osAccount.DomainServerConfigManager.addServerConfig(configParams).then((
  serverConfig: osAccount.DomainServerConfig) => {
  console.info('add domain server configuration successfully, the added config: ' + JSON.stringify(serverConfig));
  osAccount.DomainServerConfigManager.removeServerConfig(serverConfig.id);
  console.info('remove domain server configuration successfully');
}).catch((err: BusinessError) => {
  console.error(`add server configuration failed, code is ${err.code}, message is ${err.message}`);
});
```

## updateServerConfig

```TypeScript
static updateServerConfig(configId: string, parameters: Record<string, Object>): Promise<DomainServerConfig>
```

Updates the domain server configuration. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configId | string | Yes | Server configuration ID. |
| parameters | Record&lt;string, Object&gt; | Yes | Domain server configuration parameters, which are used to configure the connection information of the domain server. The parameters include the server address and port number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md)&gt; | Promise used to return the updated domain server configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid server config parameters. |
| 12300211 | Server unreachable. |
| 12300212 | Server config not found. |
| 12300213 | Server config already exists. |
| 12300214 | Server config has been associated with an account. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let configParams: Record<string, Object> = {
  'uri': 'test.example.com',
  'port': 100
};
osAccount.DomainServerConfigManager.addServerConfig(configParams).then((
  serverConfig: osAccount.DomainServerConfig) => {
  console.info('add domain server configuration successfully, the added config: ' + JSON.stringify(serverConfig));
  osAccount.DomainServerConfigManager.updateServerConfig(serverConfig.id, configParams).then((data) => {
    console.info('update domain server configuration successfully, return config: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`update domain server configuration failed, code is ${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`add server configuration failed, code is ${err.code}, message is ${err.message}`);
});
```
