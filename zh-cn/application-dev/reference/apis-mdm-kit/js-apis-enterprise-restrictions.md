# @ohos.enterprise.restrictions （限制类策略）

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

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或者 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS<sup>15+</sup>

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager


**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                       |
| feature  | string                                                  | 是   | feature名称。<br/>- bluetooth：设备蓝牙能力。当已经通过[addDisallowedBluetoothDevices](js-apis-enterprise-bluetoothManager.md#bluetoothmanageradddisallowedbluetoothdevices20)接口或者[addAllowedBluetoothDevices](js-apis-enterprise-bluetoothManager.md#bluetoothmanageraddallowedbluetoothdevices)接口设置了蓝牙设备黑名单或者白名单，再通过本接口禁用设备蓝牙能力，会优先生效禁用设备蓝牙能力。直到设备蓝牙能力启用后，黑白名单才会生效。<br/>- modifyDateTime：设备修改系统时间能力，当前仅支持2in1设备使用。<br/>- printer：设备打印能力，当前仅支持2in1设备使用。<br/>- hdc：设备HDC能力。<br/>- microphone：设备麦克风能力。<br/>- fingerprint：设备指纹认证能力。当已经通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)设置了某用户禁用设备指纹认证能力时，再通过本接口启用设备指纹认证能力，会报策略冲突。<br/>- usb：设备USB能力。禁用后外接的USB设备无法使用，即在当前设备为HOST模式时，无法外接其他DEVICE设备。<br/>  以下四种情况再通过本接口禁用设备USB能力，会报策略冲突。<br/>  1）通过[addAllowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageraddallowedusbdevices)接口添加了USB设备可用白名单。<br/>  2）通过[setUsbStorageDeviceAccessPolicy](js-apis-enterprise-usbManager.md#usbmanagersetusbstoragedeviceaccesspolicy)接口设置了USB存储设备访问策略为只读/禁用。<br/>  3）通过[addDisallowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageradddisallowedusbdevices14)接口添加了禁止使用的USB设备类型。<br/>  4）通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)接口禁用了某用户USB存储设备写入能力。<br/>- wifi：设备WIFI能力。<br/>- tethering<sup>14+</sup>：网络共享能力（设备已有网络共享给其他设备的能力，即共享热点能力）。<br/>- inactiveUserFreeze<sup>14+</sup>：非活跃用户运行能力，当前仅支持2in1设备使用。企业空间场景下，系统切换到企业空间用户，个人空间用户属于非活跃用户。<br/>- camera<sup>14+</sup>：设备相机能力。<br/>- mtpClient<sup>18+</sup>：MTP客户端能力(包含读取和写入)，当前仅支持2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。当已经通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)设置了某用户禁用MTP客户端写入能力时，再通过本接口禁用MTP客户端能力，会报策略冲突。<br/>- mtpServer<sup>18+</sup>：MTP服务端能力，当前仅支持手机、平板、2in1设备使用。<br/>- sambaClient<sup>20+</sup>：samba客户端能力，当前仅支持2in1设备使用。samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。SMB协议是客户机/服务器型协议，客户机通过该协议可以访问服务器上的共享文件系统、打印机及其他资源。<br/>- sambaServer<sup>20+</sup>：samba服务端能力，当前仅支持2in1设备使用。<br/>- backupAndRestore<sup>20+</sup>：备份和恢复能力，禁用后设备的"设置--系统--备份和恢复"、"设置--云空间"置灰，当前仅支持手机、平板使用。如果要完全禁用设备的备份和恢复能力，建议同时调用[applicationManager.addDisallowedRunningBundlesSync](./js-apis-enterprise-applicationManager.md#applicationmanageradddisallowedrunningbundlessync)接口禁止具备备份和恢复能力的应用运行，如备份和恢复、手机助手、云空间应用。<br/>- maintenanceMode<sup>20+</sup>：设备维修模式能力，当前仅支持手机、平板、2in1设备使用。<br/>- mms<sup>20+</sup>：multimedia messaging service，设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。<br/>- sms<sup>20+</sup>：short messaging service，设备接收、发送短信的能力，当前仅支持手机、平板设备使用。<br/>- mobileData<sup>20+</sup>：蜂窝数据能力，当前仅支持手机、平板设备使用。<br/>- airplaneMode<sup>20+</sup>：飞行模式能力，当前仅支持手机、平板设备使用。<br/>- vpn<sup>20+</sup>：Virtual Private Network（虚拟专用网络），VPN能力。<br/>- notification<sup>20+</sup>：设备通知能力。禁用后，由三方应用自身发出的通知将不会显示。<br/>- nfc<sup>20+</sup>：Near Field Communication（近距离无线通信），NFC能力。<!--RP1--><!--RP1End--> <br/> **说明：** 从API version 15开始，应用申请权限ohos.permission.PERSONAL_MANAGE_RESTRICTIONS并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口设置以下特性：bluetooth、hdc、microphone、usb、wifi、tethering、camera<!--RP3--><!--RP3End-->。 |
| disallow | boolean                                                 | 是   | true表示禁止使用，false表示允许使用。                        |

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

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

try {
  restrictions.setDisallowedPolicy(wantTemp, 'printer', true);
  console.info('Succeeded in setting printer disabled');
} catch (err) {
  console.error(`Failed to set printer disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicy

getDisallowedPolicy(admin: Want, feature: string): boolean

获取某特性的禁用状态。 

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS 或者 ohos.permission.PERSONAL_MANAGE_RESTRICTIONS<sup>15+</sup>

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                       |
| feature | string                                                  | 是   | feature名称。<br/>- bluetooth：设备蓝牙能力。<br/>- modifyDateTime：设备修改系统时间能力，当前仅支持2in1设备使用。<br/>- printer：设备打印能力，当前仅支持2in1设备使用。<br/>- hdc：设备HDC能力。<br/>- microphone：设备麦克风能力。<br/>- fingerprint：设备指纹认证能力。<br/>- usb：设备USB能力。禁用后外接的USB设备无法使用，即在当前设备为HOST模式时，无法外接其他DEVICE设备。<br/>- wifi：设备WIFI能力。<br/>- tethering<sup>14+</sup>：网络共享能力（设备已有网络共享给其他设备的能力，即共享热点能力）。 <br/>- inactiveUserFreeze<sup>14+</sup>：非活跃用户运行能力，当前仅支持2in1设备使用。企业空间场景下，系统切换到企业空间用户，个人空间用户属于非活跃用户。<br/>- camera<sup>14+</sup>：设备相机能力。<br/>- mtpClient<sup>18+</sup>：MTP客户端能力（包含读取和写入），当前仅支持2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。<br/>- mtpServer<sup>18+</sup>：MTP服务端能力，当前仅支持手机、平板、2in1设备使用。<br/>- sambaClient<sup>20+</sup>：samba客户端能力，当前仅支持2in1设备使用。samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，由服务器及客户端程序构成。SMB（Server Messages Block，信息服务块）是一种在局域网上共享文件和打印机的一种通信协议，它为局域网内的不同计算机之间提供文件及打印机等资源的共享服务。SMB协议是客户机/服务器型协议，客户机通过该协议可以访问服务器上的共享文件系统、打印机及其他资源。<br/>- sambaServer<sup>20+</sup>：samba服务端能力，当前仅支持2in1设备使用。<br/>- backupAndRestore<sup>20+</sup>：备份和恢复能力，禁用后设备的"设置--系统--备份和恢复"、"设置--云空间"置灰，当前仅支持手机、平板使用。<br/>- maintenanceMode<sup>20+</sup>：设备维修模式能力，当前仅支持手机、平板、2in1设备使用。<br/>- mms<sup>20+</sup>：multimedia messaging service，设备接收、发送彩信的能力，当前仅支持手机、平板设备使用。<br/>- sms<sup>20+</sup>：short messaging service，设备接收、发送短信的能力，当前仅支持手机、平板设备使用。<br/>- mobileData<sup>20+</sup>：蜂窝数据能力，当前仅支持手机、平板设备使用。<br/>- airplaneMode<sup>20+</sup>：飞行模式能力，当前仅支持手机、平板设备使用。<br/>- vpn<sup>20+</sup>：Virtual Private Network（虚拟专用网络），VPN能力。<br/>- notification<sup>20+</sup>：设备通知能力。<br/>- nfc<sup>20+</sup>：Near Field Communication（近距离无线通信），NFC能力。<!--RP2--><!--RP2End--> <br/> **说明：** 从API version 15开始，应用申请权限ohos.permission.PERSONAL_MANAGE_RESTRICTIONS并[激活为自带设备管理应用](./js-apis-enterprise-adminManager.md#adminmanagerstartadminprovision15)，可以使用此接口获取以下特性状态：bluetooth、hdc、microphone、usb、wifi、tethering、camera<!--RP4--><!--RP4End-->。 |

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
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

try {
  let result: boolean = restrictions.getDisallowedPolicy(wantTemp, 'printer');
  console.info(`Succeeded in querying is the printing function disabled : ${result}`);
} catch (err) {
  console.error(`Failed to set printer disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.setDisallowedPolicyForAccount<sup>14+</sup>

setDisallowedPolicyForAccount(admin: Want, feature: string, disallow: boolean, accountId: number): void

设置禁用/启用指定用户的某特性。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                   |
| feature  | string                                                  | 是   | feature名称。<br/>- fingerprint：设备指纹认证能力，当前仅支持2in1设备使用。使用此参数时有以下规则：<br/>1. 通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用了设备指纹认证能力，再使用本接口传入此参数，会报策略冲突。<br/>2. 通过本接口设置禁用/启用指定用户的设备指纹认证能力后，再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用设备指纹认证能力时，后者会覆盖前者的策略。此后再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口启用设备指纹认证能力，则所有用户都允许使用设备指纹认证能力。<br/>- mtpClient<sup>20+</sup>：MTP客户端能力（仅包含写入），当前仅支持2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。当已经通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用了设备MTP客户端能力时，再通过本接口禁用某用户MTP客户端写入能力，会报策略冲突。<br/>- usbStorageDeviceWrite<sup>20+</sup>：USB存储设备写入能力，当前仅支持2in1设备使用。<!--RP5--><!--RP5End--><br/>  以下三种情况再通过本接口禁用某用户USB存储设备写入能力，会报策略冲突。<br/>  1）通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口设置了设备USB能力禁用。<br/>  2）通过[setUsbStorageDeviceAccessPolicy](js-apis-enterprise-usbManager.md#usbmanagersetusbstoragedeviceaccesspolicy)接口设置了USB存储设备访问策略为只读/禁用。<br/>  3）通过[addDisallowedUsbDevices](js-apis-enterprise-usbManager.md#usbmanageradddisallowedusbdevices14)接口添加了存储类型的USB设备禁用。 |
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
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

try {
  restrictions.setDisallowedPolicyForAccount(wantTemp, 'fingerprint', true, 100);
  console.info('Succeeded in setting fingerprint disabled');
} catch (err) {
  console.error(`Failed to set fingerprint disabled. Code is ${err.code}, message is ${err.message}`);
}
```

## restrictions.getDisallowedPolicyForAccount<sup>14+</sup>

getDisallowedPolicyForAccount(admin: Want, feature: string, accountId: number): boolean

获取指定用户的某特性状态。 

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                   |
| feature | string                                                  | 是   | feature名称。<br/>- fingerprint：设备指纹认证能力，当前仅支持2in1设备使用。使用此参数时有以下规则：当已经通过[setDisallowedPolicyForAccount](#restrictionssetdisallowedpolicyforaccount14)接口设置禁用/启用指定用户的设备指纹认证能力后，再通过[setDisallowedPolicy](#restrictionssetdisallowedpolicy)接口禁用设备指纹认证能力时，后者会覆盖前者的策略。即此时调用本接口结果为false。<br/>- mtpClient<sup>20+</sup>：MTP客户端能力（仅包含写入），当前仅支持2in1设备使用。MTP（MediaTransferProtocol，媒体传输协议），该协议允许用户在移动设备上线性访问媒体文件。<br/>- usbStorageDeviceWrite<sup>20+</sup>：USB存储设备写入能力，当前仅支持2in1设备使用。 |
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
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

try {
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

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                   |
| feature  | string                                                  | 是   | feature名称。<br/>- snapshotSkip：屏幕快照能力。 |
| list | Array\<string>                                                 | 是   | 包名等内容的名单集合。                      |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |                   |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let valueList:Array<string> = ["com.xx.aa.", "com.xx.bb"];
try {
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

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                   |
| feature  | string                                                  | 是   | feature名称。<br/>- snapshotSkip：屏幕快照能力。 |
| list | Array\<string>                                                 | 是   | 包名等内容的名单集合。                       |
| accountId | number                                                 | 是   | 用户ID，取值范围：大于等于0。<br/>accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9)等接口来获取。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |                    |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let valueList:Array<string> = ["com.xx.aa.", "com.xx.bb"];
try {
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

**参数：**

| 参数名  | 类型                                                    | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                   |
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
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

try {
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

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。                                   |
| settingsItem  | string                                                  | 是   | 行为名称。<br/>- setApn：APN设置，当前仅支持手机、平板使用。<br/>- powerLongPress：长按电源键打开电源菜单，当前仅支持手机、平板使用。 |
| restricted | boolean                                                 | 是   | 是否限制行为。true表示限制，false表示允许。                       |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |                    |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

try {
  restrictions.setUserRestriction(wantTemp, 'setApn', true);
  console.info('Succeeded in restricting from setting apn');
} catch (err) {
  console.error(`Failed to restrict from setting apn. Code is ${err.code}, message is ${err.message}`);
}
```