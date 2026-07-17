# addSerialRight（系统接口）

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## addSerialRight

```TypeScript
function addSerialRight(tokenId: number, portId: number): void
```

为应用程序添加访问串口设备权限。serialManager.requestSerialRight会触发弹窗请求用户授权；addSerialRight不会触发弹窗，而是直接添加应用程序访问设备的权限。应用退出自动移除对串口设备的访问权限，在应用重启后需要重新申请授权。

**起始版本：** 19

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-serialManager-function addSerialRight(tokenId: int, portId: int): void--><!--Device-serialManager-function addSerialRight(tokenId: int, portId: int): void-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | number | 是 | 需要访问权限的tokenId。 |
| portId | number | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getportlist-1)获取的串口参数SerialPort。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) |  |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) |  |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |
| [14400005](../../apis-basic-services-kit/errorcode-usb.md#14400005-数据库操作异常) |  |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) |  |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) |  |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';


function addSerialRight() {
  // 获取串口列表
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: ', JSON.stringify(portList));
  if (portList === undefined || portList.length === 0) {
    console.info('portList is empty');
    return;
  }

  let portId: number = portList[0].portId;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

  bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
    console.info('getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(bundleInfo));
    let tokenId = bundleInfo.appInfo.accessTokenId;
    try {
      // 串口增加权限
      serialManager.addSerialRight(tokenId, portId);
      console.info('addSerialRight success, portId: ' + portId);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to add serial right. Code: ${err.code}, message: ${err.message}`);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to get bundle info for self. Code: ${error.code}, message: ${error.message}`);
  });
}

```

