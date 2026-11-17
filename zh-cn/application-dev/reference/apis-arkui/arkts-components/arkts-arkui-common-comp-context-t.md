# Context

```TypeScript
declare type Context = import('../api/application/Context').default
```

返回当前组件所在Ability的Context，Context的具体类型为当前Ability关联的Context对象。例如：在UIAbility窗口中的页面调用该接口，返回类型为UIAbilityContext。在ExtensionAbility窗口中的页面调用该接口，返回类型为ExtensionContext。

**类型：** import('../api/application/Context').default

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare type Context = import('../api/application/Context').default--><!--Device-unnamed-declare type Context = import('../api/application/Context').default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
