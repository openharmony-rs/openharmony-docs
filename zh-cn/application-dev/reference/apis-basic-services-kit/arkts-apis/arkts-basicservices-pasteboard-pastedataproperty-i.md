# PasteDataProperty

定义剪贴板中所有内容条目的属性，包含时间戳、数据类型、粘贴范围以及一些附加数据等， 该属性必须通过[setProperty](arkts-basicservices-pasteboard-pastedata-i.md#setproperty)方法，才能设置到剪贴板中。

**起始版本：** 23

<!--Device-pasteboard-interface PasteDataProperty--><!--Device-pasteboard-interface PasteDataProperty-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## 导入模块

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## additions

```TypeScript
additions: Record<string, RecordData>
```

设置其他附加属性数据。格式为键值对。

**类型：** Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

<!--Device-PasteDataProperty-additions: Record<string, RecordData>--><!--Device-PasteDataProperty-additions: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## localOnly

```TypeScript
localOnly: boolean
```

配置剪贴板内容是否为“仅在本地”，true表示仅在本地有效，false表示允许跨设备传输。默认值为false。 其值会被shareOption属性覆盖，推荐使用[ShareOption](arkts-basicservices-pasteboard-shareoption-e.md)属性。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteDataProperty-localOnly: boolean--><!--Device-PasteDataProperty-localOnly: boolean-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## mimeTypes

```TypeScript
readonly mimeTypes: Array<string>
```

剪贴板内容条目的数据类型，非重复的类型列表。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteDataProperty-readonly mimeTypes: Array<string>--><!--Device-PasteDataProperty-readonly mimeTypes: Array<string>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## shareOption

```TypeScript
shareOption: ShareOption
```

指示剪贴板数据可以粘贴到的范围，默认值为CROSSDEVICE。与localOnly属性互斥，设置shareOption会影响localOnly的实际值。

**类型：** [ShareOption](arkts-basicservices-pasteboard-shareoption-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteDataProperty-shareOption: ShareOption--><!--Device-PasteDataProperty-shareOption: ShareOption-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## tag

```TypeScript
tag: string
```

用户自定义标签，默认为空。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteDataProperty-tag: string--><!--Device-PasteDataProperty-tag: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## timestamp

```TypeScript
readonly timestamp: long
```

剪贴板数据的写入时间戳（单位：已开机时间的ns数）。

**类型：** long

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteDataProperty-readonly timestamp: long--><!--Device-PasteDataProperty-readonly timestamp: long-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

