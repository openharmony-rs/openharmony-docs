| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace distributedDeviceManager<br>差异内容：declare namespace distributedDeviceManager|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：distributedDeviceManager；<br>API声明：interface DeviceBasicInfo<br>差异内容：interface DeviceBasicInfo|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceBasicInfo；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceBasicInfo；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceBasicInfo；<br>API声明：deviceType: string;<br>差异内容：deviceType: string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceBasicInfo；<br>API声明：networkId?: string;<br>差异内容：networkId?: string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：distributedDeviceManager；<br>API声明：enum DeviceStateChange<br>差异内容：enum DeviceStateChange|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceStateChange；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceStateChange；<br>API声明：AVAILABLE = 1<br>差异内容：AVAILABLE = 1|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceStateChange；<br>API声明：UNAVAILABLE = 2<br>差异内容：UNAVAILABLE = 2|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：distributedDeviceManager；<br>API声明：function createDeviceManager(bundleName: string): DeviceManager;<br>差异内容：function createDeviceManager(bundleName: string): DeviceManager;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：distributedDeviceManager；<br>API声明：function releaseDeviceManager(deviceManager: DeviceManager): void;<br>差异内容：function releaseDeviceManager(deviceManager: DeviceManager): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：distributedDeviceManager；<br>API声明：interface DeviceManager<br>差异内容：interface DeviceManager|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getAvailableDeviceListSync(): Array\<DeviceBasicInfo>;<br>差异内容：getAvailableDeviceListSync(): Array\<DeviceBasicInfo>;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getAvailableDeviceList(callback: AsyncCallback\<Array\<DeviceBasicInfo>>): void;<br>差异内容：getAvailableDeviceList(callback: AsyncCallback\<Array\<DeviceBasicInfo>>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getAvailableDeviceList(): Promise\<Array\<DeviceBasicInfo>>;<br>差异内容：getAvailableDeviceList(): Promise\<Array\<DeviceBasicInfo>>;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getLocalDeviceNetworkId(): string;<br>差异内容：getLocalDeviceNetworkId(): string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getLocalDeviceName(): string;<br>差异内容：getLocalDeviceName(): string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getLocalDeviceType(): number;<br>差异内容：getLocalDeviceType(): number;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getLocalDeviceId(): string;<br>差异内容：getLocalDeviceId(): string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getDeviceName(networkId: string): string;<br>差异内容：getDeviceName(networkId: string): string;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：getDeviceType(networkId: string): number;<br>差异内容：getDeviceType(networkId: string): number;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：startDiscovering(discoverParam: {<br>            [key: string]: Object;<br>        }, filterOptions?: {<br>            [key: string]: Object;<br>        }): void;<br>差异内容：startDiscovering(discoverParam: {<br>            [key: string]: Object;<br>        }, filterOptions?: {<br>            [key: string]: Object;<br>        }): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：stopDiscovering(): void;<br>差异内容：stopDiscovering(): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：bindTarget(deviceId: string, bindParam: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<{<br>            deviceId: string;<br>        }>): void;<br>差异内容：bindTarget(deviceId: string, bindParam: {<br>            [key: string]: Object;<br>        }, callback: AsyncCallback\<{<br>            deviceId: string;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：unbindTarget(deviceId: string): void;<br>差异内容：unbindTarget(deviceId: string): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：on(type: 'deviceStateChange', callback: Callback\<{<br>            action: DeviceStateChange;<br>            device: DeviceBasicInfo;<br>        }>): void;<br>差异内容：on(type: 'deviceStateChange', callback: Callback\<{<br>            action: DeviceStateChange;<br>            device: DeviceBasicInfo;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：off(type: 'deviceStateChange', callback?: Callback\<{<br>            action: DeviceStateChange;<br>            device: DeviceBasicInfo;<br>        }>): void;<br>差异内容：off(type: 'deviceStateChange', callback?: Callback\<{<br>            action: DeviceStateChange;<br>            device: DeviceBasicInfo;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：on(type: 'discoverSuccess', callback: Callback\<{<br>            device: DeviceBasicInfo;<br>        }>): void;<br>差异内容：on(type: 'discoverSuccess', callback: Callback\<{<br>            device: DeviceBasicInfo;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：off(type: 'discoverSuccess', callback?: Callback\<{<br>            device: DeviceBasicInfo;<br>        }>): void;<br>差异内容：off(type: 'discoverSuccess', callback?: Callback\<{<br>            device: DeviceBasicInfo;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：on(type: 'deviceNameChange', callback: Callback\<{<br>            deviceName: string;<br>        }>): void;<br>差异内容：on(type: 'deviceNameChange', callback: Callback\<{<br>            deviceName: string;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：off(type: 'deviceNameChange', callback?: Callback\<{<br>            deviceName: string;<br>        }>): void;<br>差异内容：off(type: 'deviceNameChange', callback?: Callback\<{<br>            deviceName: string;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：on(type: 'discoverFailure', callback: Callback\<{<br>            reason: number;<br>        }>): void;<br>差异内容：on(type: 'discoverFailure', callback: Callback\<{<br>            reason: number;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：off(type: 'discoverFailure', callback?: Callback\<{<br>            reason: number;<br>        }>): void;<br>差异内容：off(type: 'discoverFailure', callback?: Callback\<{<br>            reason: number;<br>        }>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：on(type: 'serviceDie', callback?: Callback\<{}>): void;<br>差异内容：on(type: 'serviceDie', callback?: Callback\<{}>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：DeviceManager；<br>API声明：off(type: 'serviceDie', callback?: Callback\<{}>): void;<br>差异内容：off(type: 'serviceDie', callback?: Callback\<{}>): void;|api/@ohos.distributedDeviceManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceManager<br>差异内容：declare namespace deviceManager|api/@ohos.distributedHardware.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：interface DeviceManager<br>差异内容：interface DeviceManager|api/@ohos.distributedHardware.deviceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.distributedDeviceManager.d.ts<br>差异内容：DistributedServiceKit|api/@ohos.distributedDeviceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.distributedHardware.deviceManager.d.ts<br>差异内容：DistributedServiceKit|api/@ohos.distributedHardware.deviceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.DistributedServiceKit.d.ts<br>差异内容：DistributedServiceKit|kits/@kit.DistributedServiceKit.d.ts|
