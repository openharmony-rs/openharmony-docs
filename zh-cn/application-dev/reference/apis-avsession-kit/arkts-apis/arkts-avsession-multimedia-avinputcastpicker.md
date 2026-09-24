# @ohos.multimedia.avInputCastPicker

录音设备选择组件


## 导入模块

```TypeScript
import { AVInputCastPicker } from '@kit.AVSessionKit';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AVInputCastPicker](arkts-avsession-multimedia-avinputcastpicker-avinputcastpicker-s.md) | 录音设备选择组件，可用于切换音频输入设备。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnPickerStateCallback](arkts-avsession-onpickerstatecallback-t.md) | Callback for picker state |

## 示例

录音设备选择组件功能的示例说明参考如下。

```TypeScript
import { AVCastPickerState, AVInputCastPicker } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {

  @State pickerImage: ResourceStr = $r('app.media.layered_image'); // 自定义资源。

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
        AVInputCastPicker({
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
