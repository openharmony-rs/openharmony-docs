# getOnlineUpdater（系统接口）

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getOnlineUpdater

```TypeScript
function getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater
```

获取在线升级对象，可用于在线检查新版本、下载升级包、安装升级包等操作。适用于设备厂商的OTA(详见[术语](../../../basic-services/update/update-kit-term.md))升级客户端应用、在线系统升级等场景，帮助用户及时获取系统更新，提升升级效率和用户体验。

**原理说明**：

该方法通过系统服务接口获取在线升级对象，该对象提供检查新版本、下载升级包、安装升级包等核心功能。

**约束和限制**：

- 检查新版本和下载升级包都必须依赖设备厂商部署的升级包管理服务器。

**起始版本：** 9

<!--Device-update-function getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater--><!--Device-update-function getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeInfo | [UpgradeInfo](arkts-basicservices-update-upgradeinfo-i-sys.md) | 是 | 升级对象信息（UpgradeInfo），用于标识调用方和升级业务类型。upgradeApp字段为调用方包名，格式为com.xxx.xxx.xxx，长度范围[1，255]，单位：字符。每段长度范围[1，64]，单位：字符。仅支持字母、数字和点号，每段必须以字母开头，不能包含连续点号或以点号开头结尾，超出范围或格式错误时抛出异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Updater](arkts-basicservices-update-updater-i-sys.md) | 用于执行在线升级相关操作的工具类对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };  
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

```

