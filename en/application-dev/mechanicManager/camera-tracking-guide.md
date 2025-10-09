# Intelligent Tracking Photography
<!--Kit: Mechanic Kit-->
<!--Subsystem: Mechanic-->
<!--Owner: @hobbycao-->
<!--Designer: @saga2025-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @foryourself-->

Mechanic Manager is supported since API version 20. In application scenarios such as video recording and live streaming, you may want to provide users with mechanic devices more enriched photography experiences, including professional photography functions like intelligent camera tracking and automatic composition.

The intelligent camera tracking function enables automated tracking of faces and objects through mechanic devices, enhancing photography quality and user experience and helping developers to build smarter, more efficient photography solutions.

## Available APIs

For details about how to use the public APIs of Mechanic Manager, see [@ohos.distributedHardware.mechanicManager (Mechanic Manager)](../reference/apis-mechanic-kit/js-apis-mechanicManager.md).

| Name                                                              | Description                      |
| -------------------------------------------------------------------- | -------------------------- |
|on(type: 'attachStateChange', callback: Callback\<AttachStateChangeInfo>): void | Registers the callback listener for **attachStateChange** events.<br>**Note**: This API is supported since API version 20.|
|off(type: 'attachStateChange', callback?: Callback\<AttachStateChangeInfo>): void | Unregisters the callback listener for **attachStateChange** events.<br>**Note**: This API is supported since API version 20.|
|getAttachedMechDevices(): MechInfo[] | Obtain the list of connected mechanic devices.<br>**Note**: This API is supported since API version 20.|
|setCameraTrackingEnabled(isEnabled: boolean): void | Enables or disables camera tracking.<br>**Note**: This API is supported since API version 20.|
|getCameraTrackingEnabled(): boolean | Checks whether camera tracking is enabled.<br>**Note**: This API is supported since API version 20.|
|on(type: 'trackingStateChange', callback: Callback\<TrackingEventInfo>): void | Registers a callback listener for the **trackingStateChange** events.<br>**Note**: This API is supported since API version 20.|
|off(type: 'trackingStateChange', callback?: Callback\<TrackingEventInfo>): void | Unregisters the callback listener for **trackingStateChange** events.<br>**Note**: This API is supported since API version 20.|
|setCameraTrackingLayout(trackingLayout: CameraTrackingLayout): void | Sets the camera tracking layout.<br>**Note**: This API is supported since API version 20.|
|getCameraTrackingLayout(): CameraTrackingLayout | Obtains the camera tracking layout of the mechanic device.<br>**Note**: This API is supported since API version 20.|
|on(type: 'rotationAxesStatusChange', callback: Callback\<RotationAxesStateChangeInfo>): void | Registers a callback listener for the **rotationAxesStatusChange** events.<br>**Note**: This API is supported since API version 20.|
|off(type: 'rotationAxesStatusChange', callback?: Callback\<RotationAxesStateChangeInfo>): void | Unregisters the callback listener for **rotationAxesStatusChange** events.<br>**Note**: This API is supported since API version 20.|

## How to Develop

### Getting Started

1. Prepare a mechanic device that supports MechanicKit.

2. Ensure that the mechanic device is connected to the development device via Bluetooth.

### Managing the Device Connection Status

Dynamic device connection status management helps to ensure that the application responds promptly when the mechanic device is connected or disconnected.

1. Import the **mechanicManager** module.

    ```ts
    import { mechanicManager } from '@kit.MechanicKit';
    ```

2. Obtain the list of connected mechanic devices.

    ```ts
    let savedMechanicIds: number[] = [];

    try {
    const devices = mechanicManager.getAttachedMechDevices();
    console.info('Connected devices:', devices);

    devices.forEach(device => {
        console.info(`Device ID: ${device.mechId}`);
        console.info(`Device Name: ${device.mechName}`);
        console.info(`Device Type: ${device.mechDeviceType}`);
        
    // Save the MechId of the device whose device type is GIMBAL_DEVICE.
        if (device.mechDeviceType === mechanicManager.MechDeviceType.GIMBAL_DEVICE) {
        savedMechanicIds.push(device.mechId);
        console.info(`GIMBAL_TYPE device saved ID: ${device.mechId}`);
        } else {
        console.info(`Skip non-gimbal devices: ${device.mechId}`);
        }
    });

    console.info('List of saved gimbal device IDs:', savedMechanicIds);
    } catch (err) {
    console.error('Error getting attached devices:', err);
    }
    ```

3. Listen for device connection state changes.

    ```ts
    const attachStateChangeCallback = (info: mechanicManager.AttachStateChangeInfo) => {
    if (info.state === mechanicManager.AttachState.ATTACHED) {
        console.info('Device attached:', info.mechInfo);
        // Process the device connection logic.
        handleDeviceAttached(info.mechInfo);
    } else if (info.state === mechanicManager.AttachState.DETACHED) {
        console.info('Device detached:', info.mechInfo);
        // Process the device disconnection logic.
        handleDeviceDetached(info.mechInfo);
    }
    };

    // Register a callback listener.
    mechanicManager.on('attachStateChange', attachStateChangeCallback);
    ```

