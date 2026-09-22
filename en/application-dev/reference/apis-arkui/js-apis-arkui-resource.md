# Resource
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ca610c3b31eac2a84ffac21a107ce522b473feb1 translatedAt=2026-08-29T09:37:19.502Z pushedAt=2026-08-31T12:24:04.921Z -->

Provides APIs for accessing application and system resources. Resources can be accessed through **$r** and **$rawfile**, which are applicable to scenarios such as multi-language adaptation, dark/light mode switch, resolution adaptation for different devices, and loading local raw resource files. For details about resource types and usage, see [Resource Categories and Access](../../quick-start/resource-categories-and-access.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 

## $r

$r(value: string, ...params: any[]): Resource

Obtains information about application resources, system resources, or HSP resources, which is applicable to scenarios such as multi-language adaptation, dark/light mode switch, and resolution adaptation for different devices. **\$r** is converted by the toolchain into a [Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9) object during compilation. To access application resources or system resources through **\$r**, see [Resource Categories and Access](../../quick-start/resource-categories-and-access.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                                                                                                                                                                                                                                                                                                                                                             |
| ------ | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value  | string | Yes   | Resource identifier, accessed in the format of `belonging.type.name`.<br>**belonging**: resource source. The value can be **sys**, **app**, or **[hsp_name]**.<br>**type**: resource type. The value can be **boolean**, **color**, **float**, **intarray**, **integer**, **pattern**, **plural**, **strarray**, **string**, or **media**.<br>**name**: resource name. Application resource names are defined in the **resources** directory of the project. For how to obtain system resource names, see [Resource Categories and Access](../../quick-start/resource-categories-and-access.md).<br/>If the format is incorrect or the resource does not exist, the returned **Resource** object does not contain valid resource information. |
| ...params | any[]  | No   | Remaining parameters you passed, used to format the resource content. The parameters replace the placeholders in the resource string in sequence.  |

**Return value**

| Type                             | Description                                                      |
| --------------------------------- | ---------------------------------------------------------- |
| [Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9) | Resource object containing the package name, module name, resource ID, and more.|

**Example**

```ts
@Entry
@Component
struct Page {
  build() {
    Row() {
      Column() {
        Text($r('app.string.app_name'))
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

For sample code about how to access resources in an HSP, see [Cross-HAP/HSP Resources](../../quick-start/resource-categories-and-access.md#cross-haphsp-resources).

## $rawfile

$rawfile(value: string): Resource

Obtains information about resources in the **rawfile** directory of the project, which is applicable to loading raw resource files such as local audio, video, and configuration files. **$r** accesses resources through resource identifiers and supports multi-language adaptation, dark/light mode switch, and resolution adaptation for different devices. **$rawfile** accesses resources through file paths and does not support the preceding adaptation capabilities, which is applicable to scenarios where raw resource files are directly accessed. **$rawfile** is converted by the toolchain into a [Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9) object during compilation. For more information, see [Resource Categories and Access](../../quick-start/resource-categories-and-access.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                                                                                                                                                                                                                                                                                                                                                             |
| ------ | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value  | string | Yes  | Relative path in the **rawfile** directory. The file name must contain a file name extension, and the path cannot start with a slash (/).|

**Return value**

| Type                             | Description                                                      |
| --------------------------------- | ---------------------------------------------------------- |
| [Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9) | Resource object containing the package name, module name, resource ID, and more.|

```ts
// Add startIcon.png to the src/main/resources/rawfile directory.

@Entry
@Component
struct Page {
  build() {
    Row() {
      Column() {
        Image($rawfile("startIcon.png"))
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

For sample code about how to access resources in an HSP, see [Accessing Resources Across HAPs/HSPs](../../quick-start/resource-categories-and-access.md#cross-haphsp-resources).
