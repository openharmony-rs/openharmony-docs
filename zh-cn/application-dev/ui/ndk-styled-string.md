# 使用属性字符串的文本绘制与显示
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

部分框架或应用具备自研的文字排版能力，在移植时，这些能力会被对接到[方舟2D图形服务的文本引擎](../graphics/complex-text-c.md)。为了避免开发者重复开发文本组件，Text组件提供了接口[NODE_TEXT_CONTENT_WITH_STYLED_STRING](../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeattributetype)，可以直接渲染方舟文本引擎生成的文本。

以下场景基于[接入ArkTS页面章节](../ui/ndk-access-the-arkts-page.md)，阐述了如何创建字体引擎文本，并利用[Text组件](../reference/apis-arkui/capi-native-node-h.md#arkui_nodetype)进行渲染显示。

> **说明：**
>
> 涉及字体引擎的接口，需在CMakeLists.txt中添加`target_link_libraries(entry PUBLIC libnative_drawing.so)`，否则链接阶段会报错。

下图展示了 `NODE_TEXT_CONTENT_WITH_STYLED_STRING` 接口的主要使用流程。

![ndk_text_style_string_activity](figures/native_styledString_activity.png)

## 创建StyledString

创建StyledString对象时，需要传入段落样式（TypographyStyle）和字体集合（FontCollection）。段落样式定义了文本的整体布局属性，字体集合用于提供字体资源。

### 创建StyledString对象

使用[OH_ArkUI_StyledString_Create](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_create)接口创建StyledString对象，需要传入段落样式和字体集合。

``` C++
// 创建段落样式
OH_Drawing_TypographyStyle *typographyStyle = OH_Drawing_CreateTypographyStyle();
OH_Drawing_SetTypographyTextAlign(typographyStyle, OH_Drawing_TextAlign::TEXT_ALIGN_CENTER);
OH_Drawing_SetTypographyTextMaxLines(typographyStyle, 10);

// 创建StyledString对象
ArkUI_StyledString *styledString = OH_ArkUI_StyledString_Create(typographyStyle, OH_Drawing_CreateFontCollection());
```

> **说明：**
>
> `OH_Drawing_`前缀的接口由方舟字体引擎提供，参考[简单文本绘制与显示（C/C++)](../graphics/simple-text-c.md)、[复杂文本绘制与显示（C/C++）](../graphics/complex-text-c.md)。

## 设置StyledString样式

StyledString支持为文本中的不同部分设置不同的样式，包括段落样式和文本样式。

### 设置段落样式

段落样式定义了一段文字的整体属性，例如最大显示行数、文字方向、对齐方式等。

**表1** 段落样式设置接口

| 接口 | 描述 |
| ---- | ---- |
| [OH_Drawing_CreateTypographyStyle](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtypographystyle) | 创建段落样式对象。 |
| [OH_Drawing_SetTypographyTextAlign](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_settypographytextalign) | 设置文本对齐方式。 |
| [OH_Drawing_SetTypographyTextMaxLines](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_settypographytextmaxlines) | 设置文本最大行数。 |

以下代码示例设置了文字居中，最大行数限制为10。

``` C++
OH_Drawing_TypographyStyle *typographyStyle = OH_Drawing_CreateTypographyStyle();
OH_Drawing_SetTypographyTextAlign(typographyStyle, OH_Drawing_TextAlign::TEXT_ALIGN_CENTER);
OH_Drawing_SetTypographyTextMaxLines(typographyStyle, 10);
```

### 设置文本样式

不同内容的文本可以设置不同的文本样式，但必须按照以下三个接口的逻辑调用顺序进行设置，否则将无法生效。

1. [OH_ArkUI_StyledString_PushTextStyle](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_pushtextstyle)：将文字样式推入栈中。
2. [OH_ArkUI_StyledString_AddText](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_addtext)：添加要修改样式的文字内容。
3. [OH_ArkUI_StyledString_PopTextStyle](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_poptextstyle)：将文字样式弹出栈。

**表2** 文本样式设置接口

