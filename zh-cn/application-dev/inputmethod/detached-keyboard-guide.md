# 适配分离键盘
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

在大屏设备（折叠屏展开态、平板）上，用户双手握持设备两侧打字时，传统底部固定键盘无法满足舒适的握持体验。分离键盘（FLAG_DETACHED）将软键盘左右分离、中间镂空，双手自然落在分离键盘上，中间区域可显示更多应用内容。

本指南在已实现一个输入法应用的前提下，介绍如何适配分离键盘，包括切换面板到分离态、设置分离态UI布局、设置分离态热区、拖动分离态键盘、切换回固定态等功能。

## 约束与限制

分离态键盘从API版本26.1.0开始支持。在输入法应用已经创建面板的情况下，可以切换面板状态到分离态，分离态键盘面板宽度会自动调整为屏幕宽度，只能纵向移动。

## 框架原理

- 输入法应用可以调用[changeFlag](../reference/apis-ime-kit/js-apis-inputmethodengine.md#changeflag10)或[updatePanelRectSync](../reference/apis-ime-kit/js-apis-inputmethodengine.md#updatepanelrectsync)将面板切换至分离态。
- 分离态下，面板宽度强制等于屏幕宽度，面板仅可纵向移动（[moveTo](../reference/apis-ime-kit/js-apis-inputmethodengine.md#moveto10)仅y生效），支持[startMoving](../reference/apis-ime-kit/js-apis-inputmethodengine.md#startmoving15)拖动。
- 通过[updatePanelRect](../reference/apis-ime-kit/js-apis-inputmethodengine.md#updatepanelrect)或[updatePanelRectSync](../reference/apis-ime-kit/js-apis-inputmethodengine.md#updatepanelrectsync)设置分离态面板的位置和高度，宽度参数会被静默忽略。
- 通过[updateRegion](../reference/apis-ime-kit/js-apis-inputmethodengine.md#updateregion15)设置左右两部分区域为热区，中间镂空区域不接收触摸事件，触摸穿透到下层应用。

## 开发准备

在开始适配分离键盘前，需确保已完成以下准备工作：

- 已创建输入法应用工程，并成功创建SOFT_KEYBOARD类型的面板。
- 已了解[PanelFlag](../reference/apis-ime-kit/js-apis-inputmethodengine.md#panelflag10)枚举类型的基本概念。

## 开发步骤

### 切换面板到分离态

在实现一个输入法应用，并创建SOFT_KEYBOARD类型面板后，可以调用[changeFlag](../reference/apis-ime-kit/js-apis-inputmethodengine.md#changeflag10)或[updatePanelRectSync](../reference/apis-ime-kit/js-apis-inputmethodengine.md#updatepanelrectsync)将面板切换至分离态。切换成功后，面板宽度自动等于屏幕宽度，无需手动设置，建议使用updatePanelRectSync同时切换PanelFlag和设置键盘窗口高度。

<!-- @[input_case_detached_switchToDetachedPanel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/DetachedKeyboard/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->

``` TypeScript
public switchToDetachedPanel(): void {
  if (this.mPanel === undefined) {
    this.addLog('switchToDetachedPanel panel is undefined');
    return;
  }
  let dis: display.Display | undefined = undefined;
  try {
    dis = display.getPrimaryDisplaySync();
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`switchToDetachedPanel get display catch error: ${error.code} ${error.message}`);
    return;
  }
  if (dis === undefined) {
    this.addLog('switchToDetachedPanel display is undefined');
    return;
  }
  let screenWidth = dis.width;
  let screenHeight = dis.height;
  if (dis.width > dis.height) {
    screenWidth = dis.height;
    screenHeight = dis.width;
  }
  let detachedHeight = Math.floor(screenHeight * KEYBOARD_DETACHED_HEIGHT_RATE);
  let landHeight = Math.floor(screenWidth * KEYBOARD_DETACHED_HEIGHT_RATE)
  let landscapeRect: window.Rect = {
    left: 0,
    top: screenWidth - landHeight,
    width: screenHeight,
    height: landHeight
  };
  let portraitRect: window.Rect = {
    left: 0,
    top: screenHeight - detachedHeight,
    width: screenWidth,
    height: detachedHeight
  };
  let panelRect: inputMethodEngine.PanelRect = {
    landscapeRect: landscapeRect,
    portraitRect: portraitRect
  };
  try {
    this.mPanel.updatePanelRectSync(inputMethodEngine.PanelFlag.FLAG_DETACHED, panelRect);
    this.mPanelWidth = dis.width;
    this.mPanelHeight = dis.width > dis.height ? landHeight : detachedHeight;
    this.addLog(`switchToDetachedPanel success, width = ${dis.width}, height = ${detachedHeight}`);
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`switchToDetachedPanel catch error: ${error.code} ${error.message}`);
  }
  // 将左右两半键盘区域设置为热区，中间透明区域不接收输入事件
  this.refreshSplitHotZone(dis.width, detachedHeight);
}
```

### 设置分离态UI布局

分离态下，键盘UI需要根据`isSplitKeyboard`状态切换布局：左右两半键盘区域+中间透明镂空区域。键盘根组件背景在分离态下设为透明，使中间镂空区域可穿透显示下层应用内容。

<!-- @[input_case_detached_detached_ui](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/DetachedKeyboard/entry/src/main/ets/components/KeyMenu.ets) -->

``` TypeScript
// 分体键盘左半部分
@Builder
splitLeft() {
  Column({ space: this.inputStyle.keyGap }) {
    Row({ space: this.inputStyle.keyGap }) {
      ForEach(this.keyList.slice(0, 5), (item: keySourceListType) => {
        KeyItemNumber({ keyValue: item })
      }, (item: keySourceListType) => item.content)
    }
    .width('100%')
    .layoutWeight(1)

    Row({ space: this.inputStyle.keyGap }) {
      ForEach(this.keyList.slice(10, 15), (item: keySourceListType) => {
        KeyItemNumber({ keyValue: item })
      }, (item: keySourceListType) => item.content)
    }
    .width('100%')
    .layoutWeight(1)

    Row({ space: this.inputStyle.keyGap }) {
      Stack() {
        Image($rawfile(this.keyState === KeyState.ONCE_UPPER_CASE ? 'shift light.svg' : this.keyState === KeyState.UPPER_CASE ? 'shift light long.svg' : 'shift.svg'))
          .width(this.inputStyle.featurePicSize)
          .height(this.inputStyle.featurePicSize)
      }
      .backgroundColor($r('app.color.key_item_gray'))
      .borderRadius(4)
      .onClick(() => {
        if (this.keyState === KeyState.LOWER_CASE) {
          this.keyState = KeyState.ONCE_UPPER_CASE;
        } else if (this.keyState === KeyState.ONCE_UPPER_CASE) {
          this.keyState = KeyState.UPPER_CASE;
        } else if (this.keyState === KeyState.UPPER_CASE) {
          this.keyState = KeyState.LOWER_CASE;
        }
      })
      .height('100%')
      .layoutWeight(1.5)
      .shadow({ radius: 1, color: $r('app.color.shadow'), offsetY: 3 })
      .stateStyles({
        normal: normalStyles, pressed: pressedStyles
      })

      ForEach(this.keyList.slice(19, 23), (item: keySourceListType) => {
        KeyItemNumber({ keyValue: item })
      }, (item: keySourceListType) => item.content)
    }
    .width('100%')
    .layoutWeight(1)

    Row({ space: this.inputStyle.keyGap }) {
      KeyItem({ keyValue: { content: ',', title: ',', upperContent: ',' } })
      SpaceItem({ spaceWeight: 2.5 })
    }
    .width('100%')
    .layoutWeight(1)
  }
  .width('40%')
  .height('100%')
  .backgroundColor(this.styleMode === 1 ? '#D5D8DD' : '#ffffff')
  .borderRadius(16)
  .padding(this.inputStyle.keyGap)
}

// 分体键盘右半部分
@Builder
splitRight() {
  Column({ space: this.inputStyle.keyGap }) {
    Row({ space: this.inputStyle.keyGap }) {
      ForEach(this.keyList.slice(5, 10), (item: keySourceListType) => {
        KeyItemNumber({ keyValue: item })
      }, (item: keySourceListType) => item.content)
    }
    .width('100%')
    .layoutWeight(1)

    Row({ space: this.inputStyle.keyGap }) {
      ForEach(this.keyList.slice(15, 19), (item: keySourceListType) => {
        KeyItemNumber({ keyValue: item })
      }, (item: keySourceListType) => item.content)
    }
    .width('100%')
    .layoutWeight(1)

    Row({ space: this.inputStyle.keyGap }) {
      ForEach(this.keyList.slice(23), (item: keySourceListType) => {
        KeyItemNumber({ keyValue: item })
      }, (item: keySourceListType) => item.content)
      DeleteItem()
    }
    .width('100%')
    .layoutWeight(1)

    Row({ space: this.inputStyle.keyGap }) {
      KeyItem({ keyValue: { content: '.', title: '.', upperContent: '.' } })
      ReturnItem({ returnWeight: 2 })
    }
    .width('100%')
    .layoutWeight(1)
  }
  .width('40%')
  .height('100%')
  .backgroundColor(this.styleMode === 1 ? '#D5D8DD' : '#ffffff')
  .borderRadius(16)
  .padding(this.inputStyle.keyGap)
}

build() {
  if (this.isSplitKeyboard) {
    Column() {
      Row() {
        this.splitLeft()
        Column()
          .layoutWeight(1)
          .height('100%')
        this.splitRight()
      }
      .width('100%')
      .layoutWeight(1)
      .padding({
        left: this.inputStyle.paddingLeftRight,
        right: this.inputStyle.paddingLeftRight
      })
    }
    .width('100%')
    .height('100%')
  } else {
    Column() {
      Column({ space: this.inputStyle.keyGap }) {
      Row({ space: this.inputStyle.keyGap }) {
        ForEach(this.keyList.slice(0, 10), (item: keySourceListType) => {
          KeyItemNumber({ keyValue: item })
        }, (item: keySourceListType) => item.content)
      }
      .width('100%')
      .layoutWeight(1)

      Row({ space: this.inputStyle.keyGap }) {
        Stack() {
        }.layoutWeight(0.5)

        ForEach(this.keyList.slice(10, 19), (item: keySourceListType) => {
          KeyItemNumber({ keyValue: item })
        }, (item: keySourceListType) => item.content)
        Stack() {
        }.layoutWeight(0.5)
      }
      .width('100%')
      .layoutWeight(1)

      Row({ space: this.inputStyle.keyGap }) {
        Stack() {
          Image($rawfile(this.keyState === KeyState.ONCE_UPPER_CASE ? 'shift light.svg' : this.keyState === KeyState.UPPER_CASE ? 'shift light long.svg' : 'shift.svg'))
            .width(this.inputStyle.featurePicSize)
            .height(this.inputStyle.featurePicSize)
        }
        .backgroundColor($r('app.color.key_item_gray'))
        .borderRadius(4)
        .onClick(() => {
          if (this.keyState === KeyState.LOWER_CASE) {
            this.keyState = KeyState.ONCE_UPPER_CASE;
          } else if (this.keyState === KeyState.ONCE_UPPER_CASE) {
            this.keyState = KeyState.UPPER_CASE;
          } else if (this.keyState === KeyState.UPPER_CASE) {
            this.keyState = KeyState.LOWER_CASE;
          }
        })
        .height('100%')
        .layoutWeight(1.5)
        .shadow({ radius: 1, color: $r('app.color.shadow'), offsetY: 3 })
        .stateStyles({
          normal: normalStyles, pressed: pressedStyles
        })

        ForEach(this.keyList.slice(19), (item: keySourceListType) => {
          KeyItemNumber({ keyValue: item })
        }, (item: keySourceListType) => item.content)
        DeleteItem()
      }
      .width('100%')
      .layoutWeight(1)

      Row({ space: this.inputStyle.keyGap }) {
        KeyItem({ keyValue: { content: ',', title: ',', upperContent: ',' } })
        SpaceItem({ spaceWeight: 5 })
        KeyItem({ keyValue: { content: '.', title: '.', upperContent: '.' } })
        ReturnItem({ returnWeight: 2.5 })
      }
      .width('100%')
      .layoutWeight(1)

    }
    .width('100%')
    .layoutWeight(1)
    .padding({
      left: this.inputStyle.paddingLeftRight,
      right: this.inputStyle.paddingLeftRight,
      top: this.inputStyle.keyGap,
      bottom: this.inputStyle.keyGap
    })
    .backgroundColor(this.styleMode === 1 ? '' : '#ffffff')
    }
    .width('100%')
    .height('100%')
  }
}
```

### 设置分离态热区

分离键盘左右两部分区域为有效输入区域，中间镂空区域不接收触摸事件。通过[updateRegion](../reference/apis-ime-kit/js-apis-inputmethodengine.md#updateregion15)设置自定义热区。

<!-- @[input_case_detached_refreshSplitHotZone](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/DetachedKeyboard/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->

``` TypeScript
// 按分体面板尺寸刷新左右热区，中间透明区域不接收输入事件
public refreshSplitHotZone(width: number, height: number): void {
  if (this.mPanel === undefined) {
    this.addLog('refreshSplitHotZone panel is undefined');
    return;
  }
  if (width <= 0 || height <= 0) {
    this.addLog(`refreshSplitHotZone invalid size, width = ${width}, height = ${height}`);
    return;
  }
  let halfWidth = Math.floor(width * KEYBOARD_SPLIT_WIDTH_RATE);
  let inputRegion: window.Rect[] = [
    { left: 0, top: 0, width: halfWidth, height: height },
    { left: width - halfWidth, top: 0, width: halfWidth, height: height }
  ];
  try {
    this.mPanel.updateRegion(inputRegion);
    this.addLog(`refreshSplitHotZone success, width = ${width}, height = ${height}`);
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`refreshSplitHotZone catch error: ${error.code} ${error.message}`);
  }
}
```

### 拖动分离态键盘

分离态面板支持通过[startMoving](../reference/apis-ime-kit/js-apis-inputmethodengine.md#startmoving15)启动拖动模式。

通过startMoving启动拖动模式，用户可手指拖动调整键盘位置。拖动结束后调用[moveTo](../reference/apis-ime-kit/js-apis-inputmethodengine.md#moveto10)同步位置并刷新热区。

<!-- @[input_case_detached_startMovingPanel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/DetachedKeyboard/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->

``` TypeScript
public startMovingPanel(): void {
  if (this.mPanel === undefined) {
    this.addLog('startMovingPanel panel is undefined');
    return;
  }
  try {
    this.mPanel.startMoving();
    this.addLog('startMovingPanel success');
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`startMovingPanel catch error: ${error.code} ${error.message}`);
  }
}
```

### 切换回固定态

如需从分离态切换回固定态，调用updatePanelRectSync设置FLG_FIXED，并将热区恢复为整个面板区域。

<!-- @[input_case_detached_switchToFixedPanel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/DetachedKeyboard/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->

``` TypeScript
public switchToFixedPanel(): void {
  if (this.mPanel === undefined) {
    this.addLog('switchToFixedPanel panel is undefined');
    return;
  }
  let dis: display.Display | undefined = undefined;
  try {
    dis = display.getPrimaryDisplaySync();
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`switchToFixedPanel get display catch error: ${error.code} ${error.message}`);
    return;
  }
  if (dis === undefined) {
    this.addLog('switchToFixedPanel display is undefined');
    return;
  }
  let screenWidth = dis.width;
  let screenHeight = dis.height;
  if (dis.width > dis.height) {
    screenWidth = dis.height;
    screenHeight = dis.width;
  }
  let keyHeight = Math.floor(screenHeight * KEYBOARD_HEIGHT_RATE_PHONE);
  let landHeight = Math.floor(screenWidth * KEYBOARD_HEIGHT_RATE_PHONE)
  let landscapeRect: window.Rect = {
    left: 0,
    top: screenWidth - landHeight,
    width: screenHeight,
    height: landHeight
  };
  let portraitRect: window.Rect = {
    left: 0,
    top: screenHeight - keyHeight,
    width: screenWidth,
    height: keyHeight
  };
  let panelRect: inputMethodEngine.PanelRect = {
    landscapeRect: landscapeRect,
    portraitRect: portraitRect
  };
  try {
    this.mPanel.updatePanelRectSync(inputMethodEngine.PanelFlag.FLG_FIXED, panelRect);
    this.addLog(`switchToFixedPanel success`);
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`switchToFixedPanel catch error: ${error.code} ${error.message}`);
  }
  // 恢复普通键盘后，将热区重置为整个面板区域
  let inputRegion: window.Rect[] = [
    { left: 0, top: 0, width: dis.width, height: keyHeight }
  ];
  try {
    this.mPanel.updateRegion(inputRegion);
    this.addLog('switchToFixedPanel updateRegion success');
  } catch (err) {
    let error = err as BusinessError;
    this.addLog(`switchToFixedPanel updateRegion catch error: ${error.code} ${error.message}`);
  }
}
```

## 实现效果

![分离态键盘](./figures/detached_keyboard.jpeg)
