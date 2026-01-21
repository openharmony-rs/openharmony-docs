# Requesting Frame Rates for Custom Content
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hudi33-->
<!--Designer: @hudi33-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

When you use native APIs to develop an application based on the [XComponent](../ui/napi-xcomponent-guidelines.md), you can request an independent frame rate for custom content in scenarios such as gaming and custom UI framework interconnection.

## Available APIs

| Name | Description    |
|-----|--------|
| OH_NativeXComponent_SetExpectedFrameRateRange (OH_NativeXComponent *component, OH_NativeXComponent_ExpectedRateRange *range) | Sets the expected frame rate range.|
| OH_NativeXComponent_RegisterOnFrameCallback (OH_NativeXComponent *component, OH_NativeXComponent_OnFrameCallback *callback) | Registers the display update callback and enables the callback for each frame.|
| OH_NativeXComponent_UnRegisterOnFrameCallback (OH_NativeXComponent *component) | Deregisters the display update callback and disables the callback for each frame.|

For details about the APIs, see [OH_NativeXComponent Native XComponent](../reference/apis-arkui/capi-oh-nativexcomponent-native-xcomponent.md).

## How to Develop

   > **NOTE**
   >
   > This section draws a graphic through the native Drawing module and presents it using the native Window module. For details, see [Using Drawing to Draw and Display Graphics](graphic-drawing-overview.md).

1. Add dependencies.

   Add the following library to **CMakeLists.txt**.

   ```txt
   libace_napi.z.so
   libace_ndk.z.so
   libnative_window.so
   libnative_drawing.so
   ```

   Import the required header files.

   ```c++
   #include <ace/xcomponent/native_interface_xcomponent.h>
   #include "napi/native_api.h"
   #include <native_drawing/drawing_bitmap.h>
   #include <native_drawing/drawing_color.h>
   #include <native_drawing/drawing_canvas.h>
   #include <native_drawing/drawing_pen.h>
   #include <native_drawing/drawing_brush.h>
   #include <native_drawing/drawing_path.h>
   #include <native_drawing/drawing_text_typography.h>
   #include <native_window/external_window.h>
   #include <cmath>
   #include <algorithm>
   #include <stdint.h>
   #include <sys/mman.h>
   ```

2. Define an ArkTS API file and name it **XComponentContext.ts**, which is used to connect to the native layer.
   ```ts
   export default interface XComponentContext {
   register(): void;
   unregister(): void;
   };
   ```

3. Define a demo page, which contains two **XComponents**.

   ```ts
   import XComponentContext from "../interface/XComponentContext";

   @Entry
   @Component
   struct Index {
     private xComponentContext1: XComponentContext | undefined = undefined;
     private xComponentContext2: XComponentContext | undefined = undefined;
     
    build() {
      Column() {
        Row() {
          XComponent({ id: 'xcomponentId_30', type: XComponentType.SURFACE, libraryname: 'entry' })
            .onLoad((xComponentContext) => {
              this.xComponentContext1 = xComponentContext as XComponentContext;
            }).width('832px')
        }.height('40%')

        Row() {
          XComponent({ id: 'xcomponentId_120', type: XComponentType.SURFACE, libraryname: 'entry' })
            .onLoad((xComponentContext) => {
              this.xComponentContext2 = xComponentContext as XComponentContext;
            }).width('832px') // Multiples of 64
        }.height('40%')
      }
    }
   }
   ```

4. Configure the frame rate and register the callback function at the native layer.

   ```ts
   static void TestCallback(OH_NativeXComponent *component, uint64_t timestamp, uint64_t targetTimestamp) // Define the callback function for each frame.
   {
       // ...
       // Obtain the surface size of the XComponent.
       int32_t xSize = OH_NativeXComponent_GetXComponentSize(component, nativeWindow, &width, &height);
       if ((xSize == OH_NATIVEXCOMPONENT_RESULT_SUCCESS) && (render != nullptr)) {
           render->Prepare();
           render->Create();
           if (id == "xcomponentId_30") {
               // When the frame rate is 30 Hz, the frame moves by 16 pixels at a time.
               render->ConstructPath(16, 16, render->defaultOffsetY);
           }
           if (id == "xcomponentId_120") {
               // When the frame rate is 120 Hz, the frame moves by 4 pixels at a time.
               render->ConstructPath(4, 4, render->defaultOffsetY);
           }
     	 // ...
       }
   }
   ```

   > **NOTE**
   >
   > - The callback function runs in the UI main thread. To avoid adverse impact on the performance, time-consuming operations related to the UI thread should not run in the callback function.
   > - After the instance calls **OH_NativeXComponent_RegisterOnFrameCallback**, it must call **OH_NativeXComponent_UnregisterOnFrameCallback** when it no longer needs to control the frame rate, so as to avoid memory leakage and impact on performance and power consumption.
   > - Before API version 18, if the application calls **OH_NativeXComponent_RegisterOnFrameCallback** to set the callback function and does not unregister the callback function, the application can receive the expected callback when the XComponent instance exists.
   > - From API version 18 onwards, if the application calls **OH_NativeXComponent_RegisterOnFrameCallback** to set the callback function and does not unregister the callback function, the application can receive the expected callback only when the XComponent is on the tree.

   ```ts
   void SampleXComponent::RegisterOnFrameCallback(OH_NativeXComponent *nativeXComponent) 
   {
       OH_NativeXComponent_RegisterOnFrameCallback(nativeXComponent, TestCallback); // Register the callback function and enable callback for each frame.
   }
   
   napi_value SampleXComponent::NapiRegister(napi_env env, napi_callback_info info)
   {
       // ...
       render->RegisterOnFrameCallback(nativeXComponent); // Register the callback function and enable callback for each frame at the TS layer.
       // ...
   }
   
   napi_value SampleXComponent::NapiUnregister(napi_env env, napi_callback_info info)
   {
       // ...
       The OH_NativeXComponent_UnregisterOnFrameCallback(nativeXComponent); // Deregister the callback function for each frame at the TS layer.
       // ...
   }
   ```

5. Register and deregister the callback function for each frame at the TS layer.

   ```ts
   Row() {
       Button('Start')
         .id('Start')
         .fontSize(14)
         .fontWeight(500)
         .margin({ bottom: 20, right: 6, left: 6 })
         .onClick(() => {
           if (this.xComponentContext1) {
             this.xComponentContext1.register();
           }
           if (this.xComponentContext2) {
             this.xComponentContext2.register();
           }
         })
         .width('30%')
         .height(40)
         .shadow(ShadowStyle.OUTER_DEFAULT_LG)
       
       Button('Stop')
         .id('Stop')
         .fontSize(14)
         .fontWeight(500)
         .margin({ bottom: 20, left: 6 })
         .onClick(() => {
           if (this.xComponentContext1) {
             this.xComponentContext1.unregister();
           }
           if (this.xComponentContext2) {
             this.xComponentContext2.unregister();
           }
         })
         .width('30%')
         .height(40)
         .shadow(ShadowStyle.OUTER_DEFAULT_LG)
   }
   ```

<!--RP1-->
## Samples

- [DisplaySync (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/DisplaySync)
<!--RP1End-->
