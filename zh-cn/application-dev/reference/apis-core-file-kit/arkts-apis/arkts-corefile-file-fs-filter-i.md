# Filter

文件过滤配置项，支持listFile接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface Filter--><!--Device-unnamed-export interface Filter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## displayName

```TypeScript
displayName?: Array<string>
```

文件名模糊匹配，各个关键词OR关系。当前仅支持通配符*。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Filter-displayName?: Array<string>--><!--Device-Filter-displayName?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## excludeMedia

```TypeScript
excludeMedia?: boolean
```

是否排除Media中已有的文件。true：排除Media中已有的文件；false：不排除Media中已有的文件。预留字段，暂不支持使用。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Filter-excludeMedia?: boolean--><!--Device-Filter-excludeMedia?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## fileSizeOver

```TypeScript
fileSizeOver?: long
```

文件大小匹配，大于指定大小的文件，单位为Byte。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Filter-fileSizeOver?: long--><!--Device-Filter-fileSizeOver?: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## lastModifiedAfter

```TypeScript
lastModifiedAfter?: double
```

文件最近修改时间匹配，在指定时间点及之后的文件。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Filter-lastModifiedAfter?: double--><!--Device-Filter-lastModifiedAfter?: double-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mimeType

```TypeScript
mimeType?: Array<string>
```

mime类型完全匹配，各个关键词OR关系。预留字段，暂不支持使用。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Filter-mimeType?: Array<string>--><!--Device-Filter-mimeType?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## suffix

```TypeScript
suffix?: Array<string>
```

文件后缀名完全匹配，各个关键词OR关系。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Filter-suffix?: Array<string>--><!--Device-Filter-suffix?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

