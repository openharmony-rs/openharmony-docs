# Window Development FAQs
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## How to Launch Application B During the Startup of Application A

**Solution**

Application A can call the [on('windowStageEvent')](../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageevent9) API to listen for the [WindowStageEvent.ACTIVE](../reference/apis-arkui/arkts-apis-window-e.md#windowstageeventtype9) event and then call the [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) API to launch application B.

**Code Example**

```ts
// applicationA EntryAbility.ts
export default class EntryAbility extends UIAbility {

    context = getConText(this) as common.UIAbilityContext;

    onWindowStageCreate(windowStage: window.WindowStage): void {
        let want: Want = {
            deviceId: '',
            bundleName: 'com.example.applicationB',
            abilityName: 'EntryAbility'
        };

        let options: StartOptions = {
            displayId: 0
        };

        windowStage.on('windowStageEvent', (data) => {
            let eventType: window.WindowStageEventType = data;
            // Listen for Application A switching to the ACTIVE state.
            if (eventType === window.WindowStageEventType.ACTIVE) {
                try {
                    // Launch application B.
                    this.context.startAbility(want, options, (err: BusinessError) => {
                        if (err.code) {
                            // Handle service logic errors.
                            console.error(`Failed to start ability, code is ${err.code}, message is ${err.message}.`);
                            return;
                        }
                        // Carry out normal service processing.
                        console.info('Succeeded in starting Ability.');
                    });
                } catch (err) {
                    // Handle input parameter errors.
                    let code = (err as BusinessError).code;
                    let message = (err as BusinessError).message;
                    console.error(`Failed to start ability, code is ${code}, message is ${message}.`);
                }
            }
        });
    }
}
```
