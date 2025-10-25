# 基于标准化数据结构的控件 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 场景介绍

我们提供了部分标准化数据结构的预置卡片，当需要展示标准化数据结构数据时，可以直接引用提供的预置卡片，快捷地展示数据。

## 内容卡片控件

在需要展示内容（标题、描述、图片、应用信息）并在点击后跳转至对应来源时，可以使用内容卡片快速的展示信息。开发者只需要调用[ContentFormCard](../reference/apis-arkdata/js-apis-data-UdmfComponents.md#contentformcard)接口，传入[ContentForm](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#contentform14)数据、卡片宽高、点击事件回调函数即可获得良好的展示效果。

从API version 20开始，支持使用[内容卡片控件](../reference/apis-arkdata/js-apis-data-UdmfComponents.md)。

### 接口说明

以下为内容卡片接口介绍：

| 接口名称                                                                                    | 描述                                          | 
|-----------------------------------------------------------------------------------------|---------------------------------------------|
| ContentFormCard({contentFormData: uniformDataStruct.ContentForm, formType: FormType, formWidth?: number, formHeight?: number, handleOnClick?: Function}) | 按照固定的样式展示传入的内容卡片数据，并在点击操作时，执行回调函数，并跳转至配置的页面。 |

### 开发示例

<!-- @[components_based_on_uniform_data_structure](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/ContentForm/entry/src/main/ets/pages/Index.ets) -->