# SystemSoundManager（系统接口）

管理系统声音。在调用SystemSoundManager的接口前，需要先通过[getSystemSoundManager](arkts-audio-systemsoundmanager-getsystemsoundmanager-f-sys.md#getsystemsoundmanager)创建实例。

**起始版本：** 10

<!--Device-systemSoundManager-interface SystemSoundManager--><!--Device-systemSoundManager-interface SystemSoundManager-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## addCustomizedTone

```TypeScript
addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, externalUri: string): Promise<string>
```

通过铃音uri将自定义铃音添加到铃音库。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_RINGTONE

<!--Device-SystemSoundManager-addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, externalUri: string): Promise<string>--><!--Device-SystemSoundManager-addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, externalUri: string): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| toneAttr | [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i-sys.md) | 是 | 铃音属性。 |
| externalUri | string | 是 | 外部存储器中的铃音uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回铃音在铃音库中的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation is not allowed, e.g. ringtone to add is not customized. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. Possible causes:1. The target file size exceeds 2 GB;2. Failed to find the specified file;3. System sound manager service error. |
| [20700004](../errorcode-audio-ringtone-sys.md#20700004-数据大小超过限制) | Data size exceeds the limit. Note:This error is returned when the file size is between 200MB and 2GB.<br>**适用版本：** 20+ |
| [20700005](../errorcode-audio-ringtone-sys.md#20700005-文件个数超过限制) | The number of files exceeds the limit.<br>**适用版本：** 20+ |
| [20700006](../errorcode-audio-ringtone-sys.md#20700006-rom空间不足) | Insufficient ROM space.<br>**适用版本：** 20+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let title = 'test'; // 需更改为实际名称。
let fileName = 'displayName_test'; // 需更改为实际文件名。
let categoryValue = systemSoundManager.TONE_CATEGORY_ALARM;

let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
toneAttrs.setTitle(title);
toneAttrs.setFileName(fileName);
toneAttrs.setCategory(categoryValue);

let path = 'file://data/test.ogg'; // 需更改为实际铃音uri。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.addCustomizedTone(context, toneAttrs, path).then((value: string) => {
  console.info('Succeeded in doing addCustomizedTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to addCustomizedTone. Code: ${err.code}, message: ${err.message}`);
});

```

## addCustomizedTone

```TypeScript
addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, fd: number, offset?: number, length?: number)
      : Promise<string>
```

通过文件描述符fd将自定义铃音添加到铃音库。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_RINGTONE

<!--Device-SystemSoundManager-addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, fd: int, offset?: long, length?: long)      : Promise<string>--><!--Device-SystemSoundManager-addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, fd: int, offset?: long, length?: long)      : Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| toneAttr | [ToneAttrs](arkts-audio-systemsoundmanager-toneattrs-i-sys.md) | 是 | 铃音属性。 |
| fd | number | 是 | 文件描述符，可通过[fileIo.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md#open)获取。 |
| offset | number | 否 | 读取数据的偏移量（以字节为单位）。默认情况下为0。 |
| length | number | 否 | 读取的数据的长度（以字节为单位）。默认情况下，长度为偏移后的剩余全部字节数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回铃音在铃音库中的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation is not allowed, e.g. ringtone to add is not customized. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. Possible causes:1. The target file size exceeds 2 GB;2. Failed to find the specified file;3. Ringtone library error.4. System sound manager service error. |
| [20700004](../errorcode-audio-ringtone-sys.md#20700004-数据大小超过限制) | Data size exceeds the limit. Note:This error is returned when the file size is between 200MB and 2GB.<br>**适用版本：** 20+ |
| [20700005](../errorcode-audio-ringtone-sys.md#20700005-文件个数超过限制) | The number of files exceeds the limit.<br>**适用版本：** 20+ |
| [20700006](../errorcode-audio-ringtone-sys.md#20700006-rom空间不足) | Insufficient ROM space.<br>**适用版本：** 20+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let title = 'test'; // 需更改为实际名称。
let fileName = 'displayName_test'; // 需更改为实际文件名。
let categoryValue = systemSoundManager.TONE_CATEGORY_ALARM;

let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
toneAttrs.setTitle(title);
toneAttrs.setFileName(fileName);
toneAttrs.setCategory(categoryValue);

let fd = 10; // 需更改为实际铃音fd。
let offset = 0; // 需更改为实际所需偏移量。
let length = 50; // 需更改为实际所需数据长度。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.addCustomizedTone(context, toneAttrs, fd, offset, length).then((value: string) => {
  console.info('Succeeded in doing addCustomizedTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to addCustomizedTone. Code: ${err.code}, message: ${err.message}`);
});

