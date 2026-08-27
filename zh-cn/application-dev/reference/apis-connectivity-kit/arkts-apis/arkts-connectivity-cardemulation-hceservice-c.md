# HceService

提供HCE卡模拟的实现，主要包括接收对端读卡设备的APDU数据，并响应APDU数据到对端读卡设备。使用HCE相关接口前，必须先判断设备是否支持HCE卡模拟能力。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

## 导入模块

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## off('hceCmd')

```TypeScript
off(type: 'hceCmd', callback?: AsyncCallback<number[]>): void
```

取消APDU数据接收的订阅。使用callback异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hceCmd' | 是 | 要取消订阅的事件类型，固定填"hceCmd"字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 否 | 回调函数，返回的每个number十六进制表示，范围是0x00~0xFF。不填该参数则取消订阅该type对应的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { hilog } from '@kit.PerformanceAnalysisKit';
import { cardEmulation } from '@kit.ConnectivityKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { bundleManager, AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();
let element: bundleManager.ElementName;
const apduCallback: AsyncCallback<number[]> = (err, data) => {
  // 处理数据和异常
  console.info("AsyncCallback got apdu data");
};

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testHce', '%{public}s', 'Ability onCreate');
    element = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName
    }
    hceService.on('hceCmd', apduCallback);
  }
  onDestroy() {
    hilog.info(0x0000, 'testHce', '%{public}s', 'Ability onDestroy');
    hceService.off('hceCmd', apduCallback);
    hceService.stop(element);
  }
  // 生命周期内的其他功能
}
```

## on('hceCmd')

```TypeScript
on(type: 'hceCmd', callback: AsyncCallback<number[]>): void
```

订阅回调，用于接收对端读卡设备发送的APDU数据，应用程序需要在HCE卡模拟页面的onCreate函数里面调用该订阅函数。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hceCmd' | 是 | 要订阅的回调类型，固定填"hceCmd"字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 是 | 回调函数，返回的是符合APDU协议的数据，每个number十六进制表示，范围是0x00~0xFF。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 12+ |

**示例**

ArkTS示例：

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { hilog } from '@kit.PerformanceAnalysisKit';
import { cardEmulation } from '@kit.ConnectivityKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { bundleManager, AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();
let element: bundleManager.ElementName;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testHce', '%{public}s', 'Ability onCreate');
    element = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName
    }
    const apduCallback: AsyncCallback<number[]> = (err, data) => {
      // 处理数据和异常
      console.info("got apdu data");
    };
    hceService.on('hceCmd', apduCallback);
  }
  onDestroy() {
    hilog.info(0x0000, 'testHce', '%{public}s', 'Ability onDestroy');
    hceService.stop(element);
  }
  // 生命周期内的其他功能
}
```

JS示例：

```TypeScript
// 适用于轻量级智能穿戴设备
import cardEmulation from '@ohos.nfc.cardEmulation';

let appName = "com.example.testquestionlite";

export default {
  data:{
    fontSize: '30px',
    fontColor: '#50609f',
    hide: 'show',
    headCon: appName,
    paymentAid: ["A0000000041010", "A0000000041012"]
  },
  onCreate() {
    console.info('onCreate');
  },
  onReady() {
    cardEmulation.hasHceCapability();
    cardEmulation.isDefaultService(appName, cardEmulation.CardType.PAYMENT);
    cardEmulation.isDefaultService(appName, cardEmulation.CardType.OTHER);
    let HceService = new cardEmulation.HceService();

    HceService.start(appName, this.paymentAid);
    HceService.on("hceCmd", (data) => {
      console.info('data:' + data);
      // 应用程序实际想要发送的数据， 此处仅作为示例
      let responseData = [0x1, 0x2];
      HceService.transmit(responseData, () => {
        console.info('sendResponse start');
      });
      console.info('sendResponse end');
    });
  },
  onDestroy() {
  }
  // 生命周期内的其他功能
}
```

## sendResponse

```TypeScript
sendResponse(responseApdu: number[]): void
```

发送APDU数据到对端读卡设备。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [transmit](#transmit)

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| responseApdu | number[] | 是 | 发送到对端读卡设备的符合APDU协议的数据，每个number十六进制表示，范围是0x00~0xFF。 |

**示例**

JS示例：

```TypeScript
<!-- 适用于轻量级智能穿戴设备 -->
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        测试
    </text>
    <input type="button" value="sendResponse" style="width: 240px; height: 50px; margin: 5px;" onclick="onClick"></input>
</div>
```

```TypeScript
/* 适用于轻量级智能穿戴设备 */
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// 适用于轻量级智能穿戴设备
// xxx.js
import cardEmulation from '@ohos.nfc.cardEmulation';

export default  {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    onClick() {
        var hceService = new cardEmulation.HceService();
        hceService.on("hceCmd", (err, res) => {
            if(err.data === 0) {
                console.info('callback => Operation hceCmd succeeded. Data: ${JSON.stringify(res)}');
                hceService.sendResponse([0x00,0xa4,0x04,0x00,
                    0x0e,0x32,0x50,0x41,0x59,0x2e,0x53,0x59,0x53,0x2e,0x44,0x44,
                    0x46,0x30,0x31,0x00]);
            } else {
                console.info('callback => Operation hceCmd failed. Cause: ${JSON.stringify(err.data)}');
            }
        })
    }
}
```

## start

```TypeScript
start(elementName: ElementName, aidList: string[]): void
```

启动HCE业务功能。包括设置当前应用为前台优先，动态注册AID列表。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | 是 | 所属应用声明NFC卡模拟能力的页面信息（至少包含bundleName、abilityName这两项的赋值），不可以为空。 |
| aidList | string[] | 是 | 动态注册卡模拟的AID列表，允许为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-nfc卡模拟状态异常) | Card emulation running state is abnormal in service. |

