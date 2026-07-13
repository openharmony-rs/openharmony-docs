# getOnlineUpdater（系统接口）

## getOnlineUpdater

```TypeScript
function getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater
```

获取在线升级对象。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeInfo | UpgradeInfo | 是 | 升级对象信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Updater | 升级对象。 |

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

