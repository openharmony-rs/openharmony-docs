# Using Theme Fonts (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## Overview

Theme fonts are specialized custom fonts available for use in theme applications. You can enable them using specific APIs.


## Implementation Mechanism

**Figure 1** Switching and using theme fonts

![themeText_native](figures/themeText_native.jpg)

When switching and using theme fonts, the application must subscribe to theme font change events. After receiving such an event, it must call the page refresh API to switch the theme font. Without this step, the new theme font will apply only after the application is restarted. To draw text with a theme font, use **OH_Drawing_GetFontCollectionGlobalInstance** to obtain the global font collection object, which contains theme font information.

> **NOTE**
>
> You cannot use **OH_Drawing_CreateSharedFontCollection** to draw text with a theme font because this API returns a font collection object that does not contain any theme font information.


## Available APIs

The following table lists the APIs for registering and using theme fonts. For details, see [Drawing](../reference/apis-arkgraphics2d/capi-drawing.md).

| Name| Description|
| -------- | -------- |
| OH_Drawing_FontCollection\* OH_Drawing_GetFontCollectionGlobalInstance(void) | Obtains an **OH_Drawing_FontCollection** object.|
| [onConfigurationUpdate()](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) | Called when system configuration is updated.<br>Currently, theme applications provide only an ArkTS API to publish change events. Therefore, cross-language calling is required for your application.|


## How to Develop

1. Make sure that you can apply a theme font in the theme applications on your device.

2. Rewrite the **onConfigurationUpdate** function in the entry file (**EntryAbility.ets** in the default project) to respond to **fontId** changes and adapt to theme font switching and page refreshing.

   ```c++
   // entry/src/main/ets/entryability/EntryAbility.ets
   export default class EntryAbility extends UIAbility {
       // ...  
       preFontId ="";
       onConfigurationUpdate(newConfig: Configuration):void{
           let fontId = newConfig.fontId;
           if(fontId && fontId !=this.preFontId){
               this.preFontId = fontId;
               // Call the C++ code.
           }
       }
       // ...
   };
   ```

   When the system configuration information (**newConfig** in the example) changes, the **onConfigurationUpdate** function is triggered. The application can obtain the **fontId** from the configuration information sent by the system and determine whether the **fontId** is the same as that saved locally to identify the theme font switching. If they are different, update the local **fontId** and call the C++ code to update the typography result.

3. This step and the following steps use the theme fonts in C++. Decide which language to use based on your needs. For details about cross-language calling, see [Node-API Overview](../napi/napi-introduction.md).

   Add the following library to the `src/main/cpp/CMakeLists.txt` file of the project.
   ```c++
   libnative_drawing.so
   ```

   Include header files.

   <!-- @[theme_font_c_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   #include <native_drawing/drawing_font_collection.h>
   #include <native_drawing/drawing_text_typography.h>
   #include <native_drawing/drawing_register_font.h>
   ```

4. Create a font manager.

   > **NOTE**
   >
   > The registered theme fonts are used for the global font collection object. Therefore, you must use **OH_Drawing_GetFontCollectionGlobalInstance**. If you use **OH_Drawing_CreateSharedFontCollection** or **OH_Drawing_CreateFontCollection**, the theme fonts will be unavailable. The global font collection object obtained by **OH_Drawing_GetFontCollectionGlobalInstance** cannot be released because it can lead to disordered font rendering.

   <!-- @[theme_font_c_draw_text_step1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   OH_Drawing_FontCollection *fontCollection = OH_Drawing_GetFontCollectionGlobalInstance();
   ```

5. **OH_Drawing_SetTextStyleFontFamilies()** can be used to specify the font family name for implementing the specified font. However, to use a theme font, do not call **OH_Drawing_SetTextStyleFontFamilies()** to avoid using the specified font instead of the theme font.

   <!-- @[theme_font_c_draw_text_step2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   OH_Drawing_TextStyle *myTextStyle = OH_Drawing_CreateTextStyle();
   // const char* myFontFamilies[] = {"otherFontFamilyName"};
   // Do not use this API to specify the font.
   // OH_Drawing_SetTextStyleFontFamilies(textStyle, 1, myFontFamilies);
   ```

6. Set the paragraph text to "Hello World. \nThis is the theme font.", which will use the theme font.

   <!-- @[theme_font_c_draw_text_step3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   // Set other text styles.
   OH_Drawing_SetTextStyleColor(myTextStyle, OH_Drawing_ColorSetArgb(0xFF, 0x00, 0x00, 0x00));
   // Set the font size to 100.0.
   OH_Drawing_SetTextStyleFontSize(myTextStyle, 100.0);
   // Create a paragraph style object to set the typography style.
   OH_Drawing_TypographyStyle *typographyStyle = OH_Drawing_CreateTypographyStyle();
   OH_Drawing_SetTypographyTextAlign(typographyStyle, TEXT_ALIGN_LEFT); // Set the typography to left alignment.
   // Create a paragraph generator.
   OH_Drawing_TypographyCreate *handler = OH_Drawing_CreateTypographyHandler(typographyStyle, fontCollection);
   // Set the text style in the paragraph generator.
   OH_Drawing_TypographyHandlerPushTextStyle(handler, myTextStyle);
   // Set the text content in the paragraph generator.
   const char *text = "Hello World. \nThis is the theme font.";
   OH_Drawing_TypographyHandlerAddText(handler, text);
   // Generate a paragraph using the paragraph generator.
   OH_Drawing_Typography *typography = OH_Drawing_CreateTypography(handler);
   ```

## Effect

The following figures show how text is rendered with different theme fonts in a theme application.

The following figures are for reference only.

**Figure 2** Effect of theme font 1

![themeFont_native_01](figures/NdkThemeFont.PNG)

**Figure 3** Effect of theme font 2

![themeFont_native_02](figures/themeFont_native_02.png)
