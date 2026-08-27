# @ohos.InputMethodExtensionAbility(InputMethodExtensionAbility)

###### 约束限制
 <br>
 <br>为保障系统安全性和稳定性，防止InputMethodExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考
 [附录](../../../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md#附录)。
 <br>
 <br>另外输入法应用区分基础模式和完整体验模式，关于基础模式和完整体验模式说明如下：
 <br>
 <br>**基础模式介绍：**
 <br>基础模式下，输入法扩展（InputMethodExtensionAbility）进程无法拉起其他UIAbility或ExtensionAbility。
 <br>
 <br>基础模式下，输入法扩展会受到系统管控，不能使用涉及访问或泄露用户个人数据的各种接口，同时无法将数据传递出进程。管控功能包括但不限于：网络、短信、电话、麦克风、定位、相机、蓝牙、壁纸、支付、日历、游戏、扬声器、Wi-Fi、剪切板、多媒体
 、联系人、公共事件、系统账号、健康数据、地图服务、推送服务、融合搜索、共享内存、分布式特性、广告设备标识、振动等。
 <br>
 <br>基础模式下，输入法扩展可以使用基础输入功能必要的系统能力，例如，IME Kit、ArkUI、窗口、图形、屏幕管理等。
 <br>
 <br> 基础模式下，输入法扩展对共享沙箱只读，对输入法扩展独立沙箱可读写；应用主入口可以对共享沙箱及其独立沙箱读写。
 <br>
 <br>**完整体验模式介绍：**
 <br>
 <br>完整体验模式下，输入法扩展不受基础模式相关限制，例如可以拉起其他UIAbility或ExtensionAbility、可以调用访问用户数据的接口等。
 <br>
 <br>完整体验模式下，输入法扩展可以对共享沙箱读写。
 <br>
 <br>###### 附录
 <br>
 <br>InputMethodExtensionAbility不支持以下模块的引用。<br>
 | Kit | 模块 |
 | -------- | -------- |
 | Ability Kit |  [@ohos.ability.featureAbility (FeatureAbility模块)](../../apis-ability-kit/arkts-apis/arkts-ability-featureability.md)</br>
 [@ohos.ability.particleAbility (ParticleAbility模块)](../../apis-ability-kit/arkts-apis/arkts-ability-particleability.md) |
 | Background Tasks Kit |
 [@ohos.resourceschedule.backgroundTaskManager (后台任务管理)](../../apis-background-tasks-kit/arkts-apis/arkts-resourceschedule-backgroundtaskmanager.md)
 </br>[@ohos.reminderAgentManager (后台代理提醒)](../../apis-background-tasks-kit/arkts-apis/arkts-reminderagentmanager.md)
 </br> [@ohos.reminderAgent (后台代理提醒)](../../apis-background-tasks-kit/arkts-apis/arkts-reminderagent.md) |
 | Basic Services Kit | [@ohos.account.osAccount (系统账号管理)](../../apis-basic-services-kit/arkts-apis/arkts-account-osaccount.md)
 </br>[@ohos.account.distributedAccount (分布式账号管理)](../../apis-basic-services-kit/arkts-apis/arkts-account-distributedaccount.md)
 </br>[@ohos.wallpaper (壁纸)](../../apis-basic-services-kit/arkts-apis/arkts-wallpaper.md) |
 | Connectivity Kit |  @ohos.bluetooth (蓝牙)
 </br>@ohos.bluetoothManager (蓝牙)</br>nfctech (标准NFC-Tag Nfc 技术)
 </br>[@ohos.nfc.controller (标准NFC)](../../apis-connectivity-kit/arkts-apis/arkts-nfc-controller.md)
 </br>[@ohos.nfc.cardEmulation (标准NFC-cardEmulation)](../../apis-connectivity-kit/arkts-apis/arkts-nfc-cardemulation.md)
 </br>[@ohos.connectedTag (有源标签)](../../apis-connectivity-kit/arkts-apis/arkts-connectedtag.md)</br>[@ohos.wifiext (WLAN扩展接口)](../../apis-connectivity-kit/arkts-apis/arkts-wifiext.md)
 </br>[@ohos.wifiManager (WLAN)](../../apis-connectivity-kit/arkts-apis/arkts-wifimanager.md)</br>[@ohos.wifiManagerExt (WLAN扩展接口)](../../apis-connectivity-kit/arkts-apis/arkts-wifimanagerext.md)
 </br>[tagSession (标准NFC-Tag TagSession)](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession-tagsession-i.md)</br> |
 | Location Kit | [@ohos.geolocation (位置服务)](../../apis-location-kit/arkts-apis/arkts-geolocation.md)
 </br>[@ohos.geoLocationManager (位置服务)](../../apis-location-kit/arkts-apis/arkts-geolocationmanager.md) |
 | Telephony Kit | [@ohos.telephony.call (拨打电话)](../../apis-telephony-kit/arkts-apis/arkts-telephony-call.md)</br>[@ohos.telephony.data (蜂窝数据)](../../apis-telephony-kit/arkts-apis/arkts-telephony-data.md)
 </br>[@ohos.telephony.observer (电话服务状态监听)](../../apis-telephony-kit/arkts-apis/arkts-telephony-observer.md)</br>[@ohos.telephony.radio (网络搜索)](../../apis-telephony-kit/arkts-apis/arkts-telephony-radio.md)
 </br>[@ohos.telephony.sms (短信服务)](../../apis-telephony-kit/arkts-apis/arkts-telephony-sms.md)</br>[@ohos.telephony.sim (SIM卡管理)](../../apis-telephony-kit/arkts-apis/arkts-telephony-sim.md) |


## 导入模块

```TypeScript
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [InputMethodExtensionAbility(InputMethodExtensionAbility)](arkts-ime-inputmethodextensionability-c.md) | @ohos.InputMethodExtensionAbility模块提供输入法ExtensionAbility（扩展能力基类）的基础类定义，是开发输入法应用的入口和生命周期管理框架。 本模块是输入法ExtensionAbility的核心类模块，定义了`InputMethodExtensionAbility`类，作为输入法应用的Extension基类。开发者需继承该类并实现`onCreate`和`onDestroy`生命周期回调， 系统在拉起和销毁输入法Extension时自动调用这些回调。 本模块提供两大核心能力：1）通过`onCreate(want)`回调实现输入法应用的初始化——系统拉起输入法Extension时调用，开发者在此完成资源加载、面板创建等初始化工作；2）通过`onDestroy()` 回调实现输入法应用的资源清理——系统销毁输入法Extension时调用，开发者在此释放资源。此外，通过`context`属性提供`InputMethodExtensionContext`上下文对象，供开发者在生命周期内执行销毁自身、 拉起其他应用等上下文级操作。 当开发输入法应用时必须使用本模块。开发者通过继承`InputMethodExtensionAbility` → 在module.json5中配置ExtensionAbility信息 → 系统拉起时触发`onCreate`（初始化） → 系统销毁或开发者主动调用`context.destroy()`时触发`onDestroy`（清理）。 |