| 接口 | 描述 |
| ---- | ---- |
| [OH_Drawing_CreateTextStyle](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtextstyle) | 创建文本样式对象。 |
| [OH_Drawing_SetTextStyleFontSize](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_settextstylefontsize) | 设置字体大小。 |
| [OH_Drawing_SetTextStyleColor](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_settextstylecolor) | 设置字体颜色。 |

使用[OH_Drawing_CreateTextStyle](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtextstyle)创建文本样式。以下示例设置"Hello"字体大小28px，颜色为0xFF707070；设置"World!"字体大小为28px，颜色为0xFF2787D9。

``` C++
// 创建StyledString对象
ArkUI_StyledString *styledString = OH_ArkUI_StyledString_Create(typographyStyle, OH_Drawing_CreateFontCollection());

// 创建第一个文本样式
OH_Drawing_TextStyle *textStyle = OH_Drawing_CreateTextStyle();
OH_Drawing_SetTextStyleFontSize(textStyle, 28);
OH_Drawing_SetTextStyleColor(textStyle, OH_Drawing_ColorSetArgb(0xFF, 0x70, 0x70, 0x70));

// 设置"Hello"文本及其样式
OH_ArkUI_StyledString_PushTextStyle(styledString, textStyle);
OH_ArkUI_StyledString_AddText(styledString, "Hello");
OH_ArkUI_StyledString_PopTextStyle(styledString);

// 创建第二个文本样式
OH_Drawing_TextStyle *worldTextStyle = OH_Drawing_CreateTextStyle();
OH_Drawing_SetTextStyleFontSize(worldTextStyle, 28);
OH_Drawing_SetTextStyleColor(worldTextStyle, OH_Drawing_ColorSetArgb(0xFF, 0x27, 0x87, 0xD9));

// 设置"World!"文本及其样式
OH_ArkUI_StyledString_PushTextStyle(styledString, worldTextStyle);
OH_ArkUI_StyledString_AddText(styledString, "World!");
OH_ArkUI_StyledString_PopTextStyle(styledString);
```

> **说明：**
>
> - 文本样式设置必须严格按照`PushTextStyle` -> `AddText` -> `PopTextStyle`的顺序调用，否则样式不会生效。
> - `OH_ArkUI_StyledString_`前缀的接口由Text组件提供，`OH_Drawing_`前缀的接口由方舟字体引擎提供。

## 添加占位符

占位符保留指定大小的空白区域，此区域不绘制文字，但参与布局测量，影响文字排版。行高是文字高度与占位高度中的较大值。

占位符功能主要用于图文混排场景，可以在文本中插入指定大小的空白区域，用于挂载Image组件或其他自定义内容。

### 添加占位符

使用[OH_ArkUI_StyledString_AddPlaceholder](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_addplaceholder)接口在文本中插入占位符。

``` C++
// 设置"Hello"文本及其样式
OH_Drawing_TextStyle *textStyle = OH_Drawing_CreateTextStyle();
OH_Drawing_SetTextStyleFontSize(textStyle, 28);
OH_Drawing_SetTextStyleColor(textStyle, OH_Drawing_ColorSetArgb(0xFF, 0x70, 0x70, 0x70));
OH_ArkUI_StyledString_PushTextStyle(styledString, textStyle);
OH_ArkUI_StyledString_AddText(styledString, "Hello");
OH_ArkUI_StyledString_PopTextStyle(styledString);

// 添加占位符，此区域内不会绘制文字，可以在此位置挂载Image组件实现图文混排
OH_Drawing_PlaceholderSpan placeHolder{.width = 100, .height = 100};
OH_ArkUI_StyledString_AddPlaceholder(styledString, &placeHolder);

// 设置"World!"文本及其样式
OH_Drawing_TextStyle *worldTextStyle = OH_Drawing_CreateTextStyle();
OH_Drawing_SetTextStyleFontSize(worldTextStyle, 28);
OH_Drawing_SetTextStyleColor(worldTextStyle, OH_Drawing_ColorSetArgb(0xFF, 0x27, 0x87, 0xD9));
OH_ArkUI_StyledString_PushTextStyle(styledString, worldTextStyle);
OH_ArkUI_StyledString_AddText(styledString, "World!");
OH_ArkUI_StyledString_PopTextStyle(styledString);
```

## 布局与绘制

