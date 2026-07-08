# Distributed Device Management Development

<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hwzhangchuang-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=9f53a9e77747af975b5a889ab884bf4bcac288aa translatedAt=2026-06-30T10:23:16.867Z pushedAt=2026-06-30T13:18:06.469Z -->

## Introduction

As users own an increasing variety of devices, distributed services extend the capabilities of the local device by enabling different devices to collaborate in complex scenarios.

Distributed device management serves as the entry point to distributed services and provides unified management of nearby trusted and untrusted devices.

It provides the following capabilities:

- **Discovery**<br/>

  Discovers and reports nearby devices. Devices must be connected to the same LAN or have Bluetooth enabled.

- **Binding**<br/>

  Before different devices can collaborate in distributed services, they must establish a trusted relationship. For nearby untrusted devices, binding establishes a trusted relationship between devices. Device management provides authentication frameworks such as PIN code, touch, scan, and proximity authentication, and supports integration with various authentication interaction APIs.

- **Query**<br/>

  Queries local device information, nearby online trusted devices, and trusted device information.

- **Listening**<br/>

  Listens for device online and offline events. When a device comes online, a trusted relationship has been established and distributed operations can be initiated. When a device goes offline, distributed services are unavailable.

### Working Principles

  As the entry point to distributed services, device management requires an app to proactively bind a discovered device and establish a trusted relationship for the intended scenario. After the service ends, the app determines whether to remove the binding. The app controls the removal of the trusted relationship between devices.

### Constraints

  To use device management capabilities, users must ensure that devices are connected to the same LAN or that Bluetooth is enabled. Otherwise, these capabilities are unavailable.

  Device information is sensitive user data. Therefore, even when devices are connected to the same LAN or Bluetooth is enabled, an app must request the data synchronization permission from the user before obtaining device location information. The system provides device management capabilities to the app only after the user grants permission.

<!--RP1-->
<!--RP1End-->

## Requesting Permissions

### Scenario

Before using system capabilities for distributed device management, an app must check whether it has obtained the user's authorization to access distributed data synchronization information. If authorization has not been granted, the app can request the required distributed data synchronization permission from the user.

**ohos.permission.DISTRIBUTED_DATASYNC**: distributed data synchronization permission

To use device management capabilities, an app must declare this permission and obtain user authorization.

### How to Develop

This guide applies to the stage model.

1. Declare the **ohos.permission.DISTRIBUTED_DATASYNC** permission in the **module.json5** file.

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

2. Import the **abilityAccessCtrl** module to obtain the capability for requesting permissions.

   ```ts
   import { abilityAccessCtrl } from '@kit.AbilityKit';
   ```

3. Call the [requestPermissionsFromUser()](../../application-dev/reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9) API to request the distributed data synchronization permission via a dynamic dialog box, as it uses the **user_grant** authorization mode.

   <!-- @[permissions_user_grant](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/pages/Index.ets) --> 

   ``` TypeScript
   let atManager = abilityAccessCtrl.createAtManager();
   atManager.requestPermissionsFromUser(context, ['ohos.permission.DISTRIBUTED_DATASYNC'])
     .then(async (data) => {
       logger.info(`data: ${JSON.stringify(data)}`);
       // ...
     })
     .catch((err: BusinessError) => {
       logger.error(`requestPermissionsFromUser error: ${JSON.stringify(err)}`);
     });
   ```

## Discovering Devices

### Scenario

You can call device discovery APIs to obtain nearby available devices.

### Available APIs

startDiscovering(discoverParam: {[key:&nbsp;string]:&nbsp;Object;} , filterOptions?: {[key:&nbsp;string]:&nbsp;Object;} ): void;

