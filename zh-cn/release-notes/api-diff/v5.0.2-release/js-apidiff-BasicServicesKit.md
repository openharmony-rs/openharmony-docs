| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：AppAccountManager；<br>API声明：getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：12400001|类名：AppAccountManager；<br>API声明：getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>差异内容：NA|api/@ohos.account.appAccount.d.ts|
|删除错误码|类名：AppAccountManager；<br>API声明：getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;<br>差异内容：12400001|类名：AppAccountManager；<br>API声明：getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;<br>差异内容：NA|api/@ohos.account.appAccount.d.ts|
|删除错误码|类名：AppAccountManager；<br>API声明：on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>差异内容：12400001|类名：AppAccountManager；<br>API声明：on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>差异内容：NA|api/@ohos.account.appAccount.d.ts|
|删除错误码|类名：AppAccountManager；<br>API声明：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：12400001|类名：AppAccountManager；<br>API声明：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.account.appAccount.d.ts|
|删除错误码|类名：AppAccountManager；<br>API声明：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>差异内容：12400001|类名：AppAccountManager；<br>API声明：setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>差异内容：NA|api/@ohos.account.appAccount.d.ts|
|错误码变更|类名：AppAccountManager；<br>API声明：setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：12300001,12300002,12300003,12400001,401|类名：AppAccountManager；<br>API声明：setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：12300001,12300002,12300003,12400005,401|api/@ohos.account.appAccount.d.ts|
|错误码变更|类名：AppAccountManager；<br>API声明：setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;<br>差异内容：12300001,12300002,12300003,12400001,401|类名：AppAccountManager；<br>API声明：setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;<br>差异内容：12300001,12300002,12300003,12400005,401|api/@ohos.account.appAccount.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class PrintExtensionAbility<br>差异内容：export default class PrintExtensionAbility|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：PrintExtensionAbility；<br>API声明：onCreate(want: Want): void;<br>差异内容：onCreate(want: Want): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：PrintExtensionAbility；<br>API声明：onStartDiscoverPrinter(): void;<br>差异内容：onStartDiscoverPrinter(): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：PrintExtensionAbility；<br>API声明：onStopDiscoverPrinter(): void;<br>差异内容：onStopDiscoverPrinter(): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：PrintExtensionAbility；<br>API声明：onConnectPrinter(printerId: number): void;<br>差异内容：onConnectPrinter(printerId: number): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：PrintExtensionAbility；<br>API声明：onDisconnectPrinter(printerId: number): void;<br>差异内容：onDisconnectPrinter(printerId: number): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：PrintExtensionAbility；<br>API声明：onDestroy(): void;<br>差异内容：onDestroy(): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|新增API|NA|类名：deviceInfo；<br>API声明：const productModelAlias: string;<br>差异内容：const productModelAlias: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：function createData(data: Record\<string, ValueType>): PasteData;<br>差异内容：function createData(data: Record\<string, ValueType>): PasteData;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MAX_RECORD_NUM = 512;<br>差异内容：const MAX_RECORD_NUM = 512;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_HTML = 'text/html';<br>差异内容：const MIMETYPE_TEXT_HTML = 'text/html';|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_WANT = 'text/want';<br>差异内容：const MIMETYPE_TEXT_WANT = 'text/want';|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_PLAIN = 'text/plain';<br>差异内容：const MIMETYPE_TEXT_PLAIN = 'text/plain';|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_URI = 'text/uri';<br>差异内容：const MIMETYPE_TEXT_URI = 'text/uri';|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：const MIMETYPE_PIXELMAP = 'pixelMap';<br>差异内容：const MIMETYPE_PIXELMAP = 'pixelMap';|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：addEntry(type: string, value: ValueType): void;<br>差异内容：addEntry(type: string, value: ValueType): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：getValidTypes(types: Array\<string>): Array\<string>;<br>差异内容：getValidTypes(types: Array\<string>): Array\<string>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：PasteDataRecord；<br>API声明：getData(type: string): Promise\<ValueType>;<br>差异内容：getData(type: string): Promise\<ValueType>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：setAppShareOptions(shareOptions: ShareOption): void;<br>差异内容：setAppShareOptions(shareOptions: ShareOption): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：removeAppShareOptions(): void;<br>差异内容：removeAppShareOptions(): void;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：getMimeTypes(): Promise\<Array\<string>>;<br>差异内容：getMimeTypes(): Promise\<Array\<string>>;|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrinterState<br>差异内容：enum PrinterState|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterState；<br>API声明：PRINTER_ADDED = 0<br>差异内容：PRINTER_ADDED = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterState；<br>API声明：PRINTER_REMOVED = 1<br>差异内容：PRINTER_REMOVED = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterState；<br>API声明：PRINTER_CAPABILITY_UPDATED = 2<br>差异内容：PRINTER_CAPABILITY_UPDATED = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterState；<br>API声明：PRINTER_CONNECTED = 3<br>差异内容：PRINTER_CONNECTED = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterState；<br>API声明：PRINTER_DISCONNECTED = 4<br>差异内容：PRINTER_DISCONNECTED = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterState；<br>API声明：PRINTER_RUNNING = 5<br>差异内容：PRINTER_RUNNING = 5|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintJobState<br>差异内容：enum PrintJobState|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobState；<br>API声明：PRINT_JOB_PREPARE = 0<br>差异内容：PRINT_JOB_PREPARE = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobState；<br>API声明：PRINT_JOB_QUEUED = 1<br>差异内容：PRINT_JOB_QUEUED = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobState；<br>API声明：PRINT_JOB_RUNNING = 2<br>差异内容：PRINT_JOB_RUNNING = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobState；<br>API声明：PRINT_JOB_BLOCKED = 3<br>差异内容：PRINT_JOB_BLOCKED = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobState；<br>API声明：PRINT_JOB_COMPLETED = 4<br>差异内容：PRINT_JOB_COMPLETED = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintJobSubState<br>差异内容：enum PrintJobSubState|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_COMPLETED_SUCCESS = 0<br>差异内容：PRINT_JOB_COMPLETED_SUCCESS = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_COMPLETED_FAILED = 1<br>差异内容：PRINT_JOB_COMPLETED_FAILED = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_COMPLETED_CANCELLED = 2<br>差异内容：PRINT_JOB_COMPLETED_CANCELLED = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_COMPLETED_FILE_CORRUPTED = 3<br>差异内容：PRINT_JOB_COMPLETED_FILE_CORRUPTED = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_OFFLINE = 4<br>差异内容：PRINT_JOB_BLOCK_OFFLINE = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_BUSY = 5<br>差异内容：PRINT_JOB_BLOCK_BUSY = 5|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_CANCELLED = 6<br>差异内容：PRINT_JOB_BLOCK_CANCELLED = 6|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_OUT_OF_PAPER = 7<br>差异内容：PRINT_JOB_BLOCK_OUT_OF_PAPER = 7|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_OUT_OF_INK = 8<br>差异内容：PRINT_JOB_BLOCK_OUT_OF_INK = 8|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_OUT_OF_TONER = 9<br>差异内容：PRINT_JOB_BLOCK_OUT_OF_TONER = 9|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_JAMMED = 10<br>差异内容：PRINT_JOB_BLOCK_JAMMED = 10|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_DOOR_OPEN = 11<br>差异内容：PRINT_JOB_BLOCK_DOOR_OPEN = 11|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_SERVICE_REQUEST = 12<br>差异内容：PRINT_JOB_BLOCK_SERVICE_REQUEST = 12|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_LOW_ON_INK = 13<br>差异内容：PRINT_JOB_BLOCK_LOW_ON_INK = 13|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_LOW_ON_TONER = 14<br>差异内容：PRINT_JOB_BLOCK_LOW_ON_TONER = 14|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_REALLY_LOW_ON_INK = 15<br>差异内容：PRINT_JOB_BLOCK_REALLY_LOW_ON_INK = 15|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_BAD_CERTIFICATE = 16<br>差异内容：PRINT_JOB_BLOCK_BAD_CERTIFICATE = 16|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_ACCOUNT_ERROR = 18<br>差异内容：PRINT_JOB_BLOCK_ACCOUNT_ERROR = 18|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_PRINT_PERMISSION_ERROR = 19<br>差异内容：PRINT_JOB_BLOCK_PRINT_PERMISSION_ERROR = 19|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_PRINT_COLOR_PERMISSION_ERROR = 20<br>差异内容：PRINT_JOB_BLOCK_PRINT_COLOR_PERMISSION_ERROR = 20|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_NETWORK_ERROR = 21<br>差异内容：PRINT_JOB_BLOCK_NETWORK_ERROR = 21|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_SERVER_CONNECTION_ERROR = 22<br>差异内容：PRINT_JOB_BLOCK_SERVER_CONNECTION_ERROR = 22|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_LARGE_FILE_ERROR = 23<br>差异内容：PRINT_JOB_BLOCK_LARGE_FILE_ERROR = 23|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_FILE_PARSING_ERROR = 24<br>差异内容：PRINT_JOB_BLOCK_FILE_PARSING_ERROR = 24|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_SLOW_FILE_CONVERSION = 25<br>差异内容：PRINT_JOB_BLOCK_SLOW_FILE_CONVERSION = 25|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_RUNNING_UPLOADING_FILES = 26<br>差异内容：PRINT_JOB_RUNNING_UPLOADING_FILES = 26|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_RUNNING_CONVERTING_FILES = 27<br>差异内容：PRINT_JOB_RUNNING_CONVERTING_FILES = 27|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintJobSubState；<br>API声明：PRINT_JOB_BLOCK_UNKNOWN = 99<br>差异内容：PRINT_JOB_BLOCK_UNKNOWN = 99|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintErrorCode<br>差异内容：enum PrintErrorCode|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_NONE = 0<br>差异内容：E_PRINT_NONE = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_NO_PERMISSION = 201<br>差异内容：E_PRINT_NO_PERMISSION = 201|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_INVALID_PARAMETER = 401<br>差异内容：E_PRINT_INVALID_PARAMETER = 401|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_GENERIC_FAILURE = 13100001<br>差异内容：E_PRINT_GENERIC_FAILURE = 13100001|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_RPC_FAILURE = 13100002<br>差异内容：E_PRINT_RPC_FAILURE = 13100002|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_SERVER_FAILURE = 13100003<br>差异内容：E_PRINT_SERVER_FAILURE = 13100003|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_INVALID_EXTENSION = 13100004<br>差异内容：E_PRINT_INVALID_EXTENSION = 13100004|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_INVALID_PRINTER = 13100005<br>差异内容：E_PRINT_INVALID_PRINTER = 13100005|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_INVALID_PRINT_JOB = 13100006<br>差异内容：E_PRINT_INVALID_PRINT_JOB = 13100006|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintErrorCode；<br>API声明：E_PRINT_FILE_IO = 13100007<br>差异内容：E_PRINT_FILE_IO = 13100007|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum ApplicationEvent<br>差异内容：enum ApplicationEvent|api/@ohos.print.d.ts|
|新增API|NA|类名：ApplicationEvent；<br>API声明：APPLICATION_CREATED = 0<br>差异内容：APPLICATION_CREATED = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：ApplicationEvent；<br>API声明：APPLICATION_CLOSED_FOR_STARTED = 1<br>差异内容：APPLICATION_CLOSED_FOR_STARTED = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：ApplicationEvent；<br>API声明：APPLICATION_CLOSED_FOR_CANCELED = 2<br>差异内容：APPLICATION_CLOSED_FOR_CANCELED = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise\<void>;<br>差异内容：function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise\<void>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function updatePrinterInDiscovery(printerInformation: PrinterInformation): Promise\<void>;<br>差异内容：function updatePrinterInDiscovery(printerInformation: PrinterInformation): Promise\<void>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function removePrinterFromDiscovery(printerId: string): Promise\<void>;<br>差异内容：function removePrinterFromDiscovery(printerId: string): Promise\<void>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：function getPrinterInformationById(printerId: string): Promise\<PrinterInformation>;<br>差异内容：function getPrinterInformationById(printerId: string): Promise\<PrinterInformation>;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrinterInformation<br>差异内容：interface PrinterInformation|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：printerId: string;<br>差异内容：printerId: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：printerName: string;<br>差异内容：printerName: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：printerStatus: PrinterStatus;<br>差异内容：printerStatus: PrinterStatus;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：capability?: PrinterCapabilities;<br>差异内容：capability?: PrinterCapabilities;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：uri?: string;<br>差异内容：uri?: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：printerMake?: string;<br>差异内容：printerMake?: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterInformation；<br>API声明：options?: string;<br>差异内容：options?: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：interface PrinterCapabilities<br>差异内容：interface PrinterCapabilities|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：supportedPageSizes: Array\<PrintPageSize>;<br>差异内容：supportedPageSizes: Array\<PrintPageSize>;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：supportedColorModes: Array\<PrintColorMode>;<br>差异内容：supportedColorModes: Array\<PrintColorMode>;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：supportedDuplexModes: Array\<PrintDuplexMode>;<br>差异内容：supportedDuplexModes: Array\<PrintDuplexMode>;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：supportedMediaTypes?: Array\<string>;<br>差异内容：supportedMediaTypes?: Array\<string>;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：supportedQualities?: Array\<PrintQuality>;<br>差异内容：supportedQualities?: Array\<PrintQuality>;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：supportedOrientations?: Array\<PrintOrientationMode>;<br>差异内容：supportedOrientations?: Array\<PrintOrientationMode>;|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterCapabilities；<br>API声明：options?: string;<br>差异内容：options?: string;|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintQuality<br>差异内容：enum PrintQuality|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintQuality；<br>API声明：QUALITY_DRAFT = 3<br>差异内容：QUALITY_DRAFT = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintQuality；<br>API声明：QUALITY_NORMAL = 4<br>差异内容：QUALITY_NORMAL = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintQuality；<br>API声明：QUALITY_HIGH = 5<br>差异内容：QUALITY_HIGH = 5|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrintOrientationMode<br>差异内容：enum PrintOrientationMode|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintOrientationMode；<br>API声明：ORIENTATION_MODE_PORTRAIT = 0<br>差异内容：ORIENTATION_MODE_PORTRAIT = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintOrientationMode；<br>API声明：ORIENTATION_MODE_LANDSCAPE = 1<br>差异内容：ORIENTATION_MODE_LANDSCAPE = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintOrientationMode；<br>API声明：ORIENTATION_MODE_REVERSE_LANDSCAPE = 2<br>差异内容：ORIENTATION_MODE_REVERSE_LANDSCAPE = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintOrientationMode；<br>API声明：ORIENTATION_MODE_REVERSE_PORTRAIT = 3<br>差异内容：ORIENTATION_MODE_REVERSE_PORTRAIT = 3|api/@ohos.print.d.ts|
|新增API|NA|类名：PrintOrientationMode；<br>API声明：ORIENTATION_MODE_NONE = 4<br>差异内容：ORIENTATION_MODE_NONE = 4|api/@ohos.print.d.ts|
|新增API|NA|类名：print；<br>API声明：enum PrinterStatus<br>差异内容：enum PrinterStatus|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterStatus；<br>API声明：PRINTER_IDLE = 0<br>差异内容：PRINTER_IDLE = 0|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterStatus；<br>API声明：PRINTER_BUSY = 1<br>差异内容：PRINTER_BUSY = 1|api/@ohos.print.d.ts|
|新增API|NA|类名：PrinterStatus；<br>API声明：PRINTER_UNAVAILABLE = 2<br>差异内容：PRINTER_UNAVAILABLE = 2|api/@ohos.print.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function hasAccessoryRight(accessory: USBAccessory): boolean;<br>差异内容：function hasAccessoryRight(accessory: USBAccessory): boolean;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function requestAccessoryRight(accessory: USBAccessory): Promise\<boolean>;<br>差异内容：function requestAccessoryRight(accessory: USBAccessory): Promise\<boolean>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function cancelAccessoryRight(accessory: USBAccessory): void;<br>差异内容：function cancelAccessoryRight(accessory: USBAccessory): void;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function getAccessoryList(): Array\<Readonly\<USBAccessory>>;<br>差异内容：function getAccessoryList(): Array\<Readonly\<USBAccessory>>;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function openAccessory(accessory: USBAccessory): USBAccessoryHandle;<br>差异内容：function openAccessory(accessory: USBAccessory): USBAccessoryHandle;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：function closeAccessory(accessoryHandle: USBAccessoryHandle): void;<br>差异内容：function closeAccessory(accessoryHandle: USBAccessoryHandle): void;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBAccessory<br>差异内容：interface USBAccessory|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBAccessory；<br>API声明：manufacturer: string;<br>差异内容：manufacturer: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBAccessory；<br>API声明：product: string;<br>差异内容：product: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBAccessory；<br>API声明：description: string;<br>差异内容：description: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBAccessory；<br>API声明：version: string;<br>差异内容：version: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBAccessory；<br>API声明：serialNumber: string;<br>差异内容：serialNumber: string;|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：usbManager；<br>API声明：interface USBAccessoryHandle<br>差异内容：interface USBAccessoryHandle|api/@ohos.usbManager.d.ts|
|新增API|NA|类名：USBAccessoryHandle；<br>API声明：accessoryFd: number;<br>差异内容：accessoryFd: number;|api/@ohos.usbManager.d.ts|
|删除API|类名：pasteboard；<br>API声明：const MAX_RECORD_NUM: number;<br>差异内容：const MAX_RECORD_NUM: number;|NA|api/@ohos.pasteboard.d.ts|
|删除API|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_HTML: string;<br>差异内容：const MIMETYPE_TEXT_HTML: string;|NA|api/@ohos.pasteboard.d.ts|
|删除API|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_WANT: string;<br>差异内容：const MIMETYPE_TEXT_WANT: string;|NA|api/@ohos.pasteboard.d.ts|
|删除API|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_PLAIN: string;<br>差异内容：const MIMETYPE_TEXT_PLAIN: string;|NA|api/@ohos.pasteboard.d.ts|
|删除API|类名：pasteboard；<br>API声明：const MIMETYPE_TEXT_URI: string;<br>差异内容：const MIMETYPE_TEXT_URI: string;|NA|api/@ohos.pasteboard.d.ts|
|删除API|类名：pasteboard；<br>API声明：const MIMETYPE_PIXELMAP: string;<br>差异内容：const MIMETYPE_PIXELMAP: string;|NA|api/@ohos.pasteboard.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.app.ability.PrintExtensionAbility.d.ts<br>差异内容：BasicServicesKit|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|API从不支持元服务到支持元服务|类名：deviceInfo；<br>API声明：const sdkApiVersion: number;<br>差异内容：NA|类名：deviceInfo；<br>API声明：const sdkApiVersion: number;<br>差异内容：atomicservice|api/@ohos.deviceInfo.d.ts|
