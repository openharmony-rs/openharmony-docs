# ReuseOptions

复用选项，用于配置复用标识ID，相同复用标识ID的组件会被互相复用，提高复用匹配的精确度。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## reuseId

```TypeScript
reuseId? : ReuseIdCallback
```

复用标识ID，相同复用标识ID的V2自定义组件会被互相复用。默认的复用标识ID为自定义组件名。在API版本26.0.0之前，当reuseId不是显式返回字符串字面量的回调方法时，实际的复用标识ID为该自定义组件的名称。例如，`Child().reuse({ reuseId: () =&gt; getReuseId() })`的实 际复用标识ID为`"Child"`。在API版本26.0.0及以后，支持将非显式返回字符串字面量形式的reuseId作为实际的复用标识ID。例如，`Child().reuse({ reuseId: () =&gt; getReuseId() })`的实际复用标识ID为 `getReuseId()`的返回结果。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
