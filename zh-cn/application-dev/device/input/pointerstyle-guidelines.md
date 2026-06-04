# 鼠标光标开发指导

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

鼠标光标控制提供鼠标光标显示和隐藏、光标样式查询和设置的能力。使用场景例如：用户在全屏观看视频时，开发者可以控制鼠标光标的显示隐藏；当用户执行取色时，开发者可以将鼠标光标样式切换为取色器样式。

## 导入模块

```js
import { pointer } from '@kit.InputKit';
```

## 接口说明

鼠标光标控制常用接口如下表所示，接口详细介绍请参见[@ohos.multimodalInput.pointer (鼠标光标)](../../reference/apis-input-kit/js-apis-pointer.md)。

| 接口名称                                                       | 描述                                                         |
| ------------------------------------------ | ------------------------------------------------------- |
| isPointerVisible(callback: AsyncCallback\<boolean>): void | 获取鼠标光标显示或隐藏状态。                                 |
| setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void | 设置鼠标光标显示或隐藏状态，该接口会影响全局鼠标光标的显示状态。 |
| setPointerStyle(windowId: number, pointerStyle: PointerStyle, callback: AsyncCallback\<void>): void | 设置鼠标光标样式，该接口会影响指定窗口鼠标光标样式。         |
| getPointerStyle(windowId: number, callback: AsyncCallback\<PointerStyle>): void | 查询鼠标光标样式。                                           |

## 设置鼠标光标隐藏

用户在全屏观看视频时，可以调用鼠标光标的隐藏接口设置鼠标光标不可见，提升用户体验。

### 开发步骤

1. 应用切换到全屏播放。
2. 在应用中调用鼠标光标隐藏接口隐藏光标。
3. 应用退出全屏播放。
4. 在应用中调用鼠标光标显示接口显示光标。

ArkTS-Dyn示例：

