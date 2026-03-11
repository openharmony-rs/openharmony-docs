# Distributed Device Management Development
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hwzhangchuang-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

## Introduction

The distributed service allows multiple physically separated devices to be integrated into a virtual Super Device, allowing one device to control others and sharing data among devices with distributed communication capabilities.

As the entry of the distributed service, distributed device management implements unified management of trusted and untrusted devices nearby.

Distributed device management provides the following functionalities:

- **Discovering devices**<br>
  Discover and report the devices that are connected to the same LAN or have Bluetooth enabled. You can filter devices based on the device type, distance, and whether the device is trusted.

- **Binding a device**<br>
  Bind an untrusted device discovered to establish a trust relationship with each other. The device authentication framework provides a variety of authentication modes, such as PIN-based pairing, tap-to-pair, and scan-to-pair, and supports diversified authentication APIs.

- **Querying device information**<br>
  Obtain local device information, brief information about all the trusted devices, and detailed information about a trusted device.

- **Listening for devices**<br>
  Listen for online/offline status of nearby devices. If a device goes online, the device is trusted and distributed operations can be performed. If a device goes offline, the distributed service is unavailable.

### Working Principles

  When discovering a device, the application initiates a request for binding the device to establish a trust relationship. When the service ends, the service determines whether to unbind the device.

### Constraints

  The distributed service is available only for the devices connected to the same LAN or have Bluetooth enabled.

  Device information is sensitive user data. Even if the devices are connected to the same LAN or have Bluetooth enabled, the application must request the ohos.permission.DISTRIBUTED_DATASYNC permission from the user before obtaining the device location. The system provides the device management capabilities for the application only after the user has granted the permission.

## Requesting Permissions

### Scenario

To use the distributed device management capabilities, your application must have the ohos.permission.DISTRIBUTED_DATASYNC permission, which allows application data to be exchanged between devices. This permission is a user_grant permission, which means the application must apply for user authorization.

Before using the distributed device management capabilities, the application must be checked for the

required permission.

### How to Develop

The APIs used in this section are based on the stage model.

1. Declare the ohos.permission.DISTRIBUTED_DATASYNC permission in the **module.json5** file.

   ```ts
   {
     "module" : {
       "requestPermissions":[
         {
           "name" : "ohos.permission.DISTRIBUTED_DATASYNC",
           "reason": "$string:distributed_permission",
           "usedScene": {
             "abilities": [
               "MainAbility"
             ],
             "when": "inuse"
           }
         }
       ]
     }
   }
   ```
2. Import the **abilityAccessCtrl** module, which is used to obtain the capability of applying for permissions.

   ```ts
   import { abilityAccessCtrl } from '@kit.AbilityKit';
   ```