StyledString在设置到Text组件之前，需要先完成布局计算，然后再进行渲染。

### 文本布局

文字样式和内容设置完成后，调用字体引擎接口[OH_Drawing_TypographyLayout](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_typographylayout)对文本进行布局，传入最大宽度。超过此宽度的文字会自动换行。

``` C++
// 基于StyledString创建Typography对象
OH_Drawing_Typography *typography = OH_ArkUI_StyledString_CreateTypography(styledString);

// 进行文本布局，需传入布局宽度
// 布局宽度 = Text组件宽度 - (左padding + 右padding)
OH_Drawing_TypographyLayout(typography, 400);
```

> **说明：**
>
> 未经过布局的文本无法显示，必须在设置到Text组件之前完成布局。

### 文本绘制

文本绘制由字体引擎与图形交互完成，无需额外设置。Text组件会在ArkUI渲染机制下，在组件触发绘制时调用字体引擎绘制接口。此处仅需将已创建的StyledString对象传递给已创建的Text组件。

首先需要创建Text组件并设置其基本属性（如宽度和高度），然后将StyledString设置到Text组件中。

``` C++
// 创建Text组件
ArkUI_NativeNodeAPI_1 *nodeApi = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
    OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
if (nodeApi == nullptr) {
    return;
}

ArkUI_NodeHandle text = nodeApi->createNode(ARKUI_NODE_TEXT);
ArkUI_NumberValue textWidth[] = {{.f32 = 300}};
ArkUI_AttributeItem textWidthItem = {.value = textWidth, .size = 1};
nodeApi->setAttribute(text, NODE_WIDTH, &textWidthItem);

ArkUI_NumberValue textHeight[] = {{.f32 = 100}};
ArkUI_AttributeItem textHeightItem = {.value = textHeight, .size = 1};
nodeApi->setAttribute(text, NODE_HEIGHT, &textHeightItem);

// 布局完成后，将StyledString设置给Text组件
ArkUI_AttributeItem styledStringItem = {.object = styledString};
nodeApi->setAttribute(text, NODE_TEXT_CONTENT_WITH_STYLED_STRING, &styledStringItem);
```

## 序列化与反序列化

从API version 14开始，StyledString提供了属性字符串的序列化和反序列化功能，支持将格式化字符串转换为字节数组或HTML格式，便于数据的存储、传输和跨平台使用。

**表3** 序列化与反序列化接口

| 接口 | 描述 |
| ---- | ---- |
| [OH_ArkUI_StyledString_Descriptor_Create](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_descriptor_create) | 创建属性字符串描述符。 |
| [OH_ArkUI_UnmarshallStyledStringDescriptor](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_unmarshallstyledstringdescriptor) | 反序列化字节数据到描述符。 |
| [OH_ArkUI_ConvertToHtml](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_converttohtml) | 将描述符转换为HTML格式。 |
| [OH_ArkUI_StyledString_Descriptor_Destroy](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_descriptor_destroy) | 销毁属性字符串描述符。 |

以下示例展示了如何创建描述符、反序列化字节数据、转换为HTML并进行验证。

``` C++
static void SerializeAndDeserializeStyledString()
{
    // 准备测试数据
    uint8_t data_bytes[] = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08};
    size_t dataSize = sizeof(data_bytes) / sizeof(data_bytes[0]);

    // 创建属性字符串描述符
    auto desc = OH_ArkUI_StyledString_Descriptor_Create();
    if (desc == nullptr) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "styledString", "Create Descriptor failed");
        return;
    }

    // 反序列化字节数据
    auto status = OH_ArkUI_UnmarshallStyledStringDescriptor(data_bytes, dataSize, desc);
    OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "styledString", "Unmarshall status: %{public}d", status);

    // 转换为HTML格式
    const char* html = OH_ArkUI_ConvertToHtml(desc);
    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "styledString", "html: [%{public}s]", html);

    size_t resultSize = dataSize + 2;
    uint8_t *buf1 = (uint8_t *)malloc(10 * sizeof(uint8_t));
    if (buf1 == nullptr) {
        OH_ArkUI_StyledString_Descriptor_Destroy(desc);
        return;
    }

    OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "styledString", "resultSize: %{public}zu", resultSize);
    uint8_t *buf2 = (uint8_t *)malloc(resultSize * sizeof(uint8_t));

    // 序列化字节数组
    if (buf2 != nullptr) {
        if (resultSize >= dataSize) {
            for (size_t i = 0; i < dataSize; i++) {
                buf2[i] = data_bytes[i];
            }
        } else {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "styledString",
                         "Buf too small: %{public}zu < %{public}zu", resultSize, dataSize);
            free(buf2);
            free(buf1);
            OH_ArkUI_StyledString_Descriptor_Destroy(desc);
            return;
        }
        bool equal = true;
        for (size_t i = 0; i < dataSize && equal; i++) equal = (data_bytes[i] == buf2[i]);
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "styledString",
            "Before: %{public}zu, After: %{public}zu, Equal: %{public}d", dataSize, resultSize, equal);
        free(buf2);
    }
    free(buf1);

    // 释放描述符
    OH_ArkUI_StyledString_Descriptor_Destroy(desc);
}
```

