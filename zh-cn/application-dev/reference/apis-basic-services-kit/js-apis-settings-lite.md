# @ohos.settingsLite (设置信息)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Applications-->
<!--Owner: @guo_san_quan-->
<!--Designer: @tuonixiaositing-->
<!--Tester: @c30034487-->
<!--Adviser: @fang-jinxu-->

本模块提供轻量级设置能力，支持跳转至设置页面。

> **说明：**
> 
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块
**支持设备**：Lite Wearable
```js
import settingsLite from '@ohos.settingsLite';
```

## settingsLite.openPinSettingPage
**支持设备**：Lite Wearable

openPinSettingPage(): void

打开密码设置页面。

**系统能力：** SystemCapability.Applications.Settings.Core.Lite

**模型约束：** 此接口仅可在FA模型下使用。

**起始版本：** 6.1.1(24)

**示例：**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.openPinSettingPage();
```

## settingsLite.openNfcSettingsPage
**支持设备**：Lite Wearable

openNfcSettingsPage(): void

打开NFC设置页面。

**系统能力：** SystemCapability.Applications.Settings.Core.Lite

**模型约束：** 此接口仅可在FA模型下使用。

**起始版本：** 6.1.1(24)

**示例：**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.openNfcSettingsPage();
```

## settingsLite.openDoubleClickSettingsPage
**支持设备**：Lite Wearable

openDoubleClickSettingsPage(): void

打开按键设置-双击下按键页面。

**系统能力：** SystemCapability.Applications.Settings.Core.Lite

**模型约束：** 此接口仅可在FA模型下使用。

**起始版本：** 6.1.1(24)

**示例：**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.openDoubleClickSettingsPage();
```

## settingsLite.isDoubleClickAppForSelf
**支持设备**：Lite Wearable

isDoubleClickAppForSelf(callback: ClickCallback): void

判断双击下按键的默认启动应用是否为本应用。

**系统能力：** SystemCapability.Applications.Settings.Core.Lite

**模型约束：** 此接口仅可在FA模型下使用。

**起始版本：** 6.1.1(24)

**参数：**

| 参数名      | 类型                              | 必填  | 说明      |
| -------- | ------------------------------- | --- | ------- |
| callback | [ClickCallback](#clickcallback) | 是   | 返回检查结果。 |

**示例：**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.isDoubleClickAppForSelf({
    onResult(result) {
        console.info('isDoubleClickAppForSelf result: ' + result);
    }
});
```

## ClickCallback

按键设置-双击下按键页面检查回调。

**系统能力：** SystemCapability.Applications.Settings.Core.Lite

| 名称       | 类型                        | 说明                                  |
| -------- | ------------------------- | ----------------------------------- |
| onResult | (result: boolean) => void | 双击下按键的默认启动应用为当前应用则返回true，否则返回false。 |