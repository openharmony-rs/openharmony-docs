# AbilityComponent (System API)

独立显示Ability的容器。

> **说明：** 
> 
> 从API version 10开始，该组件不再维护，推荐使用[UIExtensionComponent](arkts-arkui-uiextensioncomponent-comp-sys.md#ui_extension_componentsystem-api)。
> 
> 本模块为系统接口。

## 使用约束

AbilityComponent为独立层次渲染，不能在之上叠加其他显示内容。

AbilityComponent不支持处理输入事件，事件不经过当前Ability，直接分发给内部的Ability处理。

AbilityComponent需设置且只能设置width、height，且width、height不支持动态更新。

被拉起的Ability必须继承[WindowExtension](../arkts-apis/arkts-arkui-application-windowextensionability-windowextensionability-c-sys.md)。

## 子组件

无

## AbilityComponent

```TypeScript
AbilityComponent(value: { want: import('../api/@ohos.app.ability.Want').default })
```

创建AbilityComponent。当AbilityComponent被使用时调用。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [UIExtensionComponentInterface](arkts-arkui-uiextensioncomponent-comp-sys.md#uiextensioncomponentinterface)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { want: import('../api/@ohos.app.ability.Want').default } | 是 | 默认加载的Ability描述。 |

## 汇总

## 示例

```TypeScript
// xxx.ets
@Entry
@Component
struct MyComponent {

  build() {
      Column() {
          AbilityComponent({
              want: {
                  bundleName: '',
                  abilityName: ''
              },
          })
          .onConnect(() => {
              console.log('AbilityComponent connect')
          })
          .onDisconnect(() => {
              console.log('AbilityComponent disconnect')
          })
      }
  }
}
```