4. Process device connection and disconnection events.

    ```ts
    function handleDeviceAttached(mechInfo: mechanicManager.MechInfo) {
    console.info(`New device is connected: ${mechInfo.mechName} (ID: ${mechInfo.mechId})`);
    savedMechanicIds.push(mechInfo.mechId);
    // To do sth.
    }

    function handleDeviceDetached(mechInfo: mechanicManager.MechInfo) {
    console.info(`Device disconnected: ${mechInfo.mechName} (ID: ${mechInfo.mechId})`);
    savedMechanicIds.filter(id => id !== mechInfo.mechId);
    // To do sth.
    }
    ```

5. Disable listening for device connection state changes.

    ```ts
    // Cancel listening for device connection state changes.
    mechanicManager.off('attachStateChange', attachStateChangeCallback);
    ```

### Enabling Intelligent Camera Tracking

After the intelligent tracking photography function is enabled, the mechanic device will automatically detect faces and perform tracking photography.

1. Enable the intelligent tracking photography function.

    ```ts
    try {
    // Check whether savedMechIds is empty.
    // Check the tracking status.
    const isEnabled = mechanicManager.getCameraTrackingEnabled();

    if (isEnabled == false) {
        // Enable the tracking photography function.
        mechanicManager.setCameraTrackingEnabled(true);
        console.info('Camera tracking enabled');
    }

    console.info('Is tracking currently enabled:', isEnabled);
    } catch (err) {
    console.error('Failed to enable camera tracking:', err);
    }
    ```

2. Enable listening for tracking state change events.

    ```ts
    const trackingStateCallback = (eventInfo : mechanicManager.TrackingEventInfo) => {
    switch (eventInfo.event) {
        case mechanicManager.TrackingEvent.CAMERA_TRACKING_USER_ENABLED:
        console.info('The user has enabled camera tracking');
        handleTrackingEnabled();
        break;
        case mechanicManager.TrackingEvent.CAMERA_TRACKING_USER_DISABLED:
        console.info('The user has disabled camera tracking');
        handleTrackingDisabled();
        break;
        case mechanicManager.TrackingEvent.CAMERA_TRACKING_LAYOUT_CHANGED:
        console.info('Tracking layout has changed');
        handleLayoutChanged();
        break;
    }
    };

    // Register the listener for tracking state changes.
    mechanicManager.on('trackingStateChange', trackingStateCallback);
    ```

3. Process the tracking state change events.

    ```ts
    function handleTrackingEnabled() {
    console.info('Handling trace enable events');
    // Update the UI status.
    updateTrackingUI(true);
    }

    function handleTrackingDisabled() {
    console.info('Handling trace disabled events');
    // Update the UI status.
    updateTrackingUI(false);
    }

    function handleLayoutChanged() {
    try {
        const newLayout = mechanicManager.getCameraTrackingLayout();
        console.info('New Tracking Layout:', newLayout);
        // Update the UI based on the new layout.
        updateLayoutUI(newLayout);
    } catch (err) {
        console.error('Failed to get new layout:', err);
    }
    }

    function updateTrackingUI(enabled: boolean) {
    // Update the tracking status on the UI.
    // To do sth.
    console.info('Update tracking UI status:', enabled);
    }

    function updateLayoutUI(layout : mechanicManager.CameraTrackingLayout) {
    // Update the layout status on the UI.
    // To do sth.
    console.info('Update layout UI:', layout);
    }
    ```

4. Disable listening for tracking state change events.

    ```ts
    // Cancel listening for the specified callback of tracking state changes.
    mechanicManager.off('trackingStateChange', trackingStateCallback);

    // Or cancel listening for all callbacks of tracking state changes.
    mechanicManager.off('trackingStateChange');
    ```

### Debugging and Verification

To ensure proper functioning of Mechanic Manager, perform the following steps for debugging and verification:

**Connection Setup**

1. Ensure that the mechanic device is paired with and connected to the development device via Bluetooth.
2. Place the development device on the mechanic device.

**Test Procedure**

1. **Querying the device list**: Call `getAttachedMechDevices` to query the list of connected mechanic devices and check whether all mechanic devices are correctly identified.
2. **Enabling intelligent tracking photography**: Call `setCameraTrackingEnabled` to enable the intelligent tracking photography function, and call `getCameraTrackingEnabled` to verify the status. Check whether the device can automatically rotate with the target.

**Test Result Description**

- If a list containing all mechanic device is returned after `getAttachedMechDevices` is called, the device identification is normal.
- If `true` is returned after `getCameraTrackingEnabled` is called, the intelligent tracking photography function is successfully enabled.
