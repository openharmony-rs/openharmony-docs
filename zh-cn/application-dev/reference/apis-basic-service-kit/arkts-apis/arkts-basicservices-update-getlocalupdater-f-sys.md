# getLocalUpdater（系统接口）

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getLocalUpdater

```TypeScript
function getLocalUpdater(): LocalUpdater
```

获取本地升级对象。

**起始版本：** 9

<!--Device-update-function getLocalUpdater(): LocalUpdater--><!--Device-update-function getLocalUpdater(): LocalUpdater-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalUpdater](arkts-basicservices-update-localupdater-i-sys.md) | 本地升级对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();

```

