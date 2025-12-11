| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Deleted error code|Class name: AppAccountManager;<br>API declaration: getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>DIfferences: 12400001|Class name: AppAccountManager;<br>API declaration: getAccountsByOwner(owner: string, callback: AsyncCallback\<Array\<AppAccountInfo>>): void;<br>DIfferences: NA|api/@ohos.account.appAccount.d.ts|
|Deleted error code|Class name: AppAccountManager;<br>API declaration: getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;<br>DIfferences: 12400001|Class name: AppAccountManager;<br>API declaration: getAccountsByOwner(owner: string): Promise\<Array\<AppAccountInfo>>;<br>DIfferences: NA|api/@ohos.account.appAccount.d.ts|
|Deleted error code|Class name: AppAccountManager;<br>API declaration: on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>DIfferences: 12400001|Class name: AppAccountManager;<br>API declaration: on(type: 'accountChange', owners: Array\<string>, callback: Callback\<Array\<AppAccountInfo>>): void;<br>DIfferences: NA|api/@ohos.account.appAccount.d.ts|
|Deleted error code|Class name: AppAccountManager;<br>API declaration: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>DIfferences: 12400001|Class name: AppAccountManager;<br>API declaration: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback\<void>): void;<br>DIfferences: NA|api/@ohos.account.appAccount.d.ts|
|Deleted error code|Class name: AppAccountManager;<br>API declaration: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>DIfferences: 12400001|Class name: AppAccountManager;<br>API declaration: setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise\<void>;<br>DIfferences: NA|api/@ohos.account.appAccount.d.ts|
|Error code change|Class name: AppAccountManager;<br>API declaration: setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;<br>DIfferences: 12300001,12300002,12300003,12400001,401|Class name: AppAccountManager;<br>API declaration: setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void;<br>DIfferences: 12300001,12300002,12300003,12400005,401|api/@ohos.account.appAccount.d.ts|
|Error code change|Class name: AppAccountManager;<br>API declaration: setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;<br>DIfferences: 12300001,12300002,12300003,12400001,401|Class name: AppAccountManager;<br>API declaration: setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>;<br>DIfferences: 12300001,12300002,12300003,12400005,401|api/@ohos.account.appAccount.d.ts|
|New API |NA|Class name: global;<br>API declaration: export default class PrintExtensionAbility<br>DIfferences: export default class PrintExtensionAbility|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: PrintExtensionAbility;<br>API declaration: onCreate(want: Want): void;<br>DIfferences: onCreate(want: Want): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: PrintExtensionAbility;<br>API declaration: onStartDiscoverPrinter(): void;<br>DIfferences: onStartDiscoverPrinter(): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: PrintExtensionAbility;<br>API declaration: onStopDiscoverPrinter(): void;<br>DIfferences: onStopDiscoverPrinter(): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: PrintExtensionAbility;<br>API declaration: onConnectPrinter(printerId: number): void;<br>DIfferences: onConnectPrinter(printerId: number): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: PrintExtensionAbility;<br>API declaration: onDisconnectPrinter(printerId: number): void;<br>DIfferences: onDisconnectPrinter(printerId: number): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: PrintExtensionAbility;<br>API declaration: onDestroy(): void;<br>DIfferences: onDestroy(): void;|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New API |NA|Class name: deviceInfo;<br>API declaration: const productModelAlias: string;<br>DIfferences: const productModelAlias: string;|api/@ohos.deviceInfo.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: function createData(data: Record\<string, ValueType>): PasteData;<br>DIfferences: function createData(data: Record\<string, ValueType>): PasteData;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: const MAX_RECORD_NUM = 512;<br>DIfferences: const MAX_RECORD_NUM = 512;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_HTML = 'text/html';<br>DIfferences: const MIMETYPE_TEXT_HTML = 'text/html';|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_WANT = 'text/want';<br>DIfferences: const MIMETYPE_TEXT_WANT = 'text/want';|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_PLAIN = 'text/plain';<br>DIfferences: const MIMETYPE_TEXT_PLAIN = 'text/plain';|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_URI = 'text/uri';<br>DIfferences: const MIMETYPE_TEXT_URI = 'text/uri';|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: const MIMETYPE_PIXELMAP = 'pixelMap';<br>DIfferences: const MIMETYPE_PIXELMAP = 'pixelMap';|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: PasteDataRecord;<br>API declaration: addEntry(type: string, value: ValueType): void;<br>DIfferences: addEntry(type: string, value: ValueType): void;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: PasteDataRecord;<br>API declaration: getValidTypes(types: Array\<string>): Array\<string>;<br>DIfferences: getValidTypes(types: Array\<string>): Array\<string>;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: PasteDataRecord;<br>API declaration: getData(type: string): Promise\<ValueType>;<br>DIfferences: getData(type: string): Promise\<ValueType>;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: SystemPasteboard;<br>API declaration: setAppShareOptions(shareOptions: ShareOption): void;<br>DIfferences: setAppShareOptions(shareOptions: ShareOption): void;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: SystemPasteboard;<br>API declaration: removeAppShareOptions(): void;<br>DIfferences: removeAppShareOptions(): void;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: SystemPasteboard;<br>API declaration: getMimeTypes(): Promise\<Array\<string>>;<br>DIfferences: getMimeTypes(): Promise\<Array\<string>>;|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrinterState<br>DIfferences: enum PrinterState|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterState;<br>API declaration: PRINTER_ADDED = 0<br>DIfferences: PRINTER_ADDED = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterState;<br>API declaration: PRINTER_REMOVED = 1<br>DIfferences: PRINTER_REMOVED = 1|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterState;<br>API declaration: PRINTER_CAPABILITY_UPDATED = 2<br>DIfferences: PRINTER_CAPABILITY_UPDATED = 2|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterState;<br>API declaration: PRINTER_CONNECTED = 3<br>DIfferences: PRINTER_CONNECTED = 3|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterState;<br>API declaration: PRINTER_DISCONNECTED = 4<br>DIfferences: PRINTER_DISCONNECTED = 4|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterState;<br>API declaration: PRINTER_RUNNING = 5<br>DIfferences: PRINTER_RUNNING = 5|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrintJobState<br>DIfferences: enum PrintJobState|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobState;<br>API declaration: PRINT_JOB_PREPARE = 0<br>DIfferences: PRINT_JOB_PREPARE = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobState;<br>API declaration: PRINT_JOB_QUEUED = 1<br>DIfferences: PRINT_JOB_QUEUED = 1|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobState;<br>API declaration: PRINT_JOB_RUNNING = 2<br>DIfferences: PRINT_JOB_RUNNING = 2|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobState;<br>API declaration: PRINT_JOB_BLOCKED = 3<br>DIfferences: PRINT_JOB_BLOCKED = 3|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobState;<br>API declaration: PRINT_JOB_COMPLETED = 4<br>DIfferences: PRINT_JOB_COMPLETED = 4|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrintJobSubState<br>DIfferences: enum PrintJobSubState|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_COMPLETED_SUCCESS = 0<br>DIfferences: PRINT_JOB_COMPLETED_SUCCESS = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_COMPLETED_FAILED = 1<br>DIfferences: PRINT_JOB_COMPLETED_FAILED = 1|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_COMPLETED_CANCELLED = 2<br>DIfferences: PRINT_JOB_COMPLETED_CANCELLED = 2|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_COMPLETED_FILE_CORRUPTED = 3<br>DIfferences: PRINT_JOB_COMPLETED_FILE_CORRUPTED = 3|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_OFFLINE = 4<br>DIfferences: PRINT_JOB_BLOCK_OFFLINE = 4|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_BUSY = 5<br>DIfferences: PRINT_JOB_BLOCK_BUSY = 5|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_CANCELLED = 6<br>DIfferences: PRINT_JOB_BLOCK_CANCELLED = 6|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_OUT_OF_PAPER = 7<br>DIfferences: PRINT_JOB_BLOCK_OUT_OF_PAPER = 7|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_OUT_OF_INK = 8<br>DIfferences: PRINT_JOB_BLOCK_OUT_OF_INK = 8|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_OUT_OF_TONER = 9<br>DIfferences: PRINT_JOB_BLOCK_OUT_OF_TONER = 9|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_JAMMED = 10<br>DIfferences: PRINT_JOB_BLOCK_JAMMED = 10|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_DOOR_OPEN = 11<br>DIfferences: PRINT_JOB_BLOCK_DOOR_OPEN = 11|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_SERVICE_REQUEST = 12<br>DIfferences: PRINT_JOB_BLOCK_SERVICE_REQUEST = 12|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_LOW_ON_INK = 13<br>DIfferences: PRINT_JOB_BLOCK_LOW_ON_INK = 13|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_LOW_ON_TONER = 14<br>DIfferences: PRINT_JOB_BLOCK_LOW_ON_TONER = 14|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_REALLY_LOW_ON_INK = 15<br>DIfferences: PRINT_JOB_BLOCK_REALLY_LOW_ON_INK = 15|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_BAD_CERTIFICATE = 16<br>DIfferences: PRINT_JOB_BLOCK_BAD_CERTIFICATE = 16|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_ACCOUNT_ERROR = 18<br>DIfferences: PRINT_JOB_BLOCK_ACCOUNT_ERROR = 18|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_PRINT_PERMISSION_ERROR = 19<br>DIfferences: PRINT_JOB_BLOCK_PRINT_PERMISSION_ERROR = 19|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_PRINT_COLOR_PERMISSION_ERROR = 20<br>DIfferences: PRINT_JOB_BLOCK_PRINT_COLOR_PERMISSION_ERROR = 20|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_NETWORK_ERROR = 21<br>DIfferences: PRINT_JOB_BLOCK_NETWORK_ERROR = 21|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_SERVER_CONNECTION_ERROR = 22<br>DIfferences: PRINT_JOB_BLOCK_SERVER_CONNECTION_ERROR = 22|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_LARGE_FILE_ERROR = 23<br>DIfferences: PRINT_JOB_BLOCK_LARGE_FILE_ERROR = 23|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_FILE_PARSING_ERROR = 24<br>DIfferences: PRINT_JOB_BLOCK_FILE_PARSING_ERROR = 24|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_SLOW_FILE_CONVERSION = 25<br>DIfferences: PRINT_JOB_BLOCK_SLOW_FILE_CONVERSION = 25|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_RUNNING_UPLOADING_FILES = 26<br>DIfferences: PRINT_JOB_RUNNING_UPLOADING_FILES = 26|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_RUNNING_CONVERTING_FILES = 27<br>DIfferences: PRINT_JOB_RUNNING_CONVERTING_FILES = 27|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintJobSubState;<br>API declaration: PRINT_JOB_BLOCK_UNKNOWN = 99<br>DIfferences: PRINT_JOB_BLOCK_UNKNOWN = 99|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrintErrorCode<br>DIfferences: enum PrintErrorCode|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_NONE = 0<br>DIfferences: E_PRINT_NONE = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_NO_PERMISSION = 201<br>DIfferences: E_PRINT_NO_PERMISSION = 201|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_INVALID_PARAMETER = 401<br>DIfferences: E_PRINT_INVALID_PARAMETER = 401|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_GENERIC_FAILURE = 13100001<br>DIfferences: E_PRINT_GENERIC_FAILURE = 13100001|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_RPC_FAILURE = 13100002<br>DIfferences: E_PRINT_RPC_FAILURE = 13100002|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_SERVER_FAILURE = 13100003<br>DIfferences: E_PRINT_SERVER_FAILURE = 13100003|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_INVALID_EXTENSION = 13100004<br>DIfferences: E_PRINT_INVALID_EXTENSION = 13100004|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_INVALID_PRINTER = 13100005<br>DIfferences: E_PRINT_INVALID_PRINTER = 13100005|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_INVALID_PRINT_JOB = 13100006<br>DIfferences: E_PRINT_INVALID_PRINT_JOB = 13100006|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintErrorCode;<br>API declaration: E_PRINT_FILE_IO = 13100007<br>DIfferences: E_PRINT_FILE_IO = 13100007|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum ApplicationEvent<br>DIfferences: enum ApplicationEvent|api/@ohos.print.d.ts|
|New API |NA|Class name: ApplicationEvent;<br>API declaration: APPLICATION_CREATED = 0<br>DIfferences: APPLICATION_CREATED = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: ApplicationEvent;<br>API declaration: APPLICATION_CLOSED_FOR_STARTED = 1<br>DIfferences: APPLICATION_CLOSED_FOR_STARTED = 1|api/@ohos.print.d.ts|
|New API |NA|Class name: ApplicationEvent;<br>API declaration: APPLICATION_CLOSED_FOR_CANCELED = 2<br>DIfferences: APPLICATION_CLOSED_FOR_CANCELED = 2|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise\<void>;<br>DIfferences: function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise\<void>;|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: function updatePrinterInDiscovery(printerInformation: PrinterInformation): Promise\<void>;<br>DIfferences: function updatePrinterInDiscovery(printerInformation: PrinterInformation): Promise\<void>;|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: function removePrinterFromDiscovery(printerId: string): Promise\<void>;<br>DIfferences: function removePrinterFromDiscovery(printerId: string): Promise\<void>;|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: function getPrinterInformationById(printerId: string): Promise\<PrinterInformation>;<br>DIfferences: function getPrinterInformationById(printerId: string): Promise\<PrinterInformation>;|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: interface PrinterInformation<br>DIfferences: interface PrinterInformation|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: printerId: string;<br>DIfferences: printerId: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: printerName: string;<br>DIfferences: printerName: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: printerStatus: PrinterStatus;<br>DIfferences: printerStatus: PrinterStatus;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: description?: string;<br>DIfferences: description?: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: capability?: PrinterCapabilities;<br>DIfferences: capability?: PrinterCapabilities;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: uri?: string;<br>DIfferences: uri?: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: printerMake?: string;<br>DIfferences: printerMake?: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterInformation;<br>API declaration: options?: string;<br>DIfferences: options?: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: interface PrinterCapabilities<br>DIfferences: interface PrinterCapabilities|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: supportedPageSizes: Array\<PrintPageSize>;<br>DIfferences: supportedPageSizes: Array\<PrintPageSize>;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: supportedColorModes: Array\<PrintColorMode>;<br>DIfferences: supportedColorModes: Array\<PrintColorMode>;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: supportedDuplexModes: Array\<PrintDuplexMode>;<br>DIfferences: supportedDuplexModes: Array\<PrintDuplexMode>;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: supportedMediaTypes?: Array\<string>;<br>DIfferences: supportedMediaTypes?: Array\<string>;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: supportedQualities?: Array\<PrintQuality>;<br>DIfferences: supportedQualities?: Array\<PrintQuality>;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: supportedOrientations?: Array\<PrintOrientationMode>;<br>DIfferences: supportedOrientations?: Array\<PrintOrientationMode>;|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterCapabilities;<br>API declaration: options?: string;<br>DIfferences: options?: string;|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrintQuality<br>DIfferences: enum PrintQuality|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintQuality;<br>API declaration: QUALITY_DRAFT = 3<br>DIfferences: QUALITY_DRAFT = 3|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintQuality;<br>API declaration: QUALITY_NORMAL = 4<br>DIfferences: QUALITY_NORMAL = 4|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintQuality;<br>API declaration: QUALITY_HIGH = 5<br>DIfferences: QUALITY_HIGH = 5|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrintOrientationMode<br>DIfferences: enum PrintOrientationMode|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintOrientationMode;<br>API declaration: ORIENTATION_MODE_PORTRAIT = 0<br>DIfferences: ORIENTATION_MODE_PORTRAIT = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintOrientationMode;<br>API declaration: ORIENTATION_MODE_LANDSCAPE = 1<br>DIfferences: ORIENTATION_MODE_LANDSCAPE = 1|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintOrientationMode;<br>API declaration: ORIENTATION_MODE_REVERSE_LANDSCAPE = 2<br>DIfferences: ORIENTATION_MODE_REVERSE_LANDSCAPE = 2|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintOrientationMode;<br>API declaration: ORIENTATION_MODE_REVERSE_PORTRAIT = 3<br>DIfferences: ORIENTATION_MODE_REVERSE_PORTRAIT = 3|api/@ohos.print.d.ts|
|New API |NA|Class name: PrintOrientationMode;<br>API declaration: ORIENTATION_MODE_NONE = 4<br>DIfferences: ORIENTATION_MODE_NONE = 4|api/@ohos.print.d.ts|
|New API |NA|Class name: print;<br>API declaration: enum PrinterStatus<br>DIfferences: enum PrinterStatus|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterStatus;<br>API declaration: PRINTER_IDLE = 0<br>DIfferences: PRINTER_IDLE = 0|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterStatus;<br>API declaration: PRINTER_BUSY = 1<br>DIfferences: PRINTER_BUSY = 1|api/@ohos.print.d.ts|
|New API |NA|Class name: PrinterStatus;<br>API declaration: PRINTER_UNAVAILABLE = 2<br>DIfferences: PRINTER_UNAVAILABLE = 2|api/@ohos.print.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: function hasAccessoryRight(accessory: USBAccessory): boolean;<br>DIfferences: function hasAccessoryRight(accessory: USBAccessory): boolean;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: function requestAccessoryRight(accessory: USBAccessory): Promise\<boolean>;<br>DIfferences: function requestAccessoryRight(accessory: USBAccessory): Promise\<boolean>;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: function cancelAccessoryRight(accessory: USBAccessory): void;<br>DIfferences: function cancelAccessoryRight(accessory: USBAccessory): void;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: function getAccessoryList(): Array\<Readonly\<USBAccessory>>;<br>DIfferences: function getAccessoryList(): Array\<Readonly\<USBAccessory>>;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: function openAccessory(accessory: USBAccessory): USBAccessoryHandle;<br>DIfferences: function openAccessory(accessory: USBAccessory): USBAccessoryHandle;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: function closeAccessory(accessoryHandle: USBAccessoryHandle): void;<br>DIfferences: function closeAccessory(accessoryHandle: USBAccessoryHandle): void;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: interface USBAccessory<br>DIfferences: interface USBAccessory|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: USBAccessory;<br>API declaration: manufacturer: string;<br>DIfferences: manufacturer: string;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: USBAccessory;<br>API declaration: product: string;<br>DIfferences: product: string;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: USBAccessory;<br>API declaration: description: string;<br>DIfferences: description: string;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: USBAccessory;<br>API declaration: version: string;<br>DIfferences: version: string;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: USBAccessory;<br>API declaration: serialNumber: string;<br>DIfferences: serialNumber: string;|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: usbManager;<br>API declaration: interface USBAccessoryHandle<br>DIfferences: interface USBAccessoryHandle|api/@ohos.usbManager.d.ts|
|New API |NA|Class name: USBAccessoryHandle;<br>API declaration: accessoryFd: number;<br>DIfferences: accessoryFd: number;|api/@ohos.usbManager.d.ts|
| Deleted API|Class name: pasteboard;<br>API declaration: const MAX_RECORD_NUM: number;<br>DIfferences: const MAX_RECORD_NUM: number;|NA|api/@ohos.pasteboard.d.ts|
| Deleted API|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_HTML: string;<br>DIfferences: const MIMETYPE_TEXT_HTML: string;|NA|api/@ohos.pasteboard.d.ts|
| Deleted API|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_WANT: string;<br>DIfferences: const MIMETYPE_TEXT_WANT: string;|NA|api/@ohos.pasteboard.d.ts|
| Deleted API|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_PLAIN: string;<br>DIfferences: const MIMETYPE_TEXT_PLAIN: string;|NA|api/@ohos.pasteboard.d.ts|
| Deleted API|Class name: pasteboard;<br>API declaration: const MIMETYPE_TEXT_URI: string;<br>DIfferences: const MIMETYPE_TEXT_URI: string;|NA|api/@ohos.pasteboard.d.ts|
| Deleted API|Class name: pasteboard;<br>API declaration: const MIMETYPE_PIXELMAP: string;<br>DIfferences: const MIMETYPE_PIXELMAP: string;|NA|api/@ohos.pasteboard.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>DIfferences: NA|Class name: global;<br>API declaration: api\@ohos.app.ability.PrintExtensionAbility.d.ts<br>DIfferences: BasicServicesKit|api/@ohos.app.ability.PrintExtensionAbility.d.ts|
|New support for atomic services|Class name: deviceInfo;<br>API declaration: const sdkApiVersion: number;<br>DIfferences: NA|Class name: deviceInfo;<br>API declaration: const sdkApiVersion: number;<br>DIfferences: atomicservice|api/@ohos.deviceInfo.d.ts|
