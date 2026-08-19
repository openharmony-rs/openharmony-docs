# addSerialRight（系统接口）

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## addSerialRight

```TypeScript
function addSerialRight(tokenId: int, portId: int): void
```

为应用添加访问串口设备权限。使用前需先通过[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取串口列表，从中获得有效的portId。调用成 功后，应用获得对指定串口设备的访问权限，可进行打开、读写等操作；调用失败则抛出相应错误码，应用无法访问该串口设备。 **使用场景**： - 系统应用在静默授权且无需用户确认的场景下使用，静默授权指系统应用在无需用户交互的情况下，直接通过系统接口获取串口设备访问权限的方式，如系统内部组件间通信、后台服务自动连接串口设备。系统通过检查应用权限（ ohos.permission.MANAGE_USB_CONFIG）来识别是否允许静默授权，跳过用户确认环节直接授予权限。 - 与requestSerialRight的区别： [serialManager.requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)会触发弹窗请求用户授权，适用于需要 用户明确授权的场景；addSerialRight不触发弹窗，而是直接添加应用访问设备的权限，适用于系统应用自动化管理的场景。应用退出后，系统会自动移除对串口设备的访问权限，在应用重启后需要重新申请授权。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-serialManager-function addSerialRight(tokenId: int, portId: int): void--><!--Device-serialManager-function addSerialRight(tokenId: int, portId: int): void-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | int | 是 | 应用访问令牌ID，标识需要访问串口设备权限的应用。可通过 [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md) 获取。 |
| portId | int | 是 | 串口设备的端口号，用于唯一标识串口设备，可通过 [serialManager.getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取有效的端口号。需确保端口号存在否则会返回31400003错误 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [201](../../errorcode-universal.md#201-权限校验失败) |  |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |
| [14400005](../errorcode-usb.md#14400005-数据库操作异常) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |

**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
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
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION;
  bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
    console.info('getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(bundleInfo));
    let tokenId = bundleInfo.appInfo.accessTokenId;
    try {
      serialManager.addSerialRight(tokenId, portId);
      console.info('addSerialRight success, portId: ' + portId);
    } catch (error) {
      console.error('addSerialRight error, ' + JSON.stringify(error));
    }
  }).catch((error) => {
    console.error('getBundleInfoForSelf failed, error = ' + JSON.stringify(error));
  });
}
```

