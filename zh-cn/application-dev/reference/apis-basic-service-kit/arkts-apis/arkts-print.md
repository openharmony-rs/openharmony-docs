# @ohos.print

该模块为基本打印的操作API，提供调用基础打印功能的接口。

**起始版本：** 10

<!--Device-unnamed-declare namespace print--><!--Device-unnamed-declare namespace print-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addPrinter](arkts-basicservices-print-addprinter-f.md#addprinter) | 添加打印机到系统中，使用Promise异步回调。 |
| [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md#addprintertodiscovery) | 添加打印机到系统打印机发现列表，使用Promise异步回调。 |
| [getAddedPrinters](arkts-basicservices-print-getaddedprinters-f.md#getaddedprinters) | 获取系统中已添加的打印机列表，使用Promise异步回调。 |
| [getPrinterInformationById](arkts-basicservices-print-getprinterinformationbyid-f.md#getprinterinformationbyid) | 根据打印机id获取打印机信息，使用Promise异步回调。 |
| [notifyWatermarkComplete](arkts-basicservices-print-notifywatermarkcomplete-f.md#notifywatermarkcomplete) | 通知水印处理完成。 |
| [off](arkts-basicservices-print-off-f.md#off-3) | 取消注册打印机变动事件回调，使用callback回调。 |
| [on](arkts-basicservices-print-on-f.md#on-3) | 注册打印机变动事件回调，使用callback回调。 |
| [print](arkts-basicservices-print-f.md#print) | 打印接口，传入文件进行打印，使用callback异步回调。拉起系统打印预览界面，需要使用[print](arkts-basicservices-print-f.md#print)接口，传入context。 |
| [print](arkts-basicservices-print-f.md#print-1) | 打印接口，传入文件进行打印，使用Promise异步回调。拉起系统打印预览界面，需要使用[print](arkts-basicservices-print-f.md#print)接口，传入context。 |
| [print](arkts-basicservices-print-f.md#print-2) | 打印接口，传入文件进行打印，使用callback异步回调。 |
| [print](arkts-basicservices-print-f.md#print-3) | 打印接口，传入文件进行打印，使用Promise异步回调。 |
| [print](arkts-basicservices-print-f.md#print-4) | 打印接口，传入文件进行打印，三方应用需要更新打印文件，使用Promise异步回调。当前支持的文件类型：".pdf"。 |
| [registerWatermarkCallback](arkts-basicservices-print-registerwatermarkcallback-f.md#registerwatermarkcallback) | 注册强制水印处理的监听事件。 |
| [removePrinterFromDiscovery](arkts-basicservices-print-removeprinterfromdiscovery-f.md#removeprinterfromdiscovery) | 从系统打印机发现列表里移除打印机，使用Promise异步回调。 |
| [startPrint](arkts-basicservices-print-startprint-f.md#startprint) | 打印接口，传入文件或者二进制数据进行打印，使用Promise异步回调。 |
| [unregisterWatermarkCallback](arkts-basicservices-print-unregisterwatermarkcallback-f.md#unregisterwatermarkcallback) | 注销强制水印处理的监听事件。 |
| [updatePrinterInDiscovery](arkts-basicservices-print-updateprinterindiscovery-f.md#updateprinterindiscovery) | 更新打印机能力到系统打印机发现列表，使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addPrinterToCups](arkts-basicservices-print-addprintertocups-f-sys.md#addprintertocups) | 添加打印机到cups，使用Promise异步回调。 |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addprinters) | 添加打印机，使用callback异步回调。 |
| [addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addprinters-1) | 添加打印机，使用Promise异步回调。 |
| [analyzePrintEvents](arkts-basicservices-print-analyzeprintevents-f-sys.md#analyzeprintevents) | 分析打印事件。 |
| [authPrintJob](arkts-basicservices-print-authprintjob-f-sys.md#authprintjob) | 验证打印作业。 |
| [authSmbDeviceAsRegisteredUser](arkts-basicservices-print-authsmbdeviceasregistereduser-f-sys.md#authsmbdeviceasregistereduser) | 以注册用户身份对SMB设备进行身份验证，并获取可用打印机。 |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelprintjob) | 取消已发送到打印机的打印任务，使用callback异步回调。 |
| [cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelprintjob-1) | 取消已发送到打印机的打印任务，使用Promise异步回调。 |
| [checkPreferencesConflicts](arkts-basicservices-print-checkpreferencesconflicts-f-sys.md#checkpreferencesconflicts) | 检查首选项冲突。 |
| [connectPrinter](arkts-basicservices-print-connectprinter-f-sys.md#connectprinter) | 通过打印机ID连接打印机，使用callback异步回调。 |
| [connectPrinter](arkts-basicservices-print-connectprinter-f-sys.md#connectprinter-1) | 通过打印机ID连接打印机，使用Promise异步回调。 |
| [connectPrinterByIdAndPpd](arkts-basicservices-print-connectprinterbyidandppd-f-sys.md#connectprinterbyidandppd) | 根据打印机ID查询推荐的打印机驱动程序。 |
| [connectPrinterByIpAndPpd](arkts-basicservices-print-connectprinterbyipandppd-f-sys.md#connectprinterbyipandppd) | 通过打印机IP和ppd连接打印机。 |
| [deletePrinterFromCups](arkts-basicservices-print-deleteprinterfromcups-f-sys.md#deleteprinterfromcups) | 从cups中删除打印机，使用Promise异步回调。 |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectprinter) | 断开特定打印机的连接，使用callback异步回调。 |
| [disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectprinter-1) | 断开特定打印机的连接，使用Promise异步回调。 |
| [discoverUsbPrinters](arkts-basicservices-print-discoverusbprinters-f-sys.md#discoverusbprinters) | 发现usb打印机，使用Promise异步回调。 |
| [getPrinterDefaultPreferences](arkts-basicservices-print-getprinterdefaultpreferences-f-sys.md#getprinterdefaultpreferences) | 按打印机ID获取默认首选项。 |
| [getPrinterInfoById](arkts-basicservices-print-getprinterinfobyid-f-sys.md#getprinterinfobyid) | 根据打印机id获取打印机信息，使用Promise异步回调。 |
| [getSharedHosts](arkts-basicservices-print-getsharedhosts-f-sys.md#getsharedhosts) | 获取所有可用的共享主机。 |
| [notifyPrintService](arkts-basicservices-print-notifyprintservice-f-sys.md#notifyprintservice) | 将spooler关闭信息通知打印服务，使用callback异步回调。 |
| [notifyPrintService](arkts-basicservices-print-notifyprintservice-f-sys.md#notifyprintservice-1) | 将spooler关闭信息通知打印服务，使用Promise异步回调。 |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyprintserviceevent) | 将打印应用相关事件通知打印服务，使用Promise异步回调。 |
| [notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyprintserviceevent-1) | 将打印应用相关事件通知打印服务，使用Promise异步回调。 |
| [off](arkts-basicservices-print-off-f-sys.md#off) | 取消注册打印机状态变化事件回调，使用callback回调。 |
| [off](arkts-basicservices-print-off-f-sys.md#off-1) | 取消注册打印任务状态变化事件回调，使用callback回调。 |
| [off](arkts-basicservices-print-off-f-sys.md#off-2) | 取消注册打印扩展信息变化事件回调，使用callback回调。 |
| [offPrinterInfoQuery](arkts-basicservices-print-offprinterinfoquery-f-sys.md#offprinterinfoquery) | 查询到的打印机信息的Unregister事件回调。 |
| [on](arkts-basicservices-print-on-f-sys.md#on) | 注册打印机状态变化事件回调，使用callback回调。 |
| [on](arkts-basicservices-print-on-f-sys.md#on-1) | 注册打印任务状态变化事件回调，使用callback回调。 |
| [on](arkts-basicservices-print-on-f-sys.md#on-2) | 注册打印扩展信息变化事件回调，使用callback回调。 |
| [onPrinterInfoQuery](arkts-basicservices-print-onprinterinfoquery-f-sys.md#onprinterinfoquery) | 为查询到的打印机信息注册事件回调。 |
| [queryAllActivePrintJobs](arkts-basicservices-print-queryallactiveprintjobs-f-sys.md#queryallactiveprintjobs) | 查询所有活跃中的打印任务，使用Promise进行异步回调。 |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryallprintjobs) | 查询所有打印任务，使用callback异步回调。 |
| [queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryallprintjobs-1) | 查询所有打印任务，使用Promise异步回调。 |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryallprinterextensioninfos) | 查询所有已安装的打印机扩展服务，使用callback异步回调。 |
| [queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryallprinterextensioninfos-1) | 查询所有已安装的打印机扩展服务，使用Promise异步回调。 |
| [queryAllPrinterPpds](arkts-basicservices-print-queryallprinterppds-f-sys.md#queryallprinterppds) | 查询所有打印机ppd。 |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryprintjobbyid) | 按打印任务ID查询打印任务，使用callback异步回调。 |
| [queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryprintjobbyid-1) | 按打印任务ID查询打印任务，使用Promise异步回调。 |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryprintjoblist) | 查询所有打印任务，使用callback异步回调。 |
| [queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryprintjoblist-1) | 查询所有打印任务，使用Promise异步回调。 |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryprintercapability) | 查询打印机能力，使用callback异步回调。 |
| [queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryprintercapability-1) | 查询打印机能力，使用Promise异步回调。 |
| [queryPrinterCapabilityByUri](arkts-basicservices-print-queryprintercapabilitybyuri-f-sys.md#queryprintercapabilitybyuri) | 使用打印机的uri查询打印机能力，使用Promise异步回调。 |
| [queryPrinterInfoByIp](arkts-basicservices-print-queryprinterinfobyip-f-sys.md#queryprinterinfobyip) | 根据ip查询打印机信息。 |
| [queryRecommendDriversById](arkts-basicservices-print-queryrecommenddriversbyid-f-sys.md#queryrecommenddriversbyid) | 根据打印机ID查询推荐的打印机驱动程序。 |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removeprinters) | 移除打印机，使用callback异步回调。 |
| [removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removeprinters-1) | 移除打印机，使用Promise异步回调。 |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestprintpreview) | 请求预览打印数据，使用callback回调。 |
| [requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestprintpreview-1) | 请求预览打印数据，使用Promise异步回调。 |
| [restartPrintJob](arkts-basicservices-print-restartprintjob-f-sys.md#restartprintjob) | 重新打印之前打印过的打印任务，使用Promise异步回调。 |
| [savePdfFileJob](arkts-basicservices-print-savepdffilejob-f-sys.md#savepdffilejob) | 保存打印作业的pdf文件。 |
| [setDefaultPrinter](arkts-basicservices-print-setdefaultprinter-f-sys.md#setdefaultprinter) | 设置默认打印机，使用Promise异步回调。 |
| [setPrinterPreferences](arkts-basicservices-print-setprinterpreferences-f-sys.md#setprinterpreferences) | 设置打印机首选项，使用Promise异步回调。 |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f-sys.md#startdiscoverprinter) | 通过指定“打印扩展能力列表”来发现打印机，发现的打印机具备包含指定的打印扩展能力。如果指定空的打印扩展能力列表，则表示加载所有扩展能力。使用callback异步回调。 |
| [startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f-sys.md#startdiscoverprinter-1) | 通过指定“打印扩展能力列表”来发现打印机，发现的打印机具备包含指定的打印扩展能力。如果指定空的打印扩展能力列表，则表示加载所有扩展能力，使用Promise异步回调。 |
| [startGettingPrintFile](arkts-basicservices-print-startgettingprintfile-f-sys.md#startgettingprintfile) | 开始获取打印文件，使用Callback异步回调。 |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startprintjob) | 开始打印任务，使用callback异步回调。 |
| [startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startprintjob-1) | 开始打印任务，使用Promise异步回调。 |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f-sys.md#stopdiscoverprinter) | 停止发现打印机，使用callback异步回调。 |
| [stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f-sys.md#stopdiscoverprinter-1) | 停止发现打印机，使用Promise异步回调。 |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateextensioninfo) | 更新打印扩展状态，使用callback异步回调。 |
| [updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateextensioninfo-1) | 更新打印扩展状态，使用Promise异步回调。 |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f-sys.md#updateprintjobstate) | 更新打印任务状态，使用callback异步回调。 |
| [updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f-sys.md#updateprintjobstate-1) | 更新打印任务状态，使用Promise异步回调。 |
| [updatePrinterInformation](arkts-basicservices-print-updateprinterinformation-f-sys.md#updateprinterinformation) | 更新系统中打印机的部分信息，使用Promise异步回调。当前仅允许更新[PrinterInformation](arkts-basicservices-print-printerinformation-i.md)的alias和options字段。 |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updateprinterstate) | 更新打印机状态，使用callback异步回调。 |
| [updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updateprinterstate-1) | 更新打印机状态，使用Promise异步回调。 |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updateprinters) | 更新特定打印机的信息，使用callback异步回调。 |
| [updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updateprinters-1) | 更新特定打印机的信息，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PpdInfo](arkts-basicservices-print-ppdinfo-i.md) | 定义打印机所使用驱动的PPD文件信息的接口。 |
| [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | 定义打印参数的接口。 |
| [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) | 第三方应用程序实现此接口来渲染要打印的文件。 |
| [PrintJobData](arkts-basicservices-print-printjobdata-i.md) | 定义打印任务的接口。 |
| [PrintPageRange](arkts-basicservices-print-printpagerange-i.md) | 定义打印范围的接口。 |
| [PrintPageSize](arkts-basicservices-print-printpagesize-i.md) | 定义打印页面尺寸的接口。 |
| [PrintTask](arkts-basicservices-print-printtask-i.md) | 打印任务完成后的事件监听回调接口类。 |
| [PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md) | 定义打印机能力的接口。 |
| [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | 定义打印机信息的接口。 |
| [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md) | 定义打印机首选项的接口。 |
| [SharedHost](arkts-basicservices-print-sharedhost-i.md) | 定义共享设备信息的接口。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PreviewAttribute](arkts-basicservices-print-previewattribute-i-sys.md) | 定义打印预览属性的接口。 |
| [PrintJob](arkts-basicservices-print-printjob-i-sys.md) | 定义打印任务的接口。 |
| [PrintMargin](arkts-basicservices-print-printmargin-i-sys.md) | 定义打印页边距的接口。 |
| [PrintResolution](arkts-basicservices-print-printresolution-i-sys.md) | 定义打印分辨率的接口。 |
| [PrinterCapability](arkts-basicservices-print-printercapability-i-sys.md) | 定义打印能力的接口。 |
| [PrinterExtensionInfo](arkts-basicservices-print-printerextensioninfo-i-sys.md) | 定义打印扩展信息的接口。 |
| [PrinterInfo](arkts-basicservices-print-printerinfo-i-sys.md) | 定义打印信息的接口。 |
| [PrinterRange](arkts-basicservices-print-printerrange-i-sys.md) | 定义打印范围的接口。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | 打印应用事件的枚举。 |
| [DefaultPrinterType](arkts-basicservices-print-defaultprintertype-e.md) | 默认打印类型的枚举。 |
| [DocFlavor](arkts-basicservices-print-docflavor-e.md) | 打印数据来源形式的枚举。 |
| [PrintColorMode](arkts-basicservices-print-printcolormode-e.md) | 打印色彩模式的枚举。 |
| [PrintDirectionMode](arkts-basicservices-print-printdirectionmode-e.md) | 打印纸张方向的枚举。 |
| [PrintDocumentAdapterState](arkts-basicservices-print-printdocumentadapterstate-e.md) | 打印任务状态的枚举。 |
| [PrintDocumentFormat](arkts-basicservices-print-printdocumentformat-e.md) | 打印数据格式的枚举。 |
| [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md) | 打印单双面模式的枚举。 |
| [PrintErrorCode](arkts-basicservices-print-printerrorcode-e.md) | 打印错误代码的枚举。 |
| [PrintFileCreationState](arkts-basicservices-print-printfilecreationstate-e.md) | 打印文件创建状态的枚举。 |
| [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | 打印任务状态的枚举。 |
| [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | 打印任务子状态的枚举。 |
| [PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md) | 打印方向的枚举。 |
| [PrintPageType](arkts-basicservices-print-printpagetype-e.md) | 打印纸张类型的枚举。 |
| [PrintQuality](arkts-basicservices-print-printquality-e.md) | 打印质量的枚举。 |
| [PrinterEvent](arkts-basicservices-print-printerevent-e.md) | 打印机相关事件的枚举。 |
| [PrinterState](arkts-basicservices-print-printerstate-e.md) | 打印机状态的枚举。 |
| [PrinterStatus](arkts-basicservices-print-printerstatus-e.md) | 打印机状态的枚举。 |
| [WatermarkHandleResult](arkts-basicservices-print-watermarkhandleresult-e.md) | 强制水印处理结果的枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PrinterChangeCallback](arkts-basicservices-print-printerchangecallback-t.md) | 将打印机事件和打印机信息作为参数的回调方法。 |
| [WatermarkCallback](arkts-basicservices-print-watermarkcallback-t.md) | 定义用来注册强制水印处理的监听事件时使用的回调类型。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PrinterInfoQueryCallback](arkts-basicservices-print-printerinfoquerycallback-t-sys.md) | 定义注册监听printInfoQuery事件的回调类型。printInfo的值表示打印机信息。ppdInfo的值表示所有打印机的ppd信息。 |
<!--DelEnd-->

