# enterKioskMode

## Modules to Import

```TypeScript
import { kioskManager } from '@kit.AbilityKit';
```

## enterKioskMode

```TypeScript
function enterKioskMode(context: UIAbilityContext): Promise<void>
```

Enters kiosk mode. This API uses a promise to return the result. This API can be properly called only on phones, PC/2-in-1 devices, and tablets. On other devices, it returns the error code 801.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) | Yes | Context of the UIAbility that needs to enter kiosk mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Failed to connect to the system service. |
| [16000110](../errorcode-ability.md#16000110-application-is-not-in-the-kiosk-mode-list) | The current application is not in Kiosk app list and cannot enter Kiosk mode. |
| [16000111](../errorcode-ability.md#16000111-application-is-already-in-kiosk-mode) | The system is already in Kiosk mode and cannot enter Kiosk mode again. |
| [16000113](../errorcode-ability.md#16000113-ability-is-not-in-the-foreground) | Current ability is not in foreground.<br>**Applicable version:** 20 - 26.0.0 |

**Examples**

```TypeScript
import { common, kioskManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private uiAbilityContext: common.UIAbilityContext | undefined =
    this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Button('enterKioskMode').margin({ top: 30 })
        .onClick(() => {
          kioskManager.enterKioskMode(this.uiAbilityContext)
            .then(() => {
              hilog.info(0x0000, 'testTag', '%{public}s', 'enterKioskMode success');
            })
            .catch((error: BusinessError) => {
              hilog.error(0x0000, 'testTag', '%{public}s', `enterKioskMode failed. Code: ${error.code}, message: ${error.message}`);
            });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
