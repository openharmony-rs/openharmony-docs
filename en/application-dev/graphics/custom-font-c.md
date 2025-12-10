# Registering and Using Custom Fonts (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## Overview

Custom fonts are created or selected by developers based on application requirements. They are usually used to implement specific text styles or meet unique design requirements. If an application needs to use a specific text style and character set, you can register and use custom fonts for text rendering.


## Implementation Process

**Registering custom fonts** refers to registering font files (such as TTF and OTF files) from application resources to the system so that applications can use these fonts for text rendering. The registration process is to register font files with the system font library through the font management API so that the font files can be called in applications.

**Using custom fonts** refers to explicitly specifying registered custom fonts for text drawing in applications. You can select a specific text style (such as normal, bold, and italic) as required and apply it to UI elements, text controls, or other text display areas to ensure that the design requirements are met and a consistent visual effect is provided.


## Available APIs

The following table lists the APIs for registering and using custom fonts. For details, see [Drawing](../reference/apis-arkgraphics2d/capi-drawing.md).

| Name| Description| 
| -------- | -------- |
| OH_Drawing_CreateSharedFontCollection (void) | Creates a shareable font set object OH_Drawing_FontCollection.| 
| OH_Drawing_RegisterFont (OH_Drawing_FontCollection\* , const char\* fontFamily, const char\* familySrc ) | Registers a custom font with the font manager. The supported font file formats are .ttf and .otf.| 
| OH_Drawing_CreateTextStyle(void) | Creates a pointer to the OH_Drawing_TextStyle object to set the text style.| 
| OH_Drawing_SetTextStyleFontFamilies (OH_Drawing_TextStyle \*, int, const char \*fontFamilies[]) | Sets the font families for a text style.| 
| OH_Drawing_UnregisterFont (OH_Drawing_FontCollection\* , const char\* fontFamily) | Unregisters a custom font by font family name.| 

## How to Develop
1. Add the following libraries to the `src/main/cpp/CMakeLists.txt` file of the project:
   ```c++
   libnative_drawing.so
   ```

2. Import the required header files.

   <!-- @[theme_font_c_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   #include <native_drawing/drawing_font_collection.h>
   #include <native_drawing/drawing_text_typography.h>
   #include <native_drawing/drawing_register_font.h>
   ```

3. Create a font manager. You are advised to use OH_Drawing_CreateSharedFontCollection() to create a shared font set object.

   > **Note:**
   >
   > Both OH_Drawing_CreateFontCollection() and OH_Drawing_CreateSharedFontCollection() can be used to create an OH_Drawing_FontCollection object. However, the font set pointer object created by OH_Drawing_CreateFontCollection() can be used by only one OH_Drawing_TypographyCreate object. If the font set object needs to be shared by multiple OH_Drawing_TypographyCreate objects, use OH_Drawing_CreateSharedFontCollection() to create a shared font set object.

   <!-- @[custom_font_c_custom_font_text_step1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   OH_Drawing_FontCollection *fontCollection = OH_Drawing_CreateSharedFontCollection();
   ```

4. Set the font family name and sandbox path of the custom font.

   > **Note:**
   >
   > Ensure that the available custom font file to be registered is correctly placed in the /system/fonts/NotoSerifTamil[wdth,wght].ttf directory on the application device.

   <!-- @[custom_font_c_custom_font_text_step2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   //Use the font family name when using the custom font.
   const char* fontFamily = "myFamilyName"; 
   //This path is the path of the custom font file to be registered on the application device. Ensure that the custom font file is correctly placed in this path.
   const char* fontPath = "/system/fonts/NotoSerifTamil[wdth,wght].ttf"; 
   ```

5. Register the custom font using OH_Drawing_RegisterFont() in the font manager.

   You can check the API return result to determine whether the registration is successful.

   The following lists the return results of the OH_Drawing_RegisterFont API and their meanings:

   0 indicates that the registration is successful, 1 indicates that the file does not exist, 2 indicates that the file fails to be opened, 3 indicates that the file fails to be read, 4 indicates that the file fails to be found, 5 indicates that the file size fails to be obtained, and 9 indicates that the file is damaged.

   <!-- @[custom_font_c_custom_font_text_step3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   // 0: success; 1: file not found; 2: file opening failure; 3: file reading failure; 4: file search failure; 5: file size obtaining failure; 9: file damage
   int errorCode = OH_Drawing_RegisterFont(fontCollection, fontFamily, fontPath);
   ```

6. After the custom font is successfully registered, use the OH_Drawing_CreateTextStyle() API to create a text style object and use the OH_Drawing_SetTextStyleFontFamilies() API to add the custom font.

   <!-- @[custom_font_c_custom_font_text_step4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   //If the custom font has been successfully registered, enter the font family name of the custom font.
   const char* myFontFamilies[] = {"myFamilyName"}; 
   //Add the custom font that can be used.
   OH_Drawing_SetTextStyleFontFamilies(textStyle, 1, myFontFamilies);
   ```

7. Generate the final paragraph text and use the custom font to implement final text drawing and display.

   <!-- @[custom_font_c_custom_font_text_step5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   //Set other text styles.
   OH_Drawing_SetTextStyleColor(textStyle , OH_Drawing_ColorSetArgb(0xFF, 0x00, 0x00, 0x00));
   // Set the font size to 60.0.
   OH_Drawing_SetTextStyleFontSize(textStyle, 60.0);
   // Create a paragraph style object to set the typesetting style.
   OH_Drawing_TypographyStyle *typographyStyle = OH_Drawing_CreateTypographyStyle();
   OH_Drawing_SetTypographyTextAlign(typographyStyle, TEXT_ALIGN_LEFT); // Set the paragraph style to left alignment.
   // Create a paragraph generator.
   OH_Drawing_TypographyCreate* handler = OH_Drawing_CreateTypographyHandler(typographyStyle, fontCollection);
   // Set the text style in the paragraph generator.
   OH_Drawing_TypographyHandlerPushTextStyle(handler, textStyle);
   // Set the text content in the paragraph generator.
   const char* text = "hello,This text uses a custom font";
   OH_Drawing_TypographyHandlerAddText(handler, text);
   // Generate a paragraph using the paragraph generator.
   OH_Drawing_Typography* typography = OH_Drawing_CreateTypography(handler);
   // Set the maximum width.
   double maxWidth = width_;
   OH_Drawing_TypographyLayout(typography, maxWidth);
   // Draw the text on the canvas (0,100).
   OH_Drawing_TypographyPaint(typography, cCanvas_, 0, 100);
   ```

8. To release a custom font, call OH_Drawing_UnregisterFont.

   <!-- @[custom_font_c_custom_font_text_step6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKThemFontAndCustomFontText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

   ```C++
   // Unregister the custom font.
   OH_Drawing_UnregisterFont(fontCollection, fontFamily);
   OH_Drawing_TypographyCreate* handler1 = OH_Drawing_CreateTypographyHandler(typographyStyle, fontCollection);
   // Set the text style in the paragraph generator.
   OH_Drawing_TypographyHandlerPushTextStyle(handler1, textStyle);
   // Set the text content in the paragraph generator.
   const char* text1 = "hello,The custom font of this text is deregistered.";
   OH_Drawing_TypographyHandlerAddText(handler1, text1);
   // Generate a paragraph using the paragraph generator.
   OH_Drawing_Typography* typography1 = OH_Drawing_CreateTypography(handler1);
   OH_Drawing_TypographyLayout(typography1, maxWidth);
   // Draw the text on the canvas (0,300).
   OH_Drawing_TypographyPaint(typography1, cCanvas_, 0, 300);
   ```
