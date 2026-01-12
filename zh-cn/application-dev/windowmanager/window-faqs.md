# 窗口开发常见问题
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 如何在应用A启动过程中拉起另一个应用B

**解决措施**

应用A调用[on('windowStageEvent')](../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageevent9)接口监听[WindowStageEvent.ACTIVE](../reference/apis-arkui/arkts-apis-window-e.md#windowstageeventtype9)事件后调用[startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability)接口拉起应用B。

**代码示例**

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
            // 监听应用A切换到ACTIVE状态
            if (eventType === window.WindowStageEventType.ACTIVE) {
                try {
                    // 拉起应用B
                    this.context.startAbility(want, options, (err: BusinessError) => {
                        if (err.code) {
                            // 处理业务逻辑错误
                            console.error(`Failed to start ability, code is ${err.code}, message is ${err.message}.`);
                            return;
                        }
                        // 执行正常业务
                        console.info('Succeeded in starting Ability.');
                    });
                } catch (err) {
                    // 处理入参错误异常
                    let code = (err as BusinessError).code;
                    let message = (err as BusinessError).message;
                    console.error(`Failed to start ability, code is ${code}, message is ${message}.`);
                }
            }
        });
    }
}
```

