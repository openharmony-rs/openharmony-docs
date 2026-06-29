# @ohos.usbManager.serial (串口管理)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块主要提供串口管理功能，包括打开和关闭设备的串口、写入和读取数据、设置和获取串口的配置参数、权限管理等。串口管理采用系统级权限控制机制，应用需要通过系统接口获取访问权限后方可对串口设备进行读写操作。

> **说明：**
>
> 本模块首批接口从API version 19开始支持。后续版本的新增接口，采用上标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.usbManager.serial (串口管理)](js-apis-serialManager.md)。

## 导入模块

```ts
import serialManager from '@ohos.usbManager.serial';
```

## serialManager.addSerialRight

ArkTS-Dyn: addSerialRight(tokenId: number, portId: number): void

ArkTS-Sta: addSerialRight(tokenId: int, portId: int): void

为应用程序添加访问串口设备权限。使用前需先通过[getPortList](js-apis-serialManager.md#serialmanagergetportlist)获取串口列表，从中获得有效的portId。调用成功后，应用获得对指定串口设备的访问权限，可进行打开、读写等操作；调用失败则抛出相应错误码，应用无法访问该串口设备。

**使用场景**：
- 系统应用在需要静默授权且无需用户确认的场景下使用，如系统内部组件间通信、后台服务自动连接串口设备。
- 与requestSerialRight的区别：serialManager.requestSerialRight会触发弹窗请求用户授权，适用于需要用户明确授权的场景；addSerialRight不触发弹窗，而是直接添加应用程序访问设备的权限，适用于系统应用自动化管理的场景。应用退出后，系统会自动移除对串口设备的访问权限，在应用重启后需要重新申请授权。

**系统接口：** 此接口为系统接口

**ArkTS-Dyn起始版本**：19

**ArkTS-Sta起始版本**：23

**需要权限：**  ohos.permission.MANAGE_USB_CONFIG

**系统能力：**  SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名     | 类型     | 必填 | 说明                                  |
|---------|--------|----|-------------------------------------|
| tokenId | ArkTS-Dyn: number<br> ArkTS-Sta: int| 是  | 应用访问令牌ID，需要访问串口设备权限的应用tokenId。可通过bundleManager.getBundleInfoForSelf获取bundleInfo.appInfo.accessTokenId来获得。|
| portId  | ArkTS-Dyn: number<br> ArkTS-Sta: int | 是  | 串口设备的端口号，用于唯一标识串口设备，可通过[serialManager.getPortList](js-apis-serialManager.md#serialmanagergetportlist)获取有效的端口号。需确保端口号存在否则会返回31400003错误。|

**返回值：**

| 类型 | 说明 |
| --- | --- |
| void | 无返回值 |


**错误码：**

以下错误码的详细介绍参见[通用错误码](../errorcode-universal.md)和[USB服务错误码](errorcode-usb.md)。

| 错误码ID | 错误信息                                                     | 说明 |
| -------- | ------------------------------------------------------------ | --- |
| 201      | Permission verification failed. The application does not have the permission required to call the API. | 权限验证失败，请检查应用是否具有所需权限。 |
| 202      | Permission verification failed. A non-system application calls a system API. | 权限验证失败，非系统应用调用了系统接口，请确认应用是否具有系统权限。 |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 参数错误。可能原因：1. 必填参数未指定；2. 参数类型错误；3. 参数校验失败。 |
| 14400005 | Database operation exception. | 数据库操作异常，请检查数据库状态后重试。 |
| 31400001 | Serial port management exception. | 串口管理异常，请检查串口设备状态。 |
| 31400003 | PortId does not exist. | 端口号不存在，请检查端口号是否正确。 |

**示例：**
```ts
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { JSON } from '@kit.ArkTS';
import serialManager from '@ohos.usbManager.serial';

// 获取串口列表
function addSerialRight() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: ', JSON.stringify(portList));
  if (portList === undefined || portList.length === 0) {
    console.info('portList is empty');
    return;
  }

  let portId: int = portList[0].portId;
  // 串口增加权限
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;
  bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
    console.info('getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(bundleInfo));
    let tokenId = bundleInfo.appInfo.accessTokenId;
    try {
      serialManager.addSerialRight(tokenId, portId);
      console.info('addSerialRight success, portId: ' + portId);
    } catch (error) {
      console.error('addSerialRight error, ' + JSON.stringify(error));
    }
  }).catch((error : BusinessError) => {
    console.error('getBundleInfoForSelf failed, error = ' + JSON.stringify(error));
  });
}
```
