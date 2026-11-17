# getCertManagerConfig（系统接口）

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getCertManagerConfig

```TypeScript
function getCertManagerConfig(configNames: Array<string>) : Promise<Array<ConfigItem>>
```

查询证书管理系统配置信息。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function getCertManagerConfig(configNames: Array<string>) : Promise<Array<ConfigItem>>--><!--Device-certificateManager-function getCertManagerConfig(configNames: Array<string>) : Promise<Array<ConfigItem>>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configNames | Array&lt;string&gt; | 是 | 证书管理配置项名称。<br>最大长度为16且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ConfigItem](arkts-devicecertificate-certificatemanager-configitem-i-sys.md)&gt;&gt; | 返回配置数据的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. <br> The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [17500011](../errorcode-certManager.md#17500011-入参校验失败) | The input parameters validation failed. <br> Possible causes: The length of configNames exceeds the limit, or the array is empty, or the array element value is invalid. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed; <br>2. Memory operation error; 3. File operation error. Please try again. |
