# Registering and Using Custom Fonts (ArkTS)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Overview

Custom fonts are fonts created or selected by developers based on application requirements. They are usually used to implement specific text styles or fulfill distinct design goals. To render specific text styles and characters, applications can register and use custom fonts.

## Workflow

**Registering custom fonts** is to register font files (such as .ttf and .otf files) from application resources to the system so that applications can use these fonts for text rendering. The registration process is to register font files with the system font library through the font management API so that the font files can be called in the application.

**Using custom fonts** is to explicitly specify registered custom fonts for text rendering in an application. You can select a specific text style (such as regular, bold, and italic) as required and apply it to UI elements, text controls, or other text display areas to meet design requirements and provide consistent visual effect.


## Available APIs

The following table lists the APIs for registering and using theme fonts. For details, see [@ohos.graphics.text (Text)](../reference/apis-arkgraphics2d/js-apis-graphics-text.md).

| API| Description| 
| -------- | -------- |
| loadFontSync(name: string, path: string \| Resource): void | Registers a font from a file in the specified path. This API returns the result synchronously.<br>**NOTE**<br>Ensure that the custom font has been registered. If performance is not a critical concern, you are advised to use the synchronous API.| 
| loadFont(name: string, path: string \| Resource): Promise&lt;void&gt; | Registers a font based on the specified name and file path. This API uses a promise to return the result. This API is supported since API version 14.| 
| unloadFontSync(name: string): void | Unregisters a font based on the specified name. This API is synchronous. This API is supported since API version 20.|
| unloadFont(name: string): Promise\<void\> | Unregisters a font based on the specified name. This API uses a promise to return the result. This API is supported since API version 20.|

## How to Develop

1. Import the required module.

   ```ts
   import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI'
   import { UIContext } from '@kit.ArkUI'
   import { text } from '@kit.ArkGraphics2D'
   ```

2. Register a custom font. You can use either of the following methods:

   ```ts
   // Register the custom font.
   let fontCollection = text.FontCollection.getGlobalInstance()
   // Method 1: /system/fonts/myFontFile.ttt is only an example path. You need to enter the actual file path.
   fontCollection.loadFontSync('myFamilyName0', 'file:///system/fonts/myFontFile.ttf')
   
   // Method 2: Ensure that the custom font file myFontFile.ttf is stored in the entry/src/main/resources/rawfile directory of your application project.
   fontCollection.loadFontSync('myFamilyName1',$rawfile('myFontFile.ttf'))
   ```

3. Use the custom font.

   ```ts
   // Enter the font family name passed when the custom font is registered.
   let myFontFamily: Array<string> = ["myFamilyName0"]
   // Set the text style.
   let myTextStyle: text.TextStyle = {
     color: { alpha: 255, red: 255, green: 0, blue: 0 },
     fontSize: 100,
     // Add the custom font to the text style.
     fontFamilies: myFontFamily
   };
   ```

4. Create a paragraph style and use the font manager instance to construct a **ParagraphBuilder** instance.

   ```ts
   // Create a paragraph style object to set the typography style.
   let myParagraphStyle: text.ParagraphStyle = {textStyle: myTextStyle}
   // Create a paragraph generator.
   let paragraphBuilder: text.ParagraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
   ```

5. Build a paragraph.

   ```ts
   // Set the text style in the paragraph generator.
   paragraphBuilder.pushStyle(myTextStyle);
   // Set the text content in the paragraph generator.
   paragraphBuilder.addText("Custom font test");
   // Generate a paragraph using the paragraph generator.
   let paragraph = paragraphBuilder.build();
   ```

6. To release a custom font, call the unloadFontSync API.

   ```ts
   // Unregister the custom font.
   fontCollection.unloadFontSync(familyName)
   // Refresh the node that uses fontCollection after the unregistration.
   newNode.invalidate()
   ```

## Sample Code

The following uses method 1 as an example to draw the text "Custom font test". Check the sample code below.

Ensure that the custom font file is stored in the correct path on the device.

