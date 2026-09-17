# HidDeviceSdp

Describe the HID device capability fields of this endpoint being queried.

**Since:** 23

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## description

```TypeScript
description: string
```

description for this Bluetooth hid device. Maximum length is 50 bytes.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptors

```TypeScript
descriptors: Uint8Array
```

descriptors identifies the descriptors associated with the bluetooth hid device.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## name

```TypeScript
name: string
```

name of this Bluetooth hid device. Maximum length is 50 bytes.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## provider

```TypeScript
provider: string
```

provider of this Bluetooth hid device. Maximum length is 50 bytes.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## subclass

```TypeScript
subclass: Subclass
```

Subclass of this Bluetooth HID device. Subclass represents the specific HID device type.

**Type:** [Subclass](arkts-connectivity-hid-subclass-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core
