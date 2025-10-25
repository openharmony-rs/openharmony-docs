# 标准化数据结构 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->


## 场景介绍

针对[UTD标准化数据类型](../reference/apis-arkdata/js-apis-data-uniformTypeDescriptor.md#uniformdatatype)中的部分常见类型，为了方便业务使用，我们按照不同的数据类型提供了标准化数据结构，例如系统定义的桌面图标类型（对应的标准化数据类型标识为'openharmony.app-item'），我们明确定义了该数据结构对应的相关描述信息。

某些业务场景下应用可以直接使用我们具体定义的UTD标准化数据结构，例如跨应用拖拽场景。拖出方应用可以按照标准化数据结构将拖拽数据写入[拖拽事件](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#dragevent7)，拖入方应用从拖拽事件中读取拖拽数据并按照标准化数据结构进行数据的解析。这使得不同应用间的数据交互遵从相同的标准定义，有效减少了跨应用数据交互的开发工作量。

## 接口说明

UDMF针对部分标准化数据类型定义的标准化数据结构如下所示：

| 数据结构                                                                                                |       数据类型        | 说明   |
|-----------------------------------------------------------------------------------------------------| :-------------------: |------|
| [PlainText](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#plaintext)                  |      'general.plain-text'        | 纯文本。  |
| [Hyperlink](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#hyperlink)                  |       'general.hyperlink'       | 超链接。  |
| [HTML](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#html)                            |         'general.html'          | 富文本。  |
| [OpenHarmonyAppItem](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#openharmonyappitem) | 'openharmony.app-item'    | 图标。   |
| [ContentForm](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#contentform14)            | 'general.content-form'    | 内容卡片。 |

## 开发步骤

以使用标准化数据结构定义数据内容（包含超链接、纯文本两条数据记录）为例，提供基本的开发步骤。

数据提供方可通过UDMF提供的addRecord()接口，使用getRecords()接口获取当前数据对象内的所有数据记录。

1. 导入对应模块。

<!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/UniformDataStructure/entry/src/main/ets/pages/UdmfInterface.ets) -->

2.添加并获取数据记录

<!-- @[unified_data_structure](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/UniformDataStructure/entry/src/main/ets/pages/UdmfInterface.ets) -->