<!-- @[pointer_visible](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Text("Click to hide pointer")
  .onClick(() => {
    // 1.应用切换到全屏播放
    // 2.调用鼠标光标隐藏接口隐藏光标
    try {
      pointer.setPointerVisible(false, (error: Error) => {
        if (error) {
          hilog.error(DOMAIN, 'Pointer', `Set pointer visible failed, error: %{public}s`,
            JSON.stringify(error, ["code", "message"]));
          return;
        }
        hilog.info(DOMAIN, 'Pointer', 'Set pointer visible success.');
      });
    } catch (error) {
      hilog.error(DOMAIN, 'Pointer', `The mouse pointer hide attributes is failed. %{public}s`,
        JSON.stringify(error, ["code", "message"]));
    }
  })
  // ...

// 3.应用退出全屏播放
// 4.调用鼠标光标显示接口显示光标
Text("Click to display pointer")
  .onClick(() => {
    try {
      pointer.setPointerVisible(true, (error: Error) => {
        if (error) {
          hilog.error(DOMAIN, 'Pointer', `Set pointer visible failed, error: %{public}s`,
            JSON.stringify(error, ["code", "message"]));
          return;
        }
        hilog.info(DOMAIN, 'Pointer', 'Set pointer visible success.');
      });
    } catch (error) {
      hilog.error(DOMAIN, 'Pointer', `Set pointer visible failed, error: %{public}s`,
        JSON.stringify(error, ["code", "message"]));
    }
  })
  // ...
```

ArkTS-Sta示例：

<!-- @[pointer_visible](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputKit/ArkTsPointer-Sta/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
'use static'

import pointer from '@ohos.multimodalInput.pointer';
import window from '@ohos.window';
import hilog from '@ohos.hilog';
import { BusinessError, Callback, AsyncCallback } from '@ohos.base';
import { Entry, Component, Column, Text, RelativeContainer,
  WordBreak, FontWeight, TextAlign, HorizontalAlign } from '@ohos.arkui.component';
const DOMAIN: int = 0x0000;
const TAG: string = 'Pointer';

@Entry
@Component
struct Index {
  // 隐藏鼠标光标
  async hidePointer(): Promise<void> {
    try {
      await pointer.setPointerVisible(false);
      hilog.info(DOMAIN, TAG, 'Set pointer visible success.');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      const errorCode: int = err.code;
      const errorMessage: string = err.message;
      hilog.error(DOMAIN, TAG, `The mouse pointer hide attributes is failed. code: %{public}d, message: %{public}s`,
        errorCode, errorMessage);
    }
  }

  // 显示鼠标光标
  async showPointer(): Promise<void> {
    try {
      await pointer.setPointerVisible(true);
      hilog.info(DOMAIN, TAG, 'Set pointer visible success.');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      const errorCode: int = err.code;
      const errorMessage: string = err.message;
      hilog.error(DOMAIN, TAG, `Set pointer visible failed. code: %{public}d, message: %{public}s`,
        errorCode, errorMessage);
    }
  }

  build() {
    RelativeContainer() {
      Column() {
        // 点击隐藏鼠标光标
        Text("Click to hide pointer")
          .onClick(() => {
            this.hidePointer();
          })
          // ...
        // 点击显示鼠标光标
        Text("Click to display pointer")
          .onClick(() => {
            this.showPointer();
          })
          // ...
      }
      // ...
    }
  }
}
```


## 设置鼠标光标样式

当开发者设计取色器特性时，可以将鼠标光标样式切换为取色器样式，完成取色后，设置鼠标光标样式为默认样式，该接口设置和查询当前应用内指定窗口的光标样式，总共可设置49种光标样式，具体参考[PointerStyle](../../reference/apis-input-kit/js-apis-pointer.md#pointerstyle)。

### 开发步骤

1. 开发者使能取色功能。
2. 调用窗口实例获取对应的窗口ID。
3. 设置鼠标光标样式为取色器样式。
4. 取色结束。
5. 设置鼠标光标样式为默认样式。

ArkTS-Dyn示例：

<!-- @[pointer_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Text(`Click to set the mouse pointer style to the color picker style`)
  .onClick(() => {
    // 1.开发者使能取色功能
    // 2.调用窗口实例获取对应的窗口id
    window.getLastWindow(this.getUIContext().getHostContext(),
      (error: BusinessError, windowClass: window.Window) => {
        if (error.code) {
          hilog.error(DOMAIN, 'Pointer', 'Failed to obtain the top window. Cause: %{public}s',
            JSON.stringify(error));
          return;
        }
        let windowId = windowClass.getWindowProperties().id;
        if (windowId < 0) {
          hilog.info(DOMAIN, 'Pointer', 'Invalid windowId');
          return;
        }
        try {
          // 3.设置鼠标光标样式为取色器样式
          pointer.setPointerStyle(windowId, pointer.PointerStyle.COLOR_SUCKER).then(() => {
            hilog.info(DOMAIN, 'Pointer', 'Successfully set mouse pointer style');
          });
        } catch (error) {
          hilog.error(DOMAIN, 'Pointer', `Failed to set the pointer style, error=%{public}s, msg=%{public}s`,
            JSON.stringify(error), error.message);
        }
      });
  })
  // ...


Text(`Click to set the mouse pointer style to default style`)
  .onClick(() => {
    // 4.取色结束
    window.getLastWindow(this.getUIContext().getHostContext(),
      (error: BusinessError, windowClass: window.Window) => {
        if (error.code) {
          hilog.error(DOMAIN, 'Pointer', 'Failed to obtain the top window. Cause: %{public}s',
            JSON.stringify(error));
          return;
        }
        let windowId = windowClass.getWindowProperties().id;
        if (windowId < 0) {
          hilog.info(DOMAIN, 'Pointer', 'Invalid windowId');
          return;
        }
        try {
          // 5.设置鼠标光标样式为默认样式
          pointer.setPointerStyle(windowId, pointer.PointerStyle.DEFAULT).then(() => {
            hilog.info(DOMAIN, 'Pointer', 'Successfully set mouse pointer style');
          });
        } catch (error) {
          hilog.error(DOMAIN, 'Pointer', `Failed to set the pointer style, error=%{public}s, msg=%{public}s`,
            JSON.stringify(error), error.message);
        }
      });
  })
```

ArkTS-Sta示例：

<!-- @[pointer_style](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/InputKit/ArkTsPointer-Sta/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
'use static'

import pointer from '@ohos.multimodalInput.pointer';
import window from '@ohos.window';
import hilog from '@ohos.hilog';
import { BusinessError, Callback, AsyncCallback } from '@ohos.base';

import { Entry, Component, Column, Text, RelativeContainer,
  WordBreak, FontWeight, TextAlign, HorizontalAlign } from '@ohos.arkui.component';

const DOMAIN: int = 0x0000;
const TAG: string = 'Pointer';

@Entry
@Component
struct Index {
  // 获取顶层窗口的 ID
  async getTopWindowId(): Promise<int> {
    const ctx = this.getUIContext().getHostContext();
    if (ctx === undefined) {
      hilog.info(DOMAIN, TAG, 'Failed to get host context');
      return -1;
    }
    const windowClass: window.Window = await window.getLastWindow(ctx);
    const windowId: int = windowClass.getWindowProperties().id;
    if (windowId < 0) {
      hilog.info(DOMAIN, TAG, 'Invalid windowId');
      return -1;
    }
    return windowId;
  }

  // 设置鼠标光标样式为取色器样式
  async setColorSuckerPointerStyle(): Promise<void> {
    try {
      const windowId: int = await this.getTopWindowId();
      if (windowId < 0) {
        return;
      }
      // 设置鼠标光标样式为取色器样式
      await pointer.setPointerStyle(windowId, pointer.PointerStyle.COLOR_SUCKER);
      hilog.info(DOMAIN, TAG, 'Successfully set mouse pointer style');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, `Failed to set the pointer style, code: %{public}d, message: %{public}s`,
        err.code, err.message);
    }
  }

  // 设置鼠标光标样式为默认样式
  async setDefaultPointerStyle(): Promise<void> {
    try {
      const windowId: int = await this.getTopWindowId();
      if (windowId < 0) {
        return;
      }
      // 设置鼠标光标样式为默认样式
      await pointer.setPointerStyle(windowId, pointer.PointerStyle.DEFAULT);
      hilog.info(DOMAIN, TAG, 'Successfully set mouse pointer style');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, `Failed to set the pointer style, code: %{public}d, message: %{public}s`,
        err.code, err.message);
    }
  }

  build() {
    RelativeContainer() {
      Column() {

        // [Start pointer_style]
        // 点击设置鼠标光标样式为取色器样式
        Text(`Click to set the mouse pointer style to the color picker style`)
          .onClick(() => {
            this.setColorSuckerPointerStyle();
          })
          // ...

        // 点击设置鼠标光标样式为默认样式
        Text(`Click to set the mouse pointer style to default style`)
          .onClick(() => {
            this.setDefaultPointerStyle();
          })
          // ...
      }
      // ...
    }
  }
}
```
