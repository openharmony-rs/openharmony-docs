# @ohos.settingsLite (Setting Information)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Applications-->
<!--Owner: @guo_san_quan-->
<!--Designer: @tuonixiaositing-->
<!--Tester: @c30034487-->
<!--Adviser: @fang-jinxu-->

This module provides lightweight setting capabilities and allows you to redirect to the settings page.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import settingsLite from '@ohos.settingsLite';
```

## settingsLite.openPinSettingPage

openPinSettingPage(): void

Opens the password settings page.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Model restriction:** This API can be used only in the FA model.

**Example**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.openPinSettingPage();
```

## settingsLite.openNfcSettingsPage

openNfcSettingsPage(): void

Opens the NFC settings page.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Model restriction:** This API can be used only in the FA model.

**Example**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.openNfcSettingsPage();
```

## settingsLite.openDoubleClickSettingsPage

openDoubleClickSettingsPage(): void

Opens the double-click settings page.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Model restriction:** This API can be used only in the FA model.

**Example**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.openDoubleClickSettingsPage();
```

## settingsLite.isDoubleClickAppForSelf

isDoubleClickAppForSelf(callback: ClickCallback): void

Checks whether the default application started by double-pressing the down button is the current application.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Model restriction:** This API can be used only in the FA model.

**Parameters**

| Name     | Type                             | Mandatory | Description     |
| -------- | ------------------------------- | --- | ------- |
| callback | [ClickCallback](#clickcallback) | Yes  | Callback used to return the check result.|

**Example**

```js
import settingsLite from '@ohos.settingsLite';

settingsLite.isDoubleClickAppForSelf({
    onResult(result) {
        console.info('isDoubleClickAppForSelf result: ' + result);
    }
});
```

## ClickCallback

Checks the callback on the double-click settings page.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Model restriction:** This API can be used only in the FA model.

### onResult

onResult(result: boolean):void

Defines a callback used to return the double-click result.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

**Model restriction:** This API can be used only in the FA model.

**Parameters**

| Name   | Type     | Mandatory | Description    |
| ------ | ------- | --- | ------ |
| result | boolean | Yes  | Check result.|
