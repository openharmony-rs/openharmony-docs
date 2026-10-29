# WeakRefCallback（系统接口）

```TypeScript
type WeakRefCallback = (weakRef: WeakRef<object>) => void
```

接收被销毁对象的弱引用的回调

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type WeakRefCallback = (weakRef: WeakRef<object>) => void--><!--Device-unnamed-type WeakRefCallback = (weakRef: WeakRef<object>) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| weakRef | WeakRef&lt;object&gt; | 是 | WeakRef of one object. |
