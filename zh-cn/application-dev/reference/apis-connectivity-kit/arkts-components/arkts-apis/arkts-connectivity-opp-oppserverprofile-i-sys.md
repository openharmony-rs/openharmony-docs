# OppServerProfile

Profile类，使用opp方法之前需要创建该类的实例进行操作，通过[createOppServerProfile()](arkts-connectivity-opp-createoppserverprofile-f-sys.md)方法构造此实例。

**起始版本：** 16

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## cancelTransfer

```TypeScript
cancelTransfer(): Promise<void>
```

取消文件传输。使用Promise异步回调。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth switch is off. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile is not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Failed to cancel the current transfer. |
| 2903002 | Current Transfer Information is busy. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { opp } from '@kit.ConnectivityKit';
// 创建fileHolders
try {
    let oppProfile = opp.createOppServerProfile();
    oppProfile.cancelTransfer();
} catch (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getCurrentTransferInformation

```TypeScript
getCurrentTransferInformation(): Promise<OppTransferInformation>
```

获取当前传输的文件信息。使用Promise异步回调。

**起始版本：** 16

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本16-24：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OppTransferInformation](arkts-connectivity-opp-opptransferinformation-i-sys.md)&gt; | Promise对象。返回当前传输的文件信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth switch is off. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile is not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Failed to obtain the current transmission information. |
| 2903004 | Current Transfer Information is empty. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { opp } from '@kit.ConnectivityKit';
// 创建fileHolders
try {
    let oppProfile = opp.createOppServerProfile();
    let data = oppProfile.getCurrentTransferInformation();
} catch (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## off('transferStateChange')

```TypeScript
off(type: 'transferStateChange', callback?: Callback<OppTransferInformation>): void
```

取消订阅蓝牙文件传输的进度和状态变化事件。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'transferStateChange' | 是 | 事件回调类型，支持的事件为'transferStateChange'，调用off('transferStateChange')后，停止接收文件传输进度和状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OppTransferInformation](arkts-connectivity-opp-opptransferinformation-i-sys.md)&gt; | 否 | Callback used to listen for event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |

## off('receiveIncomingFile')

```TypeScript
off(type: 'receiveIncomingFile', callback?: Callback<OppTransferInformation>): void
```

取消订阅蓝牙文件传输完成的事件。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveIncomingFile' | 是 | 事件回调类型，支持的事件为'receiveIncomingFile'，调用off('receiveIncomingFile')后，停止接收文件传输通知的事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OppTransferInformation](arkts-connectivity-opp-opptransferinformation-i-sys.md)&gt; | 否 | Callback used to listen for event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |

## on('transferStateChange')

```TypeScript
on(type: 'transferStateChange', callback: Callback<OppTransferInformation>): void
```

订阅蓝牙文件传输的进度和状态变化。

**起始版本：** 16

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本16-24：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'transferStateChange' | 是 | 事件回调类型，支持的事件为'transferStateChange'，当on('transferStateChange')调用完成后，可以收到文件传输进度和状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OppTransferInformation](arkts-connectivity-opp-opptransferinformation-i-sys.md)&gt; | 是 | 表示文件传输进度和状态变化事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 16 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |

## on('receiveIncomingFile')

```TypeScript
on(type: 'receiveIncomingFile', callback: Callback<OppTransferInformation>): void
```

订阅蓝牙文件传输事件以接收文件。

**起始版本：** 16

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本16-24：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveIncomingFile' | 是 | 事件回调类型，支持的事件为'receiveIncomingFile'，当on('receiveIncomingFile')调用完成后，表示可以收到是否有文件传输通知的事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OppTransferInformation](arkts-connectivity-opp-opptransferinformation-i-sys.md)&gt; | 是 | 表示文件传输进度和状态变化事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 16 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |

## sendFile

```TypeScript
sendFile(deviceId: string, fileHolds: Array<FileHolder>): Promise<void>
```

使用蓝牙发送文件。使用Promise异步回调。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 接收端的蓝牙MAC地址。 |
| fileHolds | Array&lt;[FileHolder](arkts-connectivity-opp-fileholder-i-sys.md)&gt; | 是 | 发送的文件数据，依据插入Array的次序进行发送。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth switch is off. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile is not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Failed to send file. |
| 2903001 | The file type is not supported. |
| 2903002 | Current Transfer Information is busy. |
| 2903003 | The file is not accessible. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs} from '@kit.CoreFileKit';
import { opp } from '@kit.ConnectivityKit';
// 创建fileHolders
try {
    let oppProfile = opp.createOppServerProfile();
    let fileHolders : Array<opp.FileHolder> = [];
    // 有效的URIS
    let uris: Array<string> = ['test1.jpg', 'test2.jpg'];
    for (let i = 0; i < uris.length; i++) {
        let filePath = uris[i];
        console.info('opp deal filePath is :' + filePath);
        let file = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
        let stat: fs.Stat = fs.statSync(file.fd);
        let fileHolder: opp.FileHolder = {
        filePath:filePath,
        fileSize:stat.size,
        fileFd:file.fd
        };
        fileHolders.push(fileHolder);
    }
    oppProfile.sendFile("11:22:33:44:55:66", fileHolders);
    // 等待文件传输完后，记得关闭文件描述符  fs.close(file.fd);
} catch (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## setIncomingFileConfirmation

```TypeScript
setIncomingFileConfirmation(accept: boolean, fileFd: number): Promise<void>
```

蓝牙接收文件。使用Promise异步回调。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accept | boolean | 是 | 表示是否接受接收文件。true表示接受，false表示不接受。 |
| fileFd | number | 是 | 接收的文件描述符，接收过程中需要保持开启。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth switch is off. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile is not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Failed to confirm the received file information. |
| 2903002 | Current Transfer Information is busy. |
| 2903003 | The file is not accessible. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs} from '@kit.CoreFileKit';
import { opp } from '@kit.ConnectivityKit';
// 创建fileHolders
let file: fs.File | undefined = undefined;
try {
    let oppProfile = opp.createOppServerProfile();
    let pathDir = "/test.jpg"; // 应用根据实际情况填写路径
    file = fs.openSync(pathDir, fs.OpenMode.CREATE | fs.OpenMode.READ_WRITE);
    oppProfile.setIncomingFileConfirmation(true, file.fd);
} catch (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
} finally {
  // 接收完成后关闭  
  if (file) {
    fs.close(file.fd);
  }
}
```

## setLastReceivedFileUri

```TypeScript
setLastReceivedFileUri(uri: string): Promise<void>
```

设置最后一个接收文件的URI。使用Promise异步回调。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 最后一个接收文件的URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Failed to set the URI of the last file. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { opp } from '@kit.ConnectivityKit';
// 创建fileHolders
try {
    let oppProfile = opp.createOppServerProfile();
    oppProfile.setLastReceivedFileUri("file://media/Photo/1/IMG_1739266559_000/screenshot_20250211_173419.jpg"); // 应用根据实际情况填写路径
} catch (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