```

## close

```TypeScript
close(fd: number): Promise<void>
```

关闭闹铃文件。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-close(fd: int): Promise<void>--><!--Device-SystemSoundManager-close(fd: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符，通过[openAlarmTone](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#openalarmtone)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fd = 50; // 需更改为目标铃声的fd。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.close(fd).then(() => {
  console.info('Succeeded in doing close.');
}).catch((err: BusinessError) => {
  console.error(`Failed to close. Code: ${err.code}, message: ${err.message}`);
});

```

## getAlarmToneAttrList

```TypeScript
getAlarmToneAttrList(context: BaseContext): Promise<ToneAttrsArray>
```

获取全部闹铃属性列表。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getAlarmToneAttrList(context: BaseContext): Promise<ToneAttrsArray>--><!--Device-SystemSoundManager-getAlarmToneAttrList(context: BaseContext): Promise<ToneAttrsArray>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrsArray&gt; | Promise对象，返回全部闹铃属性列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getAlarmToneAttrList(context).then((value: systemSoundManager.ToneAttrsArray) => {
  console.info('Succeeded in doing getAlarmToneAttrList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAlarmToneAttrList. Code: ${err.code}, message: ${err.message}`);
});

```

## getAlarmToneUri

```TypeScript
getAlarmToneUri(context: BaseContext): Promise<string>
```

获取系统当前闹铃uri。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getAlarmToneUri(context: BaseContext): Promise<string>--><!--Device-SystemSoundManager-getAlarmToneUri(context: BaseContext): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回系统当前闹铃uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getAlarmToneUri(context).then((value: string) => {
  console.info('Succeeded in doing getAlarmToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAlarmToneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## getCurrentRingtoneAttribute

```TypeScript
getCurrentRingtoneAttribute(type: RingtoneType): Promise<ToneAttrs>
```

获取正在使用的铃声属性。使用Promise异步回调。

**起始版本：** 20

<!--Device-SystemSoundManager-getCurrentRingtoneAttribute(type: RingtoneType): Promise<ToneAttrs>--><!--Device-SystemSoundManager-getCurrentRingtoneAttribute(type: RingtoneType): Promise<ToneAttrs>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrs&gt; | Promise对象，返回系统铃声的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getCurrentRingtoneAttribute(type).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getCurrentRingtoneAttribute.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getCurrentRingtoneAttribute. Code: ${err.code}, message: ${err.message}`);
});

```

## getDefaultAlarmToneAttrs

```TypeScript
getDefaultAlarmToneAttrs(context: BaseContext): Promise<ToneAttrs>
```

获取系统闹铃的属性。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getDefaultAlarmToneAttrs(context: BaseContext): Promise<ToneAttrs>--><!--Device-SystemSoundManager-getDefaultAlarmToneAttrs(context: BaseContext): Promise<ToneAttrs>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrs&gt; | Promise对象，返回系统闹铃的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getDefaultAlarmToneAttrs(context).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getDefaultAlarmToneAttrs.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getDefaultAlarmToneAttrs. Code: ${err.code}, message: ${err.message}`);
});

```

## getDefaultRingtoneAttrs

```TypeScript
getDefaultRingtoneAttrs(context: BaseContext, type: RingtoneType): Promise<ToneAttrs>
```

获取系统铃声的属性。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getDefaultRingtoneAttrs(context: BaseContext, type: RingtoneType): Promise<ToneAttrs>--><!--Device-SystemSoundManager-getDefaultRingtoneAttrs(context: BaseContext, type: RingtoneType): Promise<ToneAttrs>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrs&gt; | Promise对象，返回系统铃声的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getDefaultRingtoneAttrs(context, type).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getDefaultRingtoneAttrs.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getDefaultRingtoneAttrs. Code: ${err.code}, message: ${err.message}`);
});

