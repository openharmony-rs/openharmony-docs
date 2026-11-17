# getContext

## getContext

```TypeScript
declare function getContext(component?: Object): Context
```

获取与页面上下文组件关联的Context对象。

**起始版本：** 11

**废弃版本：** 18

**替代接口：** [getHostContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#gethostcontext)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare function getContext(component?: Object): Context--><!--Device-unnamed-declare function getContext(component?: Object): Context-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | Object | 否 | 当前自定义组件的实例。当需要获取指定自定义组件关联的Context时，传入该组件实例；不传入component或传入的参数类型非法时，返回默认上下文。默认上下文是指通过追溯当前方法的调用链所跟踪到的Context。传入component时返回该组件关联的Context，不传入时返回通过当前方法调用链跟踪到的默认上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](arkts-arkui-common-comp-context-t.md) | 返回当前组件所在Ability的Context，Context的具体类型为当前Ability关联的Context对象。例如：在UIAbility（用户界面Ability）窗口中的页面调用该接口，返回类型为UIAbilityContext；在ExtensionAbility（扩展Ability）窗口中的页面调用该接口，返回类型为ExtensionContext。 |