<!-- @[arkts_custom_font](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/CustomFont/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Index.ets
import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI'
import { UIContext } from '@kit.ArkUI'
import { text } from '@kit.ArkGraphics2D'

// Obtain the global font set instance.
let fontCollection = text.FontCollection.getGlobalInstance(); // Obtain the ArkUI global FC.
const familyName = "myFamilyName"

// Create a custom render node class to draw text.
class MyRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    // Create a canvas object.
    const canvas = context.canvas
    // Use the custom font.
    let myFontFamily: Array<string> = [familyName] // If a custom font has been registered, enter the font family name of the custom font.
    // Set the text style.
    let myTextStyle: text.TextStyle = {
      color: {
        alpha: 255,
        red: 255,
        green: 0,
        blue: 0
      },
      fontSize: 30,
      // Add the custom font to the text style.
      fontFamilies: myFontFamily
    };
    // Create a paragraph style object to set the typography style.
    let myParagraphStyle: text.ParagraphStyle = {
      textStyle: myTextStyle,
      align: 3,
      wordBreak: text.WordBreak.NORMAL
    };
    // Create a paragraph generator.
    let ParagraphGraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection)
    // Set the text style in the paragraph generator.
    ParagraphGraphBuilder.pushStyle(myTextStyle);
    // Set the text content in the paragraph generator.
    ParagraphGraphBuilder.addText("Custom font test");
    // Generate a paragraph using the paragraph generator.
    let paragraph = ParagraphGraphBuilder.build();
    // Set the paragraph width to 1000 px.
    paragraph.layoutSync(1000);
    paragraph.paint(canvas, 0, 400);
  }
}

// Create and initialize a render node instance.
const newNode = new MyRenderNode();
// Set the position and size of the render node.
newNode.frame = {
  x: 0,
  y: 0,
  width: 400,
  height: 600
};


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode {
    this.rootNode = new FrameNode(uiContext)
    if (this.rootNode == null) {
      return this.rootNode
    }
    const renderNode = this.rootNode.getRenderNode()
    if (renderNode != null) {
      renderNode.frame = {
        x: 0,
        y: 0,
        width: 300,
        height: 50
      }
      renderNode.pivot = { x: 0, y: 0 }
    }
    return this.rootNode
  }

  addNode(node: RenderNode): void {
    if (this.rootNode == null) {
      return
    }
    const renderNode = this.rootNode.getRenderNode()
    if (renderNode != null) {
      renderNode.appendChild(node)
    }
  }

  clearNodes(): void {
    if (this.rootNode == null) {
      return
    }
    const renderNode = this.rootNode.getRenderNode()
    if (renderNode != null) {
      renderNode.clearChildren()
    }
  }
}

@Entry
@Component
struct RenderTest {
  private myNodeController: MyNodeController = new MyNodeController()

  build() {
    Column() {
      Row() {
        // If fontCollection of getGlobalInstance is used to register a font, the component corresponding to the family name is automatically refreshed.
        Text("Text Component")
          .fontFamily(familyName)
        NodeContainer(this.myNodeController)
          .height('100%')
          .onAppear(() => {
            this.myNodeController.clearNodes()
            this.myNodeController.addNode(newNode)
          })
      }
      .height('90%')
      .backgroundColor(Color.White)

      Row() {
        Button($r('app.string.Button_load_font'))
          .fontSize('16fp')
          .fontWeight(500)
          .margin({ bottom: 24, right: 12 })
          .onClick(() => {
            // Register the custom font.
            fontCollection.loadFontSync(familyName, 'file:///system/fonts/NotoSansMalayalamUI-SemiBold.ttf')
            // Refresh the node that uses fontCollection after the registration.
            newNode.invalidate()
          })
          .width('30%')
          .height(40)
          .shadow(ShadowStyle.OUTER_DEFAULT_LG)
        Button($r('app.string.Button_unload_font'))
          .fontSize('16fp')
          .fontWeight(500)
          .margin({ bottom: 24, right: 12 })
          .onClick(() => {
            // Unregister the custom font.
            fontCollection.unloadFontSync(familyName)
            // Refresh the node that uses fontCollection after the unregistration.
            newNode.invalidate()
          })
          .width('30%')
          .height(40)
          .shadow(ShadowStyle.OUTER_DEFAULT_LG)
      }
      .width('100%')
      .justifyContent(FlexAlign.Center) // Align the child elements in the current Row container to the center of the main axis.
      .shadow(ShadowStyle.OUTER_DEFAULT_SM) // Set the shadow effect outside the Row container.
      .alignItems(VerticalAlign.Bottom) // Align the child elements in the current Row container to the bottom of the cross axis (vertical direction).
      .layoutWeight(1) // Set the layout weight of the current Row in the parent Column container to 1.
    }
  }
}
```

## Effect

![image_load](figures/image_load.png)
![image_unload](figures/image_unload.png)
