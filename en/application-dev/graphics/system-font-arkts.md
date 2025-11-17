# Obtaining and Using System Fonts (ArkTS)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Scenario Introduction

System fonts are preset fonts of the operating system. They are used to display text when no custom font is specified, ensuring the readability and consistency of the text.

**System fonts** are used when an app does not register custom fonts or does not explicitly specify the text style. In addition, there are multiple system fonts. You can obtain the configuration information about system fonts and switch and use system fonts based on the font family name in the information.

Currently, system fonts cannot be disabled in ArkTS, but can be disabled in native.

## Available APIs

The following table lists the common APIs and structures related to system fonts. The external APIs in ArkTS are provided by ArkUI. For details about the APIs, see [@ohos.font](../reference/apis-arkui/js-apis-font.md).

| Name| Description| 
| -------- | -------- |
| getUIFontConfig() : UIFontConfig | Obtains the system font configuration.| 

## Obtains system font information.

1. Imports the required module.

   ```ts
   import { font } from '@kit.ArkUI'
   ```

2. Obtains system font information.

   ```ts
   @Entry
   @Component
   struct FontExample {
     build() {
       Column() {
         Button("getUIFontConfig")
           .width('60%')
           .height('6%')
           .margin(50)
           .onClick(()=>{
             let fontConfig = font.getUIFontConfig();
           })
       }.width('100%')
     }
   }
   ```

3. Prints font information in logs.

   ```ts
   @Entry
   @Component
   struct FontExample {
     build() {
       Column() {
         Button("getUIFontConfig")
           .width('60%')
           .height('6%')
           .margin(50)
           .onClick(()=>{
             let fontConfig = font.getUIFontConfig();
             console.info("font-dir -----------" + String(fontConfig.fontDir.length));
             for (let i = 0; i < fontConfig.fontDir.length; i ++) {
               console.info(fontConfig.fontDir[i]);
             }
             console.info("generic-------------" + String(fontConfig.generic.length));
             for (let i = 0; i < fontConfig.generic.length; i ++){
               console.info("family:" + fontConfig.generic[i].family);
               for (let j = 0; j < fontConfig.generic[i].alias.length; j ++){
                 console.info(fontConfig.generic[i].alias[j].name + " " + fontConfig.generic[i].alias[j].weight);
               }
             }
             console.info("fallback------------" + String(fontConfig.fallbackGroups.length));
             for (let i = 0; i < fontConfig.fallbackGroups.length; i ++){
               console.info("fontSetName:" + fontConfig.fallbackGroups[i].fontSetName);
               for (let j = 0; j < fontConfig.fallbackGroups[i].fallback.length; j ++){
                 console.info("language:" + fontConfig.fallbackGroups[i].fallback[j].language + " family:" + fontConfig.fallbackGroups[i].fallback[j].family);
               }
             }
           })
       }.width('100%')
     }
   }
   ```
  The following example shows some system font configuration information of the application device system. The configuration information varies according to the device system.

  ![image_0000002211603664](figures/image_0000002211603664.png)

## Using or Switching System Fonts

You can obtain the system font configuration information and then switch and use the system font based on the font family name (fontFamilies in TextStyle).

If no font is specified, the default system font HarmonyOS Sans is used to display text.
1. Import the required module.

   ```ts
   import { text } from '@kit.ArkGraphics2D';
   ```

2. Create TextStyle1 and set fontFamilies to HarmonyOS Sans SC. The default Chinese font is HarmonyOS Sans SC.

   ```ts
   let textStyle1: text.TextStyle = {
     color: { alpha: 255, red: 255, green: 0, blue: 0 },
     fontSize: 100,
     fontFamilies:['HarmonyOS Sans SC']
   };
   ```

3. Create TextStyle2 and set fontFamilies to HarmonyOS Sans TC (these two fonts are easy to observe the difference in the same text type).

   ```ts
   let textStyle2: text.TextStyle = {
     color: { alpha: 255, red: 255, green: 0, blue: 0 },
     fontSize: 100,
     fontFamilies:['HarmonyOS Sans TC']
   };
   ```

4. Create a paragraph generator.

   ```ts
   let myParagraphStyle: text.ParagraphStyle = {
     textStyle: textStyle1,
     align: 3,
     wordBreak:text.WordBreak.NORMAL
   };
   let fontCollection = text.FontCollection.getGlobalInstance() 
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection)
   ```

5. Add textStyle1 to the paragraph style and add text.

   ```ts
   let str:string = "Module description\n"
   paragraphBuilder.pushStyle(textStyle1);
   paragraphBuilder.addText(str);
   ```

6. Add textStyle2 to the paragraph style and add text.

   ```ts
   paragraphBuilder.pushStyle(textStyle2);
   paragraphBuilder.addText(str);
   ```

7. Generate a paragraph for future drawing.

   ```ts
   let paragraph = paragraphBuilder.build()
   ```

The following figure shows the effect.

![image_0000002246563829](figures/image_0000002246563829.png)
