# animateToImmediately

## animateToImmediately

```TypeScript
declare function animateToImmediately(value: AnimateParam, event: () => void): void
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | AnimateParam | 是 | Animation settings. |
| event | () =&gt; void | 是 | Closure function that displays the animation. The system automatically inserts a<br/>transition animation for state changes caused by the closure function. |

