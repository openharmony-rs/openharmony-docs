# @ohos.pasteboard

本模块提供管理系统剪贴板的能力，支持系统复制、粘贴功能。系统剪贴板支持对文本、HTML、URI、Want、PixelMap等内容的操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace pasteboard--><!--Device-unnamed-declare namespace pasteboard-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createData](arkts-basicservices-pasteboard-createdata-f.md#createData) | 构建一个指定类型的剪贴板内容对象，根据传入的MIME类型和数据内容创建PasteData实例。 调用此方法后，系统将验证MIME类型有效性，封装数据内容，并返回可用于后续剪贴板操作的PasteData对象。 参数mimeType长度不能超过1024字节，value类型需与mimeType匹配。当需要将单一类型的数据（如纯文本、HTML、图片等）放入剪贴板时使用此方法。 mimeType优先使用已定义的常量类型（如MIMETYPE_TEXT_PLAIN），若需要传递自定义格式数据，可使用自定义MIME类型。 |
| [createData](arkts-basicservices-pasteboard-createdata-f.md#createData) | 构建一个包含多个类型数据的剪贴板内容对象，支持一次创建多个MIME类型的数据条目。 调用此方法后，系统将解析Record中的多个key-value对，创建多个PasteDataRecord条目，首个MIME类型作为默认类型。 非默认类型数据需通过[getData](arkts-basicservices-pasteboard-pastedatarecord-i.md#getData)接口读取。 应用需要将多种不同类型的数据(如文本、URI、HTML等)同时复制到剪贴板时，可使用此接口一次性构建包含多个MIME类型数据的剪贴板内容对象。 |
| [createHtmlData](arkts-basicservices-pasteboard-createhtmldata-f.md#createHtmlData) | 构建一个HTML剪贴板内容对象。 |
| [createHtmlTextRecord](arkts-basicservices-pasteboard-createhtmltextrecord-f.md#createHtmlTextRecord) | 创建一条HTML内容的条目。 |
| [createPlainTextData](arkts-basicservices-pasteboard-createplaintextdata-f.md#createPlainTextData) | 构建一个纯文本剪贴板内容对象。 |
| [createPlainTextRecord](arkts-basicservices-pasteboard-createplaintextrecord-f.md#createPlainTextRecord) | 创建一条纯文本内容条目。 |
| [createRecord](arkts-basicservices-pasteboard-createrecord-f.md#createRecord) | 创建一条指定类型的数据内容条目，将数据内容封装为PasteDataRecord对象。调用此方法后，系统将根据MIME类型封装数据内容，返回可添加到PasteData中的条目对象。 参数mimeType长度不能超过1024字节，value类型需与mimeType对应（如mimeType为MIMETYPE_TEXT_PLAIN，则value类型必须是string），参数不能为空。 - 创建的条目通常需要通过[addRecord](arkts-basicservices-pasteboard-pastedata-i.md#addRecord)方法添加到 [PasteData](arkts-basicservices-pasteboard-pastedata-i.md#PasteData)对象中才能生效。 - 典型使用流程：先通过[createData](arkts-basicservices-pasteboard-createdata-f.md#createData)创建PasteData对象， 再使用createRecord创建条目，最后通过addRecord添加条目。 |
| [createUriData](arkts-basicservices-pasteboard-createuridata-f.md#createUriData) | 构建一个URI剪贴板内容对象。 |
| [createUriRecord](arkts-basicservices-pasteboard-createurirecord-f.md#createUriRecord) | 创建一条URI内容的条目。 |
| [createWantData](arkts-basicservices-pasteboard-createwantdata-f.md#createWantData) | 构建一个Want剪贴板内容对象。 |
| [createWantRecord](arkts-basicservices-pasteboard-createwantrecord-f.md#createWantRecord) | 创建一条Want内容条目。 |
| [getSystemPasteboard](arkts-basicservices-pasteboard-getsystempasteboard-f.md#getSystemPasteboard) | 获取系统剪贴板对象，返回剪贴板服务的单例实例。调用此方法后，返回的系统剪贴板对象可用于访问剪贴板的读写、监听等功能。 每次调用返回同一实例，调用前剪贴板系统服务需要正常运行。在进行任何剪贴板读写操作前，都需要先调用此方法获取系统剪贴板对象。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [ProgressSignal](arkts-basicservices-pasteboard-progresssignal-c.md) | 定义进度取消的函数，在粘贴过程中可选择取消任务，且仅当进度指示选项[ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md#ProgressIndicator)设置为NONE时此参数才生效。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GetDataParams](arkts-basicservices-pasteboard-getdataparams-i.md) | 应用在使用剪贴板提供的文件拷贝能力的情况下需要的参数，包含目标路径、文件冲突选项、进度条类型等。调用本接口前，需确保无其他拷贝或粘贴操作正在进行。 |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 剪贴板内容对象。剪贴板内容包含一个或者多个内容条目（[PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md#PasteDataRecord)） 以及属性描述对象（[PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md#PasteDataProperty)）。 在调用PasteData的接口前，需要先通过[createData()](arkts-basicservices-pasteboard-createdata-f.md#createData) 或[getData()](arkts-basicservices-pasteboard-systempasteboard-i.md#getData)获取一个PasteData对象。 |
| [PasteDataProperty](arkts-basicservices-pasteboard-pastedataproperty-i.md) | 定义剪贴板中所有内容条目的属性，包含时间戳、数据类型、粘贴范围以及一些附加数据等， 该属性必须通过[setProperty](arkts-basicservices-pasteboard-pastedata-i.md#setProperty)方法，才能设置到剪贴板中。 |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | 对于剪贴板中内容记录的抽象定义，称之为条目。剪贴板内容部分由一个或者多个条目构成，例如一条文本内容、一份HTML、一个URI或者一个Want。 不支持在创建PasteDataRecord之后，修改PasteDataRecord的默认数据类型的值，应在创建PasteDataRecord时指定正确的默认数据类型的值。 如需刷新PasteDataRecord的属性值，请使用[addEntry](arkts-basicservices-pasteboard-pastedatarecord-i.md#addEntry)。 |
| [ProgressInfo](arkts-basicservices-pasteboard-progressinfo-i.md) | 定义进度上报的数据结构，且仅当进度指示选项[ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md#ProgressIndicator)设置为NONE时才会上报此信息。 |
| [SystemPasteboard](arkts-basicservices-pasteboard-systempasteboard-i.md) | 系统剪贴板对象。 在调用SystemPasteboard的接口前，需要先通过[getSystemPasteboard](arkts-basicservices-pasteboard-getsystempasteboard-f.md#getSystemPasteboard)获取系统剪贴板。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemPasteboard](arkts-basicservices-pasteboard-systempasteboard-i-sys.md) | 系统剪贴板对象。 在调用SystemPasteboard的接口前，需要先通过[getSystemPasteboard](arkts-basicservices-pasteboard-getsystempasteboard-f.md#getSystemPasteboard)获取系统剪贴板。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FileConflictOptions](arkts-basicservices-pasteboard-fileconflictoptions-e.md) | 定义文件拷贝冲突时的选项。 |
| [Pattern](arkts-basicservices-pasteboard-pattern-e.md) | 剪贴板支持检测的模式类型。 |
| [ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md) | 定义进度条指示选项，可选择是否采用系统默认进度显示。 |
| [ShareOption](arkts-basicservices-pasteboard-shareoption-e.md) | 可粘贴数据的范围类型枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ProgressListener](arkts-basicservices-pasteboard-progresslistener-t.md) | 定义进度数据变化的订阅函数，当选择不使用系统默认进度显示时，可设置该项获取粘贴过程的进度。 |
| [UpdateCallback](arkts-basicservices-pasteboard-updatecallback-t.md) | 表示剪贴板内容变更的回调。 |
| [ValueType](arkts-basicservices-pasteboard-valuetype-t.md) | 用于表示允许的数据字段类型。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_RECORD_NUM](arkts-basicservices-pasteboard-con.md#MAX_RECORD_NUM) | API version 10之前，此常量值为512，表示单个PasteData中所能包含的最大条目数为512。当剪贴板内容中添加的条目达到数量上限512后，后续的添加操作无效。 从API version 10开始，不再限制单个PasteData中所能包含的最大条目数。 单位: Numbers，该值必须是 [512, 512] 范围内的整数。 |
| [MIMETYPE_PIXELMAP](arkts-basicservices-pasteboard-con.md#MIMETYPE_PIXELMAP) | PixelMap内容的MIME类型，值为'pixelMap'。 |
| [MIMETYPE_TEXT_HTML](arkts-basicservices-pasteboard-con.md#MIMETYPE_TEXT_HTML) | HTML内容的MIME类型，值为'text/html'。 |
| [MIMETYPE_TEXT_PLAIN](arkts-basicservices-pasteboard-con.md#MIMETYPE_TEXT_PLAIN) | 纯文本内容的MIME类型，值为'text/plain'。 |
| [MIMETYPE_TEXT_URI](arkts-basicservices-pasteboard-con.md#MIMETYPE_TEXT_URI) | URI内容的MIME类型，值为'text/uri'。 |
| [MIMETYPE_TEXT_WANT](arkts-basicservices-pasteboard-con.md#MIMETYPE_TEXT_WANT) | Want内容的MIME类型，值为'text/want'。 |

