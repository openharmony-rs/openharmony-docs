# @ohos.InputMethodExtensionAbility (InputMethodExtensionAbility)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

本模块支持开发者自行开发输入法应用，以及管理输入法Extension的生命周期。

> **说明：**
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在Stage模型下使用。
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

## 约束限制

为保障系统安全性和稳定性，防止InputMethodExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

另外输入法应用区分基础模式和完整体验模式，关于基础模式和完整体验模式说明如下：

**基础模式介绍：**
基础模式下，输入法扩展（InputMethodExtensionAbility）进程无法拉起其他UIAbility或ExtensionAbility。

基础模式下，输入法扩展会受到系统管控，不能使用涉及访问或泄露用户个人数据的各种接口，同时无法将数据传递出进程。管控功能包括但不限于：网络、短信、电话、麦克风、定位、相机、蓝牙、壁纸、支付、日历、游戏、扬声器、Wi-Fi、剪切板、多媒体、联系人、公共事件、系统账号、健康数据、地图服务、推送服务、融合搜索、共享内存、分布式特性、广告设备标识、振动等。

基础模式下，输入法扩展可以使用基础输入功能必要的系统能力，例如，IME Kit、ArkUI、窗口、图形、屏幕管理等。

基础模式下，输入法扩展对共享沙箱只读，对输入法扩展独立沙箱可读写；应用主入口可以对共享沙箱及其独立沙箱读写。

**完整体验模式介绍：**

完整体验模式下，输入法扩展不受基础模式相关限制，例如可以拉起其他UIAbility或ExtensionAbility、可以调用访问用户数据的接口等。

完整体验模式下，输入法扩展可以对共享沙箱读写。

## 导入模块

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## InputMethodExtensionAbility

输入法Extension ability类。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

### 属性

输入法Extension ability的上下文信息。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [InputMethodExtensionContext](js-apis-inputmethod-extension-context.md) | 否 | 否 | InputMethodExtension的上下文环境，继承于ExtensionContext。 |

### onCreate

onCreate(want: Want): void

Extension生命周期回调，在拉起输入法Extension时调用，执行初始化输入法应用操作。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型          | 必填 | 说明                             |
| ------ | ----------- | ---- | ------------------------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want?.abilityName);
  }
}
```

### onDestroy

onDestroy(): void

Extension生命周期回调，在销毁输入法应用时回调，执行资源清理等操作。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onDestroy(): void {
    console.info('onDestroy');
  }
}
```
## 附录

InputMethodExtensionAbility不支持以下模块的引用。
| Kit | 模块 |
| -------- | -------- |
| Ability Kit |  [@ohos.ability.featureAbility (FeatureAbility模块)](../apis-ability-kit/js-apis-ability-featureAbility.md)</br>[@ohos.ability.particleAbility (ParticleAbility模块)](../apis-ability-kit/js-apis-ability-particleAbility.md) |
| Background Tasks Kit |  [@ohos.resourceschedule.backgroundTaskManager (后台任务管理)](../apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md)</br>[@ohos.reminderAgentManager (后台代理提醒)](../apis-backgroundtasks-kit/js-apis-reminderAgentManager.md)</br> [@ohos.reminderAgent (后台代理提醒)](../apis-backgroundtasks-kit/js-apis-reminderAgent.md) |
| Basic Services Kit | [@ohos.account.osAccount (系统账号管理)](../apis-basic-services-kit/js-apis-osAccount.md)</br>[@ohos.account.distributedAccount (分布式账号管理)](../apis-basic-services-kit/js-apis-distributed-account.md)</br>[@ohos.wallpaper (壁纸)](../apis-basic-services-kit/js-apis-wallpaper.md) |
| Connectivity Kit |  [@ohos.bluetooth (蓝牙)](../apis-connectivity-kit/js-apis-bluetooth.md)</br>[@ohos.bluetoothManager (蓝牙)](../apis-connectivity-kit/js-apis-bluetoothManager.md)</br>[nfctech (标准NFC-Tag Nfc 技术)](../apis-connectivity-kit/js-apis-nfctech.md)</br>[@ohos.nfc.controller (标准NFC)](../apis-connectivity-kit/js-apis-nfcController.md)</br>[@ohos.nfc.cardEmulation (标准NFC-cardEmulation)](../apis-connectivity-kit/js-apis-cardEmulation.md)</br>[@ohos.connectedTag (有源标签)](../apis-connectivity-kit/js-apis-connectedTag.md)</br>[@ohos.wifiext (WLAN扩展接口)](../apis-connectivity-kit/js-apis-wifiext.md)</br>[@ohos.wifiManager (WLAN)](../apis-connectivity-kit/js-apis-wifiManager.md)</br>[@ohos.wifiManagerExt (WLAN扩展接口)](../apis-connectivity-kit/js-apis-wifiManagerExt.md)</br>[tagSession (标准NFC-Tag TagSession)](../apis-connectivity-kit/js-apis-tagSession.md)</br> |
| Location Kit | [@ohos.geolocation (位置服务)](../apis-location-kit/js-apis-geolocation.md)</br>[@ohos.geoLocationManager (位置服务)](../apis-location-kit/js-apis-geoLocationManager.md) |
| Telephony Kit | [@ohos.telephony.call (拨打电话)](../apis-telephony-kit/js-apis-call.md)</br>[@ohos.telephony.data (蜂窝数据)](../apis-telephony-kit/js-apis-telephony-data.md)</br>[@ohos.telephony.observer (observer)](../apis-telephony-kit/js-apis-observer.md)</br>[@ohos.telephony.radio (网络搜索)](../apis-telephony-kit/js-apis-radio.md)</br>[@ohos.telephony.sms (短信服务)](../apis-telephony-kit/js-apis-sms.md)</br>[@ohos.telephony.sim (SIM卡管理)](../apis-telephony-kit/js-apis-sim.md) |