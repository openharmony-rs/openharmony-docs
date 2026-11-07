# Device Perception Development Guide (for System Applications Only)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=78cbd15adfb3603532824c708ed3640cf74c0375 translatedAt=2026-11-05T00:49:03.550Z pushedAt=2026-11-05T00:49:03.551Z nl=1 -->

## Overview

As distributed collaboration grows, devices increasingly need to wake one another for coordinated tasks. Based on Distributed SoftBus, OpenHarmony provides the device perception capability (softbusBase). It allows system applications to wake nearby devices through broadcasts containing custom data and discover nearby devices through scanning.

This module supports starting and stopping perception advertising and scanning, temporarily switching to high-frequency advertising, and querying discovered devices. These capabilities enable low-power, efficient wake-up and discovery among nearby devices.

### Working Principles

Device perception uses BLE advertising and scanning and does not require devices to join a network in advance. The advertiser broadcasts custom data through `startPerceptionAdv`. The scanner discovers nearby devices through `startPerceptionScan` and obtains their details through `getPerceptionDeviceList`. For short, high-frequency operations such as collaborative wake-up, the advertiser can call `setPerceptionAdvHighFreq` to switch to high-frequency advertising for 10 seconds.

Applications use `PerceptionType` to distinguish service scenarios, such as collaborative wake-up, and `PerceptionCycle` to control the scanning power consumption level.

### Constraints

- Configure the `ohos.permission.ACCESS_SOFTBUS_SYS_HAP` and `ohos.permission.DISTRIBUTED_DATASYNC` permissions.
- This capability is available only to system applications.
- Bluetooth (BLE) must be enabled on the device.
- The maximum length of custom data (`customData`) is 5 bytes. The maximum length of the device ID (`deviceId`) is 6 bytes, in network byte order (big-endian).
- This capability is supported since API version 26.0.1.

## Environment Setup

### Environment Requirements

Ensure that Bluetooth is enabled on the devices participating in perception.

### Setting Up the Environment

1. Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/deveco-studio) 4.1 or later on the development PC.
2. Update the public SDK to API version 26.0.1 or later. For details, see [OpenHarmony SDK Upgrade Assistant](../tools/openharmony-sdk-upgrade-assistant.md).
3. Connect the test device to the development PC using a USB cable.
4. Ensure that Bluetooth is enabled on the device.

## Available APIs

The following table describes commonly used APIs. For details, see [@ohos.distributed.softbusBase](../reference/apis-distributedservice-kit/js-apis-softbusBase-sys.md).

| Name | Description |
| --- | --- |
| startPerceptionAdv(type: PerceptionType, customData?: ArrayBuffer) | Starts perception advertising or updates the current owner's custom data. |
| setPerceptionAdvHighFreq(type: PerceptionType, customData?: ArrayBuffer) | Switches active perception advertising to high frequency for 10 seconds and optionally updates the custom data. |
| stopPerceptionAdv(type: PerceptionType) | Stops perception advertising for the current owner. |
| startPerceptionScan(type: PerceptionType, cycle: PerceptionCycle) | Starts perception scanning for the current owner with the specified keep-alive period. |
| stopPerceptionScan(type: PerceptionType) | Stops perception scanning and clears the list of discovered devices. |
| getPerceptionDeviceList(type: PerceptionType) | Obtains the list of devices discovered through perception scanning. |

### PerceptionType Enum

| Name | Value | Description |
| --- | --- | --- |
| PERCEPTION_TYPE_COLLABORATIVE_WAKE | 0 | Collaborative wake-up. Perception advertising or scanning of this type is used for cross-device collaborative wake-up. |

### PerceptionCycle Enum

| Name | Value | Description |
| --- | --- | --- |
| PERCEPTION_CYCLE_LOW | 0 | Low level. The keep-alive period is 150 seconds. A device is removed from the discovered device list if no advertisement is received from it within 150 seconds. |
| PERCEPTION_CYCLE_MEDIUM | 1 | Medium level. The keep-alive period is 75 seconds. A device is removed from the discovered device list if no advertisement is received from it within 75 seconds. |
| PERCEPTION_CYCLE_HIGH | 2 | High level. The keep-alive period is 30 seconds. A device is removed from the discovered device list if no advertisement is received from it within 30 seconds. |

### PerceptionDeviceInfo Structure

| Field | Type | Description |
| --- | --- | --- |
| deviceType | number | Device type identifier. It is an integer indicating the device category, for example, 0x0E for phones, 0x11 for tablets, 0x9C for TVs, and 0x0C for PCs. The actual values are defined by the system. |
| deviceId | ArrayBuffer | Device ID, up to 6 bytes long, in network byte order (big-endian). |
| customData | ArrayBuffer | Custom data carried in the advertisement, up to 5 bytes long. |

## Device Perception Development

- The advertiser calls `startPerceptionAdv()` to start advertising with custom data. For a short period of high-frequency advertising, it calls `setPerceptionAdvHighFreq()`.
- The scanner calls `startPerceptionScan()` to start scanning and `getPerceptionDeviceList()` to obtain discovered devices.
- When perception is no longer needed, call `stopPerceptionAdv()` or `stopPerceptionScan()` to stop advertising or scanning, respectively.

### Developing the Advertiser

1. Import the required module (the complete project must also import `BusinessError`, `Logger`, and other dependencies; see the sample).

    <!-- @[import_softbus_base](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    import softbusBase from '@ohos.distributed.softbusBase';
    ```

2. Configure permissions in the module.json5 file.

    ```json
    {
      "module": {
        "requestPermissions": [
          {
            "name": "ohos.permission.ACCESS_SOFTBUS_SYS_HAP"
          },
          {
            "name": "ohos.permission.DISTRIBUTED_DATASYNC",
            "reason": "$string:reason_distributed_datasync",
            "usedScene": {
              "abilities": [
                "EntryAbility"
              ],
              "when": "inuse"
            }
          }
        ]
      }
    }
    ```

3. Start perception advertising with custom data.

    <!-- @[start_adv](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
    const customData = this.buildCustomData();
    await softbusBase.startPerceptionAdv(type, customData);
    ```

4. (Optional) Switch to high frequency for 10 seconds and update the custom data.

    <!-- @[set_high_freq](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
    const customData = this.buildCustomData();
    await softbusBase.setPerceptionAdvHighFreq(type, customData);
    ```

5. Stop perception advertising.

    <!-- @[stop_adv](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
    await softbusBase.stopPerceptionAdv(type);
    ```

### Developing the Scanner

1. Import the required module (same as for the advertiser).

    <!-- @[import_softbus_base](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    import softbusBase from '@ohos.distributed.softbusBase';
    ```

2. Configure permissions in the module.json5 file (same as for the advertiser; see above).

3. Start perception scanning with the specified keep-alive period.

    <!-- @[start_scan](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
    const cycle = softbusBase.PerceptionCycle.PERCEPTION_CYCLE_MEDIUM;
    await softbusBase.startPerceptionScan(type, cycle);
    ```

4. Obtain the devices discovered through perception scanning.

    <!-- @[get_device_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
    const devices = await softbusBase.getPerceptionDeviceList(type);
    ```

5. Stop perception scanning and clear the device list.

    <!-- @[stop_scan](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedSoftbusBase/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const type = softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE;
    await softbusBase.stopPerceptionScan(type);
    ```
