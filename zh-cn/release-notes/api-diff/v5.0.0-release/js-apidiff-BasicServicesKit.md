| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API卡片权限变更|类名：global；<br>API声明：export interface Callback<br>差异内容：NA|类名：global；<br>API声明：export interface Callback<br>差异内容：form|api/@ohos.base.d.ts|
|API卡片权限变更|类名：global；<br>API声明：export interface AsyncCallback<br>差异内容：NA|类名：global；<br>API声明：export interface AsyncCallback<br>差异内容：form|api/@ohos.base.d.ts|
|API卡片权限变更|类名：global；<br>API声明：export interface BusinessError<br>差异内容：NA|类名：global；<br>API声明：export interface BusinessError<br>差异内容：form|api/@ohos.base.d.ts|
|API卡片权限变更|类名：BusinessError；<br>API声明：code: number;<br>差异内容：NA|类名：BusinessError；<br>API声明：code: number;<br>差异内容：form|api/@ohos.base.d.ts|
|API卡片权限变更|类名：BusinessError；<br>API声明：data?: T;<br>差异内容：NA|类名：BusinessError；<br>API声明：data?: T;<br>差异内容：form|api/@ohos.base.d.ts|
|API跨平台权限变更|类名：CommonEventData；<br>API声明：data?: string;<br>差异内容：NA|类名：CommonEventData；<br>API声明：data?: string;<br>差异内容：crossplatform|api/commonEvent/commonEventData.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface CommonEventPublishData<br>差异内容：NA|类名：global；<br>API声明：export interface CommonEventPublishData<br>差异内容：crossplatform|api/commonEvent/commonEventPublishData.d.ts|
|API跨平台权限变更|类名：CommonEventPublishData；<br>API声明：data?: string;<br>差异内容：NA|类名：CommonEventPublishData；<br>API声明：data?: string;<br>差异内容：crossplatform|api/commonEvent/commonEventPublishData.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace commonEventManager<br>差异内容：NA|类名：global；<br>API声明：declare namespace commonEventManager<br>差异内容：crossplatform|api/@ohos.commonEventManager.d.ts|
|API跨平台权限变更|类名：commonEventManager；<br>API声明：function publish(event: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：commonEventManager；<br>API声明：function publish(event: string, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.commonEventManager.d.ts|
|API跨平台权限变更|类名：commonEventManager；<br>API声明：function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：commonEventManager；<br>API声明：function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.commonEventManager.d.ts|
|API跨平台权限变更|类名：commonEventManager；<br>API声明：export type CommonEventPublishData = _CommonEventPublishData;<br>差异内容：NA|类名：commonEventManager；<br>API声明：export type CommonEventPublishData = _CommonEventPublishData;<br>差异内容：crossplatform|api/@ohos.commonEventManager.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace emitter<br>差异内容：NA|类名：global；<br>API声明：declare namespace emitter<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function on(event: InnerEvent, callback: Callback\<EventData>): void;<br>差异内容：NA|类名：emitter；<br>API声明：function on(event: InnerEvent, callback: Callback\<EventData>): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function on(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：NA|类名：emitter；<br>API声明：function on(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function once(event: InnerEvent, callback: Callback\<EventData>): void;<br>差异内容：NA|类名：emitter；<br>API声明：function once(event: InnerEvent, callback: Callback\<EventData>): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function once(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：NA|类名：emitter；<br>API声明：function once(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function off(eventId: number): void;<br>差异内容：NA|类名：emitter；<br>API声明：function off(eventId: number): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function off(eventId: number, callback: Callback\<EventData>): void;<br>差异内容：NA|类名：emitter；<br>API声明：function off(eventId: number, callback: Callback\<EventData>): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function off(eventId: string): void;<br>差异内容：NA|类名：emitter；<br>API声明：function off(eventId: string): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function off(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：NA|类名：emitter；<br>API声明：function off(eventId: string, callback: Callback\<EventData>): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function emit(event: InnerEvent, data?: EventData): void;<br>差异内容：NA|类名：emitter；<br>API声明：function emit(event: InnerEvent, data?: EventData): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function emit(eventId: string, data?: EventData): void;<br>差异内容：NA|类名：emitter；<br>API声明：function emit(eventId: string, data?: EventData): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function emit(eventId: string, options: Options, data?: EventData): void;<br>差异内容：NA|类名：emitter；<br>API声明：function emit(eventId: string, options: Options, data?: EventData): void;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：function getListenerCount(eventId: number \| string): number;<br>差异内容：NA|类名：emitter；<br>API声明：function getListenerCount(eventId: number \| string): number;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：export interface EventData<br>差异内容：NA|类名：emitter；<br>API声明：export interface EventData<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：EventData；<br>API声明：data?: {<br>            [key: string]: any;<br>        };<br>差异内容：NA|类名：EventData；<br>API声明：data?: {<br>            [key: string]: any;<br>        };<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：export interface InnerEvent<br>差异内容：NA|类名：emitter；<br>API声明：export interface InnerEvent<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：InnerEvent；<br>API声明：eventId: number;<br>差异内容：NA|类名：InnerEvent；<br>API声明：eventId: number;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：InnerEvent；<br>API声明：priority?: EventPriority;<br>差异内容：NA|类名：InnerEvent；<br>API声明：priority?: EventPriority;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：export enum EventPriority<br>差异内容：NA|类名：emitter；<br>API声明：export enum EventPriority<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：EventPriority；<br>API声明：IMMEDIATE = 0<br>差异内容：NA|类名：EventPriority；<br>API声明：IMMEDIATE = 0<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：EventPriority；<br>API声明：HIGH<br>差异内容：NA|类名：EventPriority；<br>API声明：HIGH<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：EventPriority；<br>API声明：LOW<br>差异内容：NA|类名：EventPriority；<br>API声明：LOW<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：EventPriority；<br>API声明：IDLE<br>差异内容：NA|类名：EventPriority；<br>API声明：IDLE<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：emitter；<br>API声明：export interface Options<br>差异内容：NA|类名：emitter；<br>API声明：export interface Options<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：Options；<br>API声明：priority?: EventPriority;<br>差异内容：NA|类名：Options；<br>API声明：priority?: EventPriority;<br>差异内容：crossplatform|api/@ohos.events.emitter.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace request<br>差异内容：NA|类名：global；<br>API声明：declare namespace request<br>差异内容：crossplatform|api/@ohos.request.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace zlib<br>差异内容：NA|类名：global；<br>API声明：declare namespace zlib<br>差异内容：crossplatform|api/@ohos.zlib.d.ts|
|syscap变更|类名：global；<br>API声明：declare namespace request<br>差异内容：NA|类名：global；<br>API声明：declare namespace request<br>差异内容：SystemCapability.Request.FileTransferAgent|api/@ohos.request.d.ts|
|syscap变更|类名：runningLock；<br>API声明：class RunningLock<br>差异内容：NA|类名：runningLock；<br>API声明：class RunningLock<br>差异内容：SystemCapability.PowerManager.PowerManager.Core|api/@ohos.runningLock.d.ts|
|syscap变更|类名：global；<br>API声明：export interface GetDeviceOptions<br>差异内容：NA|类名：global；<br>API声明：export interface GetDeviceOptions<br>差异内容：SystemCapability.Startup.SystemInfo.Lite|api/@system.device.d.ts|
|API废弃版本变更|类名：ShareOption；<br>API声明：CROSSDEVICE<br>差异内容：NA|类名：ShareOption；<br>API声明：CROSSDEVICE<br>差异内容：12|api/@ohos.pasteboard.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getCurrentTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getCurrentTime(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getCurrentTime(callback: AsyncCallback\<number>): void;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getCurrentTime(isNano?: boolean): Promise\<number>;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getCurrentTime(isNano?: boolean): Promise\<number>;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getRealActiveTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getRealActiveTime(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getRealActiveTime(callback: AsyncCallback\<number>): void;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getRealActiveTime(isNano?: boolean): Promise\<number>;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getRealActiveTime(isNano?: boolean): Promise\<number>;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getRealTime(isNano: boolean, callback: AsyncCallback\<number>): void;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getRealTime(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getRealTime(callback: AsyncCallback\<number>): void;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：systemDateTime；<br>API声明：function getRealTime(isNano?: boolean): Promise\<number>;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getRealTime(isNano?: boolean): Promise\<number>;<br>差异内容：12|api/@ohos.systemDateTime.d.ts|
|API废弃版本变更|类名：usbManager；<br>API声明：function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;<br>差异内容：NA|类名：usbManager；<br>API声明：function controlTransfer(pipe: USBDevicePipe, controlparam: USBControlParams, timeout?: number): Promise\<number>;<br>差异内容：12|api/@ohos.usbManager.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：getCode(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：getCode(callback: AsyncCallback\<number>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：setCode(code: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：setCode(code: number, callback: AsyncCallback\<void>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：setCode(code: number): Promise\<void>;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：setCode(code: number): Promise\<void>;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：getData(callback: AsyncCallback\<string>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：getData(callback: AsyncCallback\<string>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：setData(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：setData(data: string, callback: AsyncCallback\<void>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：setData(data: string): Promise\<void>;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：setData(data: string): Promise\<void>;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：setCodeAndData(code: number, data: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：setCodeAndData(code: number, data: string, callback: AsyncCallback\<void>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：setCodeAndData(code: number, data: string): Promise\<void>;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：setCodeAndData(code: number, data: string): Promise\<void>;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：isOrderedCommonEvent(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：isOrderedCommonEvent(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：isStickyCommonEvent(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：isStickyCommonEvent(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：abortCommonEvent(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：abortCommonEvent(callback: AsyncCallback\<void>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：clearAbortCommonEvent(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：clearAbortCommonEvent(callback: AsyncCallback\<void>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：getAbortCommonEvent(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：getAbortCommonEvent(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：getSubscribeInfo(callback: AsyncCallback\<CommonEventSubscribeInfo>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：getSubscribeInfo(callback: AsyncCallback\<CommonEventSubscribeInfo>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：CommonEventSubscriber；<br>API声明：finishCommonEvent(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CommonEventSubscriber；<br>API声明：finishCommonEvent(callback: AsyncCallback\<void>): void;<br>差异内容：401|api/commonEvent/commonEventSubscriber.d.ts|
|新增错误码|类名：PasteDataRecord；<br>API声明：convertToText(callback: AsyncCallback\<string>): void;<br>差异内容：NA|类名：PasteDataRecord；<br>API声明：convertToText(callback: AsyncCallback\<string>): void;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：PasteData；<br>API声明：getRecordAt(index: number): PasteDataRecord;<br>差异内容：NA|类名：PasteData；<br>API声明：getRecordAt(index: number): PasteDataRecord;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：PasteData；<br>API声明：hasMimeType(mimeType: string): boolean;<br>差异内容：NA|类名：PasteData；<br>API声明：hasMimeType(mimeType: string): boolean;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：PasteData；<br>API声明：removeRecordAt(index: number): boolean;<br>差异内容：NA|类名：PasteData；<br>API声明：removeRecordAt(index: number): boolean;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：clear(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：clear(callback: AsyncCallback\<void>): void;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：getPasteData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getPasteData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：201|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：201|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：getDataSync(): PasteData;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getDataSync(): PasteData;<br>差异内容：201|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：hasPasteData(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：hasPasteData(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：SystemPasteboard；<br>API声明：setPasteData(data: PasteData, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：setPasteData(data: PasteData, callback: AsyncCallback\<void>): void;<br>差异内容：401|api/@ohos.pasteboard.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：on(type: 'block', callback: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：on(type: 'block', callback: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：on(type: 'succeed', callback: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：on(type: 'succeed', callback: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：on(type: 'fail', callback: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：on(type: 'fail', callback: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：on(type: 'cancel', callback: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：on(type: 'cancel', callback: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：off(type: 'block', callback?: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：off(type: 'block', callback?: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：off(type: 'succeed', callback?: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：off(type: 'succeed', callback?: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：off(type: 'fail', callback?: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：off(type: 'fail', callback?: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintTask；<br>API声明：off(type: 'cancel', callback?: Callback\<void>): void;<br>差异内容：NA|类名：PrintTask；<br>API声明：off(type: 'cancel', callback?: Callback\<void>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintDocumentAdapter；<br>API声明：onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number, writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void;<br>差异内容：NA|类名：PrintDocumentAdapter；<br>API声明：onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number, writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：PrintDocumentAdapter；<br>API声明：onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void;<br>差异内容：NA|类名：PrintDocumentAdapter；<br>API声明：onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：print；<br>API声明：function print(files: Array\<string>, callback: AsyncCallback\<PrintTask>): void;<br>差异内容：NA|类名：print；<br>API声明：function print(files: Array\<string>, callback: AsyncCallback\<PrintTask>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：print；<br>API声明：function print(files: Array\<string>): Promise\<PrintTask>;<br>差异内容：NA|类名：print；<br>API声明：function print(files: Array\<string>): Promise\<PrintTask>;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：print；<br>API声明：function print(files: Array\<string>, context: Context, callback: AsyncCallback\<PrintTask>): void;<br>差异内容：NA|类名：print；<br>API声明：function print(files: Array\<string>, context: Context, callback: AsyncCallback\<PrintTask>): void;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：print；<br>API声明：function print(files: Array\<string>, context: Context): Promise\<PrintTask>;<br>差异内容：NA|类名：print；<br>API声明：function print(files: Array\<string>, context: Context): Promise\<PrintTask>;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：print；<br>API声明：function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes, context: Context): Promise\<PrintTask>;<br>差异内容：NA|类名：print；<br>API声明：function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes, context: Context): Promise\<PrintTask>;<br>差异内容：401|api/@ohos.print.d.ts|
|新增错误码|类名：request；<br>API声明：function download(config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;<br>差异内容：NA|类名：request；<br>API声明：function download(config: DownloadConfig, callback: AsyncCallback\<DownloadTask>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：request；<br>API声明：function download(config: DownloadConfig): Promise\<DownloadTask>;<br>差异内容：NA|类名：request；<br>API声明：function download(config: DownloadConfig): Promise\<DownloadTask>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：request；<br>API声明：function upload(config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;<br>差异内容：NA|类名：request；<br>API声明：function upload(config: UploadConfig, callback: AsyncCallback\<UploadTask>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：request；<br>API声明：function upload(config: UploadConfig): Promise\<UploadTask>;<br>差异内容：NA|类名：request；<br>API声明：function upload(config: UploadConfig): Promise\<UploadTask>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：on(type: 'fail', callback: (err: number) => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：on(type: 'fail', callback: (err: number) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：off(type: 'fail', callback?: (err: number) => void): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：off(type: 'fail', callback?: (err: number) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：remove(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：remove(callback: AsyncCallback\<boolean>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：remove(): Promise\<boolean>;<br>差异内容：NA|类名：DownloadTask；<br>API声明：remove(): Promise\<boolean>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：pause(callback: AsyncCallback\<void>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：pause(): Promise\<void>;<br>差异内容：NA|类名：DownloadTask；<br>API声明：pause(): Promise\<void>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：resume(callback: AsyncCallback\<void>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：resume(): Promise\<void>;<br>差异内容：NA|类名：DownloadTask；<br>API声明：resume(): Promise\<void>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：query(callback: AsyncCallback\<DownloadInfo>): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：query(callback: AsyncCallback\<DownloadInfo>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：query(): Promise\<DownloadInfo>;<br>差异内容：NA|类名：DownloadTask；<br>API声明：query(): Promise\<DownloadInfo>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：queryMimeType(callback: AsyncCallback\<string>): void;<br>差异内容：NA|类名：DownloadTask；<br>API声明：queryMimeType(callback: AsyncCallback\<string>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：DownloadTask；<br>API声明：queryMimeType(): Promise\<string>;<br>差异内容：NA|类名：DownloadTask；<br>API声明：queryMimeType(): Promise\<string>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：on(type: 'headerReceive', callback: (header: object) => void): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：on(type: 'headerReceive', callback: (header: object) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：off(type: 'headerReceive', callback?: (header: object) => void): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：off(type: 'headerReceive', callback?: (header: object) => void): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：401|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：remove(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：UploadTask；<br>API声明：remove(callback: AsyncCallback\<boolean>): void;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：UploadTask；<br>API声明：remove(): Promise\<boolean>;<br>差异内容：NA|类名：UploadTask；<br>API声明：remove(): Promise\<boolean>;<br>差异内容：201|api/@ohos.request.d.ts|
|新增错误码|类名：RunningLock；<br>API声明：hold(timeout: number): void;<br>差异内容：NA|类名：RunningLock；<br>API声明：hold(timeout: number): void;<br>差异内容：201|api/@ohos.runningLock.d.ts|
|新增错误码|类名：RunningLock；<br>API声明：unhold(): void;<br>差异内容：NA|类名：RunningLock；<br>API声明：unhold(): void;<br>差异内容：201|api/@ohos.runningLock.d.ts|
|新增错误码|类名：runningLock；<br>API声明：function create(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;<br>差异内容：NA|类名：runningLock；<br>API声明：function create(name: string, type: RunningLockType, callback: AsyncCallback\<RunningLock>): void;<br>差异内容：201|api/@ohos.runningLock.d.ts|
|新增错误码|类名：runningLock；<br>API声明：function create(name: string, type: RunningLockType): Promise\<RunningLock>;<br>差异内容：NA|类名：runningLock；<br>API声明：function create(name: string, type: RunningLockType): Promise\<RunningLock>;<br>差异内容：201|api/@ohos.runningLock.d.ts|
|新增错误码|类名：settings；<br>API声明：function setValue(context: Context, name: string, value: string, domainName: string): Promise\<boolean>;<br>差异内容：NA|类名：settings；<br>API声明：function setValue(context: Context, name: string, value: string, domainName: string): Promise\<boolean>;<br>差异内容：201|api/@ohos.settings.d.ts|
|新增错误码|类名：settings；<br>API声明：function setValueSync(context: Context, name: string, value: string, domainName: string): boolean;<br>差异内容：NA|类名：settings；<br>API声明：function setValueSync(context: Context, name: string, value: string, domainName: string): boolean;<br>差异内容：201|api/@ohos.settings.d.ts|
|新增错误码|类名：systemDateTime；<br>API声明：function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;<br>差异内容：NA|类名：systemDateTime；<br>API声明：function getUptime(timeType: TimeType, isNanoseconds?: boolean): number;<br>差异内容：401|api/@ohos.systemDateTime.d.ts|
|新增错误码|类名：usbManager；<br>API声明：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：NA|类名：usbManager；<br>API声明：function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number;<br>差异内容：401|api/@ohos.usbManager.d.ts|
|删除错误码|类名：AppAccountManager；<br>API声明：getAllAccounts(): Promise\<Array\<AppAccountInfo>>;<br>差异内容：401|类名：AppAccountManager；<br>API声明：getAllAccounts(): Promise\<Array\<AppAccountInfo>>;<br>差异内容：NA|api/@ohos.account.appAccount.d.ts|
|删除错误码|类名：DistributedAccountAbility；<br>API声明：getOsAccountDistributedInfo(): Promise\<DistributedInfo>;<br>差异内容：401|类名：DistributedAccountAbility；<br>API声明：getOsAccountDistributedInfo(): Promise\<DistributedInfo>;<br>差异内容：NA|api/@ohos.account.distributedAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：checkMultiOsAccountEnabled(): Promise\<boolean>;<br>差异内容：401|类名：AccountManager；<br>API声明：checkMultiOsAccountEnabled(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：checkOsAccountTestable(): Promise\<boolean>;<br>差异内容：401|类名：AccountManager；<br>API声明：checkOsAccountTestable(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：getOsAccountCount(): Promise\<number>;<br>差异内容：401|类名：AccountManager；<br>API声明：getOsAccountCount(): Promise\<number>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：getOsAccountLocalId(): Promise\<number>;<br>差异内容：401|类名：AccountManager；<br>API声明：getOsAccountLocalId(): Promise\<number>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：getActivatedOsAccountLocalIds(): Promise\<Array\<number>>;<br>差异内容：401|类名：AccountManager；<br>API声明：getActivatedOsAccountLocalIds(): Promise\<Array\<number>>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：getCurrentOsAccount(): Promise\<OsAccountInfo>;<br>差异内容：401|类名：AccountManager；<br>API声明：getCurrentOsAccount(): Promise\<OsAccountInfo>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：getOsAccountType(): Promise\<OsAccountType>;<br>差异内容：401|类名：AccountManager；<br>API声明：getOsAccountType(): Promise\<OsAccountType>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：AccountManager；<br>API声明：queryDistributedVirtualDeviceId(): Promise\<string>;<br>差异内容：401|类名：AccountManager；<br>API声明：queryDistributedVirtualDeviceId(): Promise\<string>;<br>差异内容：NA|api/@ohos.account.osAccount.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：delete(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|类名：DownloadTask；<br>API声明：delete(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：delete(): Promise\<boolean>;<br>差异内容：401|类名：DownloadTask；<br>API声明：delete(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：suspend(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|类名：DownloadTask；<br>API声明：suspend(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：suspend(): Promise\<boolean>;<br>差异内容：401|类名：DownloadTask；<br>API声明：suspend(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：restore(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|类名：DownloadTask；<br>API声明：restore(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：restore(): Promise\<boolean>;<br>差异内容：401|类名：DownloadTask；<br>API声明：restore(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：getTaskInfo(callback: AsyncCallback\<DownloadInfo>): void;<br>差异内容：401|类名：DownloadTask；<br>API声明：getTaskInfo(callback: AsyncCallback\<DownloadInfo>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：getTaskInfo(): Promise\<DownloadInfo>;<br>差异内容：401|类名：DownloadTask；<br>API声明：getTaskInfo(): Promise\<DownloadInfo>;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：getTaskMimeType(callback: AsyncCallback\<string>): void;<br>差异内容：401|类名：DownloadTask；<br>API声明：getTaskMimeType(callback: AsyncCallback\<string>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：DownloadTask；<br>API声明：getTaskMimeType(): Promise\<string>;<br>差异内容：401|类名：DownloadTask；<br>API声明：getTaskMimeType(): Promise\<string>;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：UploadTask；<br>API声明：delete(callback: AsyncCallback\<boolean>): void;<br>差异内容：401|类名：UploadTask；<br>API声明：delete(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：UploadTask；<br>API声明：delete(): Promise\<boolean>;<br>差异内容：401|类名：UploadTask；<br>API声明：delete(): Promise\<boolean>;<br>差异内容：NA|api/@ohos.request.d.ts|
|删除错误码|类名：systemDateTime；<br>API声明：function getTimezone(callback: AsyncCallback\<string>): void;<br>差异内容：401|类名：systemDateTime；<br>API声明：function getTimezone(callback: AsyncCallback\<string>): void;<br>差异内容：NA|api/@ohos.systemDateTime.d.ts|
|删除错误码|类名：systemDateTime；<br>API声明：function getTimezone(): Promise\<string>;<br>差异内容：401|类名：systemDateTime；<br>API声明：function getTimezone(): Promise\<string>;<br>差异内容：NA|api/@ohos.systemDateTime.d.ts|
|权限变更|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getData(callback: AsyncCallback\<PasteData>): void;<br>差异内容：ohos.permission.READ_PASTEBOARD|api/@ohos.pasteboard.d.ts|
|权限变更|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getData(): Promise\<PasteData>;<br>差异内容：ohos.permission.READ_PASTEBOARD|api/@ohos.pasteboard.d.ts|
|权限变更|类名：SystemPasteboard；<br>API声明：getDataSync(): PasteData;<br>差异内容：NA|类名：SystemPasteboard；<br>API声明：getDataSync(): PasteData;<br>差异内容：ohos.permission.READ_PASTEBOARD|api/@ohos.pasteboard.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_PERMISSION: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_PERMISSION: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_PARAMCHECK: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_PARAMCHECK: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_UNSUPPORTED: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_UNSUPPORTED: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_FILEIO: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_FILEIO: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_FILEPATH: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_FILEPATH: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_SERVICE: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_SERVICE: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const EXCEPTION_OTHERS: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const EXCEPTION_OTHERS: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const NETWORK_MOBILE: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const NETWORK_MOBILE: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const NETWORK_WIFI: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const NETWORK_WIFI: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_CANNOT_RESUME: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_CANNOT_RESUME: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_DEVICE_NOT_FOUND: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_DEVICE_NOT_FOUND: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_FILE_ALREADY_EXISTS: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_FILE_ALREADY_EXISTS: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_FILE_ERROR: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_FILE_ERROR: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_HTTP_DATA_ERROR: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_HTTP_DATA_ERROR: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_INSUFFICIENT_SPACE: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_INSUFFICIENT_SPACE: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_TOO_MANY_REDIRECTS: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_TOO_MANY_REDIRECTS: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_UNHANDLED_HTTP_CODE: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_UNHANDLED_HTTP_CODE: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_UNKNOWN: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_UNKNOWN: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_OFFLINE: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_OFFLINE: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const ERROR_UNSUPPORTED_NETWORK_TYPE: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const ERROR_UNSUPPORTED_NETWORK_TYPE: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const PAUSED_QUEUED_FOR_WIFI: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const PAUSED_QUEUED_FOR_WIFI: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const PAUSED_WAITING_FOR_NETWORK: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const PAUSED_WAITING_FOR_NETWORK: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const PAUSED_WAITING_TO_RETRY: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const PAUSED_WAITING_TO_RETRY: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const PAUSED_BY_USER: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const PAUSED_BY_USER: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const PAUSED_UNKNOWN: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const PAUSED_UNKNOWN: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const SESSION_SUCCESSFUL: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const SESSION_SUCCESSFUL: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const SESSION_RUNNING: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const SESSION_RUNNING: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const SESSION_PENDING: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const SESSION_PENDING: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const SESSION_PAUSED: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const SESSION_PAUSED: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：const SESSION_FAILED: number;<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：const SESSION_FAILED: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface DownloadConfig<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface DownloadConfig<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：url: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：url: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：header?: Object;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：header?: Object;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：enableMetered?: boolean;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：enableMetered?: boolean;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：enableRoaming?: boolean;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：enableRoaming?: boolean;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：description?: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：description?: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：networkType?: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：networkType?: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：filePath?: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：filePath?: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：title?: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：title?: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadConfig；<br>API声明：background?: boolean;<br>差异内容：ohos.permission.INTERNET|类名：DownloadConfig；<br>API声明：background?: boolean;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface DownloadInfo<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface DownloadInfo<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：description: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：description: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：downloadedBytes: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：downloadedBytes: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：downloadId: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：downloadId: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：failedReason: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：failedReason: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：fileName: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：fileName: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：filePath: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：filePath: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：pausedReason: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：pausedReason: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：status: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：status: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：targetURI: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：targetURI: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：downloadTitle: string;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：downloadTitle: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadInfo；<br>API声明：downloadTotalBytes: number;<br>差异内容：ohos.permission.INTERNET|类名：DownloadInfo；<br>API声明：downloadTotalBytes: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface DownloadTask<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface DownloadTask<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：on(type: 'progress', callback: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：off(type: 'progress', callback?: (receivedSize: number, totalSize: number) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：on(type: 'complete' \| 'pause' \| 'remove', callback: () => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：off(type: 'complete' \| 'pause' \| 'remove', callback?: () => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：on(type: 'fail', callback: (err: number) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：on(type: 'fail', callback: (err: number) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：DownloadTask；<br>API声明：off(type: 'fail', callback?: (err: number) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：DownloadTask；<br>API声明：off(type: 'fail', callback?: (err: number) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface File<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface File<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：File；<br>API声明：filename: string;<br>差异内容：ohos.permission.INTERNET|类名：File；<br>API声明：filename: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：File；<br>API声明：name: string;<br>差异内容：ohos.permission.INTERNET|类名：File；<br>API声明：name: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：File；<br>API声明：uri: string;<br>差异内容：ohos.permission.INTERNET|类名：File；<br>API声明：uri: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：File；<br>API声明：type: string;<br>差异内容：ohos.permission.INTERNET|类名：File；<br>API声明：type: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface RequestData<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface RequestData<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：RequestData；<br>API声明：name: string;<br>差异内容：ohos.permission.INTERNET|类名：RequestData；<br>API声明：name: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：RequestData；<br>API声明：value: string;<br>差异内容：ohos.permission.INTERNET|类名：RequestData；<br>API声明：value: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface UploadConfig<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface UploadConfig<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadConfig；<br>API声明：url: string;<br>差异内容：ohos.permission.INTERNET|类名：UploadConfig；<br>API声明：url: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadConfig；<br>API声明：header: Object;<br>差异内容：ohos.permission.INTERNET|类名：UploadConfig；<br>API声明：header: Object;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadConfig；<br>API声明：method: string;<br>差异内容：ohos.permission.INTERNET|类名：UploadConfig；<br>API声明：method: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadConfig；<br>API声明：files: Array\<File>;<br>差异内容：ohos.permission.INTERNET|类名：UploadConfig；<br>API声明：files: Array\<File>;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadConfig；<br>API声明：data: Array\<RequestData>;<br>差异内容：ohos.permission.INTERNET|类名：UploadConfig；<br>API声明：data: Array\<RequestData>;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface TaskState<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface TaskState<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：TaskState；<br>API声明：path: string;<br>差异内容：ohos.permission.INTERNET|类名：TaskState；<br>API声明：path: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：TaskState；<br>API声明：responseCode: number;<br>差异内容：ohos.permission.INTERNET|类名：TaskState；<br>API声明：responseCode: number;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：TaskState；<br>API声明：message: string;<br>差异内容：ohos.permission.INTERNET|类名：TaskState；<br>API声明：message: string;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：request；<br>API声明：interface UploadTask<br>差异内容：ohos.permission.INTERNET|类名：request；<br>API声明：interface UploadTask<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：on(type: 'progress', callback: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：off(type: 'progress', callback?: (uploadedSize: number, totalSize: number) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：on(type: 'headerReceive', callback: (header: object) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：on(type: 'headerReceive', callback: (header: object) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：off(type: 'headerReceive', callback?: (header: object) => void): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：off(type: 'headerReceive', callback?: (header: object) => void): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：on(type: 'complete' \| 'fail', callback: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|权限变更|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：ohos.permission.INTERNET|类名：UploadTask；<br>API声明：off(type: 'complete' \| 'fail', callback?: Callback\<Array\<TaskState>>): void;<br>差异内容：NA|api/@ohos.request.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace customConfig<br>差异内容：declare namespace customConfig|api/@ohos.customization.customConfig.d.ts|
|新增API|NA|类名：customConfig；<br>API声明：function getChannelId(): string;<br>差异内容：function getChannelId(): string;|api/@ohos.customization.customConfig.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace systemLoad<br>差异内容：declare namespace systemLoad|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：systemLoad；<br>API声明：export enum SystemLoadLevel<br>差异内容：export enum SystemLoadLevel|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：LOW = 0<br>差异内容：LOW = 0|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：NORMAL = 1<br>差异内容：NORMAL = 1|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：MEDIUM = 2<br>差异内容：MEDIUM = 2|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：HIGH = 3<br>差异内容：HIGH = 3|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：OVERHEATED = 4<br>差异内容：OVERHEATED = 4|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：WARNING = 5<br>差异内容：WARNING = 5|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：EMERGENCY = 6<br>差异内容：EMERGENCY = 6|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：SystemLoadLevel；<br>API声明：ESCAPE = 7<br>差异内容：ESCAPE = 7|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：systemLoad；<br>API声明：function on(type: 'systemLoadChange', callback: Callback\<SystemLoadLevel>): void;<br>差异内容：function on(type: 'systemLoadChange', callback: Callback\<SystemLoadLevel>): void;|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：systemLoad；<br>API声明：function off(type: 'systemLoadChange', callback?: Callback\<SystemLoadLevel>): void;<br>差异内容：function off(type: 'systemLoadChange', callback?: Callback\<SystemLoadLevel>): void;|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：systemLoad；<br>API声明：function getLevel(): Promise\<SystemLoadLevel>;<br>差异内容：function getLevel(): Promise\<SystemLoadLevel>;|api/@ohos.resourceschedule.systemload.d.ts|
|新增API|NA|类名：AccountManager；<br>API声明：getOsAccountName(): Promise\<string>;<br>差异内容：getOsAccountName(): Promise\<string>;|api/@ohos.account.osAccount.d.ts|
|新增API|NA|类名：batteryInfo；<br>API声明：const nowCurrent: number;<br>差异内容：const nowCurrent: number;|api/@ohos.batteryInfo.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_ENTER_FORCE_SLEEP = 'usual.event.ENTER_FORCE_SLEEP'<br>差异内容：COMMON_EVENT_ENTER_FORCE_SLEEP = 'usual.event.ENTER_FORCE_SLEEP'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_EXIT_FORCE_SLEEP = 'usual.event.EXIT_FORCE_SLEEP'<br>差异内容：COMMON_EVENT_EXIT_FORCE_SLEEP = 'usual.event.EXIT_FORCE_SLEEP'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_MINORSMODE_ON = 'usual.event.MINORSMODE_ON'<br>差异内容：COMMON_EVENT_MINORSMODE_ON = 'usual.event.MINORSMODE_ON'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_MINORSMODE_OFF = 'usual.event.MINORSMODE_OFF'<br>差异内容：COMMON_EVENT_MINORSMODE_OFF = 'usual.event.MINORSMODE_OFF'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：Support；<br>API声明：COMMON_EVENT_DATA_SHARE_READY = 'usual.event.DATA_SHARE_READY'<br>差异内容：COMMON_EVENT_DATA_SHARE_READY = 'usual.event.DATA_SHARE_READY'|api/@ohos.commonEventManager.d.ts|
|新增API|NA|类名：emitter；<br>API声明：export interface GenericEventData<br>差异内容：export interface GenericEventData|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：GenericEventData；<br>API声明：data?: T;<br>差异内容：data?: T;|api/@ohos.events.emitter.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：pasteStart(): void;<br>差异内容：pasteStart(): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteData；<br>API声明：pasteComplete(): void;<br>差异内容：pasteComplete(): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData>;<br>差异内容：getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getUnifiedDataSync(): unifiedDataChannel.UnifiedData;<br>差异内容：getUnifiedDataSync(): unifiedDataChannel.UnifiedData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise\<void>;<br>差异内容：setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise\<void>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setUnifiedDataSync(data: unifiedDataChannel.UnifiedData): void;<br>差异内容：setUnifiedDataSync(data: unifiedDataChannel.UnifiedData): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：Config；<br>API声明：proxy?: string;<br>差异内容：proxy?: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：PARAM = 0x30<br>差异内容：PARAM = 0x30|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：DNS = 0x50<br>差异内容：DNS = 0x50|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：TCP = 0x60<br>差异内容：TCP = 0x60|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：SSL = 0x70<br>差异内容：SSL = 0x70|api/@ohos.request.d.ts|
|新增API|NA|类名：Faults；<br>API声明：REDIRECT = 0x80<br>差异内容：REDIRECT = 0x80|api/@ohos.request.d.ts|
|新增API|NA|类名：agent；<br>API声明：interface HttpResponse<br>差异内容：interface HttpResponse|api/@ohos.request.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：readonly version: string;<br>差异内容：readonly version: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：readonly statusCode: number;<br>差异内容：readonly statusCode: number;|api/@ohos.request.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：readonly reason: string;<br>差异内容：readonly reason: string;|api/@ohos.request.d.ts|
|新增API|NA|类名：HttpResponse；<br>API声明：readonly headers: Map\<string, Array\<string>>;<br>差异内容：readonly headers: Map\<string, Array\<string>>;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：on(event: 'response', callback: Callback\<HttpResponse>): void;<br>差异内容：on(event: 'response', callback: Callback\<HttpResponse>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：Task；<br>API声明：off(event: 'response', callback?: Callback\<HttpResponse>): void;<br>差异内容：off(event: 'response', callback?: Callback\<HttpResponse>): void;|api/@ohos.request.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: number): Promise\<number>;<br>差异内容：function usbControlTransfer(pipe: USBDevicePipe, requestparam: USBDeviceRequestParams, timeout?: number): Promise\<number>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBDeviceRequestParams<br>差异内容：interface USBDeviceRequestParams|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDeviceRequestParams；<br>API声明：bmRequestType: number;<br>差异内容：bmRequestType: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDeviceRequestParams；<br>API声明：bRequest: number;<br>差异内容：bRequest: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDeviceRequestParams；<br>API声明：wValue: number;<br>差异内容：wValue: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDeviceRequestParams；<br>API声明：wIndex: number;<br>差异内容：wIndex: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDeviceRequestParams；<br>API声明：wLength: number;<br>差异内容：wLength: number;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBDeviceRequestParams；<br>API声明：data: Uint8Array;<br>差异内容：data: Uint8Array;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum CompressFlushMode<br>差异内容：export enum CompressFlushMode|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：NO_FLUSH = 0<br>差异内容：NO_FLUSH = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：PARTIAL_FLUSH = 1<br>差异内容：PARTIAL_FLUSH = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：SYNC_FLUSH = 2<br>差异内容：SYNC_FLUSH = 2|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：FULL_FLUSH = 3<br>差异内容：FULL_FLUSH = 3|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：FINISH = 4<br>差异内容：FINISH = 4|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：BLOCK = 5<br>差异内容：BLOCK = 5|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressFlushMode；<br>API声明：TREES = 6<br>差异内容：TREES = 6|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum ReturnStatus<br>差异内容：export enum ReturnStatus|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ReturnStatus；<br>API声明：OK = 0<br>差异内容：OK = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ReturnStatus；<br>API声明：STREAM_END = 1<br>差异内容：STREAM_END = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ReturnStatus；<br>API声明：NEED_DICT = 2<br>差异内容：NEED_DICT = 2|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum CompressMethod<br>差异内容：export enum CompressMethod|api/@ohos.zlib.d.ts|
|新增API|NA|类名：CompressMethod；<br>API声明：DEFLATED = 8<br>差异内容：DEFLATED = 8|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：export enum OffsetReferencePoint<br>差异内容：export enum OffsetReferencePoint|api/@ohos.zlib.d.ts|
|新增API|NA|类名：OffsetReferencePoint；<br>API声明：SEEK_SET = 0<br>差异内容：SEEK_SET = 0|api/@ohos.zlib.d.ts|
|新增API|NA|类名：OffsetReferencePoint；<br>API声明：SEEK_CUR = 1<br>差异内容：SEEK_CUR = 1|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface ZStream<br>差异内容：interface ZStream|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：nextIn?: ArrayBuffer;<br>差异内容：nextIn?: ArrayBuffer;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：availableIn?: number;<br>差异内容：availableIn?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：totalIn?: number;<br>差异内容：totalIn?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：nextOut?: ArrayBuffer;<br>差异内容：nextOut?: ArrayBuffer;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：availableOut?: number;<br>差异内容：availableOut?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：totalOut?: number;<br>差异内容：totalOut?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：dataType?: number;<br>差异内容：dataType?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZStream；<br>API声明：adler?: number;<br>差异内容：adler?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface GzHeader<br>差异内容：interface GzHeader|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：isText?: boolean;<br>差异内容：isText?: boolean;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：os?: number;<br>差异内容：os?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：time?: number;<br>差异内容：time?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：xflags?: number;<br>差异内容：xflags?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：extra?: ArrayBuffer;<br>差异内容：extra?: ArrayBuffer;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：extraLen?: number;<br>差异内容：extraLen?: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：name?: ArrayBuffer;<br>差异内容：name?: ArrayBuffer;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：comment?: ArrayBuffer;<br>差异内容：comment?: ArrayBuffer;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：hcrc?: boolean;<br>差异内容：hcrc?: boolean;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzHeader；<br>API声明：done?: boolean;<br>差异内容：done?: boolean;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface ZipOutputInfo<br>差异内容：interface ZipOutputInfo|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZipOutputInfo；<br>API声明：status: ReturnStatus;<br>差异内容：status: ReturnStatus;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：ZipOutputInfo；<br>API声明：destLen: number;<br>差异内容：destLen: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface DictionaryOutputInfo<br>差异内容：interface DictionaryOutputInfo|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DictionaryOutputInfo；<br>API声明：status: ReturnStatus;<br>差异内容：status: ReturnStatus;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DictionaryOutputInfo；<br>API声明：dictionaryLength: number;<br>差异内容：dictionaryLength: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface DecompressionOutputInfo<br>差异内容：interface DecompressionOutputInfo|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DecompressionOutputInfo；<br>API声明：status: ReturnStatus;<br>差异内容：status: ReturnStatus;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DecompressionOutputInfo；<br>API声明：destLength: number;<br>差异内容：destLength: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DecompressionOutputInfo；<br>API声明：sourceLength: number;<br>差异内容：sourceLength: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface DeflatePendingOutputInfo<br>差异内容：interface DeflatePendingOutputInfo|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DeflatePendingOutputInfo；<br>API声明：status: ReturnStatus;<br>差异内容：status: ReturnStatus;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DeflatePendingOutputInfo；<br>API声明：pending: number;<br>差异内容：pending: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：DeflatePendingOutputInfo；<br>API声明：bits: number;<br>差异内容：bits: number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface GzErrorOutputInfo<br>差异内容：interface GzErrorOutputInfo|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzErrorOutputInfo；<br>API声明：status: ReturnStatus;<br>差异内容：status: ReturnStatus;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GzErrorOutputInfo；<br>API声明：statusMsg: string;<br>差异内容：statusMsg: string;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：type InflateBackInputCallback = (inDesc: object) => ArrayBuffer;<br>差异内容：type InflateBackInputCallback = (inDesc: object) => ArrayBuffer;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: number) => number;<br>差异内容：type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: number) => number;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function compressFiles(inFiles: Array\<string>, outFile: string, options: Options): Promise\<void>;<br>差异内容：function compressFiles(inFiles: Array\<string>, outFile: string, options: Options): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function getOriginalSize(compressedFile: string): Promise\<number>;<br>差异内容：function getOriginalSize(compressedFile: string): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function createChecksum(): Promise\<Checksum>;<br>差异内容：function createChecksum(): Promise\<Checksum>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function createChecksumSync(): Checksum;<br>差异内容：function createChecksumSync(): Checksum;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function createZip(): Promise\<Zip>;<br>差异内容：function createZip(): Promise\<Zip>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function createZipSync(): Zip;<br>差异内容：function createZipSync(): Zip;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function createGZip(): Promise\<GZip>;<br>差异内容：function createGZip(): Promise\<GZip>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：function createGZipSync(): GZip;<br>差异内容：function createGZipSync(): GZip;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface Checksum<br>差异内容：interface Checksum|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：adler32(adler: number, buf: ArrayBuffer): Promise\<number>;<br>差异内容：adler32(adler: number, buf: ArrayBuffer): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：adler32Combine(adler1: number, adler2: number, len2: number): Promise\<number>;<br>差异内容：adler32Combine(adler1: number, adler2: number, len2: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：crc32(crc: number, buf: ArrayBuffer): Promise\<number>;<br>差异内容：crc32(crc: number, buf: ArrayBuffer): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：crc32Combine(crc1: number, crc2: number, len2: number): Promise\<number>;<br>差异内容：crc32Combine(crc1: number, crc2: number, len2: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：crc64(crc: number, buf: ArrayBuffer): Promise\<number>;<br>差异内容：crc64(crc: number, buf: ArrayBuffer): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：getCrcTable(): Promise\<Array\<number>>;<br>差异内容：getCrcTable(): Promise\<Array\<number>>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Checksum；<br>API声明：getCrc64Table(): Promise\<Array\<number>>;<br>差异内容：getCrc64Table(): Promise\<Array\<number>>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface Zip<br>差异内容：interface Zip|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：getZStream(): Promise\<ZStream>;<br>差异内容：getZStream(): Promise\<ZStream>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：zlibVersion(): Promise\<string>;<br>差异内容：zlibVersion(): Promise\<string>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：zlibCompileFlags(): Promise\<number>;<br>差异内容：zlibCompileFlags(): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<ZipOutputInfo>;<br>差异内容：compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<ZipOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: number): Promise\<ZipOutputInfo>;<br>差异内容：compress2(dest: ArrayBuffer, source: ArrayBuffer, level: CompressLevel, sourceLen?: number): Promise\<ZipOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：compressBound(sourceLen: number): Promise\<number>;<br>差异内容：compressBound(sourceLen: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：uncompress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<ZipOutputInfo>;<br>差异内容：uncompress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<ZipOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<DecompressionOutputInfo>;<br>差异内容：uncompress2(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise\<DecompressionOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateValidate(strm: ZStream, check: number): Promise\<ReturnStatus>;<br>差异内容：inflateValidate(strm: ZStream, check: number): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateSyncPoint(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateSyncPoint(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateSync(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateSync(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<ReturnStatus>;<br>差异内容：inflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateResetKeep(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateResetKeep(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateReset2(strm: ZStream, windowBits: number): Promise\<ReturnStatus>;<br>差异内容：inflateReset2(strm: ZStream, windowBits: number): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateReset(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateReset(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflatePrime(strm: ZStream, bits: number, value: number): Promise\<ReturnStatus>;<br>差异内容：inflatePrime(strm: ZStream, bits: number, value: number): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateMark(strm: ZStream): Promise\<number>;<br>差异内容：inflateMark(strm: ZStream): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateInit2(strm: ZStream, windowBits: number): Promise\<ReturnStatus>;<br>差异内容：inflateInit2(strm: ZStream, windowBits: number): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateInit(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateInit(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateGetHeader(strm: ZStream, header: GzHeader): Promise\<ReturnStatus>;<br>差异内容：inflateGetHeader(strm: ZStream, header: GzHeader): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<DictionaryOutputInfo>;<br>差异内容：inflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<DictionaryOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateEnd(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateEnd(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateCopy(source: Zip): Promise\<ReturnStatus>;<br>差异内容：inflateCopy(source: Zip): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateCodesUsed(strm: ZStream): Promise\<number>;<br>差异内容：inflateCodesUsed(strm: ZStream): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateBackInit(strm: ZStream, windowBits: number, window: ArrayBuffer): Promise\<ReturnStatus>;<br>差异内容：inflateBackInit(strm: ZStream, windowBits: number, window: ArrayBuffer): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateBackEnd(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：inflateBackEnd(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise\<ReturnStatus>;<br>差异内容：inflateBack(strm: ZStream, backIn: InflateBackInputCallback, inDesc: object, backOut: InflateBackOutputCallback, outDesc: object): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：inflate(strm: ZStream, flush: CompressFlushMode): Promise\<ReturnStatus>;<br>差异内容：inflate(strm: ZStream, flush: CompressFlushMode): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateInit(strm: ZStream, level: CompressLevel): Promise\<ReturnStatus>;<br>差异内容：deflateInit(strm: ZStream, level: CompressLevel): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: number, memLevel: MemLevel, strategy: CompressStrategy): Promise\<ReturnStatus>;<br>差异内容：deflateInit2(strm: ZStream, level: CompressLevel, method: CompressMethod, windowBits: number, memLevel: MemLevel, strategy: CompressStrategy): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflate(strm: ZStream, flush: CompressFlushMode): Promise\<ReturnStatus>;<br>差异内容：deflate(strm: ZStream, flush: CompressFlushMode): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateEnd(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：deflateEnd(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateBound(strm: ZStream, sourceLength: number): Promise\<number>;<br>差异内容：deflateBound(strm: ZStream, sourceLength: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateSetHeader(strm: ZStream, head: GzHeader): Promise\<ReturnStatus>;<br>差异内容：deflateSetHeader(strm: ZStream, head: GzHeader): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateCopy(source: Zip): Promise\<ReturnStatus>;<br>差异内容：deflateCopy(source: Zip): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<ReturnStatus>;<br>差异内容：deflateSetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<DictionaryOutputInfo>;<br>差异内容：deflateGetDictionary(strm: ZStream, dictionary: ArrayBuffer): Promise\<DictionaryOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateTune(strm: ZStream, goodLength: number, maxLazy: number, niceLength: number, maxChain: number): Promise\<ReturnStatus>;<br>差异内容：deflateTune(strm: ZStream, goodLength: number, maxLazy: number, niceLength: number, maxChain: number): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateReset(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：deflateReset(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateResetKeep(strm: ZStream): Promise\<ReturnStatus>;<br>差异内容：deflateResetKeep(strm: ZStream): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflatePending(strm: ZStream): Promise\<DeflatePendingOutputInfo>;<br>差异内容：deflatePending(strm: ZStream): Promise\<DeflatePendingOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise\<ReturnStatus>;<br>差异内容：deflateParams(strm: ZStream, level: CompressLevel, strategy: CompressStrategy): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：Zip；<br>API声明：deflatePrime(strm: ZStream, bits: number, value: number): Promise\<ReturnStatus>;<br>差异内容：deflatePrime(strm: ZStream, bits: number, value: number): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：zlib；<br>API声明：interface GZip<br>差异内容：interface GZip|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzdopen(fd: number, mode: string): Promise\<void>;<br>差异内容：gzdopen(fd: number, mode: string): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzbuffer(size: number): Promise\<number>;<br>差异内容：gzbuffer(size: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzopen(path: string, mode: string): Promise\<void>;<br>差异内容：gzopen(path: string, mode: string): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzeof(): Promise\<number>;<br>差异内容：gzeof(): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzdirect(): Promise\<number>;<br>差异内容：gzdirect(): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzclose(): Promise\<ReturnStatus>;<br>差异内容：gzclose(): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzclearerr(): Promise\<void>;<br>差异内容：gzclearerr(): Promise\<void>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzerror(): Promise\<GzErrorOutputInfo>;<br>差异内容：gzerror(): Promise\<GzErrorOutputInfo>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzgetc(): Promise\<number>;<br>差异内容：gzgetc(): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzflush(flush: CompressFlushMode): Promise\<ReturnStatus>;<br>差异内容：gzflush(flush: CompressFlushMode): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzfwrite(buf: ArrayBuffer, size: number, nitems: number): Promise\<number>;<br>差异内容：gzfwrite(buf: ArrayBuffer, size: number, nitems: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzfread(buf: ArrayBuffer, size: number, nitems: number): Promise\<number>;<br>差异内容：gzfread(buf: ArrayBuffer, size: number, nitems: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzclosew(): Promise\<ReturnStatus>;<br>差异内容：gzclosew(): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzcloser(): Promise\<ReturnStatus>;<br>差异内容：gzcloser(): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzwrite(buf: ArrayBuffer, len: number): Promise\<number>;<br>差异内容：gzwrite(buf: ArrayBuffer, len: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzungetc(c: number): Promise\<number>;<br>差异内容：gzungetc(c: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gztell(): Promise\<number>;<br>差异内容：gztell(): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise\<ReturnStatus>;<br>差异内容：gzsetparams(level: CompressLevel, strategy: CompressStrategy): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzseek(offset: number, whence: OffsetReferencePoint): Promise\<number>;<br>差异内容：gzseek(offset: number, whence: OffsetReferencePoint): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzrewind(): Promise\<ReturnStatus>;<br>差异内容：gzrewind(): Promise\<ReturnStatus>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzread(buf: ArrayBuffer): Promise\<number>;<br>差异内容：gzread(buf: ArrayBuffer): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzputs(str: string): Promise\<number>;<br>差异内容：gzputs(str: string): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzputc(char: number): Promise\<number>;<br>差异内容：gzputc(char: number): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzprintf(format: string, ...args: Array\<string \| number>): Promise\<number>;<br>差异内容：gzprintf(format: string, ...args: Array\<string \| number>): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzoffset(): Promise\<number>;<br>差异内容：gzoffset(): Promise\<number>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：GZip；<br>API声明：gzgets(buf: ArrayBuffer): Promise\<string>;<br>差异内容：gzgets(buf: ArrayBuffer): Promise\<string>;|api/@ohos.zlib.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const ODID: string;<br>差异内容：const ODID: string;|api/@ohos.deviceInfo.d.ts|
|起始版本有变化|类名：runningLock；<br>API声明：class RunningLock<br>差异内容：NA|类名：runningLock；<br>API声明：class RunningLock<br>差异内容：7|api/@ohos.runningLock.d.ts|
|起始版本有变化|类名：global；<br>API声明：export interface GetDeviceOptions<br>差异内容：NA|类名：global；<br>API声明：export interface GetDeviceOptions<br>差异内容：3|api/@system.device.d.ts|
|新增kit|类名：global；<br>API声明：api\commonEvent\commonEventData.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\commonEvent\commonEventData.d.ts<br>差异内容：BasicServicesKit|api/commonEvent/commonEventData.d.ts|
|新增kit|类名：global；<br>API声明：api\commonEvent\commonEventPublishData.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\commonEvent\commonEventPublishData.d.ts<br>差异内容：BasicServicesKit|api/commonEvent/commonEventPublishData.d.ts|
|新增kit|类名：global；<br>API声明：api\commonEvent\commonEventSubscribeInfo.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\commonEvent\commonEventSubscribeInfo.d.ts<br>差异内容：BasicServicesKit|api/commonEvent/commonEventSubscribeInfo.d.ts|
|新增kit|类名：global；<br>API声明：api\commonEvent\commonEventSubscriber.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\commonEvent\commonEventSubscriber.d.ts<br>差异内容：BasicServicesKit|api/commonEvent/commonEventSubscriber.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.customization.customConfig.d.ts<br>差异内容：BasicServicesKit|api/@ohos.customization.customConfig.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceschedule.systemload.d.ts<br>差异内容：BasicServicesKit|api/@ohos.resourceschedule.systemload.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace batteryInfo<br>差异内容：NA|类名：global；<br>API声明：declare namespace batteryInfo<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：batteryInfo；<br>API声明：const batterySOC: number;<br>差异内容：NA|类名：batteryInfo；<br>API声明：const batterySOC: number;<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：batteryInfo；<br>API声明：const chargingStatus: BatteryChargeState;<br>差异内容：NA|类名：batteryInfo；<br>API声明：const chargingStatus: BatteryChargeState;<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：batteryInfo；<br>API声明：export enum BatteryChargeState<br>差异内容：NA|类名：batteryInfo；<br>API声明：export enum BatteryChargeState<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：BatteryChargeState；<br>API声明：NONE<br>差异内容：NA|类名：BatteryChargeState；<br>API声明：NONE<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：BatteryChargeState；<br>API声明：ENABLE<br>差异内容：NA|类名：BatteryChargeState；<br>API声明：ENABLE<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：BatteryChargeState；<br>API声明：DISABLE<br>差异内容：NA|类名：BatteryChargeState；<br>API声明：DISABLE<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：BatteryChargeState；<br>API声明：FULL<br>差异内容：NA|类名：BatteryChargeState；<br>API声明：FULL<br>差异内容：atomicservice|api/@ohos.batteryInfo.d.ts|
|API从不支持元服务到支持元服务|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'<br>差异内容：NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'<br>差异内容：atomicservice|api/@ohos.commonEventManager.d.ts|
|API从不支持元服务到支持元服务|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'<br>差异内容：NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'<br>差异内容：atomicservice|api/@ohos.commonEventManager.d.ts|
|API从不支持元服务到支持元服务|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'<br>差异内容：NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'<br>差异内容：atomicservice|api/@ohos.commonEventManager.d.ts|
|API从不支持元服务到支持元服务|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'<br>差异内容：NA|类名：Support；<br>API声明：COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'<br>差异内容：atomicservice|api/@ohos.commonEventManager.d.ts|
|API从不支持元服务到支持元服务|类名：emitter；<br>API声明：export interface Options<br>差异内容：NA|类名：emitter；<br>API声明：export interface Options<br>差异内容：atomicservice|api/@ohos.events.emitter.d.ts|