## startHCE

```TypeScript
startHCE(aidList: string[]): boolean
```

启动HCE业务功能。包括设置当前应用为前台优先，动态注册AID列表。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [start](#start)

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aidList | string[] | 是 | 动态注册卡模拟的AID列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 启动HCE功能或HCE已启动， false: 启动失败。 |

**示例**

JS示例：

```TypeScript
<!-- 适用于轻量级智能穿戴设备 -->
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        测试
    </text>
    <input type="button" value="startHCE" style="width: 240px; height: 50px; margin: 5px;" onclick="onClick"></input>
</div>
```

```TypeScript
/* 适用于轻量级智能穿戴设备 */
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// 适用于轻量级智能穿戴设备
// xxx.js
import cardEmulation from '@ohos.nfc.cardEmulation';

export default  {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    onClick() {
        var hceService = new cardEmulation.HceService();
        hceService.startHCE([
            "F0010203040506", "A0000000041010"
        ])
    }
}
```

## stop

```TypeScript
stop(elementName: ElementName): void
```

停止HCE业务功能。包括取消APDU数据接收的订阅，退出当前应用前台优先，释放动态注册的AID列表。应用程序需要在HCE卡模拟页面的onDestroy函数里调用该接口。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | 是 | 所属应用声明NFC卡模拟能力的页面信息（至少包含bundleName、abilityName这两项的赋值），不可以为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-nfc卡模拟状态异常) | Card emulation running state is abnormal in service. |

## stopHCE

```TypeScript
stopHCE(): boolean
```

停止HCE业务功能。包括退出当前应用前台优先，释放动态注册的AID列表，释放hceCmd的订阅。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [stop](#stop)

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 禁用HCE功能或HCE已禁用，false: 禁用失败。 |

**示例**

JS示例：

```TypeScript
<!-- 适用于轻量级智能穿戴设备 -->
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        测试
    </text>
    <input type="button" value="stopHCE" style="width: 240px; height: 50px; margin: 5px;" onclick="onClick"></input>
</div>
```

```TypeScript
/* 适用于轻量级智能穿戴设备 */
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// 适用于轻量级智能穿戴设备
// xxx.js
import cardEmulation from '@ohos.nfc.cardEmulation';

export default  {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    onClick() {
        var hceService = new cardEmulation.HceService();
        hceService.stopHCE();
    }
}
```

## transmit

```TypeScript
transmit(response: number[]): Promise<void>
```

发送APDU数据到对端读卡设备，使用Promise异步回调。应用程序必须在 on收到读卡设备发送的APDU数据后，才调用该接口响应数 据。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | number[] | 是 | 发送到对端读卡设备的符合APDU协议的数据，每个number十六进制表示，范围是0x00~0xFF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-nfc卡模拟状态异常) | Card emulation running state is abnormal in service. |

**示例**

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();

// 应用程序实际想要发送的数据， 此处仅作为示例
const responseData = [0x1, 0x2];
hceService.transmit(responseData).then(() => {
  // 处理 promise 的回调
  console.info("transmit Promise success.");
}).catch((err: BusinessError) => {
  console.error("transmit Promise error:", err);
});
```

```TypeScript
// 适用于轻量级智能穿戴设备
import cardEmulation from '@ohos.nfc.cardEmulation';

let hceService = new cardEmulation.HceService();

// 应用程序实际想要发送的数据， 此处仅作为示例
let responseData = [0x1, 0x2];
hceService.transmit(responseData).then(() => {
  // 处理 promise 的回调
  console.info("transmit Promise success.");
});
console.info("transmit Promise end.");
```

## transmit

```TypeScript
transmit(response: number[], callback: AsyncCallback<void>): void
```

发送APDU数据到对端读卡设备，应用程序必须在on收到读 卡设备发送的APDU数据后，才调用该接口响应数据。使用Callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | number[] | 是 | 发送到对端读卡设备的符合APDU协议的数据，每个number十六进制表示，范围是0x00~0xFF。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当发送APDU数据成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-nfc卡模拟状态异常) | Card emulation running state is abnormal in service. |

**示例**

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();

// 应用程序实际想要发送的数据， 此处仅作为示例
try {
  const responseData = [0x1, 0x2];

  hceService.transmit(responseData, (err : BusinessError)=> {
    if (err) {
      console.error(`transmit AsyncCallback err Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info("transmit AsyncCallback success.");
    }
  });
} catch (error) {
  console.error(`transmit AsyncCallback catch Code: ${(error as BusinessError).code}, ` +
    `message: ${(error as BusinessError).message}`);
}
```

```TypeScript
// 适用于轻量级智能穿戴设备
import cardEmulation from '@ohos.nfc.cardEmulation';

let hceService = new cardEmulation.HceService();

// 应用程序实际想要发送的数据， 此处仅作为示例
let responseData = [0x1, 0x2];
hceService.transmit(responseData, () => {
  console.info("transmit Promise success.");
});
console.info("transmit Promise end.");
```
