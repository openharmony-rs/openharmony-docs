# @ohos.selectionInput.SelectionExtensionContext(划词扩展上下文)

## 导入模块

```TypeScript
import { SelectionExtensionContext } from '@kit.BasicServicesKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SelectionExtensionContext(划词扩展上下文)](arkts-basicservices-selectioninput-selectionextensioncontext-selectionextensioncontext-c.md) | SelectionExtensionContext是 [SelectionExtensionAbility](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c.md)的上下文，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。每个SelectionExtensionAbility组件实例化时，系统都会自动创建对应的SelectionExtensionContext。开发者可以通过SelectionExtensionContext调用 [startAbility](arkts-basicservices-selectioninput-selectionextensioncontext-selectionextensioncontext-c.md#startability)接口拉起同应用内其他Ability。适用于在划词扩展场景中需要跳转至应用内其他Ability的情况，帮助用户在划词 操作后快速获取与划词内容关联的功能或信息。 |
