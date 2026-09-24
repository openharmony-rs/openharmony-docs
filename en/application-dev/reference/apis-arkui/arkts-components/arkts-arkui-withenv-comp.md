# WithEnv(Define the WithEnv component that allows setting environment properties for child components.)

The **WithEnv** component is used to set a local environment variable scope for a child component tree. Developers can use this component to provide custom environment variables for descendant components, or set system environment variables.

> **NOTE** > > - Custom environment variables can be set through [customEnv](arkts-arkui-withenv-comp-attribute.md#customenv). > - System environment variable keys can be set through [env](arkts-arkui-withenv-comp-attribute.md#env). They are stored in > [WritableEnvKey](arkts-arkui-common-comp-writableenvkey-c.md). > - When **WithEnv** is nested, the nearest scope takes effect for environment variables with the same name.

## Summary

## Examples

### Example 1: Setting Local Font Scale

This example uses  to set a local font scale for components within the scope.

Since API version 26.0.0, the env attribute and the key WritableEnvKey.FONT_SCALE are added.

```TypeScript
// xxx.ets
import { WithEnv } from '@kit.ArkUI';
@Entry
@Component
struct WithEnvExample1 {
  @State fontScale: number = 1.0;

  build() {
    Column({ space: 12 }) {
      Row({ space: 8 }) {
        Button('Zoom out 0.5x')
          .onClick(() => {
            this.fontScale = 0.5;
          })
        Button('Normal 1.0x')
          .onClick(() => {
            this.fontScale = 1.0;
          })
        Button('Zoom in 1.5x')
          .onClick(() => {
            this.fontScale = 1.5;
          })
      }

      WithEnv() {
        Column({ space: 8 }) {
          Text('Text within the current font scale scope')
            .fontSize(16)
          Text('This text is also affected by the WithEnv font scaling')
            .fontSize(14)
            .fontColor('#99182431')
        }
        .width('100%')
        .alignItems(HorizontalAlign.Start)
      }
      .env(WritableEnvKey.FONT_SCALE, this.fontScale) // Set the local font scale ratio.
    }
    .padding(12)
    .width('100%')
  }
}
```

### Example 2: Setting Local Layout Direction

This example uses  to set the local layout direction for components within the scope.

Since API version 26.0.0, the env attribute and the key WritableEnvKey.DIRECTION are added.

```TypeScript
// xxx.ets
import { WithEnv } from '@kit.ArkUI';

@Entry
@Component
struct WithEnvExample2 {
  @State directionValue: Direction = Direction.Ltr;

  build() {
    Column({ space: 12 }) {
      Row({ space: 10 }) {
        Column().backgroundColor('#F0FAFF').width(60).height('100%')
        Column().backgroundColor('#2787D9').width(60).height('100%')
        Column().backgroundColor('#004AAF').width(60).height('100%')

      }.backgroundColor('#D5D5D5').width(200).height(50)

      WithEnv() {
        Row({ space: 10 }) {
          Column().backgroundColor('#F0FAFF').width(60).height('100%')
          Column().backgroundColor('#2787D9').width(60).height('100%')
          Column().backgroundColor('#004AAF').width(60).height('100%')

        }.backgroundColor('#D5D5D5').width(200).height(50)
      }
      .env(WritableEnvKey.DIRECTION, this.directionValue) // Set local layout direction.

      Button('change direction').onClick(() => {
        if (this.directionValue === Direction.Ltr) {
          this.directionValue = Direction.Rtl;
        } else {
          this.directionValue = Direction.Ltr;
        }
      })
    }
    .width('80%')
    .height('30%')
  }
}
```
