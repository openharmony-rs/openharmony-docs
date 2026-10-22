# requestAutoFill

## 导入模块

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## requestAutoFill

```TypeScript
export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void
```

触发自动填充请求。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-autoFillManager-export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void--><!--Device-autoFillManager-export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | Indicates the ui context where the filling operation will be performed. |
| request | [FillRequest](arkts-ability-autofillmanager-fillrequest-t.md) | 是 | Indicates the struct of automatic filling request. |
| callback | [AutoFillCallback](arkts-ability-autofillmanager-autofillcallback-i.md) | 否 | Indicates the callback that used to receive the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
// Index.ets
import { autoFillManager } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// request需按照实际工程配置
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
// 定义自动填充回调
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
              // 发起填充请求
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
