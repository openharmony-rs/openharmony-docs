# Converged Short-Range Service Development Overview

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @guoxiadi-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=2dfae07aab20af8fdc02150f7d49baaef283b81a translatedAt=2026-05-30T02:49:51.762Z pushedAt=2026-06-01T11:15:21.645Z -->

## Overview

The converged short-range communication service (converged short-range for short) is a service in OpenHarmony that centrally manages short-range communication technologies. Currently, it implements the **PartnerAgent** service module internally.

This module provides interoperability services between partner devices and OpenHarmony devices. Typical scenarios include:<br>

- Media control: A watch displays the music or video currently played on an OpenHarmony device. Partner devices such as watches or headsets can control media playback on the OpenHarmony device, for example, playing the previous or next item, and playing or pausing media.

- Call control: When an OpenHarmony device receives an incoming call, the watch is notified and displays the caller number and contact name. Partner devices such as watches or headsets can answer or reject incoming calls on the OpenHarmony device.

- Health monitoring: Wearables collect human health data in real time and report the data to OpenHarmony devices. OpenHarmony devices can display health monitoring data in real time.

These scenarios require partner devices to maintain long-term interconnection with OpenHarmony devices. When data interaction occurs, such as media control, call control, or health data interaction, applications must be wakeable and capable of exchanging data. This service provides a solution for keeping application processes wakeable, ensuring that partner device vendor applications required by partner devices can be woken up and run properly during data interaction.

## System Architecture

![PartnerAgent Service Architecture Diagram](figures/fusionConnectivity-architecture.png)

### Module Function Description

The overall architecture is divided into the application layer, framework layer (providing APIs), and system service layer.

* **Application layer**

  * **System settings**: Calls the `partnerAgent-sys` system APIs to enable or disable the capability of a partner device. After this capability is disabled, the **PartnerAgent** service will no longer start the partner device Extension.

  * **Partner device application**: An end-user application implemented by an ecosystem device vendor, which calls the `bindDevice()` API of `partnerAgent` to register partner devices.

  * **Partner device Extension**: A `PartnerAgentExtensionAbility` implemented by a partner device application. This extension ability can establish Bluetooth connections with partner devices and transmit Bluetooth data. After receiving commands from partner devices, the partner device Extension can perform media control and call control.

- **Framework layer**

  * **partnerAgent-sys**: Provides the `enableDeviceControl` and `disableDeviceControl` APIs for system settings to enable or disable the capability of a partner device. After this capability is disabled, the PartnerAgent service will no longer start the partner device Extension.

  * **partnerAgent**: Provides APIs such as `bindDevice`, `unbindDevice`, and `getBoundDevices` for partner device applications, and handles registration, binding, and unregistration of partner devices.

  * **PartnerAgentExtensionAbility**: Provides APIs such as `onDeviceDiscovered` for partner device Extensions, and notifies a partner device Extension that the corresponding partner device has been discovered.

  * **PartnerAgentExtensionContext**: Provides context information for a partner device Extension when it is started.

- **System service layer**

  * **Partner device registration management**: Manages registered partner device information.

    * A partner device application can call `bindDevice` to register a partner device, and call `unbindDevice` to deregister a partner device.

    * After the **PartnerAgent** service detects that a partner device is registered, it calls Bluetooth service APIs to perform BLE scanning and listen for Bluetooth connection status to discover the partner device.

    * In the following scenarios, the **PartnerAgent** service automatically unregisters a device: 1. the Bluetooth pairing relationship of a partner device registered by a partner device application has been lost for more than 30 days; 2. the partner device application associated with a registered partner device is uninstalled.

  * **PartnerAgentExtensionAbility management**: Controls partner device Extensions. After a partner device registered by a partner device application is discovered through Bluetooth BLE scanning or Bluetooth connection, this module starts the partner device Extension process and notifies the partner device Extension through the `onDeviceDiscovered` API.

  * **PartnerAgent service lifecycle management**: Provides dynamic startup and shutdown of the **PartnerAgent** service process to prevent resource waste.

  * **Proxy notification**: Manages notification reminders on the minus 1 screen. It mainly reminds users that the partner device Extension process is running in the background, which increases power consumption and may control the media and call capabilities of OpenHarmony devices.

  * **Bluetooth service/AbilityManager service/SAMgr management/notification service**: Basic OpenHarmony system services. The Bluetooth service is responsible for Bluetooth scanning, Bluetooth connection, and Bluetooth data transmission. The AbilityManager service provides the capability of starting and destroying partner device Extensions. SAMgr management is responsible for starting and destroying the **PartnerAgent** service. The notification service is responsible for displaying notifications on the minus 1 screen.