```

## getDefaultSystemToneAttrs

```TypeScript
getDefaultSystemToneAttrs(context: BaseContext, type: SystemToneType): Promise<ToneAttrs>
```

获取系统提示音的属性。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getDefaultSystemToneAttrs(context: BaseContext, type: SystemToneType): Promise<ToneAttrs>--><!--Device-SystemSoundManager-getDefaultSystemToneAttrs(context: BaseContext, type: SystemToneType): Promise<ToneAttrs>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | 是 | 待获取播放器的系统提示音的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrs&gt; | Promise对象，返回系统提示音的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getDefaultSystemToneAttrs(context, type).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getDefaultSystemToneAttrs.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getDefaultSystemToneAttrs. Code: ${err.code}, message: ${err.message}`);
});

```

## getHapticsAttrsSyncedWithTone

```TypeScript
getHapticsAttrsSyncedWithTone(context: BaseContext, toneUri: string): Promise<ToneHapticsAttrs>
```

获取与指定铃音同步的振动属性。使用Promise异步回调。

**起始版本：** 14

<!--Device-SystemSoundManager-getHapticsAttrsSyncedWithTone(context: BaseContext, toneUri: string): Promise<ToneHapticsAttrs>--><!--Device-SystemSoundManager-getHapticsAttrsSyncedWithTone(context: BaseContext, toneUri: string): Promise<ToneHapticsAttrs>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| toneUri | string | 是 | 待获取同步振动的系统铃声Uri,可通过[getRingtoneAttrList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneattrlist)或[getSystemToneAttrList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getsystemtoneattrlist)等获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneHapticsAttrs&gt; | Promise对象，返回与指定铃音同步的振动属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. For example, the input URI is not used for tones. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let toneUri: string = '/data/storage/el2/base/RingTone/alarms/test.ogg'; // 需更改为实际铃音uri。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getHapticsAttrsSyncedWithTone(context, toneUri).then((value: systemSoundManager.ToneHapticsAttrs) => {
  console.info('Succeeded in doing getHapticsAttrsSyncedWithTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getHapticsAttrsSyncedWithTone. Code: ${err.code}, message: ${err.message}`);
});

```

## getMockHapticRingtonePlayer

```TypeScript
getMockHapticRingtonePlayer(
      context: BaseContext, type: RingtoneType, ringtoneUri: string): Promise<RingtonePlayer | null>
```

获取模拟触觉铃声播放器，根据指定的铃声类型和铃音文件URI，播放该铃音文件对应的振动文件及其模拟触觉声音文件。使用Promise异步回调。
> **说明：**  
>  
> - 调用该接口前，请确保传入的ringtoneUri在系统中存在，否则会出现异常和错误。例如无法播放匹配的触觉声音文件。  
>  
> - 通过该接口获取实例后，在服务终止时需主动调用RingtonePlayer的  
> [release](arkts-audio-ringtoneplayer-ringtoneplayer-i-sys.md#release)方法释放播放器资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemSoundManager-getMockHapticRingtonePlayer(      context: BaseContext, type: RingtoneType, ringtoneUri: string): Promise<RingtonePlayer | null>--><!--Device-SystemSoundManager-getMockHapticRingtonePlayer(      context: BaseContext, type: RingtoneType, ringtoneUri: string): Promise<RingtonePlayer | null>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 待获取播放器的铃声类型。 |
| ringtoneUri | string | 是 | 铃音文件的URI，需确保在系统文件中真实存在。<br>如果为自定义铃声需使用[addCustomizedTone](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#addcustomizedtone)接口返回的ringtoneUri，确保铃音文件URI在铃音库中存在。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RingtonePlayer \| null&gt; | Promise对象，成功返回模拟触觉铃声播放器实例，发生错误时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter verification failed. Possible causes:1.The type exceeds the valid range, please use the RingtoneType enum for input.2.The ringtoneUri does not exist or is incorrectly formatted, please use the ringtoneUri returned by the {@link SystemSoundManager#addCustomizedTone}. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. The ringtone database access timed out or encountered an error.It is recommended to restart your phone. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | null = null;
let ringtoneUri = 'file://data/test.json'; // 需更改为目标铃音文件URI。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getMockHapticRingtonePlayer(context, type, ringtoneUri).then((value: systemSoundManager.RingtonePlayer | null) => {
  if (value != null) {
    console.info('Succeeded in doing getMockHapticRingtonePlayer.');
    systemRingtonePlayer = value;
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to getMockHapticRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});

```

## getMockHapticRingtonePlayer

```TypeScript
getMockHapticRingtonePlayer(context: BaseContext, hapticUri: string): Promise<RingtonePlayer | null>
```

