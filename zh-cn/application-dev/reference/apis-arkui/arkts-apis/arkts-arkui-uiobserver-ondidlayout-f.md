# on_didLayout

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## on('didLayout')

```TypeScript
export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void
```

监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void--><!--Device-uiObserver-export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| context | [UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  didLayoutCallback = () => {
    console.info("Layout布局完成");
  }
  build() {
    Column() {
      Button('注册布局完成监听')
        .onClick(() => {
          uiObserver.on('didLayout', this.getUIContext(), this.didLayoutCallback);
        })
    }
  }
}
```

