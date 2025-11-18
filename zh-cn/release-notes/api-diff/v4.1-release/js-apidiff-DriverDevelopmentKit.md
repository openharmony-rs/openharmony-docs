| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：export type DriverExtensionContext = _DriverExtensionContext;<br>差异内容：export type DriverExtensionContext = _DriverExtensionContext;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class DriverExtensionAbility<br>差异内容：export default class DriverExtensionAbility|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：DriverExtensionAbility；<br>API声明：context: DriverExtensionContext;<br>差异内容：context: DriverExtensionContext;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：DriverExtensionAbility；<br>API声明：onInit(want: Want): void;<br>差异内容：onInit(want: Want): void;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：DriverExtensionAbility；<br>API声明：onRelease(): void;<br>差异内容：onRelease(): void;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：DriverExtensionAbility；<br>API声明：onConnect(want: Want): rpc.RemoteObject \| Promise\<rpc.RemoteObject>;<br>差异内容：onConnect(want: Want): rpc.RemoteObject \| Promise\<rpc.RemoteObject>;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：DriverExtensionAbility；<br>API声明：onDisconnect(want: Want): void \| Promise\<void>;<br>差异内容：onDisconnect(want: Want): void \| Promise\<void>;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：DriverExtensionAbility；<br>API声明：onDump(params: Array\<string>): Array\<string>;<br>差异内容：onDump(params: Array\<string>): Array\<string>;|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace deviceManager<br>差异内容：declare namespace deviceManager|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function queryDevices(busType?: number): Array\<Readonly\<Device>>;<br>差异内容：function queryDevices(busType?: number): Array\<Readonly\<Device>>;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function bindDevice(deviceId: number, onDisconnect: AsyncCallback\<number>, callback: AsyncCallback\<{<br>        deviceId: number;<br>        remote: rpc.IRemoteObject;<br>    }>): void;<br>差异内容：function bindDevice(deviceId: number, onDisconnect: AsyncCallback\<number>, callback: AsyncCallback\<{<br>        deviceId: number;<br>        remote: rpc.IRemoteObject;<br>    }>): void;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function bindDevice(deviceId: number, onDisconnect: AsyncCallback\<number>): Promise\<{<br>        deviceId: number;<br>        remote: rpc.IRemoteObject;<br>    }>;<br>差异内容：function bindDevice(deviceId: number, onDisconnect: AsyncCallback\<number>): Promise\<{<br>        deviceId: number;<br>        remote: rpc.IRemoteObject;<br>    }>;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback\<number>, callback: AsyncCallback\<RemoteDeviceDriver>): void;<br>差异内容：function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback\<number>, callback: AsyncCallback\<RemoteDeviceDriver>): void;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback\<number>): Promise\<RemoteDeviceDriver>;<br>差异内容：function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback\<number>): Promise\<RemoteDeviceDriver>;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function unbindDevice(deviceId: number, callback: AsyncCallback\<number>): void;<br>差异内容：function unbindDevice(deviceId: number, callback: AsyncCallback\<number>): void;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：function unbindDevice(deviceId: number): Promise\<number>;<br>差异内容：function unbindDevice(deviceId: number): Promise\<number>;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：export enum BusType<br>差异内容：export enum BusType|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：BusType；<br>API声明：USB = 1<br>差异内容：USB = 1|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：interface Device<br>差异内容：interface Device|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：Device；<br>API声明：busType: BusType;<br>差异内容：busType: BusType;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：Device；<br>API声明：deviceId: number;<br>差异内容：deviceId: number;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：Device；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：interface USBDevice<br>差异内容：interface USBDevice|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：vendorId: number;<br>差异内容：vendorId: number;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：USBDevice；<br>API声明：productId: number;<br>差异内容：productId: number;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：deviceManager；<br>API声明：interface RemoteDeviceDriver<br>差异内容：interface RemoteDeviceDriver|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：RemoteDeviceDriver；<br>API声明：deviceId: number;<br>差异内容：deviceId: number;|api/@ohos.driver.deviceManager.d.ts|
|新增API|NA|类名：RemoteDeviceDriver；<br>API声明：remote: rpc.IRemoteObject;<br>差异内容：remote: rpc.IRemoteObject;|api/@ohos.driver.deviceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.DriverExtensionAbility.d.ts<br>差异内容：DriverDevelopmentKit|api/@ohos.app.ability.DriverExtensionAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.driver.deviceManager.d.ts<br>差异内容：DriverDevelopmentKit|api/@ohos.driver.deviceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.DriverDevelopmentKit.d.ts<br>差异内容：DriverDevelopmentKit|kits/@kit.DriverDevelopmentKit.d.ts|
