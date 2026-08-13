# Typeface

Typeface类用于表示和管理字体对象。支持的字体操作包括：获取字体族名、从字体文件或rawfile资源构造字体、结合字体属性构造新字体，以及检查字体的加粗、斜体状态等。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-class Typeface--><!--Device-drawing-class Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## getFamilyName

```TypeScript
getFamilyName(): string
```

获取字体的族名，即一套字体设计的名称。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-Typeface-getFamilyName(): string--><!--Device-Typeface-getFamilyName(): string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字体的族名，表示当前Typeface对象对应的字体设计名称。 |

## getFamilyName

```TypeScript
getFamilyName(): string | undefined
```

获取字体的族名，即一套字体设计的名称。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Typeface-getFamilyName(): string | undefined--><!--Device-Typeface-getFamilyName(): string | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字体的族名，表示当前Typeface对象对应的字体设计名称。创建失败时返回undefined。 |

## isBold

```TypeScript
isBold(): boolean
```

检查字体是否加粗。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Typeface-isBold(): boolean--><!--Device-Typeface-isBold(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前字体是否加粗。true表示字体加粗，false表示字体未加粗。 |

## isItalic

```TypeScript
isItalic(): boolean
```

检查字体是否为斜体。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Typeface-isItalic(): boolean--><!--Device-Typeface-isItalic(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前字体是否为斜体。true表示字体为斜体，false表示字体非斜体。 |

## makeFromCurrent

```TypeScript
makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface
```

基于当前字体结合字体属性构造新的字体对象。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface--><!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 是 | 字体属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回基于当前字体结合字体属性构造的字体对象（异常情况下会返回空指针）。 |

## makeFromCurrent

```TypeScript
makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface | undefined
```

基于当前字体结合字体属性构造新的字体对象。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface | undefined--><!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 是 | 字体属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回基于当前字体结合字体属性构造的字体对象（异常情况下会返回空指针）。 |

## makeFromFile

```TypeScript
static makeFromFile(filePath: string): Typeface
```

从指定字体文件构造字体。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromFile(filePath: string): Typeface--><!--Device-Typeface-static makeFromFile(filePath: string): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示字体资源存放的路径。应用沙箱路径和真实物理路径的对应关系请参考 [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从指定字体文件加载的字体对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromFile

```TypeScript
static makeFromFile(filePath: string): Typeface | undefined
```

从指定字体文件构造字体。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Typeface-static makeFromFile(filePath: string): Typeface | undefined--><!--Device-Typeface-static makeFromFile(filePath: string): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示字体资源存放的路径。应用沙箱路径和真实物理路径的对应关系请参考 [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从指定字体文件加载的字体对象。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromFileWithArguments

```TypeScript
static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface
```

根据字体文件路径和字体属性构造新的字体。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface--><!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示字体资源存放的路径。应用沙箱路径和真实物理路径的对应关系请参考 [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系)。 |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 是 | 字体属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从指定字体文件加载并结合字体属性构造的字体对象（异常情况下会返回空指针）。 |

## makeFromFileWithArguments

```TypeScript
static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface | undefined
```

根据字体文件路径和字体属性构造新的字体。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface | undefined--><!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示字体资源存放的路径。应用沙箱路径和真实物理路径的对应关系请参考 [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系)。 |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 是 | 字体属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从指定字体文件加载并结合字体属性构造的字体对象（异常情况下会返回空指针）。 |

## makeFromRawFile

```TypeScript
static makeFromRawFile(rawfile: Resource): Typeface
```

使用指定的字体文件构造字体，该字体文件需保存在应用资源文件夹的rawfile路径下。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface--><!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 指定字体文件对应的资源对象。当前只支持``\\$rawfile``格式引用的资源对象，对应格式写为``\\$rawfile('filePath')``，其中filePath为 指定字体文件相对于工程中resources/rawfile目录的相对路径。如将字体文件直接存放在resources/rawfile目录下，则引用格式应写为：``\\$rawfile(' HarmonyOS_Sans_Bold.ttf')``；也可以创建子目录，将字体文件存放在resources/rawfile/ttf下，则引用格式应写为：``\\$rawfile('ttf/ HarmonyOS_Sans_Bold.ttf')``。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从rawfile资源加载的字体对象（异常情况下会返回空指针）。 |

## makeFromRawFile

```TypeScript
static makeFromRawFile(rawfile: Resource): Typeface | undefined
```

使用指定的字体文件构造字体，该字体文件需保存在应用资源文件夹的rawfile路径下。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface | undefined--><!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 指定字体文件对应的资源对象。当前只支持``\\$rawfile``格式引用的资源对象，对应格式写为``\\$rawfile('filePath')``，其中filePath为 指定字体文件相对于工程中resources/rawfile目录的相对路径。如将字体文件直接存放在resources/rawfile目录下，则引用格式应写为：``\\$rawfile(' HarmonyOS_Sans_Bold.ttf')``；也可以创建子目录，将字体文件存放在resources/rawfile/ttf下，则引用格式应写为：``\\$rawfile('ttf/ HarmonyOS_Sans_Bold.ttf')``。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从rawfile资源加载的字体对象（异常情况下会返回空指针）。 |

## makeFromRawFileWithArguments

```TypeScript
static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface
```

使用指定的字体文件和字体属性构造新的字体，该字体文件需保存在应用资源文件夹的rawfile路径下。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface--><!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 指定字体文件对应的资源对象。当前只支持``\\$rawfile``格式引用的资源对象，传入非``\\$rawfile``格式的资源对象时返回空指针。对应格式写为``\\$ rawfile('filePath')``，其中filePath为指定字体文件相对于工程中resources/rawfile目录的相对路径。 |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 是 | 字体属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从rawfile资源加载并结合字体属性构造的字体对象（异常情况下会返回空指针）。 |

## makeFromRawFileWithArguments

```TypeScript
static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface | undefined
```

使用指定的字体文件和字体属性构造新的字体，该字体文件需保存在应用资源文件夹的rawfile路径下。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface | undefined--><!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 指定字体文件对应的资源对象。当前只支持``\\$rawfile``格式引用的资源对象，传入非``\\$rawfile``格式的资源对象时返回空指针。对应格式写为``\\$ rawfile('filePath')``，其中filePath为指定字体文件相对于工程中resources/rawfile目录的相对路径。 |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | 是 | 字体属性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | 返回从rawfile资源加载并结合字体属性构造的字体对象（异常情况下会返回空指针）。 |

