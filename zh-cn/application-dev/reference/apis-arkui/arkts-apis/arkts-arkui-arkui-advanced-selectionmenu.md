# @ohos.arkui.advanced.SelectionMenu

## 导入模块

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [SelectionMenu](arkts-arkui-arkui-advanced-selectionmenu-selectionmenu-f.md) | 入参为空时，文本选择菜单组件SelectionMenu内容区大小及组件大小为零。例如，富文本组件RichEditor使用bindSelectionMenu接口绑定一个SelectionMenu的右键菜单，则右键富文本组件区域时无任何菜单弹出。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | 选中内容信息。 |
| [EditorMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-editormenuoptions-i.md) | 编辑菜单选项。 |
| [ExpandedMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-expandedmenuoptions-i.md) | 扩展下拉菜单。 |
| [SelectionMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | SelectionMenuOptions定义SelectionMenu的可选菜单类型项及其配置参数。 |

## 示例

```TypeScript
### 示例1（RichEditor绑定不同触发方式的自定义文本选择菜单）

该示例展示了文本绑定不同触发方式的自定义文本选择菜单的效果。

> 说明：
> 
> 系统暂未预置加粗、斜体等图标，示例代码使用本地资源图标，开发者使用时需自行替换editorMenuOptions中icon项的资源。
> 
> 示例图为鼠标操作触发的自定义菜单弹出效果。


```

```TypeScript
### 示例2（设置Symbol类型图标）

从API version 18开始，该示例通过设置EditorMenuOptions的属性symbolStyle，展示了使用系统Symbol图标的方法。


```

```TypeScript
### 示例3（设置背景板材质）

该示例通过设置SelectionMenuOptions的属性backgroundSystemMaterial，展示了超薄样式的背景板材质。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，SelectionMenuOptions新增backgroundSystemMaterial属性。
```