获取模拟触觉铃声播放器，根据指定的触觉文件URI播放振动文件及其对应的模拟触觉声音文件。使用Promise异步回调。
> **说明：**  
>  
> - 调用该接口前，请确保传入的hapticUri在系统中存在，否则会出现异常和错误。例如无法播放匹配的触觉声音文件。  
>  
> - 通过该接口获取实例后，在服务终止时需主动调用RingtonePlayer的  
> [release](arkts-audio-ringtoneplayer-ringtoneplayer-i-sys.md#release)方法释放播放器资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemSoundManager-getMockHapticRingtonePlayer(context: BaseContext, hapticUri: string): Promise<RingtonePlayer | null>--><!--Device-SystemSoundManager-getMockHapticRingtonePlayer(context: BaseContext, hapticUri: string): Promise<RingtonePlayer | null>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| hapticUri | string | 是 | 触觉文件的URI，需确保为JSON文件且在系统文件中真实存在。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RingtonePlayer \| null&gt; | Promise对象，成功返回模拟触觉铃声播放器实例，发生错误时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [20700002](../errorcode-audio-ringtone-sys.md#20700002-参数检查失败) | Parameter verification failed. The hapticUri does not exist or is incorrectly formatted. Ensure it is a JSON file and that it exists in the system's file system. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. The ringtone database access timed out or encountered an error.It is recommended to restart your phone. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | null = null;
let hapticUri = 'file://data/test.json'; // 需更改为目标触觉文件URI。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getMockHapticRingtonePlayer(context, hapticUri).then((value: systemSoundManager.RingtonePlayer | null) => {
  if (value != null) {
    console.info('Succeeded in doing getMockHapticRingtonePlayer.');
    systemRingtonePlayer = value;
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to getMockHapticRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});

```

## getRingtoneAttrList

```TypeScript
getRingtoneAttrList(context: BaseContext, type: RingtoneType): Promise<ToneAttrsArray>
```

获取系统铃声的属性列表。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getRingtoneAttrList(context: BaseContext, type: RingtoneType): Promise<ToneAttrsArray>--><!--Device-SystemSoundManager-getRingtoneAttrList(context: BaseContext, type: RingtoneType): Promise<ToneAttrsArray>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrsArray&gt; | Promise对象，返回系统铃声的属性列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getRingtoneAttrList(context, type).then((value: systemSoundManager.ToneAttrsArray) => {
  console.info('Succeeded in doing getRingtoneAttrList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getRingtoneAttrList. Code: ${err.code}, message: ${err.message}`);
});

```

## getRingtonePlayer

```TypeScript
getRingtonePlayer(context: BaseContext, type: RingtoneType): Promise<RingtonePlayer>
```

获取系统铃声播放器。使用Promise异步回调。

**起始版本：** 11

<!--Device-SystemSoundManager-getRingtonePlayer(context: BaseContext, type: RingtoneType): Promise<RingtonePlayer>--><!--Device-SystemSoundManager-getRingtonePlayer(context: BaseContext, type: RingtoneType): Promise<RingtonePlayer>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 待获取播放器的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RingtonePlayer&gt; | Promise对象，返回获取的系统铃声播放器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getRingtonePlayer(context, type).then((value: systemSoundManager.RingtonePlayer) => {
  console.info('Succeeded in doing getRingtonePlayer.');
  systemRingtonePlayer = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to getRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});

```

## getRingtoneUri

```TypeScript
getRingtoneUri(context: BaseContext, type: RingtoneType): Promise<string>
```

获取系统铃声uri。使用Promise异步回调。

**起始版本：** 11