## 资源管理

Text组件不对StyledString及相关对象的生命周期进行管理，需由开发者自行负责。字体引擎接口均配有相应的销毁方法。

**表4** 资源销毁接口

| 接口 | 描述 |
| ---- | ---- |
| [OH_ArkUI_StyledString_Destroy](../reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstring_destroy) | 销毁属性字符串对象。 |
| [OH_Drawing_DestroyTextStyle](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_destroytextstyle) | 销毁文本样式对象。 |
| [OH_Drawing_DestroyTypographyStyle](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_destroytypographystyle) | 销毁段落样式对象。 |

当Text组件仍在界面上显示时，此时释放会导致文字无法绘制。在实际业务场景下需确保Text组件不再使用时才释放。

``` C++
// 在Text组件不再使用时释放StyledString对象
OH_ArkUI_StyledString_Destroy(styledString);

// 释放文本样式对象
OH_Drawing_DestroyTextStyle(textStyle);

// 释放段落样式对象
OH_Drawing_DestroyTypographyStyle(typographyStyle);
```

## 完整示例

本篇示例仅提供核心接口的调用方法，完整的示例工程请参考<!--RP1-->[StyledStringNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StyledStringNDK)<!--RP1End-->。

<!-- @[obtain_create_text_all](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StyledStringNDK/entry/src/main/cpp/manager.cpp) -->

