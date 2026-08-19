# addDeviceAccessRight（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## addDeviceAccessRight

```TypeScript
function addDeviceAccessRight(tokenId: string, deviceName: string): boolean
```

添加应用访问设备的权限。系统应用默认拥有访问设备权限，调用此接口不会产生影响。适用于系统设置应用、设备管理应用等需要为第三方应用授权访问USB设备的场景。授权立即生效并持久化存储，设备重启后仍然有效。授权范围为指定的USB设备实 例，多个应用可以同时获得同一设备的访问权限。 [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)会触发弹窗请求用户授权；addDeviceAccessRight不会触发弹窗，而是直接添加应用程序访问设备的权限。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function addDeviceAccessRight(tokenId: string, deviceName: string): boolean--><!--Device-usbManager-function addDeviceAccessRight(tokenId: string, deviceName: string): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | string | 是 | 应用的唯一标识符，可通过 [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取。 |
| deviceName | string | 是 | 设备名称，格式为'bus-port'，例如'1-1'，可通过[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)接口获取设备列表后得到设备 名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回权限添加结果。返回true表示权限添加成功；返回false则表示权限添加失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |

