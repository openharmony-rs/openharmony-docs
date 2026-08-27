# unregisterForegroundDispatch

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## unregisterForegroundDispatch

```TypeScript
function unregisterForegroundDispatch(elementName: ElementName): void
```

取消注册对NFC Tag读卡事件的监听，退出前台应用优先分发。如果已注册事件监听，需要在页面退出前台或页面销毁前调用取消注册。

**起始版本：** 10

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | 是 | 所属应用读卡的页面信息（至少包含bundleName、abilityName这两项的赋值），不可以为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let discTech : number[] = [tag.NFC_A, tag.NFC_B]; // 用前台ability时所需要的技术代替
let elementName : bundleManager.ElementName;
function foregroundCb(err : BusinessError, tagInfo : tag.TagInfo) {
    if (!err) {
        console.info("foreground callback: tag found tagInfo = ", JSON.stringify(tagInfo));
    } else {
        console.error("foreground callback err: " + err.message);
        return;
    }
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
        console.info("onForeground");
        try {
            tag.registerForegroundDispatch(elementName, discTech, foregroundCb);
        } catch (e) {
            console.error("registerForegroundDispatch error: " + (e as BusinessError).message);
        }
    }

    onBackground() {
        console.info("onBackground");
        try {
            tag.unregisterForegroundDispatch(elementName);
        } catch (e) {
            console.error("unregisterForegroundDispatch error: " + (e as BusinessError).message);
        }
    }

    onWindowStageDestroy() {
        console.info("onWindowStageDestroy");
        try {
            tag.unregisterForegroundDispatch(elementName);
        } catch (e) {
            console.error("unregisterForegroundDispatch error: " + (e as BusinessError).message);
        }
    }

  // ability生命周期内的其他功能
}
```