<!--Device-SystemSoundManager-getRingtoneUri(context: BaseContext, type: RingtoneType): Promise<string>--><!--Device-SystemSoundManager-getRingtoneUri(context: BaseContext, type: RingtoneType): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统铃声uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getRingtoneUri(context, type).then((value: string) => {
  console.info('Succeeded in doing getRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## getSystemRingtonePlayer

```TypeScript
getSystemRingtonePlayer(context: Context, type: RingtoneType, callback: AsyncCallback<RingtonePlayer>): void
```

获取系统铃声播放器。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getRingtonePlayer](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneplayer)

<!--Device-SystemSoundManager-getSystemRingtonePlayer(context: Context, type: RingtoneType, callback: AsyncCallback<RingtonePlayer>): void--><!--Device-SystemSoundManager-getSystemRingtonePlayer(context: Context, type: RingtoneType, callback: AsyncCallback<RingtonePlayer>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 待获取播放器的系统铃声的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;RingtonePlayer&gt; | 是 | 回调函数。当获取系统铃声播放器成功，err为undefined data为获取到的系统铃声播放器；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtonePlayer(context, type, (err: BusinessError, value: systemSoundManager.RingtonePlayer) => {
  if (err) {
    console.error(`Failed to get system ringtone player. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the system ringtone player is obtained.`);
  systemRingtonePlayer = value;
});

```

## getSystemRingtonePlayer

```TypeScript
getSystemRingtonePlayer(context: Context, type: RingtoneType): Promise<RingtonePlayer>
```

获取系统铃声播放器。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getRingtonePlayer](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneplayer)

<!--Device-SystemSoundManager-getSystemRingtonePlayer(context: Context, type: RingtoneType): Promise<RingtonePlayer>--><!--Device-SystemSoundManager-getSystemRingtonePlayer(context: Context, type: RingtoneType): Promise<RingtonePlayer>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 待获取播放器的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RingtonePlayer&gt; | Promise对象，返回获取的系统铃声播放器。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtonePlayer(context, type).then((value: systemSoundManager.RingtonePlayer) => {
  console.info('Succeeded in doing getSystemRingtonePlayer.');
  systemRingtonePlayer = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});

```

## getSystemRingtoneUri

```TypeScript
getSystemRingtoneUri(context: Context, type: RingtoneType, callback: AsyncCallback<string>): void
```

获取系统铃声uri。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getRingtoneUri](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneuri)

<!--Device-SystemSoundManager-getSystemRingtoneUri(context: Context, type: RingtoneType, callback: AsyncCallback<string>): void--><!--Device-SystemSoundManager-getSystemRingtoneUri(context: Context, type: RingtoneType, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 待获取的系统铃声的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当获取系统铃声uri成功，err为undefined，data为获取到的系统铃声uri；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtoneUri(context, type, (err: BusinessError, value: string) => {
  if (err) {
    console.error(`Failed to get system ringtone uri. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the system ringtone uri is obtained ${value}.`);
});

```

## getSystemRingtoneUri

```TypeScript
getSystemRingtoneUri(context: Context, type: RingtoneType): Promise<string>
```

获取系统铃声uri。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [getRingtoneUri](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneuri)

<!--Device-SystemSoundManager-getSystemRingtoneUri(context: Context, type: RingtoneType): Promise<string>--><!--Device-SystemSoundManager-getSystemRingtoneUri(context: Context, type: RingtoneType): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前应用的上下文。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统铃声uri。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtoneUri(context, type).then((value: string) => {
  console.info('Succeeded in doing getSystemRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## getSystemToneAttrList

```TypeScript
getSystemToneAttrList(context: BaseContext, type: SystemToneType): Promise<ToneAttrsArray>
```

获取系统提示音的属性列表。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-getSystemToneAttrList(context: BaseContext, type: SystemToneType): Promise<ToneAttrsArray>--><!--Device-SystemSoundManager-getSystemToneAttrList(context: BaseContext, type: SystemToneType): Promise<ToneAttrsArray>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | 是 | 待获取播放器的系统提示音的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneAttrsArray&gt; | Promise对象，返回系统提示音的属性列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemToneAttrList(context, type).then((value: systemSoundManager.ToneAttrsArray) => {
  console.info('Succeeded in doing getSystemToneAttrList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemToneAttrList. Code: ${err.code}, message: ${err.message}`);
});

```

## getSystemTonePlayer

```TypeScript
getSystemTonePlayer(context: BaseContext, type: SystemToneType): Promise<SystemTonePlayer>
```

获取系统提示音播放器。使用Promise异步回调。

**起始版本：** 11

<!--Device-SystemSoundManager-getSystemTonePlayer(context: BaseContext, type: SystemToneType): Promise<SystemTonePlayer>--><!--Device-SystemSoundManager-getSystemTonePlayer(context: BaseContext, type: SystemToneType): Promise<SystemTonePlayer>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | 是 | 待获取播放器的系统提示音的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SystemTonePlayer&gt; | Promise对象，返回获取的系统提示音播放器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;
let systemTonePlayer: systemSoundManager.SystemTonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemTonePlayer(context, type).then((value: systemSoundManager.SystemTonePlayer) => {
  console.info('Succeeded in doing getSystemTonePlayer.');
    systemTonePlayer = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemTonePlayer. Code: ${err.code}, message: ${err.message}`);
});

