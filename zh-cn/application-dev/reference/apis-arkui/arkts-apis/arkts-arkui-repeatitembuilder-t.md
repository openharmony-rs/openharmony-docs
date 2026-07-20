# RepeatItemBuilder

```TypeScript
declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void
```

组件生成函数类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void--><!--Device-unnamed-declare type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| repeatItem | [RepeatItem](arkts-arkui-repeatitem-i.md)&lt;T&gt; | 是 | 将item和index结合到一起的一个状态变量。<br/>缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。  |

