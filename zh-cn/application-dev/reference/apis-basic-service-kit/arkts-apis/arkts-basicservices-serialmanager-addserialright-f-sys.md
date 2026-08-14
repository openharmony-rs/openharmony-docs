# addSerialRight（系统接口）

## addSerialRight

```TypeScript
function addSerialRight(tokenId: int, portId: int): void
```

为应用程序添加访问串口设备权限。 serialManager.requestSerialRight会触发弹窗请求用户授权；addSerialRight不会触发弹窗，而是直接添加应用程序访问设备的权限。应用退出自动移除对串口设备的访问权限，在应用重启后需要重新申请授 权。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-serialManager-function addSerialRight(tokenId: int, portId: int): void--><!--Device-serialManager-function addSerialRight(tokenId: int, portId: int): void-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | int | 是 | 需要访问权限的tokenId。 |
| portId | int | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList)获取的串口参数SerialPort。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) | PortId does not exist. |
| [14400005](../../apis-basic-services-kit/errorcode-usb.md#14400005-数据库操作异常) | Database operation exception. |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) | Serial port management exception. |

## 示例

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
  }).catch((error) => {
    console.error('getBundleInfoForSelf failed, error = ' + JSON.stringify(error));
  });
}
```

