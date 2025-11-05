# 图像类型定义

>**说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>本模块首批接口从API version 12开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。


## ImageAnalyzerConfig

图像AI分析配置项。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| types | [ImageAnalyzerType[]](#imageanalyzertype) | 是 | 图像AI分析类型。

## ImageAnalyzerType

图像AI分析类型，未设置时默认开启主体识别和文字识别功能。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 值    | 说明           |
| -------- | ----- | -------- |
| SUBJECT | 0  | 主体识别功能。 |
| TEXT | 1  | 文字识别功能。 |
| OBJECT_LOOKUP | 2  | 对象查找功能。 |

## ImageAIOptions

图像AI分析选项。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

| 名称     | 类型                | 必填   | 说明                   |
| ------ | ----------------- | ---- | -------------------- |
| types | [ImageAnalyzerType[]](#imageanalyzertype) | 否 | 图像AI分析类型。 |
| aiController | ArkTS-Dyn: [ImageAnalyzerController](#imageanalyzercontroller)<br>ArkTS-Sta: [ImageAnalyzerController](#imageanalyzercontroller) \| [ESValue](../../../quick-start/arkts-interop-overview.md#esvalue) | 否 | 图像AI分析控制器，需要对应组件的enableAnalyzer接口（例如Image组件的[enableAnalyzer](ts-basic-components-image.md#enableanalyzer11)接口）设置为true才能生效。<br>ArkTS-Sta：目前只支持[ESValue](../../../quick-start/arkts-interop-overview.md#esvalue)类型。 |

> **说明：**
>
> 该特性中的参数types优先级高于[ImageAnalyzerConfig](#imageanalyzerconfig)中的参数types，两者同时设置时以该特性设置的值为准。
>
> 该特性依赖设备能力，且需要和对应组件的enableAnalyzer接口（例如[Image组件](ts-basic-components-image.md#enableanalyzer11)）搭配使用。

## ImageAnalyzerController

图像分析控制器。可以将此对象绑定至支持的组件，通过控制器来调用支持的方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### getImageAnalyzerSupportTypes

getImageAnalyzerSupportTypes(): ImageAnalyzerType[]

获取对应组件支持的分析类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值:**

| 类型     | 描述                      |
| ------ | ----------------------- |
| ImageAnalyzerType[] | 对应组件支持的分析类型。 |


## 示例

ArkTS-Sta中使用ESValue对象封装ArkTS-Dyn aiController实例。ESValue类型仅用于动静态互操作场景：Image组件使用静态语法，ImageAnalyzerController为动态类型创建，在静态语法上下文调用动态语法创建的实例。

- 在ArkTS-Sta主模块得到ArkTS-Dyn子模块`library`创建的ArkTS-Dyn aiController对象。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  // entry/src/main/ets/pages/Index.ets  
  import { Entry, Column, Component, Image, $r, FlexAlign, ImageAnalyzerType, ImageAIOptions } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { getController } from 'library';

  @Entry
  @Component
  struct Index {
    @State options_: ImageAIOptions | undefined = undefined;

    aboutToAppear() {
      let moduleName = ESValue.load("library/Index");
      let getControllerMapFunc = moduleName.getProperty('getController');
      let controllerDynamic = getControllerMapFunc.invoke();
      let options: ImageAIOptions = {
        types: [ImageAnalyzerType.TEXT],
        aiController: controllerDynamic
      } as ImageAIOptions;
      this.options_ = options;
    }

    build() {
      Column() {
        Image($r('app.media.imageAI_text'), this.options_)
          .width(200)
          .height(200)
          .enableAnalyzer(true)
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
  }
  ```
  
- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供getController函数，创建ArkTS-Dyn对象。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import{ visionImageAnalyzer }from '@kit.Visionkit';

  export function getController() {
    let controller = new visionImageAnalyzer.VisionImageAnalyzerController();
    return controller;
  }
  ```