```

## getSystemToneUri

```TypeScript
getSystemToneUri(context: BaseContext, type: SystemToneType): Promise<string>
```

获取系统提示音uri。使用Promise异步回调。

**起始版本：** 11

<!--Device-SystemSoundManager-getSystemToneUri(context: BaseContext, type: SystemToneType): Promise<string>--><!--Device-SystemSoundManager-getSystemToneUri(context: BaseContext, type: SystemToneType): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | 是 | 被设置的系统提示音的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取的系统提示音uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemToneUri(context, type).then((value: string) => {
  console.info('Succeeded in doing getSystemToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemToneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## getToneHapticsList

```TypeScript
getToneHapticsList(context: BaseContext, isSynced: boolean): Promise<ToneHapticsAttrsArray>
```

获取同步或者非同步的系统铃音的振动属性列表。使用Promise异步回调。

**起始版本：** 14

<!--Device-SystemSoundManager-getToneHapticsList(context: BaseContext, isSynced: boolean): Promise<ToneHapticsAttrsArray>--><!--Device-SystemSoundManager-getToneHapticsList(context: BaseContext, isSynced: boolean): Promise<ToneHapticsAttrsArray>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| isSynced | boolean | 是 | 表示待获取的振动是否与某个铃音同步。true表示同步，false表示不同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneHapticsAttrsArray&gt; | Promise对象，返回同步或者非同步的系统铃音的振动属性列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getToneHapticsList(context, false).then((value: systemSoundManager.ToneHapticsAttrsArray) => {
  console.info('Succeeded in doing getToneHapticsList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getToneHapticsList. Code: ${err.code}, message: ${err.message}`);
});

```

## getToneHapticsSettings

```TypeScript
getToneHapticsSettings(context: BaseContext, type: ToneHapticsType): Promise<ToneHapticsSettings>
```

获取系统铃音的振动设置。使用Promise异步回调。

**起始版本：** 14

<!--Device-SystemSoundManager-getToneHapticsSettings(context: BaseContext, type: ToneHapticsType): Promise<ToneHapticsSettings>--><!--Device-SystemSoundManager-getToneHapticsSettings(context: BaseContext, type: ToneHapticsType): Promise<ToneHapticsSettings>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [ToneHapticsType](arkts-audio-systemsoundmanager-tonehapticstype-e-sys.md) | 是 | 待获取系统铃音的振动类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ToneHapticsSettings&gt; | Promise对象，返回铃声的振动设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.ToneHapticsType = systemSoundManager.ToneHapticsType.CALL_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getToneHapticsSettings(context, type).then((value: systemSoundManager.ToneHapticsSettings) => {
  console.info('Succeeded in doing getToneHapticsSettings.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getToneHapticsSettings. Code: ${err.code}, message: ${err.message}`);
});

```

## openAlarmTone

```TypeScript
openAlarmTone(context: BaseContext, uri: string): Promise<number>
```

打开闹铃文件。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-openAlarmTone(context: BaseContext, uri: string): Promise<int>--><!--Device-SystemSoundManager-openAlarmTone(context: BaseContext, uri: string): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 被设置的系统闹铃的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| 20700001 | Tone type mismatch, e.g. tone of uri is notification instead of alarm. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.openAlarmTone(context, uri).then((value: number) => {
  console.info('Succeeded in doing openAlarmTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to openAlarmTone. Code: ${err.code}, message: ${err.message}`);
});

```

## openToneHaptics

```TypeScript
openToneHaptics(context: BaseContext, hapticsUri: string): Promise<number>
```

打开系统铃音的振动。使用Promise异步回调。

**起始版本：** 14

<!--Device-SystemSoundManager-openToneHaptics(context: BaseContext, hapticsUri: string): Promise<int>--><!--Device-SystemSoundManager-openToneHaptics(context: BaseContext, hapticsUri: string): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| hapticsUri | string | 是 | 待打开系统铃音的振动的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. For example, the input URI is not one for haptics. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let hapticsUri = '/data/storage/el2/base/haptics/synchronized/alarms/test.json'; // 需更改为目标统铃音的振动的uri。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.openToneHaptics(context, hapticsUri).then((value: number) => {
  console.info('Succeeded in doing openToneHaptics.');
}).catch((err: BusinessError) => {
  console.error(`Failed to openToneHaptics. Code: ${err.code}, message: ${err.message}`);
});

```

