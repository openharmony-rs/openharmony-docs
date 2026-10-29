# Preset Global Hotkey Development (for System Applications Only)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6013a617915ce1f228ac64fe8f5635f01779d382 translatedAt=2026-09-28T02:27:26.106Z pushedAt=2026-09-29T01:38:54.212Z -->

## When to Use

You can use the preset global hotkeys to set the delay time for starting an ability. An example is to take a screenshot 5 seconds after the hotkey is pressed.

## Modules to Import

```js
import { shortKey } from '@kit.InputKit';
```

## Available APIs

The following table lists common APIs for system preset global shortcut keys. For details, see [@ohos.multimodalInput.shortKey (Preset Global Shortcut Keys) (System API)](../../reference/apis-input-kit/js-apis-shortKey-sys.md).

| API | Description|
| ------------------------------------------------------------ | -------------------------- |
| setKeyDownDuration(businessKey: string, delay: number, callback: AsyncCallback&lt;void&gt;): void |Sets the delay for starting an ability using the hotkey.|

## How to Develop

The following describes how to take a screenshot five seconds after the hotkey is pressed.

```js
import { shortKey } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            shortKey.setKeyDownDuration('screenshot', 5000, (error: BusinessError) => { // Set the delay time of the screenshot application to 5 seconds (5000 milliseconds).
              if (error) {
                console.error(`Set key down duration failed, error: ${JSON.stringify(error, ["code", "message"])}`);
                return;
              }
              console.info(`Set key down duration success`);
            });
          } catch (error) {
            console.error(`Set key down duration failed, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```


