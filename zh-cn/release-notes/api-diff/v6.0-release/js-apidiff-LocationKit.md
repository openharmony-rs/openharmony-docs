| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API模型切换|类名：global；<br>API声明：export default class FenceExtensionAbility<br>差异内容：NA|类名：global；<br>API声明：export default class FenceExtensionAbility<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：context: FenceExtensionContext;<br>差异内容：NA|类名：FenceExtensionAbility；<br>API声明：context: FenceExtensionContext;<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>差异内容：NA|类名：FenceExtensionAbility；<br>API声明：onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record\<string, string>): void;<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：FenceExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：NA|类名：FenceExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionAbility.d.ts|
|API模型切换|类名：global；<br>API声明：export default class FenceExtensionContext<br>差异内容：NA|类名：global；<br>API声明：export default class FenceExtensionContext<br>差异内容：stagemodelonly|api/@ohos.app.ability.FenceExtensionContext.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：3301200|类名：geoLocationManager；<br>API声明：function on(type: 'locationChange', request: LocationRequest \| ContinuousLocationRequest, callback: Callback\<Location>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：3301100,3301200|类名：geoLocationManager；<br>API声明：function off(type: 'locationChange', callback?: Callback\<Location>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：3301200|类名：geoLocationManager；<br>API声明：function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, callback: Callback\<Array\<Location>>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|删除错误码|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：3301200|类名：geoLocationManager；<br>API声明：function off(type: 'cachedGnssLocationsChange', callback?: Callback\<Array\<Location>>): void;<br>差异内容：NA|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;<br>差异内容：function on(type: 'bluetoothScanResultChange', callback: Callback\<BluetoothScanResult>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;<br>差异内容：function off(type: 'bluetoothScanResultChange', callback?: Callback\<BluetoothScanResult>): void;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export interface BluetoothScanResult<br>差异内容：export interface BluetoothScanResult|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：rssi: number;<br>差异内容：rssi: number;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：data?: ArrayBuffer;<br>差异内容：data?: ArrayBuffer;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：deviceName: string;<br>差异内容：deviceName: string;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：BluetoothScanResult；<br>API声明：connectable: boolean;<br>差异内容：connectable: boolean;|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：geoLocationManager；<br>API声明：export enum SportsType<br>差异内容：export enum SportsType|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SportsType；<br>API声明：RUNNING = 1<br>差异内容：RUNNING = 1|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SportsType；<br>API声明：WALKING<br>差异内容：WALKING|api/@ohos.geoLocationManager.d.ts|
|新增API|NA|类名：SportsType；<br>API声明：CYCLING<br>差异内容：CYCLING|api/@ohos.geoLocationManager.d.ts|
