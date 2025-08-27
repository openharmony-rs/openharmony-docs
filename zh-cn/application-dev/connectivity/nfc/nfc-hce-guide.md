# HCE卡模拟开发指南

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->

## 简介
近场通信(Near Field Communication，NFC)是一种短距高频的无线电技术，在13.56MHz频率运行，通信距离一般在10厘米距离内。HCE(Host Card Emulation)，称为基于主机的卡模拟，表示不依赖安全单元芯片，电子设备上的应用程序模拟NFC卡片和NFC读卡器通信，实现NFC刷卡业务。

## 场景介绍
应用程序模拟NFC卡片，和NFC读卡器通信完成NFC刷卡业务。从使用场景上，可以分成HCE应用前台刷卡和HCE应用后台刷卡。
- HCE应用前台刷卡<br>
前台刷卡是指在触碰NFC读卡器之前，用户先在电子设备上打开特定的应用程序，用户明确想使用所打开的应用程序和NFC读卡器进行刷卡操作。用户打开应用程序在前台，并且进入应用的刷卡页面之后，电子设备触碰NFC读卡器，只会把刷卡交易数据分发给前台应用。
- HCE应用后台刷卡<br>
后台刷卡是指不打开特定的HCE应用程序，当电子设备触碰NFC读卡器时，根据NFC读卡器选择的应用ID（Applet ID，AID，参考ISO/IEC 7816-4规范）匹配到HCE应用程序，并自动和匹配的HCE应用程序通信完成刷卡交易。如果NFC读卡器选择的应用ID，匹配到多个HCE应用程序时，说明存在冲突，需要用户打开指定的HCE应用，重新靠近NFC读卡器触发刷卡。

## HCE应用刷卡的约束条件
1. 基于刷卡安全性考虑，不论HCE应用是前台方式还是后台方式刷卡，均不支持电子设备在灭屏或熄屏状态下的HCE刷卡操作。<br>
2. 电子设备必须具备NFC控制器芯片，才支持HCE刷卡能力。对于是否具有NFC安全单元芯片，没有约束要求。<br>
3. HCE应用程序需要声明NFC卡模拟权限，具体见示例。<br>

## 接口说明

NFC卡模拟完整的JS API说明以及实例代码请参考：[NFC卡模拟接口](../../reference/apis-connectivity-kit/js-apis-cardEmulation.md)。

完成HCE卡模拟功能，可能使用到下面的接口。

| 接口名                             | 功能描述                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------ |
| start(elementName: ElementName, aidList: string[]): void                   | 启动HCE业务功能。包括设置当前应用为前台优先，动态注册AID列表。                                                               |
| stop(elementName: ElementName): void  | 停止HCE业务功能。包括取消APDU数据接收的订阅，退出当前应用前台优先，释放动态注册的AID列表。
| on(type: 'hceCmd', callback: AsyncCallback\<number[]>): void                | 订阅回调，用于接收对端读卡设备发送的APDU数据。
| transmit(response: number[]): Promise\<void>                  | 发送APDU数据到对端读卡设备。|                                                     |

## 开发步骤

### HCE应用前台刷卡
1. 在module.json5文件中声明NFC卡模拟权限，以及声明HCE特定的action。
2. import需要的NFC卡模拟模块和其他相关的模块。
3. 判断设备是否支持NFC能力和HCE能力。
4. 使能前台HCE应用程序优先处理NFC刷卡功能。
5. 订阅HCE APDU数据的接收。
6. 完成HCE刷卡APDU数据的接收和发送。
7. 退出应用程序NFC刷卡页面时，退出前台优先功能。

```ts
    "abilities": [
      {
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ts",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "ohos.want.action.home",

              // actions须包含"ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        // 添加使用nfc卡模拟需要的权限
        "name": "ohos.permission.NFC_CARD_EMULATION",
        "reason": "$string:app_name",
      }
    ]
```