3. Use **requestPermissionsFromUser** to request user authorization for the ohos.permission.DISTRIBUTED_DATASYNC permission.

   <!-- @[permissions_user_grant](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let atManager = abilityAccessCtrl.createAtManager();
    atManager.requestPermissionsFromUser(getContext(this), ['ohos.permission.DISTRIBUTED_DATASYNC'])
      .then(async (data) => {
        logger.info(`data: ${JSON.stringify(data)}`);
		// ···
      })
      .catch((err: BusinessError) => {
        logger.error(`requestPermissionsFromUser error: ${JSON.stringify(err)}`);
    });
```


## Discovering Devices

### Scenario

Discover nearby devices.

### Available APIs

startDiscovering(discoverParam: {[key:&nbsp;string]:&nbsp;Object;} , filterOptions?: {[key:&nbsp;string]:&nbsp;Object;} ): void;

Starts to discover the devices that are in the same LAN or have Bluetooth enabled. For details, see [startDiscovering](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#startdiscovering).


### How to Develop

1. Request the ohos.permission.DISTRIBUTED_DATASYNC permission for your application.

2. Import the **distributedDeviceManager** module, which provides APIs for device management.
   
   ```ts
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```

3. Import the **BusinessError** module, which provides the error codes thrown by the APIs of the **distributedDeviceManager** module.
   
   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

4. Create a device management instance. The device management instance acts as the entrance for calling distributed device management methods.

   <!-- @[create_device_manager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

``` TypeScript
  async createDeviceManager(): Promise<void> {
    if (typeof (this.deviceManager) != 'undefined') {
      return;
    }

    logger.info('[DeviceManager.RemoteDeviceModel] deviceManager.createDeviceManager begin');
    try {
      let dmInstance = distributedDeviceManager.createDeviceManager('com.samples.devicemanager');
      this.deviceManager = dmInstance
	// ···
      logger.info(`[DeviceManager.RemoteDeviceModel] createDeviceManager callback returned,
      value= ${JSON.stringify(this.deviceManager)}`);
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      logger.error(`[DeviceManager.RemoteDeviceModel] createDeviceManager throw error,
      error=${error} message=${error.message}`);
    }
    logger.info('[DeviceManager.RemoteDeviceModel] distributedDeviceManager.createDeviceManager end');
  }
```



5. Register a callback for discovering devices and calls the discovery API to discover peripheral devices. The discovery process lasts 2 minutes, and a maximum of 99 devices can be discovered.
   
   <!-- @[start_discovering](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

``` TypeScript
  startDeviceDiscovery(): void {
    if (typeof (this.deviceManager) == 'undefined') {
      logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
      promptAction.showToast({
        message: 'deviceManager has not initialized'
      });
      return;
    }
    let self = this;
    try {
      this.deviceManager.on('discoverSuccess', (data) => {
        if (data == null) {
          return;
        }
        logger.info('[DeviceManager.RemoteDeviceModel] deviceFound data=' + JSON.stringify(data));
        self.deviceFound(data);
      })
      this.deviceManager.on('discoverFailure', (data) => {
        logger.info('[DeviceManager.RemoteDeviceModel] discoverFail data=' + JSON.stringify(data));
      })
	// ···
      let discoverParam: Record<string, number> = {
        'discoverTargetType': 1
      };
      let filterOptions: Record<string, number> = this.getFilterOptions();
      logger.info('[DeviceManager.RemoteDeviceModel] startDeviceDiscovery filterOptions = ' + JSON.stringify(filterOptions));
      if (Object.entries(filterOptions).length == 0) {
        this.deviceManager.startDiscovering(discoverParam);
      } else {
        this.deviceManager.startDiscovering(discoverParam, filterOptions);
      }
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      logger.error('[DeviceManager.RemoteDeviceModel] startDeviceDiscovery failed err: ' + e.toString());
    }
  }
```


## Binding a Device

### Scenario

Bind an untrusted device discovered to establish a trust relationship.

### Available APIs

bindTarget(deviceId: string, bindParam: {[key:&nbsp;string]:&nbsp;Object;} , callback: AsyncCallback&lt;{deviceId: string;}>): void;

Binds a device. For details, see [bindTarget](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#bindtarget).

### How to Develop

1. Request the ohos.permission.DISTRIBUTED_DATASYNC permission for your application.

2. Discover devices nearby.
   
3. Bind an untrusted device.

   <!-- @[bind_target](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

``` TypeScript
  authenticateDevice(device: distributedDeviceManager.DeviceBasicInfo): void {
    logger.info('[DeviceManager.RemoteDeviceModel] authenticateDevice ' + JSON.stringify(device));
    if (typeof (this.deviceManager) == 'undefined') {
      logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
      promptAction.showToast({
        message: 'deviceManager has not initialized'
      });
      return;
    }

    for (let i = 0; i < this.discoverList.length; i++) {
      if (this.discoverList[i].deviceId != device.deviceId) {
        continue;
      }

      let bindParam: Record<string, number | string> = {
        'bindLevel': 3,
        'bindType': 1, // PIN authentication
        'targetPkgName': 'ohos.samples.etsdevicemanager',
        'appName': 'DeviceManager',
      };
      try {
        this.deviceManager.bindTarget(device.deviceId, bindParam, (err: BusinessError, data: Object) => {
          if (err) {
            logger.error('[DeviceManager.RemoteDeviceModel] authenticateDevice error:' + JSON.stringify(err));
            return;
          }
          logger.info('[DeviceManager.RemoteDeviceModel] authenticateDevice succeed:' + JSON.stringify(data));
        })
      } catch (err) {
        let e: BusinessError = err as BusinessError;
        logger.error('[DeviceManager.RemoteDeviceModel] authenticateDevice failed err: ' + e.toString());
      }
    }
  }
```



## Querying Device Information

### Scenario

Obtain information about all the online and trusted devices.

### Available APIs

getAvailableDeviceListSync(): Array&lt;DeviceBasicInfo&gt;;

Obtains information about all the available devices. For details, see [getAvailableDeviceListSync](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).

### How to Develop

1. Request the ohos.permission.DISTRIBUTED_DATASYNC permission for your application.

2. Discover devices nearby.
   
3. Bind an untrust device to establish a trust relationship.

4. Obtain information about all the online and trusted devices.

   <!-- @[get_available_device_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

``` TypeScript
  getTrustedDeviceList(): void {
    if (typeof (this.deviceManager) == 'undefined') {
      logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
      promptAction.showToast({
        message: 'deviceManager has not initialized'
      });
      return;
    }

    logger.info('[DeviceManager.RemoteDeviceModel] getTrustedDeviceList begin');
    try {
      this.trustedDeviceList = this.deviceManager.getAvailableDeviceListSync();
	// ···
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      logger.error('[DeviceManager.RemoteDeviceModel] getTrustedDeviceList error: ${error}' + error.toString());
      promptAction.showToast({
        message: 'getTrustedDeviceList failed'
      });
    }
  }
```



## Listening for Device Online/Offline Status

### Scenario

You can listen for the device online/offline status. The service will be notified when a device goes offline or online.

### Available APIs

on(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;): void;

Listens for device online/offline status. For details, see [on('deviceStateChange')](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#ondevicestatechange).

### How to Develop

1. Request the ohos.permission.DISTRIBUTED_DATASYNC permission for your application.

2. Import the **distributedDeviceManager** module, which provides APIs for device management.
   
   ```ts
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```

3. Import the **BusinessError** module, which provides the error codes thrown by the APIs of the **distributedDeviceManager** module.
   
   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

4. Create a **DeviceManager** instance.

   <!-- @[device_state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

``` TypeScript
  registerDeviceStateListener(): void {
    logger.info('[DeviceManager.RemoteDeviceModel] registerDeviceStateListener');
    if (typeof (this.deviceManager) == 'undefined') {
      logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
      promptAction.showToast({
        message: 'deviceManager has not initialized'
      });
      return;
    }

	// ···
    try {
      this.deviceManager.on('deviceStateChange', (data: dataType) => {
        if (data == null) {
          return;
        }
        logger.info('[DeviceManager.RemoteDeviceModel] deviceStateChange data=' + JSON.stringify(data));
        switch (data.action) {
          case distributedDeviceManager.DeviceStateChange.AVAILABLE:
            logger.info('[DeviceManager.RemoteDeviceModel] deviceStateChange ONLINE');
			// ···
            break;
          case distributedDeviceManager.DeviceStateChange.UNAVAILABLE:
            logger.info('[DeviceManager.RemoteDeviceModel] deviceStateChange OFFLINE');
			// ···
            break;
          default:
            break;
        }
      })
    } catch(err) {
      let e: BusinessError = err as BusinessError;
      logger.error('[DeviceManager.RemoteDeviceModel] deviceStateChange failed err: ' + e.toString());
    }
  }
```
