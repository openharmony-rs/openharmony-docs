# getContext

## getContext

```TypeScript
declare function getContext(component?: Object): Context
```

Obtains the Context object associated with a component on the page.

**起始版本：** 11

**废弃版本：** 18

**替代接口：** getHostContext

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | Object | 否 | indicate the component on the page.<br/>If no component is passed in or the passed-in parameter type is invalid, the default context is returned.<br/>The default context is the context obtained by tracing the call chain of the API.<br/>If this API is used in an asynchronous callback or not initially called on the current page, the context of the<br/>instance may fail to be traced. In this case, undefined is returned. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Context | The context type depends on the ability type.<br/>For example, if this API is called on a page of the UIAbility, the return value type is UIAbilityContext;<br/>if this API is called on a page of the ExtensionAbility, the return value type is ExtensionContext. |