## openToneList

```TypeScript
openToneList(uriList: Array<string>): Promise<Array<[string, number, SystemSoundError]>>
```

获取系统铃声的属性列表。使用Promise异步回调。

**起始版本：** 20

<!--Device-SystemSoundManager-openToneList(uriList: Array<string>): Promise<Array<[string, long, SystemSoundError]>>--><!--Device-SystemSoundManager-openToneList(uriList: Array<string>): Promise<Array<[string, long, SystemSoundError]>>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriList | Array&lt;string&gt; | 是 | 要打开的uri列表，不能超过1024个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[string, number, SystemSoundError]&gt;&gt; | Promise对象，Promise用于返回此操作的结果，返回Array内第一个参数uri，第二个参数fd，第三个参数为此uri打开的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [20700007](../errorcode-audio-ringtone-sys.md#20700007-参数无效) | Parameter is invalid, e.g. the length of uriList is too long. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();

systemSoundManagerInstance.getCurrentRingtoneAttribute(type).then((toneAttrs) => {
  console.info('Succeeded in getting current ringtone attribute.');
  systemSoundManagerInstance.openToneList([toneAttrs.getUri()]).then((value) => {
    console.info('Succeeded in opening tone list.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to open tone list. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get current ringtone attribute. Code: ${err.code}, message: ${err.message}`);
});

```

## removeCustomizedTone

```TypeScript
removeCustomizedTone(context: BaseContext, uri:string): Promise<void>
```

从铃音库中删除自定义铃音。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.WRITE_RINGTONE

<!--Device-SystemSoundManager-removeCustomizedTone(context: BaseContext, uri:string): Promise<void>--><!--Device-SystemSoundManager-removeCustomizedTone(context: BaseContext, uri:string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 铃音uri，可通过[addCustomizedTone](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#addcustomizedtone)或[getAlarmToneAttrList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getalarmtoneattrlist)等方法获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation is not allowed, e.g. ringtone of this uri is not customized. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.removeCustomizedTone(context, uri).then(() => {
  console.info('Succeeded in doing removeCustomizedTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to removeCustomizedTone. Code: ${err.code}, message: ${err.message}`);
});

```

## removeCustomizedToneList

```TypeScript
removeCustomizedToneList(uriList: Array<string>): Promise<Array<[string, SystemSoundError]>>
```

批量删除自定义铃音列表。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.WRITE_RINGTONE

<!--Device-SystemSoundManager-removeCustomizedToneList(uriList: Array<string>): Promise<Array<[string, SystemSoundError]>>--><!--Device-SystemSoundManager-removeCustomizedToneList(uriList: Array<string>): Promise<Array<[string, SystemSoundError]>>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriList | Array&lt;string&gt; | 是 | 要删除的uri列表，不能超过1024个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[string, SystemSoundError]&gt;&gt; | Promise对象，Promise用于返回此操作的结果，返回Array内第一个参数uri，第二个参数为此uri删除结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [20700007](../errorcode-audio-ringtone-sys.md#20700007-参数无效) | Parameter is invalid, e.g. the length of uriList is too long. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();

systemSoundManagerInstance.getCurrentRingtoneAttribute(type).then((toneAttrs) => {
  console.info('Succeeded in getting current ringtone attribute.');
  systemSoundManagerInstance.removeCustomizedToneList([toneAttrs.getUri()]).then((value) => {
    console.info('Succeeded in using removeCustomizedToneList function.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to use removeCustomizedToneList function. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get current ringtone attribute. Code: ${err.code}, message: ${err.message}`);
});

