# SecurityUIExtensionComponent

**SecurityUIExtensionComponent**用于将其他应用提供的UI嵌入到当前页面中。显示的内容运行在另一个进程中，当前应用不参与其布局和渲染。 通常用于需要进程隔离的模块化开发场景。目前，**SecurityUIExtensionComponent**只能启动PhotoPicker类型的**UIExtensionAbility**。

## 子组件 无

## SecurityUIExtensionComponent

```TypeScript
SecurityUIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: SecurityUIExtensionOptions
  )
```

创建**SecurityUIExtensionComponent**组件，用于嵌入显示远程**UIExtensionAbility**提供的UI。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionComponentInterface-(    want: import('../api/@ohos.app.ability.Want').default,    options?: SecurityUIExtensionOptions  ): SecurityUIExtensionComponentAttribute--><!--Device-SecurityUIExtensionComponentInterface-(    want: import('../api/@ohos.app.ability.Want').default,    options?: SecurityUIExtensionOptions  ): SecurityUIExtensionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | import('../api/@ohos.app.ability.Want').default | 是 | 要加载的Ability信息。 通过bundleName和abilityName共同确定被拉起的UIExtensionAbility， 同时需要在parameters中配置ability.want.params.uiExtensionType字段指定UIExtensionAbility的类型， 当前仅支持'sysPicker/photoPicker'。 |
| options | [SecurityUIExtensionOptions](arkts-arkui-securityuiextensionoptions-i-sys.md) | 否 | 用于构造**SecurityUIExtensionComponent**的参数。不填时各字段使用默认值。 |

## 汇总

- [SecurityUIExtensionOptions](arkts-arkui-securityuiextensionoptions-i-sys.md)
- [SecurityUIExtensionProxy](arkts-arkui-securityuiextensionproxy-i-sys.md)
- [TerminationInfo](arkts-arkui-terminationinfo-i-sys.md)
- [SecurityDpiFollowStrategy](arkts-arkui-securitydpifollowstrategy-e-sys.md)
