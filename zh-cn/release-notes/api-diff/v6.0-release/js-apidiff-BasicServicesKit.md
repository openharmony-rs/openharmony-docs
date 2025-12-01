| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare namespace systemDateTime<br>差异内容：NA|类名：global；<br>API声明：declare namespace systemDateTime<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：systemDateTime；<br>API声明：function getTime(isNanoseconds?: boolean): number;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getTime(isNanoseconds?: boolean): number;<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：systemDateTime；<br>API声明：enum TimeType<br>差异内容：NA|类名：systemDateTime；<br>API声明：enum TimeType<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：TimeType；<br>API声明：STARTUP<br>差异内容：NA|类名：TimeType；<br>API声明：STARTUP<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：TimeType；<br>API声明：ACTIVE<br>差异内容：NA|类名：TimeType；<br>API声明：ACTIVE<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：systemDateTime；<br>API声明：function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：systemDateTime；<br>API声明：function getTimezone(callback: AsyncCallback\<string>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getTimezone(callback: AsyncCallback\<string>): void;<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：systemDateTime；<br>API声明：function getTimezone(): Promise\<string>;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getTimezone(): Promise\<string>;<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API跨平台权限变更|类名：systemDateTime；<br>API声明：function getTimezoneSync(): string;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getTimezoneSync(): string;<br>差异内容：crossplatform|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：FileSpec；<br>API声明：mimeType?: string;<br>差异内容：NA|类名：FileSpec；<br>API声明：mimeType?: string;<br>差异内容：18|api/@ohos.request.d.ts|
|API废弃版本变更|类名：usbManager；<br>API声明：interface USBControlParams<br>差异内容：NA|类名：usbManager；<br>API声明：interface USBControlParams<br>差异内容：18|api/@ohos.usbManager.d.ts|
|API废弃版本变更|类名：USBControlParams；<br>API声明：request: number;<br>差异内容：NA|类名：USBControlParams；<br>API声明：request: number;<br>差异内容：18|api/@ohos.usbManager.d.ts|
|API废弃版本变更|类名：USBControlParams；<br>API声明：target: USBRequestTargetType;<br>差异内容：NA|类名：USBControlParams；<br>API声明：target: USBRequestTargetType;<br>差异内容：18|api/@ohos.usbManager.d.ts|
|API废弃版本变更|类名：USBControlParams；<br>API声明：reqType: USBControlRequestType;<br>差异内容：NA|类名：USBControlParams；<br>API声明：reqType: USBControlRequestType;<br>差异内容：18|api/@ohos.usbManager.d.ts|
|API废弃版本变更|类名：USBControlParams；<br>API声明：value: number;<br>差异内容：NA|类名：USBControlParams；<br>API声明：value: number;<br>差异内容：18|api/@ohos.usbManager.d.ts|
|API废弃版本变更|类名：USBControlParams；<br>API声明：index: number;<br>差异内容：NA|类名：USBControlParams；<br>API声明：index: number;<br>差异内容：18|api/@ohos.usbManager.d.ts|
|API废弃版本变更|类名：USBControlParams；<br>API声明：data: Uint8Array;<br>差异内容：NA|类名：USBControlParams；<br>API声明：data: Uint8Array;<br>差异内容：18|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function getDevices(): Array\<Readonly\<USBDevice>>;<br>差异内容：NA|类名：usbManager；<br>API声明：function getDevices(): Array\<Readonly\<USBDevice>>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;<br>差异内容：NA|类名：usbManager；<br>API声明：function connectDevice(device: USBDevice): Readonly\<USBDevicePipe>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function hasRight(deviceName: string): boolean;<br>差异内容：NA|类名：usbManager；<br>API声明：function hasRight(deviceName: string): boolean;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function requestRight(deviceName: string): Promise\<boolean>;<br>差异内容：NA|类名：usbManager；<br>API声明：function requestRight(deviceName: string): Promise\<boolean>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function removeRight(deviceName: string): boolean;<br>差异内容：NA|类名：usbManager；<br>API声明：function removeRight(deviceName: string): boolean;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function setInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;<br>差异内容：NA|类名：usbManager；<br>API声明：function getRawDescriptor(pipe: USBDevicePipe): Uint8Array;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function getFileDescriptor(pipe: USBDevicePipe): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function getFileDescriptor(pipe: USBDevicePipe): number;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: number): Promise\<number>;<br>差异内容：NA|类名：usbManager；<br>API声明：function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: number): Promise\<number>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;<br>差异内容：NA|类名：usbManager；<br>API声明：function bulkTransfer(pipe: USBDevicePipe, endpoint: USBEndpoint, buffer: Uint8Array, timeout?: number): Promise\<number>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function closePipe(pipe: USBDevicePipe): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function closePipe(pipe: USBDevicePipe): number;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function hasAccessoryRight(accessory: USBAccessory): boolean;<br>差异内容：NA|类名：usbManager；<br>API声明：function hasAccessoryRight(accessory: USBAccessory): boolean;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function requestAccessoryRight(accessory: USBAccessory): Promise\<boolean>;<br>差异内容：NA|类名：usbManager；<br>API声明：function requestAccessoryRight(accessory: USBAccessory): Promise\<boolean>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function cancelAccessoryRight(accessory: USBAccessory): void;<br>差异内容：NA|类名：usbManager；<br>API声明：function cancelAccessoryRight(accessory: USBAccessory): void;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function getAccessoryList(): Array\<Readonly\<USBAccessory>>;<br>差异内容：NA|类名：usbManager；<br>API声明：function getAccessoryList(): Array\<Readonly\<USBAccessory>>;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function openAccessory(accessory: USBAccessory): USBAccessoryHandle;<br>差异内容：NA|类名：usbManager；<br>API声明：function openAccessory(accessory: USBAccessory): USBAccessoryHandle;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function closeAccessory(accessoryHandle: USBAccessoryHandle): void;<br>差异内容：NA|类名：usbManager；<br>API声明：function closeAccessory(accessoryHandle: USBAccessoryHandle): void;<br>差异内容：801|api/@ohos.usbManager.d.ts|
|删除错误码|类名：commonEventManager；<br>API声明：function publish(event: string, callback: AsyncCallback\<void>): void;<br>差异内容：1500004|类名：commonEventManager；<br>API声明：function publish(event: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.commonEventManager.d.ts|
|删除错误码|类名：commonEventManager；<br>API声明：function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;<br>差异内容：1500004|类名：commonEventManager；<br>API声明：function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.commonEventManager.d.ts|
|错误码变更|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：12900003,201,401|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：201,27787277,401|api/@ohos.pasteboard.d.ts|
|错误码变更|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：12900003,201|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：201,27787277|api/@ohos.pasteboard.d.ts|
|错误码变更|类名：SystemPasteboard；<br>API声明：setData(data: PasteData, callback: AsyncCallback\<void>): void;<br>差异内容：12900003,12900004,401|类名：SystemPasteboard；<br>API声明：setData(data: PasteData, callback: AsyncCallback\<void>): void;<br>差异内容：27787277,27787278,401|api/@ohos.pasteboard.d.ts|
|错误码变更|类名：SystemPasteboard；<br>API声明：setData(data: PasteData): Promise\<void>;<br>差异内容：12900003,12900004,401|类名：SystemPasteboard；<br>API声明：setData(data: PasteData): Promise\<void>;<br>差异内容：27787277,27787278,401|api/@ohos.pasteboard.d.ts|
|错误码变更|类名：SystemPasteboard；<br>API声明：getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData>;<br>差异内容：12900003,201|类名：SystemPasteboard；<br>API声明：getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData>;<br>差异内容：201,27787277|api/@ohos.pasteboard.d.ts|
|错误码变更|类名：SystemPasteboard；<br>API声明：setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise\<void>;<br>差异内容：12900003,12900004,401|类名：SystemPasteboard；<br>API声明：setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise\<void>;<br>差异内容：27787277,27787278,401|api/@ohos.pasteboard.d.ts|
|权限变更|类名：CommonEventPublishData；<br>API声明：isSticky?: boolean;<br>差异内容：NA|类名：CommonEventPublishData；<br>API声明：isSticky?: boolean;<br>差异内容：ohos.permission.COMMONEVENT_STICKY|api/commonEvent/commonEventPublishData.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace cacheDownload<br>差异内容：declare namespace cacheDownload|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：cacheDownload；<br>API声明：interface CacheDownloadOptions<br>差异内容：interface CacheDownloadOptions|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：CacheDownloadOptions；<br>API声明：headers?: Record\<string, string>;<br>差异内容：headers?: Record\<string, string>;|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：cacheDownload；<br>API声明：function download(url: string, options: CacheDownloadOptions);<br>差异内容：function download(url: string, options: CacheDownloadOptions);|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：cacheDownload；<br>API声明：function cancel(url: string);<br>差异内容：function cancel(url: string);|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：cacheDownload；<br>API声明：function setMemoryCacheSize(bytes: number);<br>差异内容：function setMemoryCacheSize(bytes: number);|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：cacheDownload；<br>API声明：function setFileCacheSize(bytes: number);<br>差异内容：function setFileCacheSize(bytes: number);|api/@ohos.request.cacheDownload.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getChangeCount(): number;<br>差异内容：getChangeCount(): number;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：FileSpec；<br>API声明：contentType?: string;<br>差异内容：contentType?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：setMaxSpeed(speed: number): Promise\<void>;<br>差异内容：setMaxSpeed(speed: number): Promise\<void>;|api/@ohos.request.d.ts|
|新增API|NA|类名：settings；<br>API声明：function openNetworkManagerSettings(context: Context): Promise\<boolean>;<br>差异内容：function openNetworkManagerSettings(context: Context): Promise\<boolean>;|api/@ohos.settings.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum UsbTransferFlags<br>差异内容：export enum UsbTransferFlags|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferFlags；<br>API声明：USB_TRANSFER_SHORT_NOT_OK = 0<br>差异内容：USB_TRANSFER_SHORT_NOT_OK = 0|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferFlags；<br>API声明：USB_TRANSFER_FREE_BUFFER = 1<br>差异内容：USB_TRANSFER_FREE_BUFFER = 1|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferFlags；<br>API声明：USB_TRANSFER_FREE_TRANSFER = 2<br>差异内容：USB_TRANSFER_FREE_TRANSFER = 2|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferFlags；<br>API声明：USB_TRANSFER_ADD_ZERO_PACKET = 3<br>差异内容：USB_TRANSFER_ADD_ZERO_PACKET = 3|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum UsbTransferStatus<br>差异内容：export enum UsbTransferStatus|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_COMPLETED = 0<br>差异内容：TRANSFER_COMPLETED = 0|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_ERROR = 1<br>差异内容：TRANSFER_ERROR = 1|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_TIMED_OUT = 2<br>差异内容：TRANSFER_TIMED_OUT = 2|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_CANCELED = 3<br>差异内容：TRANSFER_CANCELED = 3|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_STALL = 4<br>差异内容：TRANSFER_STALL = 4|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_NO_DEVICE = 5<br>差异内容：TRANSFER_NO_DEVICE = 5|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbTransferStatus；<br>API声明：TRANSFER_OVERFLOW = 6<br>差异内容：TRANSFER_OVERFLOW = 6|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：export enum UsbEndpointTransferType<br>差异内容：export enum UsbEndpointTransferType|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbEndpointTransferType；<br>API声明：TRANSFER_TYPE_ISOCHRONOUS = 0x1<br>差异内容：TRANSFER_TYPE_ISOCHRONOUS = 0x1|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbEndpointTransferType；<br>API声明：TRANSFER_TYPE_BULK = 0x2<br>差异内容：TRANSFER_TYPE_BULK = 0x2|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbEndpointTransferType；<br>API声明：TRANSFER_TYPE_INTERRUPT = 0x3<br>差异内容：TRANSFER_TYPE_INTERRUPT = 0x3|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface UsbIsoPacketDescriptor<br>差异内容：interface UsbIsoPacketDescriptor|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbIsoPacketDescriptor；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbIsoPacketDescriptor；<br>API声明：actualLength: number;<br>差异内容：actualLength: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbIsoPacketDescriptor；<br>API声明：status: UsbTransferStatus;<br>差异内容：status: UsbTransferStatus;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface SubmitTransferCallback<br>差异内容：interface SubmitTransferCallback|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：SubmitTransferCallback；<br>API声明：actualLength: number;<br>差异内容：actualLength: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：SubmitTransferCallback；<br>API声明：status: UsbTransferStatus;<br>差异内容：status: UsbTransferStatus;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：SubmitTransferCallback；<br>API声明：isoPacketDescs: Array\<Readonly\<UsbIsoPacketDescriptor>>;<br>差异内容：isoPacketDescs: Array\<Readonly\<UsbIsoPacketDescriptor>>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface UsbDataTransferParams<br>差异内容：interface UsbDataTransferParams|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：devPipe: USBDevicePipe;<br>差异内容：devPipe: USBDevicePipe;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：flags: UsbTransferFlags;<br>差异内容：flags: UsbTransferFlags;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：endpoint: number;<br>差异内容：endpoint: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：type: UsbEndpointTransferType;<br>差异内容：type: UsbEndpointTransferType;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：timeout: number;<br>差异内容：timeout: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：length: number;<br>差异内容：length: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：callback: AsyncCallback\<SubmitTransferCallback>;<br>差异内容：callback: AsyncCallback\<SubmitTransferCallback>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：userData: Uint8Array;<br>差异内容：userData: Uint8Array;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：buffer: Uint8Array;<br>差异内容：buffer: Uint8Array;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：UsbDataTransferParams；<br>API声明：isoPacketCount: number;<br>差异内容：isoPacketCount: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function usbSubmitTransfer(transfer: UsbDataTransferParams): void;<br>差异内容：function usbSubmitTransfer(transfer: UsbDataTransferParams): void;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function usbCancelTransfer(transfer: UsbDataTransferParams): void;<br>差异内容：function usbCancelTransfer(transfer: UsbDataTransferParams): void;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：DomainAccountInfo；<br>API声明：serverConfigId?: string;<br>差异内容：serverConfigId?: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：class DomainAccountManager<br>差异内容：class DomainAccountManager|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainAccountManager；<br>API声明：static updateAccountInfo(oldAccountInfo: DomainAccountInfo, newAccountInfo: DomainAccountInfo): Promise\<void>;<br>差异内容：static updateAccountInfo(oldAccountInfo: DomainAccountInfo, newAccountInfo: DomainAccountInfo): Promise\<void>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：interface DomainServerConfig<br>差异内容：interface DomainServerConfig|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfig；<br>API声明：parameters: Record\<string, Object>;<br>差异内容：parameters: Record\<string, Object>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfig；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfig；<br>API声明：domain: string;<br>差异内容：domain: string;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：osAccount；<br>API声明：class DomainServerConfigManager<br>差异内容：class DomainServerConfigManager|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfigManager；<br>API声明：static addServerConfig(parameters: Record\<string, Object>): Promise\<DomainServerConfig>;<br>差异内容：static addServerConfig(parameters: Record\<string, Object>): Promise\<DomainServerConfig>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfigManager；<br>API声明：static removeServerConfig(configId: string): Promise\<void>;<br>差异内容：static removeServerConfig(configId: string): Promise\<void>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfigManager；<br>API声明：static updateServerConfig(configId: string, parameters: Record\<string, Object>): Promise\<DomainServerConfig>;<br>差异内容：static updateServerConfig(configId: string, parameters: Record\<string, Object>): Promise\<DomainServerConfig>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfigManager；<br>API声明：static getServerConfig(configId: string): Promise\<DomainServerConfig>;<br>差异内容：static getServerConfig(configId: string): Promise\<DomainServerConfig>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfigManager；<br>API声明：static getAllServerConfigs(): Promise\<Array\<DomainServerConfig>>;<br>差异内容：static getAllServerConfigs(): Promise\<Array\<DomainServerConfig>>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：DomainServerConfigManager；<br>API声明：static getAccountServerConfig(domainAccountInfo: DomainAccountInfo): Promise\<DomainServerConfig>;<br>差异内容：static getAccountServerConfig(domainAccountInfo: DomainAccountInfo): Promise\<DomainServerConfig>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum ParallelStrategy<br>差异内容：export enum ParallelStrategy|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ParallelStrategy；<br>API声明：PARALLEL_STRATEGY_SEQUENTIAL = 0<br>差异内容：PARALLEL_STRATEGY_SEQUENTIAL = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ParallelStrategy；<br>API声明：PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION = 1<br>差异内容：PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Options；<br>API声明：parallel?: ParallelStrategy;<br>差异内容：parallel?: ParallelStrategy;|api/@ohos.zlib.d.ts|
|起始版本有变化|类名：SystemPasteboard；<br>API声明：setAppShareOptions(shareOptions: ShareOption): void;<br>差异内容：12|类名：SystemPasteboard；<br>API声明：setAppShareOptions(shareOptions: ShareOption): void;<br>差异内容：14|api/@ohos.pasteboard.d.ts|
|起始版本有变化|类名：SystemPasteboard；<br>API声明：removeAppShareOptions(): void;<br>差异内容：12|类名：SystemPasteboard；<br>API声明：removeAppShareOptions(): void;<br>差异内容：14|api/@ohos.pasteboard.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.request.cacheDownload.d.ts<br>差异内容：BasicServicesKit|api/@ohos.request.cacheDownload.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace settings<br>差异内容：NA|类名：global；<br>API声明：declare namespace settings<br>差异内容：atomicservice|api/@ohos.settings.d.ts|
