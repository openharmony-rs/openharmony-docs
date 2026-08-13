# FontDescriptor

字体描述符信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-text-interface FontDescriptor--><!--Device-text-interface FontDescriptor-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## copyright

```TypeScript
copyright?: string
```

字体版权信息，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-copyright?: string--><!--Device-FontDescriptor-copyright?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontFamily

```TypeScript
fontFamily?: string
```

字体家族，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-fontFamily?: string--><!--Device-FontDescriptor-fontFamily?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontFeatures

```TypeScript
fontFeatures?: Array<string>
```

字体支持的OpenType特性标签数组，默认为空数组。数组中每个元素为特性标签字符串（如'liga'表示标准连字、'kern'表示字距调整），表示该字体支持的字体特性。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-fontFeatures?: Array<string>--><!--Device-FontDescriptor-fontFeatures?: Array<string>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontSubfamily

```TypeScript
fontSubfamily?: string
```

子字体家族，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-fontSubfamily?: string--><!--Device-FontDescriptor-fontSubfamily?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fullName

```TypeScript
fullName?: string
```

字体名称，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-fullName?: string--><!--Device-FontDescriptor-fullName?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## index

```TypeScript
index?: int
```

字体索引，字体文件为ttc类型时有效，ttf类型统一为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-index?: int--><!--Device-FontDescriptor-index?: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## italic

```TypeScript
italic?: int
```

是否是斜体字体，0表示非斜体，1表示斜体，默认值为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-italic?: int--><!--Device-FontDescriptor-italic?: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## languages

```TypeScript
languages?: Array<string>
```

字体支持的语言列表，默认为空数组。数组中每个元素为BCP 47格式的语言标签字符串（如'en'、'zh-Hans'），表示该字体支持的书写语言。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-languages?: Array<string>--><!--Device-FontDescriptor-languages?: Array<string>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## license

```TypeScript
license?: string
```

字体许可证信息，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-license?: string--><!--Device-FontDescriptor-license?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## localFamilyName

```TypeScript
localFamilyName?: string
```

根据系统语言配置提取字体家族名称，字体文件中若无当前语言对应配置则取“en”对应信息。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-localFamilyName?: string--><!--Device-FontDescriptor-localFamilyName?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## localFullName

```TypeScript
localFullName?: string
```

根据系统语言配置提取字体全名，字体文件中若无当前语言对应配置则取“en”对应信息。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-localFullName?: string--><!--Device-FontDescriptor-localFullName?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## localPostscriptName

```TypeScript
localPostscriptName?: string
```

根据系统语言配置提取字体唯一标识，字体文件中若无当前语言对应配置则取“en”对应信息。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-localPostscriptName?: string--><!--Device-FontDescriptor-localPostscriptName?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## localSubFamilyName

```TypeScript
localSubFamilyName?: string
```

根据系统语言配置提取子字体家族名称，字体文件中若无当前语言对应配置则取“en”对应信息。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-localSubFamilyName?: string--><!--Device-FontDescriptor-localSubFamilyName?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## manufacture

```TypeScript
manufacture?: string
```

字体制造商信息，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-manufacture?: string--><!--Device-FontDescriptor-manufacture?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## monoSpace

```TypeScript
monoSpace?: boolean
```

是否是等宽字体，true表示等宽，false表示非等宽，默认值为false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-monoSpace?: boolean--><!--Device-FontDescriptor-monoSpace?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## path

```TypeScript
path?: string
```

字体绝对路径，可取遵循系统限制的任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-path?: string--><!--Device-FontDescriptor-path?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## postScriptName

```TypeScript
postScriptName?: string
```

字体唯一标识名称，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-postScriptName?: string--><!--Device-FontDescriptor-postScriptName?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## symbolic

```TypeScript
symbolic?: boolean
```

是否支持符号，true表示支持，false表示不支持，默认值为false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-symbolic?: boolean--><!--Device-FontDescriptor-symbolic?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## trademark

```TypeScript
trademark?: string
```

字体商标信息，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-trademark?: string--><!--Device-FontDescriptor-trademark?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## variationAxisRecords

```TypeScript
variationAxisRecords?: Array<FontVariationAxis>
```

字体可变轴记录数组，用于描述字体支持的可变轴信息。非可变字体此字段为undefined。

**类型：** Array&lt;[FontVariationAxis](arkts-arkgraphics2d-text-fontvariationaxis-i.md)&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-variationAxisRecords?: Array<FontVariationAxis>--><!--Device-FontDescriptor-variationAxisRecords?: Array<FontVariationAxis>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## variationInstanceRecords

```TypeScript
variationInstanceRecords?: Array<FontVariationInstance>
```

字体可变实例记录数组，用于描述字体支持的可变实例信息。非可变字体此字段为undefined。

**类型：** Array&lt;[FontVariationInstance](arkts-arkgraphics2d-text-fontvariationinstance-i.md)&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-variationInstanceRecords?: Array<FontVariationInstance>--><!--Device-FontDescriptor-variationInstanceRecords?: Array<FontVariationInstance>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## version

```TypeScript
version?: string
```

字体版本，可取任意字符串，默认为空字符串。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-version?: string--><!--Device-FontDescriptor-version?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## weight

```TypeScript
weight?: FontWeight
```

字体字重，默认值为0。

**类型：** FontWeight

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-weight?: FontWeight--><!--Device-FontDescriptor-weight?: FontWeight-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## width

```TypeScript
width?: int
```

字体宽度，取值范围1-9整数，默认值为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontDescriptor-width?: int--><!--Device-FontDescriptor-width?: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

