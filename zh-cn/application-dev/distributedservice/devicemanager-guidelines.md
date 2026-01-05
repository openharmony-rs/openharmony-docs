# 分布式设备管理开发指南
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedHardware-->
<!--Owner: @hwzhangchuang-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

## 分布式设备管理简介

随着用户不同种类的终端设备数量不断增多，将不同设备作为本端设备能力的扩展，使设备之间协同合作完成各种复杂场景即为设备的分布式业务。

分布式设备管理是分布式业务入口，在分布式业务中对周边可信和非可信设备进行统一管理。

分布式设备管理提供如下四大功能：

- **发现**<br/>
  发现周围终端设备并上报。周围设备需要连接同局域网或者同时打开蓝牙，可以根据设备类型、距离、设备是否可信等进行筛选。

- **绑定**<br/>
  不同设备协同合作完成分布式业务的前提是设备间可信，对于周边发现的不可信设备，可通过绑定使彼此建立可信关系，提供PIN码、碰、扫、靠等设备认证框架，支持对接各种认证交互接口。

- **查询**<br/>
  查询功能包含：查询本机设备信息、查询周围的在线的可信设备、查询可信设备信息。
  
- **监听**<br/>
  监听设备上、下线。设备上线表示设备间已经可信，业务可以发起分布式操作；设备下线表示分布业务不可用。

### 运作机制

  设备管理作为分布式业务入口，需要应用在所使用的业务场景，向发现设备主动发起绑定建立可信关系；业务结束后由业务自主判断是否解除绑定关系，设备间可信关系的解除由业务自己控制。

### 约束与限制

  使用设备管理能力，需要用户确认不同设备已连接同一局域网或者蓝牙开关已开启，否则该能力不可用。

  设备信息属于用户敏感数据，所以即使用户已连接同一局域网或者蓝牙开关已开启，应用在获取设备位置前仍需向用户申请数据同步权限。在用户确认允许后，系统才会向应用提供设备管理能力。

## 申请分布式数据同步权限开发指导

### 场景概述

应用在使用分布式设备管理系统能力前，需要检查是否已经获取用户授权访问分布式数据同步信息。如未获得授权，可以向用户申请需要的分布式数据同步权限。

ohos.permission.DISTRIBUTED_DATASYNC：分布式数据同步权限

使用设备管理能力，必须申请权限，并且获得用户授权。

### 开发步骤

适用于Stage应用模型。

1. 在module.json5配置文件中配置分布式数据同步权限ohos.permission.DISTRIBUTED_DATASYNC。

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
2. 导入abilityAccessCtrl模块，用于获取权限申请的能力。

   ```ts
   import { abilityAccessCtrl } from '@kit.AbilityKit';
   ```

3. 分布式数据同步权限的授权方式为user_grant，因此需要调用requestPermissionsFromUser接口，以动态弹窗的方式向用户申请授权。

   <!-- @[permissions_user_grant](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/DistributedAppDev/DistributedAuthentication/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   let atManager = abilityAccessCtrl.createAtManager();
   atManager.requestPermissionsFromUser(getContext(this), ['ohos.permission.DISTRIBUTED_DATASYNC'])
     .then(async (data) => {
       logger.info(`data: ${JSON.stringify(data)}`);
       // ...
     })
     .catch((err: BusinessError) => {
       logger.error(`requestPermissionsFromUser error: ${JSON.stringify(err)}`);
   });
   ```


## 设备发现开发指导

### 场景概述

开发者可以调用DeviceManager设备发现相关接口，获取周边可用的设备。

### 接口说明

startDiscovering(discoverParam: {[key:&nbsp;string]:&nbsp;Object;} , filterOptions?: {[key:&nbsp;string]:&nbsp;Object;} ): void;

发现周边同局域网或者开启蓝牙的设备。详细信息参见：[startDiscovering](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#startdiscovering)。


### 开发步骤

1. 申请分布式数据同步权限。

2. 导入distributedDeviceManager模块，所有与设备管理相关的功能API，都是通过该模块提供的。
   
   ```ts
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```

3. 导入BusinessError模块，用于获取distributedDeviceManager模块相关接口抛出的错误码。
   
   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

4. 创建设备管理实例，设备管理实例是分布式设备管理方法的调用入口。

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

5. 注册发现设备的回调，调用发现接口发现周边设备。发现状态持续两分钟，超过两分钟，会停止发现，最大发现数量99个。
   
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


## 设备绑定开发指导

### 场景概述

开发者发现周边不可信设备后，通过绑定接口建立可信关系。

### 接口说明

bindTarget(deviceId: string, bindParam: {[key:&nbsp;string]:&nbsp;Object;} , callback: AsyncCallback&lt;{deviceId: string;}>): void;

设备绑定。详细信息参见：[bindTarget](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#bindtarget)。

### 开发步骤

1. 申请分布式数据同步权限。

2. 发现周边不可信设备。
   
3. 选择不可信设备id，发起设备绑定。

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
         'bindType': 1, // PIN码认证
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



## 设备信息查询开发指导

### 场景概述

设备与周边设备建立可信关系后，通过设备信息查询接口可以获取所有上线并且可信的设备。

### 接口说明

getAvailableDeviceListSync(): Array&lt;DeviceBasicInfo&gt;;

设备信息查询。详细信息参见：[getAvailableDeviceListSync](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync)。

### 开发步骤

1. 申请分布式数据同步权限。

2. 发现周边不可信设备。
   
3. 建立设备间的可信关系。

4. 查询周围上线并且可信的设备。

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
       // ...
     } catch (err) {
       let error: BusinessError = err as BusinessError;
       logger.error('[DeviceManager.RemoteDeviceModel] getTrustedDeviceList error: ${error}' + error.toString());
       promptAction.showToast({
         message: 'getTrustedDeviceList failed'
       });
     }
   }
   ```



## 设备上下线监听开发指导

### 场景概述

周边可信设备可用后会给业务报上线通知，当设备不可用时会给业务报下线通知。

### 接口说明

on(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;): void;

设备上下线监听。详细信息参见：[on('deviceStateChange')](../reference/apis-distributedservice-kit/js-apis-distributedDeviceManager.md#ondevicestatechange)。

### 开发步骤

1. 申请分布式数据同步权限。

2. 导入distributedDeviceManager模块，所有与设备管理相关的功能API，都是通过该模块提供的。
   
   ```ts
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```

3. 导入BusinessError模块，用于获取distributedDeviceManager模块相关接口抛出的错误码。
   
   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

4. 创建设备管理实例，设备管理实例是分布式设备管理方法的调用入口，并注册设备上下线回调。

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

