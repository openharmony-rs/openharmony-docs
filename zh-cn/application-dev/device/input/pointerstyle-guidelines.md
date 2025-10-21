# 鼠标光标开发指导

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

鼠标光标控制提供鼠标光标显示和隐藏、光标样式查询和设置的能力。使用场景例如：用户在全屏观看视频时，开发者可以控制鼠标光标的显示隐藏；当用户执行取色时，开发者可以将鼠标光标样式切换为取色器样式。

## 导入模块

```js
import { pointer } from '@kit.InputKit';
```

## 接口说明

鼠标光标控制常用接口如下表所示，接口详细介绍请参见[ohos.multimodalInput.pointer文档](../../reference/apis-input-kit/js-apis-pointer.md)。

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

<!-- @[pointer_visible](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

## 设置鼠标光标样式

当开发者设计取色器特性时，可以将鼠标光标样式切换为取色器样式，完成取色后，设置鼠标光标样式为默认样式，该接口设置和查询当前应用内指定窗口的光标样式，总共可设置43种光标样式，具体参考[光标样式](../../reference/apis-input-kit/js-apis-pointer.md#pointerstyle)。

### 开发步骤

1. 开发者使能取色功能。
2. 调用窗口实例获取对应的窗口id。
3. 设置鼠标光标样式为取色器样式。
4. 取色结束。
5. 设置鼠标光标样式为默认样式。

<!-- @[pointer_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->
