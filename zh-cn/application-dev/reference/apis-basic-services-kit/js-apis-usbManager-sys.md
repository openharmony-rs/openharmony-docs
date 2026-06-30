# @ohos.usbManager (USB管理)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块主要提供管理USB设备的相关功能，包括主机上查询USB设备列表、批量数据传输、控制命令传输、权限控制等；设备上端口管理、功能切换及查询等。

> **说明：**
> 
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.usbManager (USB管理)](js-apis-usbManager.md)。

## 导入模块

```ts
import usbManager from '@ohos.usbManager';
```

## usbFunctionsFromString<sup>(deprecated)</sup>

usbFunctionsFromString(funcs: string): number

在设备模式下，将字符串形式的USB功能列表转化为数字掩码。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [getFunctionsFromString](#getfunctionsfromstring12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型   | 必填 | 说明                   |
| ------ | ------ | ---- | ---------------------- |
| funcs  | string | 是   | 字符串形式的功能列表，由'acm'、'ecm'等标识组成，多个功能用','分隔。 |

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| number | 转化后的功能列表对应的数字掩码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |

**示例：**

```ts
// 定义USB功能字符串
let funcs: string = "acm";
// 将字符串转化为数字掩码
let ret: number = usbManager.usbFunctionsFromString(funcs);
```

## usbFunctionsToString<sup>(deprecated)</sup>

usbFunctionsToString(funcs: FunctionType): string

在设备模式下，将数字掩码形式的USB功能列表转化为字符串。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [getStringFromFunctions](#getstringfromfunctions12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型                          | 必填 | 说明              |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | [FunctionType](#functiontype) | 是   | 功能列表对应的数字掩码，可通过位运算组合多个功能。 |

**返回值：**

| 类型   | 说明                           |
| ------ | ------------------------------ |
| string | 转化后的字符串形式的功能列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |

**示例：**

```ts
// 定义USB功能类型组合
let funcs: number = usbManager.FunctionType.ACM | usbManager.FunctionType.ECM;
// 将数字掩码转化为字符串
let ret: string = usbManager.usbFunctionsToString(funcs);
```

## setCurrentFunctions<sup>(deprecated)</sup>

setCurrentFunctions(funcs: FunctionType): Promise\<void\>

在设备模式下，设置当前的USB功能列表。使用Promise异步回调。调用成功后，设备的USB功能将切换为指定的功能列表。适用于系统应用需要动态切换USB设备模式的场景。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [setDeviceFunctions](#setdevicefunctions12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型                          | 必填 | 说明              |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | [FunctionType](#functiontype) | 是   | 功能列表对应的数字掩码。 |

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise\<void\> | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[USB服务错误码](errorcode-usb.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 14400002 | Permission denied. The HDC is disabled by the system.                                                   |

**示例：**

```ts
import {BusinessError} from '@kit.BasicServicesKit';
// 设置USB功能类型为HDC
let funcs: number = usbManager.FunctionType.HDC;
// 异步设置当前USB功能
usbManager.setCurrentFunctions(funcs).then(() => {
    console.info('usb setCurrentFunctions successfully.');
}).catch((err: BusinessError) => {
    console.error('usb setCurrentFunctions failed: ' + err.code + ' message: ' + err.message);
});
```

## getCurrentFunctions<sup>(deprecated)</sup>

getCurrentFunctions(): FunctionType

在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [getDeviceFunctions](#getdevicefunctions12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**返回值：**

| 类型                          | 说明                              |
| ----------------------------- | --------------------------------- |
| [FunctionType](#functiontype) | 当前的USB功能列表的数字组合掩码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                        |
| -------- | ------------------------------------------------------------------------------- |
| 401      | Parameter error. No parameters are required.                                    |
| 202      | Permission denied. Normal application do not have permission to use system api. |

**示例：**

```ts
// 获取当前USB功能的数字掩码
let ret: number = usbManager.getCurrentFunctions();
```

## getPorts<sup>(deprecated)</sup>

getPorts(): Array\<USBPort\>

获取所有物理USB端口描述信息。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [getPortList](#getportlist12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**返回值：**

| 类型                       | 说明                  |
| -------------------------- | --------------------- |
| Array<[USBPort](#usbport)> | USB端口描述信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                        |
| -------- | ------------------------------------------------------------------------------- |
| 401      | Parameter error. No parameters are required.                                    |
| 202      | Permission denied. Normal application do not have permission to use system api. |

**示例：**

```ts
// 获取所有USB端口描述信息
let ret: Array<usbManager.USBPort> = usbManager.getPorts();
```

## getSupportedModes<sup>(deprecated)</sup>

getSupportedModes(portId: number): PortModeType

获取指定的端口支持的模式列表的组合掩码。适用于系统应用需要查询USB-C端口能力判断是否支持特定模式（如Host，Device或DRP模式）的场景。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [getPortSupportModes](#getportsupportmodes12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型   | 必填 | 说明     |
| ------ | ------ | ---- | -------- |
| portId | number | 是   | USB端口号，可通过[getPortList](#getportlist12)获取端口列表后得到。 |

**返回值：**

| 类型                          | 说明                       |
| ----------------------------- | -------------------------- |
| [PortModeType](#portmodetype) | 支持的模式列表的组合掩码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |

**示例：**

```ts
// 获取端口ID为0的端口支持的模式
let ret: number = usbManager.getSupportedModes(0);
```

## setPortRoles<sup>(deprecated)</sup>

setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise\<void\>

设置指定端口当前的角色模式，包含充电角色、数据传输角色。使用Promise异步回调。调用成功后端口角色将切换为指定的角色。适用于系统应用需要动态切换USB端口角色的场景。

> **说明：**
>
> 从 API version 9开始支持，从API version 12开始废弃。建议使用 [setPortRoleTypes](#setportroletypes12) 替代。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名    | 类型                            | 必填 | 说明             |
| --------- | ------------------------------- | ---- | ---------------- |
| portId    | number                          | 是   | 端口号，可通过[getPortList](#getportlist12)获取端口列表后得到。|
| powerRole | [PowerRoleType](#powerroletype) | 是   | 充电角色类型，可选值包括：NONE(无)、SOURCE(对外提供电源)、SINK(需要外部供电)。|
| dataRole  | [DataRoleType](#dataroletype)   | 是   | 数据传输角色类型，可选值包括：NONE(无)、HOST(主机角色)、DEVICE(设备角色)。|

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise\<void\> | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import {BusinessError} from '@kit.BasicServicesKit';
// 定义端口号
let portId: number = 1;
// 设置端口角色：充电角色为SOURCE，数据角色为HOST
usbManager.setPortRoles(portId, usbManager.PowerRoleType.SOURCE, usbManager.DataRoleType.HOST).then(() => {
    console.info('usb setPortRoles successfully.');
}).catch((err: BusinessError) => {
    console.error('usb setPortRoles failed: ' + err.code + ' message: ' + err.message);
});
```

## addDeviceAccessRight<sup>12+</sup>

addDeviceAccessRight(tokenId: string, deviceName: string): boolean

添加应用程序访问设备的权限。系统应用默认拥有访问设备权限，调用此接口不会产生影响。适用于系统设置应用、设备管理应用等需要为第三方应用授权访问USB设备的场景。

[usbManager.requestRight](js-apis-usbManager.md#usbmanagerrequestright)会触发弹框请求用户授权；addDeviceAccessRight不会触发弹框，而是直接添加应用程序访问设备的权限。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名     | 类型   | 必填 | 说明            |
| ---------- | ------ | ---- | --------------- |
| tokenId    | string | 是   | 应用程序的唯一标识符，可通过[bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)获取。 |
| deviceName | string | 是   | 设备名称，格式为'bus-port'，例如'1-1'，可通过[getDevices](js-apis-usbManager.md#usbmanagergetdevices)接口获取设备列表后得到设备名称。|

**返回值：**

| 类型    | 说明                                                                      |
| ------- | ------------------------------------------------------------------------- |
| boolean | 返回权限添加结果。返回true表示权限添加成功；返回false则表示权限添加失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. <br>**ArkTS模式**：该错误码仅适用于ArkTS-Dyn。|
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |
| 801      | Capability not supported.                                    |

**示例：**

```ts
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 定义设备名称
let devicesName: string = "1-1";
// 定义tokenId变量
let tokenId: string = "";

  try {
    // 获取bundle信息标志
    let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;
    // 异步获取当前应用的bundle信息
    bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
      console.info('testTag', 'getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(bundleInfo));
      // 获取应用的accessTokenId
      let token = bundleInfo.appInfo.accessTokenId;
      tokenId = token.toString();
      // 添加设备访问权限
      if (usbManager.addDeviceAccessRight(tokenId, devicesName)) {
        console.info(`Succeed in adding right`);
      }
    }).catch((err : BusinessError) => {
      console.error('testTag getBundleInfoForSelf failed' );
    });
  } catch (err) {
    console.error('testTag failed');
  }
```

## getFunctionsFromString<sup>12+</sup>

ArkTS-Dyn: getFunctionsFromString(funcs: string): number

ArkTS-Sta: getFunctionsFromString(funcs: string): int

在设备模式下，将字符串形式的USB功能列表转化为数字掩码。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型   | 必填 | 说明                   |
| ------ | ------ | ---- | ---------------------- |
| funcs  | string | 是   | 字符串形式的功能列表。可用值包括:'acm'，'ecm'，'hdc'，'mtp'，'ptp'等，可通过',(逗号)'分隔多个功能。 |

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| ArkTS-Dyn: number<br> ArkTS-Sta: int | 转化后的功能列表对应的数字掩码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                        |
| -------- | ------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. <br>**ArkTS模式**：该错误码仅适用于ArkTS-Dyn。|
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.                                    |

**示例：**

```ts
// 定义USB功能字符串
let funcs: string = "acm";
// 将字符串转化为数字掩码
let ret: int = usbManager.getFunctionsFromString(funcs);
```

## getStringFromFunctions<sup>12+</sup>

ArkTS-Dyn: getStringFromFunctions(funcs: FunctionType): string

ArkTS-Sta: getStringFromFunctions(funcs: int): string

在设备模式下，将数字掩码形式的USB功能列表转化为字符串。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型                          | 必填 | 说明              |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | ArkTS-Dyn:  [FunctionType](#functiontype)<br> ArkTS-Sta: int| 是   | 功能列表对应的数字掩码。 |

**返回值：**

| 类型   | 说明                           |
| ------ | ------------------------------ |
| string | 转化后的字符串形式的功能列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. <br>**ArkTS模式**：该错误码仅适用于ArkTS-Dyn。|
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api.   |
| 801      | Capability not supported.  |

**示例：**

```ts
let funcs: int = usbManager.FunctionType.ACM | usbManager.FunctionType.ECM;
let ret: string = usbManager.getStringFromFunctions(funcs);
```

## setDeviceFunctions<sup>12+</sup>

ArkTS-Dyn: setDeviceFunctions(funcs: FunctionType): Promise\<void\>

ArkTS-Sta: setDeviceFunctions(funcs: int): Promise\<void\>

在设备模式下，设置当前的USB功能列表。调用成功后，设备的USB功能将切换为指定的功能列表。部分USB功能可能不被当前设备支持设置前建议先查询设备支持的功能列表。

> **说明：**
>
> 从 API version 12开始支持。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型                          | 必填 | 说明              |
| ------ | ----------------------------- | ---- | ----------------- |
| funcs  | ArkTS-Dyn:  [FunctionType](#functiontype)<br> ArkTS-Sta: int| 是   | 功能列表对应的数字掩码。 |

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise\<void\> | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[USB服务错误码](errorcode-usb.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.<br>**ArkTS模式**：该错误码仅适用于ArkTS-Dyn。|
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |
| 801      | Capability not supported.                                    |
| 14400002 | Permission denied. The HDC is disabled by the system.                                                   |
| 14400006 | Unsupported operation. The function is not supported.                                                   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
// 设置USB功能类型为HDC
let funcs: int = usbManager.FunctionType.HDC;
// 异步设置设备功能
usbManager.setDeviceFunctions(funcs).then(() => {
    console.info('usb setDeviceFunctions successfully.');
}).catch((err : BusinessError) => {
    console.error('usb setDeviceFunctions failed: ' + err.code + ' message: ' + err.message);
});
```

## getDeviceFunctions<sup>12+</sup>

ArkTS-Dyn: getDeviceFunctions(): FunctionType

ArkTS-Sta: getDeviceFunctions(): int

在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。

> **说明：**
>
> 从 API version 12开始支持。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**返回值：**

| 类型                          | 说明                              |
| ----------------------------- | --------------------------------- |
| ArkTS-Dyn:  [FunctionType](#functiontype)<br> ArkTS-Sta: int| 功能列表对应的数字掩码。 |
| undefined |开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`<br>**ArkTs模式**：该返回值仅适用于ArkTs-Dyn|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                        |
| -------- | ------------------------------------------------------------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 801      | Capability not supported.                                    |
| 14400004 | Service exception. Possible causes: <br>1. No accessory is plugged in.<br>**ArkTS模式**：该错误码仅适用于ArkTS-Sta。 |

**示例：**

```ts
// 获取当前USB设备的数字掩码
let ret: int = usbManager.getDeviceFunctions();
```

## getPortList<sup>12+</sup>

getPortList(): Array\<USBPort\>

获取所有物理USB端口描述信息。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。

> **说明：**
>
> 从 API version 12开始支持。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**返回值：**

| 类型                       | 说明                  |
| -------------------------- | --------------------- |
| Array<[USBPort](#usbport)> | USB端口描述信息列表。 |
| undefined | 开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`<br>**ArkTs模式**：该返回值仅适用于ArkTs-Dyn|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |
| 801      | Capability not supported.                                    |
| 14400004 | Service exception. Possible causes: <br>1. No accessory is plugged in.<br>**ArkTS模式**：该错误码仅适用于ArkTS-Sta。 |

**示例：**

```ts
// 获取USB端口列表
let ret: Array<usbManager.USBPort> = usbManager.getPortList();
```

## getPortSupportModes<sup>12+</sup>

ArkTS-Dyn: getPortSupportModes(portId: number): PortModeType

ArkTS-Sta: getPortSupportModes(portId: int): PortModeType

获取指定的端口支持的模式列表的组合掩码。适用于系统应用需要查询USB-C端口能力判断是否支持特定模式（如Host，Device或DRP模式）的场景。

> **说明：**
>
> 从 API version 12开始支持。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型   | 必填 | 说明     |
| ------ | ------ | ---- | -------- |
| portId | ArkTS-Dyn: number<br> ArkTS-Sta: int | 是   | USB端口号，可通过[getPortList](#getportlist12)获取端口列表后得到。 |

**返回值：**

| 类型                          | 说明                       |
| ----------------------------- | -------------------------- |
| [PortModeType](#portmodetype) | 支持的模式列表的组合掩码。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[USB服务错误码](errorcode-usb.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |
| 801      | Capability not supported.                                    |

**示例：**

```ts
// 获取端口ID为0的支持模式
let ret: int = usbManager.getPortSupportModes(0);
```

## setPortRoleTypes<sup>12+</sup>

ArkTS-Dyn: setPortRoleTypes(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise\<void\>

ArkTS-Sta: setPortRoleTypes(portId: int, powerRole: PowerRoleType, dataRole: DataRoleType): Promise\<void\>

设置指定端口当前的角色模式，包含充电角色、数据传输角色。使用Promise异步回调。调用成功后端口的充电角色和数据传输角色将切换为指定的角色。

> **说明：**
>
> 从 API version 12开始支持。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：**  SystemCapability.USB.USBManager

**参数：**

| 参数名    | 类型                            | 必填 | 说明             |
| --------- | ------------------------------- | ---- | ---------------- |
| portId    | ArkTS-Dyn: number<br> ArkTS-Sta: int   | 是   | 端口号，可通过[getPortList](#getportlist12)获取端口列表后得到。 |
| powerRole | [PowerRoleType](#powerroletype) | 是   | 充电角色类型，可选值包括：NONE(无)、SOURCE(对外提供电源)、SINK(需要外部供电)。 |
| dataRole  | [DataRoleType](#dataroletype)   | 是   | 数据传输角色类型，可选值包括：NONE(无)、HOST(主机角色)、DEVICE(设备角色)。 |

**返回值：**

| 类型                | 说明          |
| ------------------- | ------------- |
| Promise\<void\> | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[USB服务错误码](errorcode-usb.md)。

| 错误码ID | 错误信息                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api.                         |
| 801      | Capability not supported.                                    |
| 14400003 | Unsupported operation. The current device does not support port role switching.                         |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
// 定义端口号
let portId: int = 1;
// 设置端口角色类型：充电角色为SOURCE，数据角色为HOST
usbManager.setPortRoleTypes(portId, usbManager.PowerRoleType.SOURCE, usbManager.DataRoleType.HOST).then(() => {
  console.info('usb setPortRoleTypes successfully.');
}).catch((err : BusinessError) => {
  console.error('usb setPortRoleTypes failed: ' + err.code + ' message: ' + err.message);
});
```

## addAccessoryRight<sup>14+</sup>

ArkTS-Dyn: addAccessoryRight(tokenId: number, accessory: USBAccessory): void

ArkTS-Sta: addAccessoryRight(tokenId: int, accessory: USBAccessory): void

为应用程序添加访问USB配件权限。适用于系统应用需要为第三方应用授权访问USB配件的场景。

usbManager.requestAccessoryRight会触发弹窗请求用户授权；addAccessoryRight不会触发弹窗，而是直接添加应用程序访问设备的权限。

> **说明：**
>
> 从 API version 14开始支持。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG，该权限为系统权限，仅系统应用可申请。系统应用可通过配置文件中的requestPermissions字段申请该权限，具体申请方式请参考[权限申请开发指导](../../security/AccessToken/permissions-for-all.md)。

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名    | 类型         | 必填 | 说明                     |
| --------- | ------------ | ---- | ------------------------ |
| tokenId   | ArkTS-Dyn: number<br> ArkTS-Sta: int   | 是   | 应用程序的唯一标识符，可通过[bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)获取。|
| accessory | [USBAccessory](js-apis-usbManager.md#usbaccessory14) | 是   | USB配件。可通过[getAccessoryList](js-apis-usbManager.md#usbmanagergetaccessorylist14)获取配件列表后获得。 |

**返回值：**

| 类型      | 说明          |
| --------- | ------------- |
| void      | 调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[USB服务错误码](errorcode-usb.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | The permission check failed. The application does not have the permission required to call the API. |
| 202      | Permission denied. Normal application do not have permission to use system api. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801      | Capability not supported.                                    |
| 14400004 | Service exception. Possible causes: 1. No accessory is plugged in. |
| 14400005 | Database operation exception.                                |

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取USB配件列表
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  // 设置bundle信息标志
  let flags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION |
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY
  // 异步获取当前应用的bundle信息
  let bundleInfo = await bundleManager.getBundleInfoForSelf(flags)
  // 获取应用的tokenId
  let tokenId: int = bundleInfo.appInfo.accessTokenId
  // 为应用添加USB配件访问权限
  usbManager.addAccessoryRight(tokenId, accList[0])
  hilog.info(0, 'testTag ui', `addAccessoryRight success`)
} catch (error: BusinessError) {
  hilog.info(0, 'testTag ui', `addAccessoryRight error ${error.code}, message is ${error.message}`)
}
```

## USBPort

USB设备端口。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**系统能力：** SystemCapability.USB.USBManager

| 名称           | 类型                            | 只读 | 可选 | 说明                                |
| -------------- | ------------------------------- | ---- | ---- | ----------------------------------- |
| id             | ArkTS-Dyn: number<br> ArkTS-Sta: int                        | 否   | 否   | USB端口唯一标识。                   |
| supportedModes | [PortModeType](#portmodetype)   | 否   | 否   | USB端口所支持的模式的数字组合掩码。status.currentMode应在此范围内。 |
| status         | [USBPortStatus](#usbportstatus) | 否   | 否   | USB端口角色。其currentMode应在supportedModes范围内。 |

## USBPortStatus

USB设备端口角色信息。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**系统能力：** SystemCapability.USB.USBManager

| 名称             | 类型 | 只读 | 可选 | 说明                   |
| ---------------- | ------| ---- | ----| ---------------------- |
| currentMode      | ArkTS-Dyn: number<br> ArkTS-Sta: int| 否   | 否     | 当前的USB模式。|
| currentPowerRole | ArkTS-Dyn: number<br> ArkTS-Sta: int| 否   | 否      | 当前设备充电模式。|
| currentDataRole  | ArkTS-Dyn: number<br> ArkTS-Sta: int | 否   | 否      | 当前设备数据传输模式。 |


## FunctionType

USB设备侧功能。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**系统能力：** SystemCapability.USB.USBManager

| 名称         | 值  | 说明       |
| ------------ | --- | ---------- |
| NONE         | 0   | 没有功能。 |
| ACM          | 1   | acm（Abstract Control Model，抽象控制模型），串口通信功能，用于模拟串口设备。|
| ECM          | 2   | ecm（Ethernet Control Model，以太网控制模型），以太网控制功能，用于网络共享。  |
| HDC          | 4   | hdc（HarmonyOS Device Connector，HarmonyOS设备连接器）。  |
| MTP          | 8   | mtp（Media Transfer Protocol，媒体传输协议）。 |
| PTP          | 16  | ptp（Picture Transfer Protocol，图片传输协议）。 |
| RNDIS        | 32  | rndis（Remote Network Driver Interface Specification，远程网络驱动接口规范），用于网络共享（暂不支持）。 |
| MIDI         | 64  | midi（Musical Instrument Digital Interface，乐器数字接口），用于MIDI设备通信（暂不支持）。 |
| AUDIO_SOURCE | 128 | 音频源功能，用于音频数据传输（暂不支持）。 |
| NCM          | 256 | ncm（Network Control Model，网络控制模型），用于高速网络共享（暂不支持）。  |

## PortModeType

USB端口模式类型。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**系统能力：** SystemCapability.USB.USBManager

| 名称      | 值 | 说明                                                 |
| --------- | -- | ---------------------------------------------------- |
| NONE      | 0  | 无。                                                 |
| UFP       | 1  | 数据上行，需要外部供电。                             |
| DFP       | 2  | 数据下行，对外提供电源。                             |
| DRP       | 3  | 既可以做DFP(Host)，也可以做UFP(Device)，当前不支持。 |
| NUM_MODES | 4  | 当前不支持。                                         |

## PowerRoleType

电源角色类型。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**系统能力：** SystemCapability.USB.USBManager

| 名称   | 值 | 说明       |
| ------ | -- | ---------- |
| NONE   | 0  | 无。       |
| SOURCE | 1  | 对外提供电源。 |
| SINK   | 2  | 需要外部供电。 |

## DataRoleType

数据角色类型。

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**系统能力：** SystemCapability.USB.USBManager

| 名称   | 值 | 说明         |
| ------ | -- | ------------ |
| NONE   | 0  | 无。         |
| HOST   | 1  | 主设备角色。 |
| DEVICE | 2  | 从设备角色。 |

