# BluetoothInfo

```TypeScript
export interface BluetoothInfo
```

Represents the device Bluetooth information.

**Since:** 12

<!--Device-bluetoothManager-export interface BluetoothInfo--><!--Device-bluetoothManager-export interface BluetoothInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
```

## connectionState

```TypeScript
connectionState: constant.ProfileConnectionState
```

Bluetooth profile connection state of the device.

**Type:** [constant.ProfileConnectionState](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-constant-profileconnectionstate-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BluetoothInfo-connectionState: constant.ProfileConnectionState--><!--Device-BluetoothInfo-connectionState: constant.ProfileConnectionState-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

Bluetooth name of the device.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BluetoothInfo-name: string--><!--Device-BluetoothInfo-name: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## state

```TypeScript
state: access.BluetoothState
```

Bluetooth state of the device.

**Type:** [access.BluetoothState](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-access-bluetoothstate-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BluetoothInfo-state: access.BluetoothState--><!--Device-BluetoothInfo-state: access.BluetoothState-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
