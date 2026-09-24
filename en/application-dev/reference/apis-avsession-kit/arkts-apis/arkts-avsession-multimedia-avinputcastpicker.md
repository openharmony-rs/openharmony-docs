# @ohos.multimedia.avInputCastPicker

## Modules to Import

```TypeScript
import { AVInputCastPicker } from '@kit.AVSessionKit';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [AVInputCastPicker](arkts-avsession-multimedia-avinputcastpicker-avinputcastpicker-s.md) | Picker used to show available input devices. @struct { AVInputCastPicker } |

### Types

| Name | Description |
| --- | --- |
| [OnPickerStateCallback](arkts-avsession-onpickerstatecallback-t.md) | Callback for picker state |

## Examples

The following is an example of using AVCastPicker:

```TypeScript
import { AVCastPickerState, AVInputCastPicker } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {

  @State pickerImage: ResourceStr = $r('app.media.layered_image'); // Custom resources.

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
