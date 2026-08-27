# off

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## off('readerMode')

```TypeScript
function off(type: 'readerMode', elementName: ElementName, callback?: AsyncCallback<TagInfo>): void
```

取消订阅NFC Tag读卡事件。设备退出读卡模式，并恢复卡模拟。如果已通过 tag.on 设置NFC的读卡器模式，需要在页面退出前台或页面销毁时调用off进行取消。

**起始版本：** 11

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'readerMode' | 是 | 要注销的回调类型，固定填"readerMode"字符串。 |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | 是 | 所属应用读卡的页面信息（至少包含bundleName、abilityName这两项的赋值），不可以为空。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | 否 | 前台读卡监听回调函数，返回读到的Tag信息。不填该参数则取消订阅该type对应的读卡回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100203](../errorcode-nfc.md#3100203-接口调用顺序错误) | The off() API can be called only when the on() has been called. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service.<br>**适用版本：** 12+ |


## off('readerModeWithInterval')

```TypeScript
function off(type: 'readerModeWithInterval', elementName: ElementName, callback?: Callback<TagInfo>): void
```

取消订阅NFC Tag读卡事件。设备退出读卡模式，并恢复卡模拟。如果已通过 tag.on 设置NFC的读卡器模式，需要在页面退出前台或页面销毁时调用 tag.off进行取 消。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'readerModeWithInterval' | 是 | 要注销的回调类型，固定填"readerModeWithInterval"字符串。 |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | 是 | 所属应用读卡的页面信息（至少包含bundleName、abilityName这两项的赋值）。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | 否 | 前台读卡监听回调函数，返回读到的Tag信息。不填该参数则取消订阅该type对应的读卡回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100203](../errorcode-nfc.md#3100203-接口调用顺序错误) | The off() API can be called only when the on() has been called. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let discTech : number[] = [tag.NFC_A, tag.NFC_B]; // 用前台ability时所需要的技术代替
let elementName : bundleManager.ElementName;
let interval : number = 200;

function readerModeCb(tagInfo: tag.TagInfo) {
    if (tagInfo == null) {
      console.error('readerModeWithInterval tagInfo is invalid');
      return;
    }
    console.info("readerModeWithInterval: tag found tagInfo = ", JSON.stringify(tagInfo));
  // taginfo的其他操作
}

export default class MainAbility extends UIAbility {
    OnCreate(want : Want, launchParam : AbilityConstant.LaunchParam) {
        console.info("OnCreate");
        elementName = {
            bundleName: want.bundleName as string,
            abilityName: want.abilityName as string,
            moduleName: want.moduleName as string
        }
    }

    onForeground() {
        console.info("on start");
        try {
            tag.on('readerModeWithInterval', elementName, discTech, readerModeCb, interval);
        } catch (e) {
            console.error("tag.on error: " + (e as BusinessError).message);
        }
    }

    onBackground() {
        console.info("onBackground");
        try {
            tag.off('readerModeWithInterval', elementName, readerModeCb);
        } catch (e) {
            console.error("tag.off error: " + (e as BusinessError).message);
        }
    }

    onWindowStageDestroy() {
        console.info("onWindowStageDestroy");
        try {
            tag.off('readerModeWithInterval', elementName, readerModeCb);
        } catch (e) {
            console.error("tag.off error: " + (e as BusinessError).message);
        }
    }

  // ability生命周期内的其他功能
}
```