```ts
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let hceElementName: bundleManager.ElementName;
let hceService: cardEmulation.HceService;

const hceCommandCb : AsyncCallback<number[]> = (error : BusinessError, hceCommand : number[]) => {
  if (!error) {
    if (hceCommand == null) {
      hilog.error(0x0000, 'testTag', 'hceCommandCb has invalid hceCommand.');
      return;
    }
    // 检查指令，发送response
    hilog.info(0x0000, 'testTag', 'hceCommand = %{public}s', JSON.stringify(hceCommand));
    let responseData = [0x90, 0x00]; // 根据接收到的不同命令更改response
    hceService.transmit(responseData).then(() => {
      hilog.info(0x0000, 'testTag', 'hceService transmit Promise success.');
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'hceService transmit Promise error = %{public}s', JSON.stringify(err));
    });
  } else {
    hilog.error(0x0000, 'testTag', 'hceCommandCb error %{public}s', JSON.stringify(error));
  }
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // 判断设备是否支持NFC能力和HCE能力
    if (!canIUse("SystemCapability.Communication.NFC.Core")) {
      hilog.error(0x0000, 'testTag', 'nfc unavailable.');
      return;
    }
    if (!cardEmulation.hasHceCapability()) {
      hilog.error(0x0000, 'testTag', 'hce unavailable.');
      return;
    }

    // hceElementName中元素不能为空，通过want获取应用的elementname或按应用实际信息填写
    hceElementName = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName,
    }
    hceService = new cardEmulation.HceService();
  }

  onForeground() {
    // 应用进入前台
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
    if (hceElementName != undefined) {
      try {
        // 调用接口使能前台HCE应用程序优先处理NFC刷卡功能
        let aidList = ["A0000000031010", "A0000000031011"]; // 修改为正确的aid
        hceService.start(hceElementName, aidList);

        // 订阅HCE APDU数据的接收
        hceService.on('hceCmd', hceCommandCb);
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'hceService.start error = %{public}s', JSON.stringify(error));
      }
    }
  }

  onBackground() {
    // 应用退到后台
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
    // 退出应用程序NFC标签页面时，调用tag模块退出前台优先功能
    if (hceElementName != undefined) {
      try {
        hceService.stop(hceElementName);
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'hceService.stop error = %{public}s', JSON.stringify(error));
      }
    }
  }
}
```

### HCE应用后台刷卡
1. 在module.json5文件中声明NFC卡模拟权限，声明HCE特定的action，声明应用能够处理的AID。
2. import需要的NFC卡模拟模块和其他相关的模块。
3. 判断设备是否支持NFC能力和HCE能力。
4. 订阅HCE APDU数据的接收。
5. 完成HCE刷卡APDU数据的接收和发送。
6. 退出应用程序时，退出订阅功能。

```ts
    "abilities": [
      {
        "name": "EntryAbility",
        "srcEntry": "./ets/entryability/EntryAbility.ts",
        "description": "$string:EntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "ohos.want.action.home",

              // actions须包含"ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
              "ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"
            ]
          }
        ],
        "metadata": [
          {
            "name": "payment-aid",
            "value": "A0000000031010" // 修改为正确的aid
          },
          {
            "name": "other-aid",
            "value": "A0000000031011" // 修改为正确的aid
          }
        ]
      }
    ],
    "requestPermissions": [
      {
        // 添加使用nfc卡模拟需要的权限
        "name": "ohos.permission.NFC_CARD_EMULATION",
        "reason": "$string:app_name",
      }
    ]
```

```ts
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let hceElementName : bundleManager.ElementName;
let hceService: cardEmulation.HceService;

const hceCommandCb : AsyncCallback<number[]> = (error : BusinessError, hceCommand : number[]) => {
  if (!error) {
    if (hceCommand == null || hceCommand == undefined) {
      hilog.error(0x0000, 'testTag', 'hceCommandCb has invalid hceCommand.');
      return;
    }

    // 检查指令，发送response
    hilog.info(0x0000, 'testTag', 'hceCommand = %{public}s', JSON.stringify(hceCommand));
    let responseData = [0x90, 0x00]; // change the response depend on different received command.
    hceService.transmit(responseData).then(() => {
      hilog.info(0x0000, 'testTag', 'hceService transmit Promise success.');
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'hceService transmit Promise error = %{public}s', JSON.stringify(err));
    });
  } else {
    hilog.error(0x0000, 'testTag', 'hceCommandCb error %{public}s', JSON.stringify(error));
  }
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // 判断设备是否支持NFC能力和HCE能力
    if (!canIUse("SystemCapability.Communication.NFC.Core")) {
      hilog.error(0x0000, 'testTag', 'nfc unavailable.');
      return;
    }
    if (!cardEmulation.hasHceCapability()) {
      hilog.error(0x0000, 'testTag', 'hce unavailable.');
      return;
    }

    hceElementName = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName,
    }
    hceService = new cardEmulation.HceService();
    hceService.on('hceCmd', hceCommandCb);
  }

  onForeground() {
    // 应用进入前台
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onDestroy() {
    // 退出应用
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
    // 退出应用程序NFC标签页面时，调用tag模块退出前台优先功能
    if (hceElementName != undefined) {
      try {
        hceService.stop(hceElementName);
      } catch (error) {
        hilog.error(0x0000, 'testTag', 'hceService.stop error = %{public}s', JSON.stringify(error));
      }
    }
  }
}
```