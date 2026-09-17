# requestAutoFill

## Modules to Import

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## requestAutoFill

```TypeScript
export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void
```

Trigger an auto fill request.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | Indicates the ui context where the filling operation will be performed. |
| request | [FillRequest](arkts-ability-autofillmanager-fillrequest-t.md) | Yes | Indicates the struct of automatic filling request. |
| callback | [AutoFillCallback](arkts-ability-autofillmanager-autofillcallback-i.md) | No | Indicates the callback that used to receive the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Configure request based on the actual project.
let request: autoFillManager.FillRequest = {
  type: autoFillManager.AutoFillType.USER_NAME,
  viewData: {
    bundleName: "com.example.testBundleName",
    pageUrl: "testPageUrl",
    pageNodeInfos: [
      {
        id: 1,
        autoFillType: autoFillManager.AutoFillType.USER_NAME,
        value: "testValue1",
        placeholder: "testPlaceholder1",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      },
      {
        id: 2,
        autoFillType: autoFillManager.AutoFillType.PASSWORD,
        value: "testValue2",
        placeholder: "testPlaceholder2",
        rect: {
          left: 1,
          top: 1,
          width: 1,
          height: 1,
        },
        isFocus: false
      }
    ],
    pageRect: {
      left: 1,
      top: 1,
      width: 1,
      height: 1
    }
  }
}
// Define the AutoFill callback.
let callback: autoFillManager.AutoFillCallback = {
  onSuccess: (viewData: autoFillManager.ViewData) => {
    console.info(`fill request on success, viewData: ${JSON.stringify(viewData)}`);
  },
  onFailure: (result: autoFillManager.FillFailureResult) => {
    console.error(`fill request on failure, result: ${JSON.stringify(result)}`);
  }
};

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  build() {
    GridRow({ gutter: { y: 20 } }) {
      GridCol({ span: 20 }) {
        Button('requestAutoFill')
          .onClick(() => {
            try {
              // Initiate the fill request.
              autoFillManager.requestAutoFill(this.uiContext, request, callback);
            } catch (error) {
              console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
    }
  }
}
```
