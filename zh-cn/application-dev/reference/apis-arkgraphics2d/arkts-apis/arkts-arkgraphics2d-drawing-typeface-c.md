# Typeface

字体，如宋体、楷体等。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-drawing-class Typeface--><!--Device-drawing-class Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## getFamilyName

```TypeScript
getFamilyName(): string
```

获取字体的族名，即一套字体设计的名称。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-Typeface-getFamilyName(): string--><!--Device-Typeface-getFamilyName(): string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字体的族名。 |

## getFamilyName

```TypeScript
getFamilyName(): string | undefined
```

Get the family name for this typeface.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Typeface-getFamilyName(): string | undefined--><!--Device-Typeface-getFamilyName(): string | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Family name. |

## isBold

```TypeScript
isBold(): boolean
```

检查字体是否加粗。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

检查字体是否是斜体。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-Typeface-isItalic(): boolean--><!--Device-Typeface-isItalic(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前字体是否是斜体。true表示字体是斜体，false表示字体不是斜体。 |

## makeFromCurrent

```TypeScript
makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface
```

基于当前字体结合字体属性构造新的字体对象。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface--><!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typefaceArguments | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | TypefaceArguments for typeface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回字体对象（异常情况下会返回空指针）。 |

## makeFromCurrent

```TypeScript
makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface | undefined
```

Generate typeface from current typeface and TypefaceArguments.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface | undefined--><!--Device-Typeface-makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typefaceArguments | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | TypefaceArguments for typeface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Typeface. |

## makeFromFile

```TypeScript
static makeFromFile(filePath: string): Typeface
```

从指定字体文件构造字体。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromFile(filePath: string): Typeface--><!--Device-Typeface-static makeFromFile(filePath: string): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示字体资源存放的路径。应用沙箱路径和真实物理路径的对应关系请参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回Typeface对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## makeFromFile

```TypeScript
static makeFromFile(filePath: string): Typeface | undefined
```

Constructs a typeface from a file.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Typeface-static makeFromFile(filePath: string): Typeface | undefined--><!--Device-Typeface-static makeFromFile(filePath: string): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | file path for typeface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Typeface. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## makeFromFileWithArguments

```TypeScript
static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface
```

根据字体文件路径和字体属性构造新的字体。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface--><!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示字体资源存放的路径。应用沙箱路径和真实物理路径的对应关系请参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| typefaceArguments | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示字体属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回字体对象（异常情况下会返回空指针）。 |

## makeFromFileWithArguments

```TypeScript
static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface | undefined
```

Generate typeface from file and TypefaceArguments.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface | undefined--><!--Device-Typeface-static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | file path for typeface. |
| typefaceArguments | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | TypefaceArguments for typeface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Typeface. |

## makeFromRawFile

```TypeScript
static makeFromRawFile(rawfile: Resource): Typeface
```

使用指定的字体文件构造字体，其中要求指定的字体文件需保存在应用资源文件夹的rawfile路径下。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface--><!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定字体文件对应的资源对象。当前只支持\_\_\_INLINE\_CODE\_USD\_0\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回Typeface对象（异常情况下会返回空指针）。 |

## makeFromRawFile

```TypeScript
static makeFromRawFile(rawfile: Resource): Typeface | undefined
```

Constructs a typeface from a file, which must be stored in the resources/rawfile directory of the application project.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface | undefined--><!--Device-Typeface-static makeFromRawFile(rawfile: Resource): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Resource object corresponding to the file.Currently, only resource objects referenced in rawfile format are supported.The corresponding format is rawfile('filePath'),where filePath is the relative path of the file to the resources/rawfile directory in the project.If the file is stored in resources/rawfile, the reference format is rawfile('HarmonyOS\_\_\_ESCAPED\_UNDERSCORE\_\_\_Sans\_\_\_ESCAPED\_UNDERSCORE\_\_\_Bold.ttf').If the file is stored in a subdirectory, for example, in resources/rawfile/ttf,the reference format is rawfile('ttf/HarmonyOS\_\_\_ESCAPED\_UNDERSCORE\_\_\_Sans\_\_\_ESCAPED\_UNDERSCORE\_\_\_Bold.ttf'). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Typeface. |

## makeFromRawFileWithArguments

```TypeScript
static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface
```

使用指定的字体文件和字体属性构造字体，其中要求指定的字体文件需保存在应用资源文件夹的rawfile路径下。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface--><!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定字体文件对应的资源对象。当前只支持\_\_\_INLINE\_CODE\_USD\_0\_\_\_，其中filePath为指定字体文件相对于工程中resources/rawfile目录的相对路径。 |
| typefaceArguments | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示字体属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回字体对象（异常情况下会返回空指针）。 |

## makeFromRawFileWithArguments

```TypeScript
static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface | undefined
```

Generate typeface from Rawfile and TypefaceArguments.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface | undefined--><!--Device-Typeface-static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | RawFile for typeface. |
| typefaceArguments | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | TypefaceArguments for typeface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Typeface. |

