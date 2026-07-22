# getLocalUpdater（系统接口）

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getLocalUpdater

```TypeScript
function getLocalUpdater(): LocalUpdater
```

获取本地升级对象，用于从本地存储设备（如SD卡）执行系统升级。调用此方法后，系统返回LocalUpdater工具类对象，提供本地升级包校验、安装等功能。

典型流程为：开发者准备升级包（格式为.zip或.bin）和证书文件（格式为.cert或.der） → 系统校验包签名和完整性 → 系统安装升级包 → 系统重启以应用新版本。

**原理说明**：

该方法获取本地升级工具对象，封装了升级包校验（验证数字签名、文件完整性、版本兼容性）和安装（解压写入系统分区）等功能。本地升级不依赖网络，从设备本地存储读取升级包。

**约束和限制**：

- 升级包必须从设备厂商官网或官方渠道下载，确保来源可信。  
- 安装前必须先校验升级包（调用verifyUpgradePackage），未校验的包可能导致系统损坏。  
- 升级过程中设备会重启，应用需做好状态保存。  
- 调用getLocalUpdater相关接口时，需要权限ohos.permission.UPDATE_SYSTEM。  
- 升级包文件路径长度不超过255字符。超出255字符时将抛出异常。

**起始版本：** 9

<!--Device-update-function getLocalUpdater(): LocalUpdater--><!--Device-update-function getLocalUpdater(): LocalUpdater-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalUpdater](arkts-basicservices-update-localupdater-i-sys.md) | 用于执行本地升级相关操作的工具类对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();

```

