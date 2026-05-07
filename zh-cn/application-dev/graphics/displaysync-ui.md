# 请求UI绘制帧率
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hudi33-->
<!--Designer: @hudi33-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

如果开发者需要以独立的帧率绘制更新操作UI界面时，可以通过DisplaySync来实现。应用中绘制内容的帧率可以使用DisplaySync实例来控制，具体请查阅[@ohos.graphics.displaySync (可变帧率)](../reference/apis-arkgraphics2d/js-apis-graphics-displaySync.md)。

## 开发步骤

此处以不同帧率改变文件组件字体大小为例，来模拟不同UI绘制帧率的效果。

1. 导入模块。
   <!-- @[display_sync_by_ui_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   import { displaySync } from '@kit.ArkGraphics2D';
   ```

2. 定义和构建DisplaySync对象。
   <!-- @[display_sync_create_object](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   @Entry
   @Component
   struct Index {
     // ...
   
     private backDisplaySyncSlow: displaySync.DisplaySync | undefined = undefined;
     private backDisplaySyncFast: displaySync.DisplaySync | undefined = undefined;
     // ...
   }
   ```

3. 定义两个文本组件。
   <!-- @[display_sync_create_text_component](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   @State drawFirstSize: number = 25;
   @State drawSecondSize: number = 25;
   
   // ...
   
   @Builder
   doSomeRenderFirst() {
     Text('30')
       .fontSize(this.drawFirstSize)
   }
   
   @Builder
   doSomeRenderSecond() {
     Text('60')
       .fontSize(this.drawSecondSize)
   }
   ```

4. 通过DisplaySync实例设置帧率和注册订阅函数。

   > **说明：**
   >
   > 订阅函数运行于UI主线程，故涉及UI线程的耗时操作不应运行于订阅函数中，以免影响性能。

   ArkTS-Dyn示例：
   <!-- @[display_sync_frame_rate_setting_and_subscription_function_registration](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   CreateDisplaySyncSlow() {
     let range: ExpectedFrameRateRange = {
       expected: 30,
       min: 0,
       max: 120
     };
   
     let draw30 = (intervalInfo: displaySync.IntervalInfo) => {
       if (this.isBigger_30) {
         this.drawFirstSize += 1;
         if (this.drawFirstSize > 150) {
           this.isBigger_30 = false;
         }
       } else {
         this.drawFirstSize -= 1;
         if (this.drawFirstSize < 25) {
           this.isBigger_30 = true;
         }
       }
     };
   
     this.backDisplaySyncSlow = displaySync.create();
     this.backDisplaySyncSlow.setExpectedFrameRateRange(range);
     this.backDisplaySyncSlow.on("frame", draw30);
   }
   ```
   ArkTS-Sta示例：
   <!-- @[display_sync_frame_rate_setting_and_subscription_function_registration](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySyncSta/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->

   ``` TypeScript
   CreateDisplaySyncSlow() {
     let range : ExpectedFrameRateRange = {
       expected: 30,
       min: 0,
       max: 120
     };
 
     // 创建DisplaySync实例
     this.backDisplaySyncSlow = displaySync.create();
     // 设置DisplaySync期望的帧率
     this.backDisplaySyncSlow?.setExpectedFrameRateRange(range);
     let draw30 = (intervalInfo: displaySync.IntervalInfo) => {
       if (this.isBigger_30) {
         this.drawFirstSize += 1;
         if (this.drawFirstSize > 150) {
           this.isBigger_30 = false;
         }
       } else {
         this.drawFirstSize -= 1;
         if (this.drawFirstSize < 25) {
           this.isBigger_30 = true;
         }
       }
     };
 
     // 注册订阅函数
     this.backDisplaySyncSlow?.onFrame(draw30);
   }
   ```

5. 开始每帧回调。
   ArkTS-Dyn示例：
   <!-- @[display_sync_start_per_frame_callback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   Button('Start')
     .id('CustomDrawStart')
     .fontSize(14)
     .fontWeight(500)
     .margin({ bottom: 10, left: 5 })
     .fontColor(Color.White)
     .onClick((): void => {
       if (this.backDisplaySyncSlow == undefined) {
         this.CreateDisplaySyncSlow();
       }
       if (this.backDisplaySyncFast == undefined) {
         this.CreateDisplaySyncFast();
       }
       if (this.backDisplaySyncSlow) {
         this.backDisplaySyncSlow.start();
       }
       if (this.backDisplaySyncFast) {
         this.backDisplaySyncFast.start();
       }
     })
     .width('20%')
     .height(40)
     .shadow(ShadowStyle.OUTER_DEFAULT_LG)
   ```

   ArkTS-Sta示例：
   <!-- @[display_sync_start_per_frame_callback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySyncSta/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->

   ``` TypeScript
   Button('Start')
     .id('CustomDrawStart')
     .fontSize(14)
     .fontWeight(500)
     .margin({ bottom: 10, left: 5 })
     .fontColor(Color.White)
     .onClick((e: ClickEvent): void => {
       if (this.backDisplaySyncSlow == undefined) {
         this.CreateDisplaySyncSlow();
       }
       if (this.backDisplaySyncFast == undefined) {
         this.CreateDisplaySyncFast();
       }
       if (this.backDisplaySyncSlow) {
         // 开始每帧回调
         this.backDisplaySyncSlow?.start();
       }
       if (this.backDisplaySyncFast) {
         // 开始每帧回调
         this.backDisplaySyncFast?.start();
       }
     })
     .width('20%')
     .height(40)
     .shadow(ShadowStyle.OUTER_DEFAULT_LG)
   ```

   > **说明：**
   >
   > 创建的DisplaySync实例在start使能后需要aboutToDisappear函数中进行stop操作并置空，避免内存泄漏问题。
   ArkTS-Dyn示例：
   <!-- @[display_sync_call_stop](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   aboutToDisappear() {
     let draw30 = (intervalInfo: displaySync.IntervalInfo) => {
       if (this.isBigger_30) {
         this.drawFirstSize += 1;
         if (this.drawFirstSize > 150) {
           this.isBigger_30 = false;
         }
       } else {
         this.drawFirstSize -= 1;
         if (this.drawFirstSize < 25) {
           this.isBigger_30 = true;
         }
       }
     };
 
     if (this.backDisplaySyncSlow) {
       // 取消订阅函数
       this.backDisplaySyncSlow.off("frame", draw30);
       this.backDisplaySyncSlow.stop();
       this.backDisplaySyncSlow = undefined;
     }
 
     if (this.backDisplaySyncFast) {
       this.backDisplaySyncFast.stop();
       this.backDisplaySyncFast = undefined;
     }
   }
   ```

   ArkTS-Sta示例：
   <!-- @[display_sync_call_stop](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySyncSta/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->

   ``` TypeScript
   aboutToDisappear() {
     let draw30 = (intervalInfo: displaySync.IntervalInfo) => {
       if (this.isBigger_30) {
         this.drawFirstSize += 1;
         if (this.drawFirstSize > 150) {
           this.isBigger_30 = false;
         }
       } else {
         this.drawFirstSize -= 1;
         if (this.drawFirstSize < 25) {
           this.isBigger_30 = true;
         }
       }
     };

     let draw60 = (intervalInfo: displaySync.IntervalInfo) => {
       if (this.isBigger_60) {
         this.drawSecondSize += 1;
         if (this.drawSecondSize > 150) {
           this.isBigger_60 = false;
         }
       } else {
         this.drawSecondSize -= 1;
         if (this.drawSecondSize < 25) {
           this.isBigger_60 = true;
         }
       }
     };

     if (this.backDisplaySyncSlow) {
       // 取消订阅函数
       this.backDisplaySyncSlow?.offFrame(draw30);
       this.backDisplaySyncSlow?.stop();
       this.backDisplaySyncSlow = undefined;
     }
 
     if (this.backDisplaySyncFast) {
       // 取消订阅函数
       this.backDisplaySyncFast?.offFrame(draw60);
       this.backDisplaySyncFast?.stop();
       this.backDisplaySyncFast = undefined;
     }
   }
   ```

6. 结束每帧回调。

   ArkTS-Dyn示例：
   <!-- @[display_sync_stop_per_frame_callback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->
   
   ``` TypeScript
   Button('Stop')
     .id('CustomDrawStop')
     .fontSize(14)
     .fontWeight(500)
     .margin({ bottom: 10, left: 5 })
     .fontColor(Color.White)
     .onClick((): void => {
       if (this.backDisplaySyncSlow) {
         this.backDisplaySyncSlow.stop();
       }
       if (this.backDisplaySyncFast) {
         this.backDisplaySyncFast.stop();
       }
     })
     .width('20%')
     .height(40)
     .shadow(ShadowStyle.OUTER_DEFAULT_LG)
   ```

   ArkTS-Sta示例：
   <!-- @[display_sync_stop_per_frame_callback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySyncSta/entry/src/main/ets/DispalySync/CustomDrawDisplaySync.ets) -->

   ``` TypeScript
   Button('Stop')
      .id('CustomDrawStop')
      .fontSize(14)
      .fontWeight(500)
      .margin({ bottom: 10, left: 5 })
      .fontColor(Color.White)
      .onClick((e: ClickEvent): void => {
        if (this.backDisplaySyncSlow) {
          // 停止每帧回调
          this.backDisplaySyncSlow?.stop();
        }
        if (this.backDisplaySyncFast) {
          // 停止每帧回调
          this.backDisplaySyncFast?.stop();
        }
      })
      .width('20%')
      .height(40)
      .shadow(ShadowStyle.OUTER_DEFAULT_LG)
   ```

<!--RP1-->
## 相关实例

- [DisplaySync (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySync)
- [DisplaySync (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkGraphics2D/DisplaySyncSta)
<!--RP1End-->