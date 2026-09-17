# @ohos.nfc.tag(Standard NFC Tags)

The **tag** module provides APIs for operating and managing NFC tags. The following tag read modes are available:

Background mode: The device reads the tag by using NFC without starting any application, and then searches for applications based on the tag type. If only one application is matched, the card reading page of that application will be started. If multiple applications are matched, an application selector will be started, asking the user to select an application. Background mode does not involve tag-related APIs. For details, see [nfc-tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md#accessing-an-nfc-tag-without-starting-an-application).

Foreground mode: A foreground application has priority to read the NFC tag discovered.

> **NOTE:** 
> 
> 2. Since API version 26.0.0, it is more accurate to determine whether a device supports NFC by calling both [canIUse("SystemCapability.Communication.NFC.Tag")](../../../reference/common/init.md#caniuse) and [nfcController.isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md). If the device does not support NFC, the application stability may be affected. For details, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).
> 
> 3. If an error is reported while importing the tag module editor, the capabilities of a specific device model may exceed the capability set defined for the default device. To use these capabilities, configure a custom SysCap by following instructions in [SystemCapability](https://developer.huawei.com/consumer/en/doc/harmonyos-references/syscap).

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [tag](arkts-connectivity-tag-n.md) | The **tag** module provides APIs for operating and managing NFC tags. The following tag read modes are available: |
