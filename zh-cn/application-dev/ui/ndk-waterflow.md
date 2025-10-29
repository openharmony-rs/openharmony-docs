# 使用瀑布流

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangyuhao-->
<!--Designer: @zcdqs-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @HelloCrease-->

ArkUI开发框架在NDK接口提供了瀑布流容器组件，通过瀑布流自身的排列规则，将不同大小的"项目"自上而下如瀑布般紧密布局。

## 接入ArkTS页面
为了使用NDK接口构建UI界面，参考[接入ArkTS页面章节](../ui/ndk-access-the-arkts-page.md)，在ArkTS页面上创建用于Native页面挂载的占位组件，并实现ArkTS侧的NativeNode模块接口。

## 使用懒加载
### NodeAdapter介绍 
NDK中提供了NodeAdapter对象替代ArkTS侧的LazyForeach功能，用于按需生成子组件。详情请参阅[NodeAdapter介绍](../ui/ndk-loading-long-list.md#nodeadapter介绍)。

### 实现懒加载适配器

使用FlowItemAdapter类管理懒加载适配器。在类的构造函数中创建NodeAdapter对象，并给NodeAdapter对象设置事件监听器，在类的析构函数中，销毁NodeAdapter对象。

<!-- @[flow_item_adapter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKWaterFlowSample/entry/src/main/cpp/FlowItemAdapter.h) -->

## 创建分组
使用WaterflowSection类管理waterflow中的分组，其中SectionOption用于描述一个分段的各项配置信息。在类的构造函数中创建ArkUI_WaterFlowSectionOption对象，在析构函数中将其销毁。


<!-- @[worterflow_section](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKWaterFlowSample/entry/src/main/cpp/WaterflowSection.h) -->


## 创建瀑布流
使用ArkUIWaterflowNode类管理Waterflow。支持通过SetLazyAdapter为其设置一个FlowItemAdapter，通过SetSection为其设置分段。

<!-- @[waterflow_define](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKWaterFlowSample/entry/src/main/cpp/waterflow.h) -->


## 使用瀑布流
创建一个ArkUIWaterflowNode类的实例，设置其宽高，并绑定NodeAdapter和分段。

<!-- @[create_waterflow_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NDKWaterFlowSample/entry/src/main/cpp/CreateWaterflowExample.h) -->

``` C
// CreateWaterflowExample.h

#ifndef MYAPPLICATION_CREATEWATERFLOWEXAMPLE_H
#define MYAPPLICATION_CREATEWATERFLOWEXAMPLE_H
#include "waterflow.h"

namespace NativeModule {
const int UI_WIDTH = 400;
const int UI_HEIGHT = 600;
const int SECTION_COUNT = 10;
const int SECTION_2_ID = 2;

inline void SetupSections(std::shared_ptr<WaterflowSection> sections)
{
    SectionOption MARGIN_GAP_SECTION_1 = {10, 2, 10, 10, {20, 30, 40, 50}, nullptr, nullptr};
    SectionOption MARGIN_GAP_SECTION_2 = {10, 4, 10, 10, {20, 30, 40, 50}, nullptr, nullptr};
    for (int i = 0; i < SECTION_COUNT; i++) {
        sections->SetSection(sections->GetSectionOptions(), i,
                             i % SECTION_2_ID ? MARGIN_GAP_SECTION_1 : MARGIN_GAP_SECTION_2);
    }
}

inline std::shared_ptr<ArkUIWaterflowNode> CreateWaterflowExample(napi_env env)
{
    auto waterflow = std::make_shared<ArkUIWaterflowNode>();
    waterflow->SetHeight(UI_HEIGHT);
    waterflow->SetWidth(UI_WIDTH);
    waterflow->SetLazyAdapter(std::make_shared<FlowItemAdapter>());
    auto sections = std::make_shared<WaterflowSection>();
    SetupSections(sections);
    waterflow->SetSection(sections);
    return waterflow;
}
} // namespace NativeModule

#endif // MYAPPLICATION_CREATEWATERFLOWEXAMPLE_H
```


![image](figures/UIWaterflow.gif)