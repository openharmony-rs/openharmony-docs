# @ohos.app.ability.UIExtensionContentSession

UIExtensionContentSession是[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)组件的界面
 操作类，提供页面加载、设置宿主应用（UIExtensionAbility组件的拉起方）窗口隐私模式等功能。当宿主应用拉起指定的UIExtensionAbility组件时，系统创建UIExtensionContentSession对象
 ，并通过[onSessionCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate)回调传递给开发者。一个
 UIExtensionAbility组件对应一个UIExtensionContentSession对象，每个UIExtensionAbility组件的UIExtensionContentSession对象之间互不影响。


## 导入模块

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | UIExtensionAbility组件的界面操作类，提供页面加载、设置宿主应用窗口隐私模式等功能。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c-sys.md) | UIExtensionAbility组件的界面操作类，提供页面加载、设置宿主应用窗口隐私模式等功能。 |
<!--DelEnd-->
