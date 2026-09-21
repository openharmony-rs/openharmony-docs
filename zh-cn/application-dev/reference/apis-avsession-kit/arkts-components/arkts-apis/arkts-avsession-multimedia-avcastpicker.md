# @ohos.multimedia.avCastPicker

## 导入模块

```TypeScript
import { AVCastPicker } from '@kit.AVSessionKit';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AVCastPicker](arkts-avsession-multimedia-avcastpicker-avcastpicker-s.md) | 本模块提供创建投播组件AVCastPicker的功能，提供设备发现连接的统一入口。 |

## 示例

投播功能的示例说明参考如下。

```TypeScript
import { AVCastPickerState, AVCastPicker } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {

  @State pickerImage: ResourceStr = $r('app.media.castPicker'); // 自定义资源。

  private onStateChange(state: AVCastPickerState) {
    if (state == AVCastPickerState.STATE_APPEARING) {
      console.info('The picker starts showing.');
    } else if (state == AVCastPickerState.STATE_DISAPPEARING) {
      console.info('The picker finishes presenting.');
    }
  }

  @Builder
  customPickerBuilder() {
    Image(this.pickerImage)
      .width('100%')
      .height('100%')
      .fillColor(Color.Black)
  }

  build() {
    Row() {
      Column() {
        AVCastPicker({
          normalColor: Color.Red,
          customPicker: () => this.customPickerBuilder(),
          onStateChange: this.onStateChange
        })
          .width('40vp')
          .height('40vp')
          .border({ width: 1, color: Color.Red })
      }.height('50%')
    }.width('50%')
  }
}
```
