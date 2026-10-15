# setWeakPinEnable

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## setWeakPinEnable

```TypeScript
function setWeakPinEnable(isEnable: boolean, fd?: number): void
```

使能弱密码库。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-securityManager-function setWeakPinEnable(isEnable: boolean, fd?: number): void--><!--Device-securityManager-function setWeakPinEnable(isEnable: boolean, fd?: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean | 是 | isEnable表示是否开启弱PIN校验。**true**表示使能。**false**表示禁用。 |
| fd | number | 否 | fd表示弱PIN文件的文件描述符。弱PIN使能时必选验证，禁用弱PIN验证时忽略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |

**示例**

弱密码库文件示例（weak_pin.txt），每行对应一个弱密码：

```TypeScript
123456
000000
111111
888888
666666
```

代码示例：

```TypeScript
import { securityManager } from '@kit.MDMKit';
import { fileIo } from '@kit.CoreFileKit';
 
// 需根据实际情况进行替换，弱密码文件需要放置在应用沙箱目录下
// 弱密码文件格式：每行对应一个弱密码，如123456、000000等
const filePath = '/data/storage/el1/base/weak_pin.txt';
let fd: number = fileIo.openSync(filePath, fileIo.OpenMode.READ_ONLY).fd;
try {
  securityManager.setWeakPinEnable(true, fd);
  console.info(`Succeeded in setting weak pin enable.`);
} catch (err) {
  console.error(`Failed to set weak pin enable. Code: ${err.code}, message: ${err.message}`);
} finally {
  fileIo.closeSync(fd);
}
```
