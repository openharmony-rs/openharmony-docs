# @ohos.enterprise.restrictions （限制类策略）
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

本模块提供设置通用限制类策略能力。可以全局禁用和解除禁用蓝牙、HDC、USB、Wi-Fi等特性。

> **说明**：
>
> 本模块首批接口从API version 12 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../mdm/mdm-kit-guide.md)。

## 导入模块

```ts
import { restrictions } from '@kit.MDMKit';
```

## restrictions.setDisallowedPolicy

setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void

设置禁用/启用某特性。 

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或者 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS<sup>15+</sup> 或者 ohos.permission.ENTERPRISE_MANAGE_NETWORK（设置不同特性所需权限不同，具体请参考表1）

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)。

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                       |
| feature  | string                                                  | 是   | 支持设置的特性清单参考表1。<br/> **说明：** 从API version 15开始，应用申请权限ohos.permission.PERSONAL_MANAGE_RESTRICTIONS并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口设置以下特性：bluetooth、hdc、microphone、usb、wifi、tethering、camera<!--RP3--><!--RP3End-->，从API版本26.0.0开始，新增支持使用此接口设置mtpServer特性。|
| disallow | boolean                                                 | 是   | true表示禁止使用，false表示允许使用。                        |

**表1 支持设置的特性清单：**
|特性|说明|需要权限|
|--------------|---------------------|--------------|
|bluetooth|设备蓝牙能力。当已经通过[addDisallowedBluetoothDevices](js-apis-enterprise-bluetoothManager.md#bluetoothmanageradddisallowedbluetoothdevices20)接口或者[addAllowedBluetoothDevices](js-apis-enterprise-bluetoothManager.md#bluetoothmanageraddallowedbluetoothdevices)接口设置了蓝牙设备禁用名单或者允许名单，再通过本接口禁用设备蓝牙能力，会优先生效禁用设备蓝牙能力。直到设备蓝牙能力启用后，禁止或允许名单才会生效。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|modifyDateTime|设备修改系统时间能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|printer|设备打印能力，在API version 23之前仅支持PC/2in1设备使用，从API version 23开始支持PC/2in1、Phone、Tablet设备。本接口禁用了设备打印能力时，通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)接口开启某用户的打印能力，该用户下的打印能力仍然被禁用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|hdc|被其他设备通过hdc连接、调试的能力。设置禁用后，其他设备无法通过hdc连接、调试此设备。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|microphone|设备麦克风能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|fingerprint|设备指纹认证能力。当已经通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)设置了某用户禁用设备指纹认证能力时，再通过本接口启用设备指纹认证能力，会报策略冲突。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|usb|设备USB能力。禁用后外接的USB设备无法使用，即在当前设备为HOST模式时，无法外接其他DEVICE设备。<br/>以下四种情况再通过本接口禁用设备USB能力，会报策略冲突。<br/>1）通过[addAllowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageraddallowedusbdevices)接口添加了USB设备可用名单。<br/>2）通过[setUsbStorageDeviceAccessPolicy](js-apis-enterprise-usbManager.md#usbmanagersetusbstoragedeviceaccesspolicy)接口设置了USB存储设备访问策略为只读/禁用。<br/>3）通过[addDisallowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageradddisallowedusbdevices14)接口添加了禁止使用的USB设备类型。<br/>4）通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)接口禁用了某用户USB存储设备写入能力。<br/>5）通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口（feature参数传入usbSerial）禁用了USB转串口。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|wifi|设备Wi-Fi能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|tethering<sup>14+</sup>|网络共享能力（设备已有网络共享给其他设备的能力，即共享热点能力）。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|inactiveUserFreeze<sup>14+</sup>|非活跃用户运行能力。禁用后，非UIAbility进程一般不会被冻结，UIAbility申请短时任务、长时任务、延迟任务或能效资源等后台运行任务也不会被冻结。当前仅支持PC/2in1设备使用。企业空间场景下，系统切换到企业空间用户，个人空间用户属于非活跃用户。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|camera<sup>14+</sup>|设备相机能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|mtpClient<sup>18+</sup>|MTP客户端能力(包含读取和写入)，当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。当已经通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)设置了某用户禁用MTP客户端写入能力时，再通过本接口禁用MTP客户端能力，会报策略冲突。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|mtpServer<sup>18+</sup>|MTP服务端能力，当前仅支持Phone、Tablet设备使用。|API version 26.0.0之前：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS，API version 26.0.0开始：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|sambaClient<sup>20+</sup>|samba客户端能力，当前仅支持PC/2in1设备使用。samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。SMB协议是客户机/服务器型协议，客户机通过该协议可以访问服务器上的共享文件系统、打印机及其他资源。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|sambaServer<sup>20+</sup>|samba服务端能力，当前仅支持PC/2in1设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|backupAndRestore<sup>20+</sup>|备份和恢复能力，禁用后设备的"设置--系统--备份和恢复"、"设置--云空间"置灰，当前仅支持手机、平板使用。如果要完全禁用设备的备份和恢复能力，建议同时调用[applicationManager.addDisallowedRunningBundlesSync](./js-apis-enterprise-applicationManager.md#applicationmanageradddisallowedrunningbundlessync)接口禁止具备备份和恢复能力的应用运行，如备份和恢复、手机助手、云空间应用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|maintenanceMode<sup>20+</sup>|设备维修模式能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|mms<sup>20+</sup>|multimedia messaging service，设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|sms<sup>20+</sup>|short messaging service，设备接收、发送短信的能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|mobileData<sup>20+</sup>|蜂窝数据能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_NETWORK|
|airplaneMode<sup>20+</sup>|飞行模式能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_NETWORK|
|vpn<sup>20+</sup>|Virtual Private Network（虚拟专用网络），VPN能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|notification<sup>20+</sup>|设备通知能力。禁用后，由系统应用和三方应用发出的通知将不会显示，而系统服务通知能力不受影响。当此设备已经通过[addAllowedNotificationBundles](./js-apis-enterprise-applicationManager.md#applicationmanageraddallowednotificationbundles)设置了应用通知白名单之后，再通过此接口禁用设备通知能力，会抛出错误码9200010。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|nfc<sup>20+</sup>|Near Field Communication（近距离无线通信），NFC能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|privateSpace<sup>20+</sup>|创建隐私空间能力，当前仅支持手机、平板使用。对已创建的隐私空间无效。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|telephoneCall<sup>20+</sup>|设备通话能力，禁用后电话无法呼入和呼出。当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|appClone<sup>21+</sup>|[应用分身能力](../../quick-start/app-clone.md)，禁用后无法创建应用分身。对已创建的应用分身无效。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|externalStorageCard<sup>21+</sup> |外置存储能力，禁用后设备无法使用外置存储，并且当前已连接的外置存储会被卸载。如果外置存储卸载时有文件正在被使用，可能会导致卸载失败，返回9200013错误码。<br/>外置存储禁用后重新启用，需要手动重新连接外置存储。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|randomMac<sup>21+</sup>|Wi-Fi连接时使用随机MAC能力，设置禁用后，连接Wi-Fi仅能使用设备物理MAC。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|unmuteDevice<sup>22+</sup>|设备媒体播放声音能力，设置禁用后，设备媒体播放将静音，[蜂窝通话](../../media/audio/audio-call-overview.md)能力不受影响。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|hdcRemote<sup>22+</sup>|设备通过hdc调试其他设备的能力，当前仅支持PC/2in1设备设置。设置禁用后，无法通过hdc调试手机、平板、PC、智能手表等设备。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|virtualService<sup>23+</sup>|设备虚拟化服务能力，即利用硬件资源的冗余，以虚拟化方式运行其他平台（如Linux、Windows）的能力。设置禁用设备虚拟化服务能力时，建议同时卸载与虚拟化服务相关的应用，并禁止其再次安装。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|usbSerial<sup>24+</sup>|设备USB转串口能力。禁用后外接的USB转串口设备无法使用。以下两种情况再通过本接口禁用设备USB转串口能力，会报策略冲突。<br/>1）通过[addAllowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageraddallowedusbdevices)接口添加了USB设备可用名单。<br/>2）通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口（feature参数传入usb）禁用了USB设备。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
<!--RP1--><!--RP1End-->

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200013  | The enterprise management policy has been successfully set, but the function has not taken effect in real time. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  restrictions.setDisallowedPolicy(wantTemp, 'printer', true);
  console.info('Succeeded in setting printer disabled');
} catch (err) {
  console.error(`Failed to set printer disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicy

getDisallowedPolicy(admin: Want \| null, feature: string): boolean

查询某特性是否被禁用。 

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或者 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS<sup>15+</sup> 或者 ohos.permission.ENTERPRISE_MANAGE_NETWORK（查询不同特性所需权限不同，具体请参考表2）

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                       |
| feature | string                                                  | 是   | 支持查询的特性清单参考下表2。 <br/> **说明：** 从API version 15开始，应用申请权限ohos.permission.PERSONAL_MANAGE_RESTRICTIONS并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口获取以下特性状态：bluetooth、hdc、microphone、usb、wifi、tethering、camera<!--RP4--><!--RP4End-->，从API版本26.0.0开始，新增支持使用此接口获取mtpServer特性状态。|

**表2 支持查询的特性清单：**
|特性|说明|需要权限|
|--------------|---------------------|--------------|
|bluetooth|设备蓝牙能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|modifyDateTime|设备修改系统时间能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|printer|设备打印能力，在API version 23之前仅支持PC/2in1设备使用，从API version 23开始支持PC/2in1、Phone、Tablet设备。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|hdc|被其他设备通过hdc连接、调试的能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|microphone|设备麦克风能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|fingerprint|设备指纹认证能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|usb|设备USB能力。禁用后外接的USB设备无法使用，即在当前设备为HOST模式时，无法外接其他DEVICE设备。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|wifi|设备Wi-Fi能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|tethering<sup>14+</sup>|网络共享能力（设备已有网络共享给其他设备的能力，即共享热点能力）。 |ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|inactiveUserFreeze<sup>14+</sup>|非活跃用户运行能力。禁用后，非UIAbility进程一般不会被冻结，UIAbility申请短时任务、长时任务、延迟任务或能效资源等后台运行任务也不会被冻结。当前仅支持PC/2in1设备使用。企业空间场景下，系统切换到企业空间用户，个人空间用户属于非活跃用户。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|camera<sup>14+</sup>|设备相机能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|mtpClient<sup>18+</sup>|MTP客户端能力（包含读取和写入），当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|mtpServer<sup>18+</sup>|MTP服务端能力，当前仅支持Phone、Tablet设备使用。|API version 26.0.0之前：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS，API version 26.0.0开始：ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS|
|sambaClient<sup>20+</sup>|samba客户端能力，当前仅支持PC/2in1设备使用。samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。SMB协议是客户机/服务器型协议，客户机通过该协议可以访问服务器上的共享文件系统、打印机及其他资源。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|sambaServer<sup>20+</sup>|samba服务端能力，当前仅支持PC/2in1设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|backupAndRestore<sup>20+</sup>|备份和恢复能力，禁用后设备的"设置--系统--备份和恢复"、"设置--云空间"置灰，当前仅支持手机、平板使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|maintenanceMode<sup>20+</sup>|设备维修模式能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|mms<sup>20+</sup>|multimedia messaging service，设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|sms<sup>20+</sup>|short messaging service，设备接收、发送短信的能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|mobileData<sup>20+</sup>|蜂窝数据能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_NETWORK|
|airplaneMode<sup>20+</sup>|飞行模式能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_NETWORK|
|vpn<sup>20+</sup>|Virtual Private Network（虚拟专用网络），VPN能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|notification<sup>20+</sup>|设备通知能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|nfc<sup>20+</sup>|Near Field Communication（近距离无线通信），NFC能力，当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|privateSpace<sup>20+</sup>|创建隐私空间能力，当前仅支持手机、平板使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|telephoneCall<sup>20+</sup>|设备通话能力，禁用后电话无法呼入和呼出。当前仅支持手机、平板设备使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|appClone<sup>21+</sup>|[应用分身能力](../../quick-start/app-clone.md)，禁用后无法创建应用分身。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|externalStorageCard<sup>21+</sup> |外置存储能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|randomMac<sup>21+</sup>|Wi-Fi连接时使用随机MAC能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|unmuteDevice<sup>22+</sup>|设备媒体播放声音能力，设置禁用后，设备媒体播放将静音，[蜂窝通话](../../media/audio/audio-call-overview.md)能力不受影响。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|hdcRemote<sup>22+</sup>|设备通过hdc调试其他设备的能力，当前仅支持PC/2in1设备设置。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|virtualService<sup>23+</sup>|设备虚拟化服务能力。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
|usbSerial<sup>24+</sup>|设备USB转串口能力。禁用后外接的USB转串口设备无法使用。|ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS|
<!--RP2--><!--RP2End-->

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回true表示feature对应的某种特性被禁用，false表示feature对应的某种特性未被禁用。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicy(wantTemp, 'printer');
  console.info(`Succeeded in querying whether the printing function is disabled. Disabled status: ${result}`);
} catch (err) {
  console.error(`Failed to get printer disabled status. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setDisallowedPolicyForAccount<sup>14+</sup>

setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void

设置禁用/启用指定用户的某特性。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)。

**参数：**

<!--Table: 10%; 10%; 10%; 70%-->
| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| feature  | string                                                  | 是   | feature名称。<br/>- fingerprint：设备指纹认证能力，当前仅支持PC/2in1设备使用。使用此参数时有以下规则：<br/>1. 通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用了设备指纹认证能力，再使用本接口传入此参数，会报策略冲突。<br/>2. 通过本接口设置禁用/启用指定用户的设备指纹认证能力后，再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用设备指纹认证能力时，后者会覆盖前者的策略。此后再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口启用设备指纹认证能力，则所有用户都允许使用设备指纹认证能力。<br/>- print<sup>20+</sup>：设备打印能力，在API version 23之前仅支持PC/2in1设备使用，从API version 23开始支持PC/2in1、Phone、Tablet设备。如果使用本接口禁用了指定用户的设备打印能力，再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口启用设备打印能力，该用户下的设备打印能力仍然被禁用。<br/>- mtpClient<sup>20+</sup>：MTP客户端能力（仅包含写入），当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。当已经通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用了设备MTP客户端能力时，再通过本接口禁用某用户MTP客户端写入能力，会报策略冲突。<br/>- usbStorageDeviceWrite<sup>20+</sup>：USB存储设备写入能力，当前仅支持PC/2in1企业设备使用。<!--RP5--><!--RP5End--><br/>  以下三种情况再通过本接口禁用某用户USB存储设备写入能力，会报策略冲突。<br/>  1）通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口设置了设备USB能力禁用。<br/>  2）通过[setUsbStorageDeviceAccessPolicy](js-apis-enterprise-usbManager.md#usbmanagersetusbstoragedeviceaccesspolicy)接口设置了USB存储设备访问策略为只读/禁用。<br/>  3）通过[addDisallowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageradddisallowedusbdevices14)接口添加了存储类型的USB设备禁用。 <br/>- diskRecoveryKey<sup>20+</sup>：恢复[密钥导出](../../security/UniversalKeystoreKit/huks-export-key-arkts.md)能力，当前仅支持PC/2in1设备使用。<br/>- sudo<sup>20+</sup>：superuser do，表示以超级用户执行，当前仅支持PC/2in1设备使用。禁用后企业空间或个人空间不能以超级用户执行。<br/>- distributedTransmissionOutgoing<sup>20+</sup>：设备间单向传输数据的能力（仅包含向其他设备传输数据）。<br/>- openFileBoost<sup>23+</sup>：<!--RP6-->文件打开加速能力<!--RP6End-->，为应用提供文件打开加速状态感知能力。应用可以通过接入对应API，感知文件的加速状态，进而应用可以实现对已加速文件给出独特的UI（user interface）标识等功能，优化用户文件打开体验，当前仅支持PC/2in1设备使用。 |
| disallow | boolean                                                 | 是   | true表示禁用，false表示启用。                        |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | the administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  restrictions.setDisallowedPolicyForAccount(wantTemp, 'fingerprint', true, 100);
  console.info('Succeeded in setting fingerprint disabled');
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicyForAccount<sup>14+</sup>

getDisallowedPolicyForAccount(admin: Want | null, feature: string, accountId: number): boolean

获取指定用户的某特性状态。 

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

<!--Table: 10%; 20%; 10%; 60%-->
| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| feature | string                                                  | 是   | feature名称。<br/>- fingerprint：设备指纹认证能力，当前仅支持PC/2in1设备使用。使用此参数时有以下规则：当已经通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)接口设置禁用/启用指定用户的设备指纹认证能力后，再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用设备指纹认证能力时，后者会覆盖前者的策略。即此时调用本接口结果为false。<br/>- mtpClient<sup>20+</sup>：MTP客户端能力（仅包含写入），当前仅支持PC/2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。<br/>- usbStorageDeviceWrite<sup>20+</sup>：USB存储设备写入能力，当前仅支持PC/2in1企业设备使用。<br/>- diskRecoveryKey<sup>20+</sup>：恢复[密钥导出](../../security/UniversalKeystoreKit/huks-export-key-arkts.md)能力，当前仅支持PC/2in1设备使用。<br/>- sudo<sup>20+</sup>：superuser do，表示以超级用户执行，当前仅支持PC/2in1设备使用。禁用后企业空间或个人空间不能以超级用户执行。<br/>- distributedTransmissionOutgoing<sup>20+</sup>：设备间单向传输数据的能力（仅包含向其他设备传输数据）。<br/>- print<sup>20+</sup>：设备打印能力，在API version 23之前仅支持PC/2in1设备使用，从API version 23开始支持PC/2in1、Phone、Tablet设备。如果使用[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用了设备打印能力，再通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)接口启用某用户下的设备打印能力，通过本接口查询结果是该用户已启用打印能力，但实际打印能力已被禁用。<br/>- openFileBoost<sup>23+</sup>：<!--RP6-->文件打开加速能力<!--RP6End-->，为应用提供文件打开加速状态感知能力。应用可以通过接入对应API，感知文件的加速状态，进而应用可以实现对已加速文件给出独特的UI（user interface）标识等功能，优化用户文件打开体验，当前仅支持PC/2in1设备使用。 |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回true表示参数feature对应的特性被禁用，false表示参数feature对应的特性未被禁用。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | the administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, 'fingerprint', 100);
  console.info(`Succeeded in querying is the fingerprint function disabled : ${result}`);
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.addDisallowedListForAccount<sup>14+</sup>

addDisallowedListForAccount(admin: Want, feature: string, list: Array\<string>, accountId: number): void

为指定用户添加禁止使用某特性的应用名单。指定用户下，添加到名单中的应用不允许使用指定的特性能力。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [合并](../../mdm/mdm-kit-multi-mdm.md#规则4合并)。

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| feature  | string                                                  | 是   | feature名称。<br/>- snapshotSkip：屏幕快照能力。 |
| list | Array\<string>                                                 | 是   | 包名等内容的名单集合。                      |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let valueList:Array<string> = ["com.xx.aa.", "com.xx.bb"];
try {
  // 参数需根据实际情况进行替换
  restrictions.addDisallowedListForAccount(wantTemp, 'snapshotSkip', valueList, 100);
  console.info('Succeeded in adding disallowed snapshotSkip feature');
} catch (err) {
  console.error(`Failed to add disallowed snapshotSkip feature. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.removeDisallowedListForAccount<sup>14+</sup>

removeDisallowedListForAccount(admin: Want, feature: string, list: Array\<string>, accountId: number): void

为指定用户移除禁止使用某特性的应用名单。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [合并](../../mdm/mdm-kit-multi-mdm.md#规则4合并)。

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| feature  | string                                                  | 是   | feature名称。<br/>- snapshotSkip：屏幕快照能力。 |
| list | Array\<string>                                                 | 是   | 包名等内容的名单集合。                       |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let valueList:Array<string> = ["com.xx.aa.", "com.xx.bb"];
try {
  // 参数需根据实际情况进行替换
  restrictions.removeDisallowedListForAccount(wantTemp, 'snapshotSkip', valueList, 100);
  console.info('Succeeded in removing disallowed snapshotSkip feature');
} catch (err) {
  console.error(`Failed to remove disallowed snapshotSkip feature. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedListForAccount<sup>14+</sup>

getDisallowedListForAccount(admin: Want, feature: string, accountId: number): Array\<string>

获取指定用户禁止使用某特性的应用名单。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| feature | string                                                  | 是   | feature名称。<br/>- snapshotSkip：屏幕快照能力。 |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Array\<string> | 用户已添加的禁用某特征的应用名单。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: Array<string> = restrictions.getDisallowedListForAccount(wantTemp, 'snapshotSkip', 100);
  console.info('Succeeded in querying disallowed list for account');
} catch (err) {
  console.error(`Failed to query disallowed list for account. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setUserRestriction<sup>20+</sup>

setUserRestriction(admin: Want, settingsItem: string, restricted: boolean): void

设置用户行为的限制规则。

**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)。

**参数：**

<!--Table: 10%; 10%; 10%; 70%-->
| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| settingsItem  | string                                                  | 是   | 行为名称。<br/>- setApn：APN设置，当前仅支持手机、平板使用。<br/>- powerLongPress：长按电源键打开电源菜单，当前仅支持手机、平板使用。<br/>- setEthernetIp：修改以太网IP地址，当前仅支持PC/2in1设备使用。<br/>- setDeviceName：修改设备名称，当前仅支持PC/2in1设备、手机、平板使用。禁用后，PC/2in1设备的设置中以下设备名称无法修改，包括关于本机、蓝牙、多设备协同->星闪。手机、平板设备设置中的关于本机、蓝牙、个人热点的设备名称无法修改。<br/>- setBiometricsAndScreenLock：修改锁屏密码，当前仅支持PC/2in1设备、手机、平板使用。|
| restricted | boolean                                                 | 是   | 是否禁用行为。true表示禁用，false表示不禁用。                       |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  restrictions.setUserRestriction(wantTemp, 'setApn', true);
  console.info('Succeeded in restricting from setting apn');
} catch (err) {
  console.error(`Failed to restrict from setting apn. Code is ${err.code}, message is ${err.message}`);
}
```
## restrictions.getUserRestricted<sup>20+</sup>

getUserRestricted(admin: Want, settingsItem: string): boolean

获取设置项的禁用状态。


**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

<!--Table: 10%; 10%; 10%; 70%-->
| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| settingsItem | string                                             | 是   | 指定设置项。<br/>- setEthernetIp：修改以太网IP地址，当前仅支持PC/2in1设备使用。<br/>- setDeviceName：修改设备名称，当前仅支持PC/2in1设备、手机、平板使用。PC/2in1设备设置中关于本机、蓝牙、多设备协同->星闪中的设备名称。手机、平板设备设置中关于本机、蓝牙、个人热点的设备名称。<br/>- setBiometricsAndScreenLock：修改锁屏密码，当前仅支持PC/2in1设备、手机、平板使用。|

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回指定设置项的禁用状态，true表示已禁用，false表示未禁用。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 入参需根据实际情况替换
  let result: boolean = restrictions.getUserRestricted(wantTemp, 'setEthernetIp');
  console.info('Succeeded in getting user restricted');
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setUserRestrictionForAccount<sup>23+</sup>

setUserRestrictionForAccount(admin: Want, settingsItem: string, accountId: number, restricted: boolean): void

设置指定用户行为的限制规则。

**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)。

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| settingsItem  | string                                                  | 是   | 行为名称。<br/>- modifyWallpaper：修改壁纸，包含锁屏壁纸和桌面壁纸。|
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。                       |
| restricted | boolean                                                 | 是   | 是否禁用行为。true表示禁用，false表示不禁用。                       |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let userId = 100;
let settingsItem: string = "modifyWallpaper";
try {
  restrictions.setUserRestrictionForAccount(wantTemp, settingsItem, userId, true);
  console.info('Succeeded in restricting from setting modifyWallpaper');
} catch (err) {
  console.error(`Failed to restrict from setting modifyWallpaper. Code is ${err.code}, message is ${err.message}`);
}
```
## restrictions.getUserRestrictedForAccount<sup>23+</sup>

getUserRestrictedForAccount(admin: Want | null, settingsItem: string, accountId: number): boolean

获取指定用户设置项的禁用状态。


**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                   |
| settingsItem | string                                             | 是   | 指定设置项。<br/>- modifyWallpaper：修改壁纸，包含锁屏壁纸和桌面壁纸。|
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。                       |


**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回指定设置项的禁用状态，true表示已禁用，false表示未禁用。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 需根据实际情况替换
let userId = 100;
let settingsItem: string = "modifyWallpaper";
try {
  let result: boolean = restrictions.getUserRestrictedForAccount(wantTemp, settingsItem, userId);
  console.info(`Succeeded in getting user restricted: ${result}`);
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}
```
## restrictions.setDisallowedPolicy<sup>24+</sup>

setDisallowedPolicy(admin: Want, feature: FeatureForDevice, disallow: boolean): void

设置禁用/启用指定设备特性，禁用后相关设备特性无法被使用。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)。

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                       |
| feature  | [FeatureForDevice](#featurefordevice24)                                                  | 是   | 指定要禁用或允许的设备特性。<br/> **说明：** 应用申请权限ohos.permission.PERSONAL_MANAGE_RESTRICTIONS并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口设置以下特性：[FeatureForDevice.WIFI_P2P](#featurefordevice24)。 |
| disallow | boolean                                                 | 是   | true表示禁止使用，false表示允许使用。                        |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured. |
| 9200013  | The enterprise management policy has been successfully set, but the function has not taken effect in real time. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  restrictions.setDisallowedPolicy(wantTemp, restrictions.FeatureForDevice.WIFI_P2P, true);
  console.info('Succeeded in setting Wi-Fi P2P disabled');
} catch (err) {
  console.error(`Failed to set Wi-Fi P2P disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicy<sup>24+</sup>

getDisallowedPolicy(admin: Want \| null, feature: FeatureForDevice): boolean

查询指定设备特性是否被禁用。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。                                       |
| feature | [FeatureForDevice](#featurefordevice24)                                                  | 是   | 指定要查询的设备特性。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回true表示feature对应的设备特性被禁用，false表示feature对应的设备特性未被禁用。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: boolean = restrictions.getDisallowedPolicy(wantTemp, restrictions.FeatureForDevice.WIFI_P2P);
  console.info(`Succeeded in querying whether Wi-Fi P2P is disabled. Disabled status: ${result}`);
} catch (err) {
  console.error(`Failed to get Wi-Fi P2P disabled status. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setDisallowedPolicyForAccount

setDisallowedPolicyForAccount(admin: Want, feature: FeatureForAccount, disallow: boolean, accountId: number): void

设置禁用/启用指定用户的某特性。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**冲突规则：** [从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)。

**参数：**

| 参数名    | 类型                                                    | 必填 | 说明                                                         |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| feature   | [FeatureForAccount](#featureforaccount)                 | 是   | 要禁用或允许的用户特性。<br>当feature值为SUPER_HUB时，如果已经通过[addUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddusernonstopapps22)接口将中转站添加到当前用户下不可关停的应用列表中，再调用本接口禁用中转站，会发生策略冲突，抛出9200010错误码。可以通过[removeUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremoveusernonstopapps22)接口将中转站从当前用户下不可关停的应用列表中移除来解决冲突。 |
| disallow  | boolean                                                 | 是   | true表示禁用，false表示启用。                                |
| accountId | number                                                  | 是   | 用户ID，取值范围：大于等于0。<br>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。<br>当feature值为SUPER_HUB时，accountId仅支持传入当前用户的用户ID，不支持跨用户设置。否则会抛出9200012错误码。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  restrictions.setDisallowedPolicyForAccount(wantTemp, restrictions.FeatureForAccount.SUPER_HUB, true, 100);
  console.info('Succeeded in setting super hub disabled');
} catch (err) {
  console.error(`Failed to set super hub disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicyForAccount

getDisallowedPolicyForAccount(admin: Want | null, feature: FeatureForAccount, accountId: number): boolean

获取指定用户的某特性状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型                                                         | 必填 | 说明                                                         |
| --------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| feature   | [FeatureForAccount](#featureforaccount)                      | 是   | 指定要查询的用户特性。 |
| accountId | number                                                       | 是   | 用户ID，取值范围：大于等于0。<br>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回true表示参数feature对应的特性被禁用，false表示参数feature对应的特性未被禁用。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicyForAccount(wantTemp, restrictions.FeatureForAccount.SUPER_HUB, 100);
  console.info(`Succeeded in querying whether the super hub is disabled: ${result}`);
} catch (err) {
  console.error(`Failed to get whether super hub is disabled. Code is ${err.code}, message is ${err.message}`);
}
```
## FeatureForDevice<sup>24+</sup>

设备特性枚举。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称                        | 值  | 说明    |
| ----------------------------| ----| ------------------------------- |
| WIFI_P2P   | 0   | Wi-Fi P2P（点对点连接），允许设备在没有接入点的情况下直接相互连接。禁用后，设备无法通过Wi-Fi P2P进行点对点连接，影响文件传输、游戏联机、屏幕共享等需要直接Wi-Fi连接的应用功能。 |
| LOCAL_INPUT   | 2   | 本地输入包含键盘、鼠标、触控板、触摸屏等。禁用后无法通过本地输入操作设备。重启后可以解除禁用。<br>**起始版本：** 26.0.0 |
| CORE_DUMP   | 6   | 创建文件转储。禁用后，无法通过任务管理器创建文件转储。<br>**起始版本：** 26.0.0 |

## FeatureForAccount

可为指定用户设置禁用/启用的特性的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

| 名称      | 值   | 说明     |
| --------- | ---- | -------- |
| MULTI_WINDOW | 0    | 系统多窗口。当前仅支持手机、平板设备使用，禁用后无法使用系统多窗口功能（分屏、一键分屏、智慧多窗、悬浮窗口）。若系统多窗口功能已开启，本次使用不受影响，但关闭后将无法再次使用。 |
| SUPER_HUB | 2    | 中转站。当前仅支持手机、平板设备使用，禁用后无法使用中转站功能。若中转站已开启，本次使用不受影响，但关闭后将无法再次使用。 |