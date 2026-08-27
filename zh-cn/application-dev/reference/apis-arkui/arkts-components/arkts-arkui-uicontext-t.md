# UIContext

```TypeScript
declare type UIContext = import('../api/@ohos.arkui.UIContext').UIContext
```

UIContext

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**属性类型：** import('../api/@ohos.arkui.UIContext').UIContext

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let uiContext: UIContext = this.getUIContext();
  }

  build() {
    // ...
  }
}
```
