# offRouterPageUpdate

## offRouterPageUpdate

```TypeScript
export function offRouterPageUpdate(context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void
```

取消监听router中page页面的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offRouterPageUpdate(context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void--><!--Device-uiObserver-export function offRouterPageUpdate(context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RouterPageInfo&gt; | 否 | 需要被注销的回调函数。 |

