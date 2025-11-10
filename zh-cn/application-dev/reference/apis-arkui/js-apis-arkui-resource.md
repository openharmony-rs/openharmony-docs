# Resource
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

提供获取应用资源或系统资源信息的接口。应用资源及系统资源的介绍及使用方法可参考[资源分类与访问](../../quick-start/resource-categories-and-access.md)。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 

## $r

ArkTS-Dyn: $r(value: string, ...params: any[]): Resource

ArkTS-Sta: $r(value: string, ...params: RecordData[]): Resource

获取应用资源或系统资源的信息。\$r会在编译期由工具链转换为[Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9)对象。通过\$r访问应用资源或系统资源，可参考[资源分类与访问](../../quick-start/resource-categories-and-access.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                                                                                                                                                                                                                                                                                                                                                              |
| ------ | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value  | string | 是   | 资源标识符，访问格式为`belonging.type.name`。<br>belonging：表示该资源为系统资源、应用资源或HSP包资源，对应的可选值分别为sys、app或[hsp_name]。<br>type：资源类型，可选值为boolean，color，float，intarray，integer，pattern，plural，strarray，string或media。<br>name：资源名称，应用资源名称定义在工程resources目录下的json文件中，系统资源名称获取可参考[资源分类与访问](../../quick-start/resource-categories-and-access.md)。 |
| params | ArkTS-Dyn: any[]<br/>ArkTS-Sta: [RecordData](../apis-arkts/js-apis-util.md#recorddata20)[]  | 否   | 开发者传入的剩余参数。如果资源里设置了占位符，开发者在使用\$r时可通过params传入额外的参数，替换资源中的占位符。例如，一个string资源的name为"test"，value为"Hello %d"，使用该资源时需要额外传入一个数字来替换掉%d，如`Text($r('app.string.test', 100))`。默认为空数组。                                                                                                                                                                                                                                                                                                                                                                            |

**返回值：**

| 类型                              | 说明                                                       |
| --------------------------------- | ---------------------------------------------------------- |
| [Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9) | 资源相关信息，包括应用包名、应用模块名、资源id等。 |

**示例：**

```ts
@Entry
@Component
struct Page {
  build() {
    Row() {
      Column() {
        // 请开发者替换为实际的资源
        Text($r('app.string.app_name'))
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## $rawfile

$rawfile(value: string): Resource

获取工程rawfile目录下的资源信息。$rawfile会在编译期由工具链转换为[Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9)对象。通过\$rawfile访问应用资源或系统资源，可参考[资源分类与访问](../../quick-start/resource-categories-and-access.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                                                                                                                                                                                                                                                                                                                                                              |
| ------ | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value  | string | 是   | rawfile目录下的相对路径。文件名需要包含后缀，路径开头不可以"/"开头。 |

**返回值：**

| 类型                              | 说明                                                       |
| --------------------------------- | ---------------------------------------------------------- |
| [Resource](../apis-localization-kit/js-apis-resource-manager.md#resource9) | 资源相关信息，包括应用包名、应用模块名、资源id等。 |

**示例：**

```ts
// src/main/resources/rawfile目录下添加startIcon.png。

@Entry
@Component
struct Page {
  build() {
    Row() {
      Column() {
        // 请开发者替换为实际的资源
        Image($rawfile("startIcon.png"))
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
