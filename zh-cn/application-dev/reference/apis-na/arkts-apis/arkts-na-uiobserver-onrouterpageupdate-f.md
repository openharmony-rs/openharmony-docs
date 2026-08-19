# onRouterPageUpdate

## 导入模块

```TypeScript
```

## onRouterPageUpdate

```TypeScript
export function onRouterPageUpdate(context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void
```

监听router中page页面的状态变化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onRouterPageUpdate(context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void--><!--Device-uiObserver-export function onRouterPageUpdate(context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) \| [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;RouterPageInfo&gt; | 是 | 回调函数。携带pageInfo，返回当前的page页面状态。 |

