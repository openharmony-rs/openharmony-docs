# @ohos.print

该模块为基本打印的操作API，提供调用基础打印功能的接口。

**起始版本：** 10

**系统能力：** SystemCapability.Print.PrintFramework

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addPrinter](arkts-basicservices-print-addprinter-f.md#addPrinter-1) | 添加打印机到系统中，使用Promise异步回调。<br/> |
| <!--DelRow-->[addPrinterToCups](arkts-basicservices-print-addprintertocups-f-sys.md#addPrinterToCups-1) | 添加打印机到cups，使用Promise异步回调。<br/> |
| [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md#addPrinterToDiscovery-1) | 添加打印机到系统打印机发现列表，使用Promise异步回调。<br/> |
| <!--DelRow-->[addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addPrinters-1) | 添加打印机，使用callback异步回调。<br/> |
| <!--DelRow-->[addPrinters](arkts-basicservices-print-addprinters-f-sys.md#addPrinters-2) | 添加打印机，使用Promise异步回调。<br/> |
| <!--DelRow-->[analyzePrintEvents](arkts-basicservices-print-analyzeprintevents-f-sys.md#analyzePrintEvents-1) | 分析打印事件。<br/> |
| <!--DelRow-->[authPrintJob](arkts-basicservices-print-authprintjob-f-sys.md#authPrintJob-1) | 验证打印作业。<br/> |
| <!--DelRow-->[authSmbDeviceAsRegisteredUser](arkts-basicservices-print-authsmbdeviceasregistereduser-f-sys.md#authSmbDeviceAsRegisteredUser-1) | 以注册用户身份对SMB设备进行身份验证，并获取可用打印机。<br/> |
| <!--DelRow-->[cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelPrintJob-1) | 取消已发送到打印机的打印任务，使用callback异步回调。<br/> |
| <!--DelRow-->[cancelPrintJob](arkts-basicservices-print-cancelprintjob-f-sys.md#cancelPrintJob-2) | 取消已发送到打印机的打印任务，使用Promise异步回调。<br/> |
| <!--DelRow-->[checkPreferencesConflicts](arkts-basicservices-print-checkpreferencesconflicts-f-sys.md#checkPreferencesConflicts-1) | 检查首选项冲突。<br/> |
| <!--DelRow-->[connectPrinter](arkts-basicservices-print-connectprinter-f-sys.md#connectPrinter-1) | 通过打印机ID连接打印机，使用callback异步回调。<br/> |
| <!--DelRow-->[connectPrinter](arkts-basicservices-print-connectprinter-f-sys.md#connectPrinter-2) | 通过打印机ID连接打印机，使用Promise异步回调。<br/> |
| <!--DelRow-->[connectPrinterByIdAndPpd](arkts-basicservices-print-connectprinterbyidandppd-f-sys.md#connectPrinterByIdAndPpd-1) | 根据打印机ID查询推荐的打印机驱动程序。<br/> |
| <!--DelRow-->[connectPrinterByIpAndPpd](arkts-basicservices-print-connectprinterbyipandppd-f-sys.md#connectPrinterByIpAndPpd-1) | 通过打印机IP和ppd连接打印机。<br/> |
| <!--DelRow-->[deletePrinterFromCups](arkts-basicservices-print-deleteprinterfromcups-f-sys.md#deletePrinterFromCups-1) | 从cups中删除打印机，使用Promise异步回调。<br/> |
| <!--DelRow-->[disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectPrinter-1) | 断开特定打印机的连接，使用callback异步回调。<br/> |
| <!--DelRow-->[disconnectPrinter](arkts-basicservices-print-disconnectprinter-f-sys.md#disconnectPrinter-2) | 断开特定打印机的连接，使用Promise异步回调。<br/> |
| <!--DelRow-->[discoverUsbPrinters](arkts-basicservices-print-discoverusbprinters-f-sys.md#discoverUsbPrinters-1) | 发现usb打印机，使用Promise异步回调。<br/> |
| [getAddedPrinters](arkts-basicservices-print-getaddedprinters-f.md#getAddedPrinters-1) | 获取系统中已添加的打印机列表，使用Promise异步回调。<br/> |
| <!--DelRow-->[getPrinterDefaultPreferences](arkts-basicservices-print-getprinterdefaultpreferences-f-sys.md#getPrinterDefaultPreferences-1) | 按打印机ID获取默认首选项。<br/> |
| <!--DelRow-->[getPrinterInfoById](arkts-basicservices-print-getprinterinfobyid-f-sys.md#getPrinterInfoById-1) | 根据打印机id获取打印机信息，使用Promise异步回调。<br/> |
| [getPrinterInformationById](arkts-basicservices-print-getprinterinformationbyid-f.md#getPrinterInformationById-1) | 根据打印机id获取打印机信息，使用Promise异步回调。<br/> |
| <!--DelRow-->[getSharedHosts](arkts-basicservices-print-getsharedhosts-f-sys.md#getSharedHosts-1) | 获取所有可用的共享主机。<br/> |
| <!--DelRow-->[notifyPrintService](arkts-basicservices-print-notifyprintservice-f-sys.md#notifyPrintService-1) | 将spooler关闭信息通知打印服务，使用callback异步回调。<br/> |
| <!--DelRow-->[notifyPrintService](arkts-basicservices-print-notifyprintservice-f-sys.md#notifyPrintService-2) | 将spooler关闭信息通知打印服务，使用Promise异步回调。<br/> |
| <!--DelRow-->[notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyPrintServiceEvent-1) | 将打印应用相关事件通知打印服务，使用Promise异步回调。<br/> |
| <!--DelRow-->[notifyPrintServiceEvent](arkts-basicservices-print-notifyprintserviceevent-f-sys.md#notifyPrintServiceEvent-2) | 将打印应用相关事件通知打印服务，使用Promise异步回调。<br/> |
| [notifyWatermarkComplete](arkts-basicservices-print-notifywatermarkcomplete-f.md#notifyWatermarkComplete-1) | 通知水印处理完成。<br/> |
| <!--DelRow-->[off](arkts-basicservices-print-off-f-sys.md#off-1) | 取消注册打印机状态变化事件回调，使用callback回调。<br/> |
| <!--DelRow-->[off](arkts-basicservices-print-off-f-sys.md#off-2) | 取消注册打印任务状态变化事件回调，使用callback回调。<br/> |
| <!--DelRow-->[off](arkts-basicservices-print-off-f-sys.md#off-3) | 取消注册打印扩展信息变化事件回调，使用callback回调。<br/> |
| [off](arkts-basicservices-print-off-f.md#off-4) | 取消注册打印机变动事件回调，使用callback回调。<br/> |
| <!--DelRow-->[offPrinterInfoQuery](arkts-basicservices-print-offprinterinfoquery-f-sys.md#offPrinterInfoQuery-1) | 查询到的打印机信息的Unregister事件回调。<br/> |
| <!--DelRow-->[on](arkts-basicservices-print-on-f-sys.md#on-1) | 注册打印机状态变化事件回调，使用callback回调。<br/> |
| <!--DelRow-->[on](arkts-basicservices-print-on-f-sys.md#on-2) | 注册打印任务状态变化事件回调，使用callback回调。<br/> |
| <!--DelRow-->[on](arkts-basicservices-print-on-f-sys.md#on-3) | 注册打印扩展信息变化事件回调，使用callback回调。<br/> |
| [on](arkts-basicservices-print-on-f.md#on-4) | 注册打印机变动事件回调，使用callback回调。<br/> |
| <!--DelRow-->[onPrinterInfoQuery](arkts-basicservices-print-onprinterinfoquery-f-sys.md#onPrinterInfoQuery-1) | 为查询到的打印机信息注册事件回调。<br/> |
| [print](arkts-basicservices-print-f.md#print-1) | 打印接口，传入文件进行打印，使用callback异步回调。拉起系统打印预览界面，需要使用[print](print.print(files: Array&lt;string&gt;, context: Context))接口，传入<br/>context。<br/> |
| [print](arkts-basicservices-print-f.md#print-2) | 打印接口，传入文件进行打印，使用Promise异步回调。拉起系统打印预览界面，需要使用[print](print.print(files: Array&lt;string&gt;, context: Context))接口，传入<br/>context。<br/> |
| [print](arkts-basicservices-print-f.md#print-3) | 打印接口，传入文件进行打印，使用callback异步回调。<br/> |
| [print](arkts-basicservices-print-f.md#print-4) | 打印接口，传入文件进行打印，使用Promise异步回调。<br/> |
| [print](arkts-basicservices-print-f.md#print-5) | 打印接口，传入文件进行打印，三方应用需要更新打印文件，使用Promise异步回调。当前支持的文件类型：".pdf"。<br/> |
| <!--DelRow-->[queryAllActivePrintJobs](arkts-basicservices-print-queryallactiveprintjobs-f-sys.md#queryAllActivePrintJobs-1) | 查询所有活跃中的打印任务，使用Promise进行异步回调。<br/> |
| <!--DelRow-->[queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryAllPrintJobs-1) | 查询所有打印任务，使用callback异步回调。<br/> |
| <!--DelRow-->[queryAllPrintJobs](arkts-basicservices-print-queryallprintjobs-f-sys.md#queryAllPrintJobs-2) | 查询所有打印任务，使用Promise异步回调。<br/> |
| <!--DelRow-->[queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryAllPrinterExtensionInfos-1) | 查询所有已安装的打印机扩展服务，使用callback异步回调。<br/> |
| <!--DelRow-->[queryAllPrinterExtensionInfos](arkts-basicservices-print-queryallprinterextensioninfos-f-sys.md#queryAllPrinterExtensionInfos-2) | 查询所有已安装的打印机扩展服务，使用Promise异步回调。<br/> |
| <!--DelRow-->[queryAllPrinterPpds](arkts-basicservices-print-queryallprinterppds-f-sys.md#queryAllPrinterPpds-1) | 查询所有打印机ppd。<br/> |
| <!--DelRow-->[queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryPrintJobById-1) | 按打印任务ID查询打印任务，使用callback异步回调。<br/> |
| <!--DelRow-->[queryPrintJobById](arkts-basicservices-print-queryprintjobbyid-f-sys.md#queryPrintJobById-2) | 按打印任务ID查询打印任务，使用Promise异步回调。<br/> |
| <!--DelRow-->[queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryPrintJobList-1) | 查询所有打印任务，使用callback异步回调。<br/> |
| <!--DelRow-->[queryPrintJobList](arkts-basicservices-print-queryprintjoblist-f-sys.md#queryPrintJobList-2) | 查询所有打印任务，使用Promise异步回调。<br/> |
| <!--DelRow-->[queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryPrinterCapability-1) | 查询打印机能力，使用callback异步回调。<br/> |
| <!--DelRow-->[queryPrinterCapability](arkts-basicservices-print-queryprintercapability-f-sys.md#queryPrinterCapability-2) | 查询打印机能力，使用Promise异步回调。<br/> |
| <!--DelRow-->[queryPrinterCapabilityByUri](arkts-basicservices-print-queryprintercapabilitybyuri-f-sys.md#queryPrinterCapabilityByUri-1) | 使用打印机的uri查询打印机能力，使用Promise异步回调。<br/> |
| <!--DelRow-->[queryPrinterInfoByIp](arkts-basicservices-print-queryprinterinfobyip-f-sys.md#queryPrinterInfoByIp-1) | 根据ip查询打印机信息。<br/> |
| <!--DelRow-->[queryRecommendDriversById](arkts-basicservices-print-queryrecommenddriversbyid-f-sys.md#queryRecommendDriversById-1) | 根据打印机ID查询推荐的打印机驱动程序。<br/> |
| [registerWatermarkCallback](arkts-basicservices-print-registerwatermarkcallback-f.md#registerWatermarkCallback-1) | 注册强制水印处理的监听事件。<br/> |
| [removePrinterFromDiscovery](arkts-basicservices-print-removeprinterfromdiscovery-f.md#removePrinterFromDiscovery-1) | 从系统打印机发现列表里移除打印机，使用Promise异步回调。<br/> |
| <!--DelRow-->[removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removePrinters-1) | 移除打印机，使用callback异步回调。<br/> |
| <!--DelRow-->[removePrinters](arkts-basicservices-print-removeprinters-f-sys.md#removePrinters-2) | 移除打印机，使用Promise异步回调。<br/> |
| <!--DelRow-->[requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestPrintPreview-1) | 请求预览打印数据，使用callback回调。<br/> |
| <!--DelRow-->[requestPrintPreview](arkts-basicservices-print-requestprintpreview-f-sys.md#requestPrintPreview-2) | 请求预览打印数据，使用Promise异步回调。<br/> |
| <!--DelRow-->[restartPrintJob](arkts-basicservices-print-restartprintjob-f-sys.md#restartPrintJob-1) | 重新打印之前打印过的打印任务，使用Promise异步回调。<br/> |
| <!--DelRow-->[savePdfFileJob](arkts-basicservices-print-savepdffilejob-f-sys.md#savePdfFileJob-1) | 保存打印作业的pdf文件。<br/> |
| <!--DelRow-->[setDefaultPrinter](arkts-basicservices-print-setdefaultprinter-f-sys.md#setDefaultPrinter-1) | 设置默认打印机，使用Promise异步回调。<br/> |
| <!--DelRow-->[setPrinterPreferences](arkts-basicservices-print-setprinterpreferences-f-sys.md#setPrinterPreferences-1) | 设置打印机首选项，使用Promise异步回调。<br/> |
| <!--DelRow-->[startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f-sys.md#startDiscoverPrinter-1) | 通过指定“打印扩展能力列表”来发现打印机，发现的打印机具备包含指定的打印扩展能力。如果指定空的打印扩展能力列表，则表示加载所有扩展能力。使用callback异步回调。<br/> |
| <!--DelRow-->[startDiscoverPrinter](arkts-basicservices-print-startdiscoverprinter-f-sys.md#startDiscoverPrinter-2) | 通过指定“打印扩展能力列表”来发现打印机，发现的打印机具备包含指定的打印扩展能力。如果指定空的打印扩展能力列表，则表示加载所有扩展能力，使用Promise异步回调。<br/> |
| <!--DelRow-->[startGettingPrintFile](arkts-basicservices-print-startgettingprintfile-f-sys.md#startGettingPrintFile-1) | 开始获取打印文件，使用Callback异步回调。<br/> |
| [startPrint](arkts-basicservices-print-startprint-f.md#startPrint-1) | 打印接口，传入文件或者二进制数据进行打印，使用Promise异步回调。<br/> |
| <!--DelRow-->[startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startPrintJob-1) | 开始打印任务，使用callback异步回调。<br/> |
| <!--DelRow-->[startPrintJob](arkts-basicservices-print-startprintjob-f-sys.md#startPrintJob-2) | 开始打印任务，使用Promise异步回调。<br/> |
| <!--DelRow-->[stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f-sys.md#stopDiscoverPrinter-1) | 停止发现打印机，使用callback异步回调。<br/> |
| <!--DelRow-->[stopDiscoverPrinter](arkts-basicservices-print-stopdiscoverprinter-f-sys.md#stopDiscoverPrinter-2) | 停止发现打印机，使用Promise异步回调。<br/> |
| [unregisterWatermarkCallback](arkts-basicservices-print-unregisterwatermarkcallback-f.md#unregisterWatermarkCallback-1) | 注销强制水印处理的监听事件。<br/> |
| <!--DelRow-->[updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateExtensionInfo-1) | 更新打印扩展状态，使用callback异步回调。<br/> |
| <!--DelRow-->[updateExtensionInfo](arkts-basicservices-print-updateextensioninfo-f-sys.md#updateExtensionInfo-2) | 更新打印扩展状态，使用Promise异步回调。<br/> |
| <!--DelRow-->[updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f-sys.md#updatePrintJobState-1) | 更新打印任务状态，使用callback异步回调。<br/> |
| <!--DelRow-->[updatePrintJobState](arkts-basicservices-print-updateprintjobstate-f-sys.md#updatePrintJobState-2) | 更新打印任务状态，使用Promise异步回调。<br/> |
| [updatePrinterInDiscovery](arkts-basicservices-print-updateprinterindiscovery-f.md#updatePrinterInDiscovery-1) | 更新打印机能力到系统打印机发现列表，使用Promise异步回调。<br/> |
| <!--DelRow-->[updatePrinterInformation](arkts-basicservices-print-updateprinterinformation-f-sys.md#updatePrinterInformation-1) | 更新系统中打印机的部分信息，使用Promise异步回调。当前仅允许更新[PrinterInformation](arkts-basicservices-print-printerinformation-i.md#PrinterInformation)的alias和options字段。<br/> |
| <!--DelRow-->[updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updatePrinterState-1) | 更新打印机状态，使用callback异步回调。<br/> |
| <!--DelRow-->[updatePrinterState](arkts-basicservices-print-updateprinterstate-f-sys.md#updatePrinterState-2) | 更新打印机状态，使用Promise异步回调。<br/> |
| <!--DelRow-->[updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updatePrinters-1) | 更新特定打印机的信息，使用callback异步回调。<br/> |
| <!--DelRow-->[updatePrinters](arkts-basicservices-print-updateprinters-f-sys.md#updatePrinters-2) | 更新特定打印机的信息，使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PpdInfo](arkts-basicservices-print-ppdinfo-i.md) | 定义打印机所使用驱动的PPD文件信息的接口。<br/> |
| <!--DelRow-->[PreviewAttribute](arkts-basicservices-print-previewattribute-i-sys.md) | 定义打印预览属性的接口。<br/> |
| [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | 定义打印参数的接口。<br/> |
| [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) | 第三方应用程序实现此接口来渲染要打印的文件。<br/> |
| <!--DelRow-->[PrintJob](arkts-basicservices-print-printjob-i-sys.md) | 定义打印任务的接口。<br/> |
| [PrintJobData](arkts-basicservices-print-printjobdata-i.md) | 定义打印任务的接口。<br/> |
| <!--DelRow-->[PrintMargin](arkts-basicservices-print-printmargin-i-sys.md) | 定义打印页边距的接口。<br/> |
| [PrintPageRange](arkts-basicservices-print-printpagerange-i.md) | 定义打印范围的接口。<br/> |
| [PrintPageSize](arkts-basicservices-print-printpagesize-i.md) | 定义打印页面尺寸的接口。<br/> |
| <!--DelRow-->[PrintResolution](arkts-basicservices-print-printresolution-i-sys.md) | 定义打印分辨率的接口。<br/> |
| [PrintTask](arkts-basicservices-print-printtask-i.md) | 打印任务完成后的事件监听回调接口类。<br/> |
| [PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md) | 定义打印机能力的接口。<br/> |
| <!--DelRow-->[PrinterCapability](arkts-basicservices-print-printercapability-i-sys.md) | 定义打印能力的接口。<br/> |
| <!--DelRow-->[PrinterExtensionInfo](arkts-basicservices-print-printerextensioninfo-i-sys.md) | 定义打印扩展信息的接口。<br/> |
| <!--DelRow-->[PrinterInfo](arkts-basicservices-print-printerinfo-i-sys.md) | 定义打印信息的接口。<br/> |
| [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | 定义打印机信息的接口。<br/> |
| [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md) | 定义打印机首选项的接口。<br/> |
| <!--DelRow-->[PrinterRange](arkts-basicservices-print-printerrange-i-sys.md) | 定义打印范围的接口。<br/> |
| [SharedHost](arkts-basicservices-print-sharedhost-i.md) | 定义共享设备信息的接口。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | 打印应用事件的枚举。<br/> |
| [DefaultPrinterType](arkts-basicservices-print-defaultprintertype-e.md) | 默认打印类型的枚举。<br/> |
| [DocFlavor](arkts-basicservices-print-docflavor-e.md) | 打印数据来源形式的枚举。<br/> |
| [PrintColorMode](arkts-basicservices-print-printcolormode-e.md) | 打印色彩模式的枚举。<br/> |
| [PrintDirectionMode](arkts-basicservices-print-printdirectionmode-e.md) | 打印纸张方向的枚举。<br/> |
| [PrintDocumentAdapterState](arkts-basicservices-print-printdocumentadapterstate-e.md) | 打印任务状态的枚举。<br/> |
| [PrintDocumentFormat](arkts-basicservices-print-printdocumentformat-e.md) | 打印数据格式的枚举。<br/> |
| [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md) | 打印单双面模式的枚举。<br/> |
| [PrintErrorCode](arkts-basicservices-print-printerrorcode-e.md) | 打印错误代码的枚举。<br/> |
| [PrintFileCreationState](arkts-basicservices-print-printfilecreationstate-e.md) | 打印文件创建状态的枚举。<br/> |
| [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | 打印任务状态的枚举。<br/> |
| [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | 打印任务子状态的枚举。<br/> |
| [PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md) | 打印方向的枚举。<br/> |
| [PrintPageType](arkts-basicservices-print-printpagetype-e.md) | 打印纸张类型的枚举。<br/> |
| [PrintQuality](arkts-basicservices-print-printquality-e.md) | 打印质量的枚举。<br/> |
| [PrinterEvent](arkts-basicservices-print-printerevent-e.md) | 打印机相关事件的枚举。<br/> |
| [PrinterState](arkts-basicservices-print-printerstate-e.md) | 打印机状态的枚举。<br/> |
| [PrinterStatus](arkts-basicservices-print-printerstatus-e.md) | 打印机状态的枚举。<br/> |
| [WatermarkHandleResult](arkts-basicservices-print-watermarkhandleresult-e.md) | 强制水印处理结果的枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PrinterChangeCallback](arkts-basicservices-print-printerchangecallback-t.md) | 将打印机事件和打印机信息作为参数的回调方法。<br/> |
| <!--DelRow-->[PrinterInfoQueryCallback](arkts-basicservices-print-printerinfoquerycallback-t-sys.md) | 定义注册监听printInfoQuery事件的回调类型。<br/>printInfo的值表示打印机信息。<br/>ppdInfo的值表示所有打印机的ppd信息。<br/> |
| [WatermarkCallback](arkts-basicservices-print-watermarkcallback-t.md) | 定义用来注册强制水印处理的监听事件时使用的回调类型。<br/> |

