# UI组件适配（特殊场景）

## 使用UIContext提供替代接口

在ArkTS-Sta中，部分废弃接口需要使用UIContext提供的接口作为替代。

### 废弃接口在自定义组件内使用

废弃接口在自定义组件内使用时，推荐使用[getUIContext()](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext)方法获取UIContext实例，再通过此实例调用对应方法来作为替代。

ArkTS-Dyn示例：

```typescript
@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context: Context = getContext(this) as Context;
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Row,
  Column,
  Text,
  FontWeight,
  Context,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            // 在自定义组件内使用，推荐使用getUIContext()方法获取UIContext实例
            let context: Context = this.getUIContext().getHostContext() as Context;
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 废弃接口在自定义组件外使用

废弃接口在自定义组件外使用时，由于getUIContext()方法只能在自定义组件内使用，推荐使用[getFocusedUIContext()](../reference/apis-arkui/js-apis-arkui-UIContext.md#getfocuseduicontext20)方法获取UIContext实例。getFocusedUIContext()可以在自定义组件内使用，也能在自定义组件外使用。

ArkTS-Dyn示例：

```typescript
let context: Context = getContext() as Context;

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
'use static'
import {
  Entry,
  Component,
  State,
  Row,
  Column,
  Text,
  FontWeight,
  Context,
  UIContext,
} from '@kit.ArkUI';

// 在自定义组件外使用，推荐使用getFocusedUIContext()方法获取UIContext实例
let context: Context = UIContext.getFocusedUIContext()!.getHostContext() as Context;

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

在[从ArkTS-Dyn到ArkTS-Sta的UI语法规则适配](arkts-dyn-sta-ui-rules.md)中，由于迁移工具无法判断废弃接口的使用场景，所以使用getFocusedUIContext()获取UIContext实例。

对于开发者，推荐根据实际场景去选择适配方法。