```

## setAlarmToneUri

```TypeScript
setAlarmToneUri(context: BaseContext, uri: string): Promise<void>
```

设置系统闹铃uri。使用Promise异步回调。

**起始版本：** 12

<!--Device-SystemSoundManager-setAlarmToneUri(context: BaseContext, uri: string): Promise<void>--><!--Device-SystemSoundManager-setAlarmToneUri(context: BaseContext, uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 被设置的系统闹铃的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| 20700001 | Tone type mismatch, e.g. tone of input uri is not an alarm tone. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setAlarmToneUri(context, uri).then(() => {
  console.info('Succeeded in doing setAlarmToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setAlarmToneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## setRingtoneUri

```TypeScript
setRingtoneUri(context: BaseContext, uri: string, type: RingtoneType): Promise<void>
```

设置系统铃声uri。使用Promise异步回调。

**起始版本：** 11

<!--Device-SystemSoundManager-setRingtoneUri(context: BaseContext, uri: string, type: RingtoneType): Promise<void>--><!--Device-SystemSoundManager-setRingtoneUri(context: BaseContext, uri: string, type: RingtoneType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 被设置的系统铃声的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setRingtoneUri(context, uri, type).then(() => {
  console.info('Succeeded in doing setRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## setSystemRingtoneUri

```TypeScript
setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType, callback: AsyncCallback<void>): void
```

设置系统铃声uri。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setRingtoneUri](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#setringtoneuri)

<!--Device-SystemSoundManager-setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType, callback: AsyncCallback<void>): void--><!--Device-SystemSoundManager-setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 被设置的系统铃声的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置系统铃声uri成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setSystemRingtoneUri(context, uri, type, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set system ringtone uri. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful setting of the system ringtone uri.`);
});

```

## setSystemRingtoneUri

```TypeScript
setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType): Promise<void>
```

设置系统铃声uri。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setRingtoneUri](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#setringtoneuri)

<!--Device-SystemSoundManager-setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType): Promise<void>--><!--Device-SystemSoundManager-setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 被设置的系统铃声的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |
| type | [RingtoneType](arkts-audio-systemsoundmanager-ringtonetype-e-sys.md) | 是 | 被设置的系统铃声的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setSystemRingtoneUri(context, uri, type).then(() => {
  console.info('Succeeded in doing setSystemRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setSystemRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## setSystemToneUri

```TypeScript
setSystemToneUri(context: BaseContext, uri: string, type: SystemToneType): Promise<void>
```

设置系统提示音uri。使用Promise异步回调。

**起始版本：** 11

<!--Device-SystemSoundManager-setSystemToneUri(context: BaseContext, uri: string, type: SystemToneType): Promise<void>--><!--Device-SystemSoundManager-setSystemToneUri(context: BaseContext, uri: string, type: SystemToneType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| uri | string | 是 | 被设置的系统提示音的uri，资源支持可参考[media.AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)。 |
| type | [SystemToneType](arkts-audio-systemsoundmanager-systemtonetype-e-sys.md) | 是 | 被设置的系统提示音的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // 需更改为目标铃声文件的uri。
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setSystemToneUri(context, uri, type).then(() => {
  console.info('Succeeded in doing setSystemToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setSystemToneUri. Code: ${err.code}, message: ${err.message}`);
});

```

## setToneHapticsSettings

```TypeScript
setToneHapticsSettings(context: BaseContext, type: ToneHapticsType, settings: ToneHapticsSettings): Promise<void>
```

设置系统铃音的振动。使用Promise异步回调。

**起始版本：** 14

<!--Device-SystemSoundManager-setToneHapticsSettings(context: BaseContext, type: ToneHapticsType, settings: ToneHapticsSettings): Promise<void>--><!--Device-SystemSoundManager-setToneHapticsSettings(context: BaseContext, type: ToneHapticsType, settings: ToneHapticsSettings): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用的上下文。 |
| type | [ToneHapticsType](arkts-audio-systemsoundmanager-tonehapticstype-e-sys.md) | 是 | 被设置的系统铃音的振动类型。 |
| settings | [ToneHapticsSettings](arkts-audio-systemsoundmanager-tonehapticssettings-i-sys.md) | 是 | 被设置的系统铃音的振动设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. For example, the input URI is not valid. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [20700003](../errorcode-audio-ringtone-sys.md#20700003-操作不支持) | Unsupported operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.ToneHapticsType = systemSoundManager.ToneHapticsType.CALL_SIM_CARD_0;
let toneHapticsSettings: systemSoundManager.ToneHapticsSettings = {
  mode: systemSoundManager.ToneHapticsMode.NON_SYNC,
  hapticsUri: '/data/storage/el2/base/haptics/synchronized/alarms/test.json', // 需更改为通过getToneHapticsList获取的Uri。
}

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setToneHapticsSettings(context, type, toneHapticsSettings).then(() => {
  console.info('Succeeded in doing setToneHapticsSettings.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setToneHapticsSettings. Code: ${err.code}, message: ${err.message}`);
});

```

