# getGlobalProxy（系统接口）

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

<a id="getglobalproxy"></a>
## getGlobalProxy

```TypeScript
function getGlobalProxy(admin: Want, callback: AsyncCallback<connection.HttpProxy>): void
```

获取网络全局代理，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md#getglobalproxysync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function getGlobalProxy(admin: Want, callback: AsyncCallback<connection.HttpProxy>): void--><!--Device-networkManager-function getGlobalProxy(admin: Want, callback: AsyncCallback<connection.HttpProxy>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;connection.HttpProxy&gt; | 是 | 回调函数。当接口调用成功，err为null，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

networkManager.getGlobalProxy(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to get network global proxy. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting network global proxy, result : ${JSON.stringify(result)}`);
});

```


<a id="getglobalproxy-1"></a>
## getGlobalProxy

```TypeScript
function getGlobalProxy(admin: Want): Promise<connection.HttpProxy>
```

获取网络全局代理，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md#getglobalproxysync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function getGlobalProxy(admin: Want): Promise<connection.HttpProxy>--><!--Device-networkManager-function getGlobalProxy(admin: Want): Promise<connection.HttpProxy>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;connection.HttpProxy&gt; | Promise used to return the global HTTP proxy information obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

networkManager.getGlobalProxy(wantTemp).then(() => {
  console.info(`Succeeded in getting network global proxy`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get network global proxy. Code: ${err.code}, message: ${err.message}`);
});

```

