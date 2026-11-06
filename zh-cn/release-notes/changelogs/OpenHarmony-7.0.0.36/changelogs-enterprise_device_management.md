# 定制子系统Changelog

## cl.customization.1 企业设备管理服务部分接口错误码的类型从string类型变更为number类型

**访问级别**

公共能力

**变更原因**

系统错误码类型应为number类型，而企业设备管理服务接口的实现一直使用string类型。为规范数据类型，从API版本26.0.0开始，企业设备管理服务新增接口的错误码类型变更为number类型。

**变更影响**

此变更涉及应用适配。
- 变更前：企业设备管理服务接口错误码类型为string类型。
- 变更后：企业设备管理服务接口错误码类型为number类型。

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let bundleNames: Array<string> = ['com.example.notificationapp'];

try {
  applicationManager.addAllowedNotificationBundles(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding allowed notification bundles.');
} catch (err) {
  console.error(`Code type is ${typeof(err.code)}`);
  // 变更前打印：Code type is string
  // 变更后打印：Code type is number
}
```


**起始API Level**

26.0.0

**变更发生版本**

从OpenHarmony SDK 7.0.0.36开始。

**变更的接口/组件**
- adminManager.enableSelfDeviceAdmin
- applicationManager.addAllowedNotificationBundles
- applicationManager.removeAllowedNotificationBundles
- applicationManager.getAllowedNotificationBundles
- applicationManager.queryBundleStatsInfos
- applicationManager.queryTrafficStats
- bundleManager.installForResult
- bundleManager.getInstalledBundleStorageStats
- deviceControl.operateDevice
- deviceSettings.setSwitchStatus
- securityManager.setScreenLockDisabledForAccount
- securityManager.isScreenLockDisabledForAccount
- securityManager.setScreenWatermarkImage
- securityManager.cancelScreenWatermarkImage
- telephonyManager.activeSim
- telephonyManager.deactiveSim
- telephonyManager.setDefaultData
- telephonyManager.getDefaultData

**适配指导**

接口默认行为变更。使用上述接口的开发者，如果业务代码使用了错误码类型判断，则需要适配。

以 `applicationManager.addAllowedNotificationBundles`为例，适配方法如下：
```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let bundleNames: Array<string> = ['com.example.notificationapp'];

try {
  applicationManager.addAllowedNotificationBundles(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding allowed notification bundles.');
} catch (err) {
  // 必须使用 number 类型进行判断
  if (err.code === 9200001) {
    // 相关业务操作
  }
}
```
