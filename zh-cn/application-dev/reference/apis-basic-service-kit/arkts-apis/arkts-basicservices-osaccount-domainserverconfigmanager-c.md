# DomainServerConfigManager

域服务器配置管理类。

**起始版本：** 18

<!--Device-osAccount-class DomainServerConfigManager--><!--Device-osAccount-class DomainServerConfigManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

<a id="addserverconfig"></a>
## addServerConfig

```TypeScript
static addServerConfig(parameters: Record<string, Object>): Promise<DomainServerConfig>
```

添加域服务器配置。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

<!--Device-DomainServerConfigManager-static addServerConfig(parameters: Record<string, Object>): Promise<DomainServerConfig>--><!--Device-DomainServerConfigManager-static addServerConfig(parameters: Record<string, Object>): Promise<DomainServerConfig>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameters | Record&lt;string, Object&gt; | 是 | 表示域服务器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DomainServerConfig&gt; | Promise对象，返回新添加的域服务器配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid server config parameters. |
| 12300211 | Server unreachable. |
| 12300213 | Server config already exists. |
| 12300215 | The number of server config reaches the upper limit. |

**示例：**

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

<a id="getaccountserverconfig"></a>
## getAccountServerConfig

```TypeScript
static getAccountServerConfig(domainAccountInfo: DomainAccountInfo): Promise<DomainServerConfig>
```

获取目标域账号的服务器配置。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

<!--Device-DomainServerConfigManager-static getAccountServerConfig(domainAccountInfo: DomainAccountInfo): Promise<DomainServerConfig>--><!--Device-DomainServerConfigManager-static getAccountServerConfig(domainAccountInfo: DomainAccountInfo): Promise<DomainServerConfig>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 表示目标域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DomainServerConfig&gt; | Promise对象，返回目标账号的域服务器配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Domain account not found. |

**示例：**

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

<a id="getallserverconfigs"></a>
## getAllServerConfigs

```TypeScript
static getAllServerConfigs(): Promise<Array<DomainServerConfig>>
```

获取所有域服务器配置。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

<!--Device-DomainServerConfigManager-static getAllServerConfigs(): Promise<Array<DomainServerConfig>>--><!--Device-DomainServerConfigManager-static getAllServerConfigs(): Promise<Array<DomainServerConfig>>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DomainServerConfig&gt;&gt; | Promise对象，返回获取的所有域服务器配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

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

<a id="getserverconfig"></a>
## getServerConfig

```TypeScript
static getServerConfig(configId: string): Promise<DomainServerConfig>
```

获取域服务器配置。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

<!--Device-DomainServerConfigManager-static getServerConfig(configId: string): Promise<DomainServerConfig>--><!--Device-DomainServerConfigManager-static getServerConfig(configId: string): Promise<DomainServerConfig>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configId | string | 是 | 表示服务器配置标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DomainServerConfig&gt; | Promise对象，返回获取的域服务器配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| 12300212 | Server config not found. |

**示例：**

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

<a id="removeserverconfig"></a>
## removeServerConfig

```TypeScript
static removeServerConfig(configId: string): Promise<void>
```

删除域服务器配置。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

<!--Device-DomainServerConfigManager-static removeServerConfig(configId: string): Promise<void>--><!--Device-DomainServerConfigManager-static removeServerConfig(configId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configId | string | 是 | 表示服务器配置标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| 12300212 | Server config not found. |
| 12300214 | Server config has been associated with an account. |

**示例：**

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

<a id="updateserverconfig"></a>
## updateServerConfig

```TypeScript
static updateServerConfig(configId: string, parameters: Record<string, Object>): Promise<DomainServerConfig>
```

更新域服务器配置。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_DOMAIN_ACCOUNT_SERVER_CONFIGS

<!--Device-DomainServerConfigManager-static updateServerConfig(configId: string, parameters: Record<string, Object>): Promise<DomainServerConfig>--><!--Device-DomainServerConfigManager-static updateServerConfig(configId: string, parameters: Record<string, Object>): Promise<DomainServerConfig>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configId | string | 是 | 表示服务器配置标识。 |
| parameters | Record&lt;string, Object&gt; | 是 | 表示域服务器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DomainServerConfig&gt; | Promise对象，返回更新后的域服务器配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid server config parameters. |
| 12300211 | Server unreachable. |
| 12300212 | Server config not found. |
| 12300213 | Server config already exists. |
| 12300214 | Server config has been associated with an account. |

**示例：**

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