``` C++
#include "manager.h"
#include <sstream>
#include <arkui/native_interface.h>
#include <arkui/styled_string.h>
// ···
#include <native_drawing/drawing_font_collection.h>
#include <native_drawing/drawing_text_declaration.h>

namespace NativeNode::Manager {
constexpr int32_t NUM_10 = 10;
constexpr int32_t NUM_28 = 28;
constexpr int32_t NUM_400 = 400;
// ···
void NodeManager::CreateNativeNode()
{
    // ···
    ArkUI_NativeNodeAPI_1 *nodeApi = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
        OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
    if (nodeApi == nullptr) {
        return;
    }
    // 创建一个Column容器组件
    ArkUI_NodeHandle column = nodeApi->createNode(ARKUI_NODE_COLUMN);
    ArkUI_NumberValue colWidth[] = {{.f32 = 300}};
    ArkUI_AttributeItem widthItem = {.value = colWidth, .size = 1};
    nodeApi->setAttribute(column, NODE_WIDTH, &widthItem);
    // 创建Text组件
    ArkUI_NodeHandle text = nodeApi->createNode(ARKUI_NODE_TEXT);
    ArkUI_NumberValue textWidth[] = {{.f32 = 300}};
    ArkUI_AttributeItem textWidthItem = {.value = textWidth, .size = 1};
    nodeApi->setAttribute(text, NODE_WIDTH, &textWidthItem);
    ArkUI_NumberValue textHeight[] = {{.f32 = 100}};
    ArkUI_AttributeItem textHeightItem = {.value = textHeight, .size = 1};
    nodeApi->setAttribute(text, NODE_HEIGHT, &textHeightItem);
    ArkUI_NumberValue borderWidth[] = {{.f32 = 1}};
    ArkUI_AttributeItem borderWidthItem = {.value = borderWidth, .size = 1};
    nodeApi->setAttribute(text, NODE_BORDER_WIDTH, &borderWidthItem);
    
    // OH_Drawing_开头的API是字体引擎提供的，typographyStyle表示段落样式。
    OH_Drawing_TypographyStyle *typographyStyle = OH_Drawing_CreateTypographyStyle();
    OH_Drawing_SetTypographyTextAlign(typographyStyle, OH_Drawing_TextAlign::TEXT_ALIGN_CENTER);
    OH_Drawing_SetTypographyTextMaxLines(typographyStyle, NUM_10);
    // 创建 ArkUI_StyledString。
    ArkUI_StyledString *styledString = OH_ArkUI_StyledString_Create(typographyStyle, OH_Drawing_CreateFontCollection());
    // 创建文本样式，设置字体和颜色。
    OH_Drawing_TextStyle *textStyle = OH_Drawing_CreateTextStyle();
    OH_Drawing_SetTextStyleFontSize(textStyle, NUM_28);
    OH_Drawing_SetTextStyleColor(textStyle, OH_Drawing_ColorSetArgb(0xFF, 0x70, 0x70, 0x70));
    // 文本样式的设置顺序push -> add -> pop.
    OH_ArkUI_StyledString_PushTextStyle(styledString, textStyle);
    OH_ArkUI_StyledString_AddText(styledString, "Hello");
    OH_ArkUI_StyledString_PopTextStyle(styledString);
    // 添加占位，此区域内不会绘制文字，可以在此位置挂载Image组件实现图文混排。
    OH_Drawing_PlaceholderSpan placeHolder{.width = 100, .height = 100};
    OH_ArkUI_StyledString_AddPlaceholder(styledString, &placeHolder);
    // 设置不同样式的文字
    OH_Drawing_TextStyle *worldTextStyle = OH_Drawing_CreateTextStyle();
    OH_Drawing_SetTextStyleFontSize(worldTextStyle, NUM_28);
    OH_Drawing_SetTextStyleColor(worldTextStyle, OH_Drawing_ColorSetArgb(0xFF, 0x27, 0x87, 0xD9));
    OH_ArkUI_StyledString_PushTextStyle(styledString, worldTextStyle);
    OH_ArkUI_StyledString_AddText(styledString, "World!");
    OH_ArkUI_StyledString_PopTextStyle(styledString);
    // 依赖StyledString对象创建字体引擎的Typography，此时它已经包含了设置的文本及其样式。
    OH_Drawing_Typography *typography = OH_ArkUI_StyledString_CreateTypography(styledString);
    // 字体引擎布局方法，需传入一个宽度，此宽度需与Text组件宽度匹配。
    // 布局宽度 = Text组件宽度 - (左padding + 右padding)
    OH_Drawing_TypographyLayout(typography, NUM_400);
    ArkUI_AttributeItem styledStringItem = {.object = styledString};
    // 布局完成后，通过NODE_TEXT_CONTENT_WITH_STYLED_STRING设置给Text组件。
    nodeApi->setAttribute(text, NODE_TEXT_CONTENT_WITH_STYLED_STRING, &styledStringItem);

    // 资源释放，应用侧可以自由决定何时释放。
    OH_ArkUI_StyledString_Destroy(styledString);
    // Text作为Column子组件
    nodeApi->addChild(column, text);
    // Column作为XComponent子组件
    OH_NativeXComponent_AttachNativeRootNode(xComponent_, column);
}
} // namespace NativeNode::Manager
```

![ndk_text_styled_string](figures/ndk_text_styled_string.png)

## 参考链接

- [StyledStringNDK示例代码](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StyledStringNDK)
- [StyledStringSample示例代码](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StyledStringSample)
- [Native Node API参考文档](../reference/apis-arkui/capi-native-node-h.md)
- [StyledString API参考文档](../reference/apis-arkui/capi-styled-string-h.md)
- [Drawing Typography API参考文档](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md)
- [Text组件属性文档](../reference/apis-arkui/capi-native-node-h.md)
- [方舟2D图形服务文档](../graphics/complex-text-c.md)