Discovers nearby devices that are connected to the same LAN or have Bluetooth enabled. For detailed information, see [startDiscovering](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#startdiscovering).

### How to Develop

1. Request the distributed data synchronization permission.

2. Import the **distributedDeviceManager** module. All device management APIs are provided through this module.

   ```ts
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```

3. Import the **BusinessError** module, which is used to obtain error codes thrown by APIs of the **distributedDeviceManager** module.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

4. Create a device management instance, which serves as the entry point for calling distributed device management methods.

   <!-- @[create_device_manager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

   ``` TypeScript
   async createDeviceManager(): Promise<void> {
     if (typeof (this.deviceManager) != 'undefined') {
       return;
     }
   
     logger.info('[DeviceManager.RemoteDeviceModel] deviceManager.createDeviceManager begin');
     try {
       let dmInstance = distributedDeviceManager.createDeviceManager('com.samples.devicemanager');
       this.deviceManager = dmInstance
       // ...
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

5. Register a callback for device discovery and call the discovery API to discover peripheral devices. Discovery lasts for two minutes and stops automatically after that. Up to 99 devices can be discovered.

   <!-- @[start_discovering](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

   ``` TypeScript
   startDeviceDiscovery(): void {
     if (typeof (this.deviceManager) == 'undefined') {
       logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
       this.showErrMsg('deviceManager has not initialized');
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
       // ...
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

6. When discovery ends or the page exits, call the API for stopping discovery to unregister the discovery listeners.

   <!-- @[stop_discovering](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) --> 

   ``` TypeScript
   stopDeviceDiscovery(): void {
     if (typeof (this.deviceManager) == 'undefined') {
       logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
       this.showErrMsg('deviceManager has not initialized');
       return;
     }
     logger.info('[DeviceManager.RemoteDeviceModel] stopDeviceDiscovery');
     try {
       this.deviceManager.stopDiscovering();
       this.deviceManager.off('discoverSuccess');
       this.deviceManager.off('discoverFailure');
     } catch (e) {
       logger.error('[DeviceManager.RemoteDeviceModel] stopDeviceDiscovery failed err: ' + e.toString());
     }
   }
   ```

## Binding a Device

### Scenario

After discovering a nearby untrusted device, you can use binding APIs to establish a trusted relationship.

### Available APIs

bindTarget(deviceId: string, bindParam: {[key:&nbsp;string]:&nbsp;Object;} , callback: AsyncCallback&lt;{deviceId: string;}>): void;

Binds a device. For details, see [bindTarget](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#bindtarget).

### How to Develop

1. Request the distributed data synchronization permission.

2. Discover nearby untrusted devices.

3. Select the ID of an untrusted device and initiate device binding.

   <!-- @[bind_target](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

   ``` TypeScript
   authenticateDevice(device: distributedDeviceManager.DeviceBasicInfo): void {
     logger.info('[DeviceManager.RemoteDeviceModel] authenticateDevice ' + JSON.stringify(device));
     if (typeof (this.deviceManager) == 'undefined') {
       logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
       this.showErrMsg('deviceManager has not initialized');
       return;
     }
   
     for (let i = 0; i < this.discoverList.length; i++) {
       if (this.discoverList[i].deviceId != device.deviceId) {
         continue;
       }
   
       let bindParam: Record<string, number | string> = {
         'bindLevel': 3,
         'bindType': 1, // PIN code authentication
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

After a device establishes a trusted relationship with nearby devices, device information query APIs can be used to obtain all online trusted devices.

### Available APIs

getAvailableDeviceListSync(): Array&lt;DeviceBasicInfo&gt;;

Queries device information. For details, see [getAvailableDeviceListSync](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).

### How to Develop

1. Request the distributed data synchronization permission.

2. Discover nearby untrusted devices.

3. Establish a trusted relationship between devices.

4. Query nearby online trusted devices.

   <!-- @[get_available_device_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

   ``` TypeScript
   getTrustedDeviceList(): void {
     if (typeof (this.deviceManager) == 'undefined') {
       logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
       this.showErrMsg('deviceManager has not initialized');
       return;
     }
   
     logger.info('[DeviceManager.RemoteDeviceModel] getTrustedDeviceList begin');
     try {
       this.trustedDeviceList = this.deviceManager.getAvailableDeviceListSync();
       // ...
     } catch (error) {
       logger.error('[DeviceManager.RemoteDeviceModel] getTrustedDeviceList error: ${error}' + error.toString());
       this.showErrMsg('getTrustedDeviceList failed');
     }
   }
   ```

## Listening for Device Online/Offline Status

### Scenario

When a nearby trusted device becomes available, the app receives an online event. When the device becomes unavailable, the app receives an offline event.

### Available APIs

on(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;): void;

Listens for device online/offline events. For details, see [on('deviceStateChange')](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#ondevicestatechange).

### How to Develop

1. Request the distributed data synchronization permission.

2. Import the **distributedDeviceManager** module. All device management APIs are provided by this module.

   ```ts
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```

3. Import the **BusinessError** module to obtain error codes thrown by APIs in the **distributedDeviceManager** module.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

4. Create a device management instance, which serves as the entry point to distributed device management APIs, and register a callback for device online and offline events.

   <!-- @[device_state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/model/RemoteDeviceModel.ets) -->

   ``` TypeScript
   registerDeviceStateListener(): void {
     logger.info('[DeviceManager.RemoteDeviceModel] registerDeviceStateListener');
     if (typeof (this.deviceManager) == 'undefined') {
       logger.error('[DeviceManager.RemoteDeviceModel] deviceManager has not initialized');
       this.showErrMsg('deviceManager has not initialized');
       return;
     }
   
     // ...
     try {
       this.deviceManager.on('deviceStateChange', (data: dataType) => {
         if (data == null) {
           return;
         }
         logger.info('[DeviceManager.RemoteDeviceModel] deviceStateChange data=' + JSON.stringify(data));
         switch (data.action) {
           case distributedDeviceManager.DeviceStateChange.AVAILABLE:
             logger.info('[DeviceManager.RemoteDeviceModel] deviceStateChange ONLINE');
             // ...
             break;
           case distributedDeviceManager.DeviceStateChange.UNAVAILABLE:
             logger.info('[DeviceManager.RemoteDeviceModel] deviceStateChange OFFLINE');
             // ...
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