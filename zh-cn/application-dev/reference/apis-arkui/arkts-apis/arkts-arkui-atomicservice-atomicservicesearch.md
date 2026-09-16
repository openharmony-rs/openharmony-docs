# @ohos.atomicservice.AtomicServiceSearch(This section describes the interfaces used by AtomicServiceSearch)

## 导入模块

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceSearch](arkts-arkui-atomicservice-atomicservicesearch-atomicservicesearch-s.md) | AtomicServiceSearch为开发者提供满足定制化需求的功能，内容包括默认显示的搜索区、可自定义的选择区和功能区（最多两个）。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [InputFilterParams](arkts-arkui-atomicservice-atomicservicesearch-inputfilterparams-i.md) | 搜索框过滤设置项。 |
| [MenuAlignParams](arkts-arkui-atomicservice-atomicservicesearch-menualignparams-i.md) | 下拉按钮与下拉菜单间的对齐方式设置项。 |
| [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md) | AtomicServiceSearch中“功能区”的初始化参数。 |
| [SearchButtonParams](arkts-arkui-atomicservice-atomicservicesearch-searchbuttonparams-i.md) | 搜索框末尾搜索按钮设置项。 |
| [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md) | AtomicServiceSearch中“搜索区”的可选属性。 |
| [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md) | AtomicServiceSearch中“选择区”的可选属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | 文本内容滚动时，触发该回调。 |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | 进行粘贴操作时，触发该回调。 |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | 下拉菜单选中某一项的回调。 |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 文本选择的位置发生变化或编辑状态下光标位置发生变化时，触发该回调。 |

## 示例

```TypeScript
### 示例1（AtomicServiceSearch添加选择区）

该示例通过select参数为AtomicServiceSearch组件添加左侧选择区。


```

```TypeScript
### 示例2（AtomicServiceSearch添加功能位）

该示例通过operation参数为AtomicServiceSearch组件添加右侧功能位。


```

```TypeScript
### 示例3（AtomicServiceSearch添加选择区及功能位）

该示例中为AtomicServiceSearch组件同时添加左侧选择区和右侧功能位。


```

```TypeScript
### 示例4（search回调事件）

该示例通过onWillInsert、onDidInsert、onWillDelete、onDidDelete接口实现了插入和删除的功能。

通过onSubmit接口实现了搜索区内容提交的功能。

通过onChange接口实现了监听搜索区内容变化的功能。


```

```TypeScript
### 示例5（AtomicServiceSearch修改样式）

该示例通过search、select、value、placeholder参数实现了AtomicServiceSearch组件样式的自定义。


```

```TypeScript
### 示例6（通过controller实现光标位置的设置）

该示例通过controller参数实现了光标位置的设置、选择指定区域中的内容及关闭编辑状态的功能。


```

```TypeScript
### 示例7（设置输入法回车键类型）

该示例通过enterKeyType属性实现了动态切换输入法回车键的效果。


```

```TypeScript
### 示例8（设置文字特性效果）

该示例通过fontFeature属性实现了文本在不同文字特性下的展示效果。


```

```TypeScript
### 示例9（设置文本自适应）

该示例通过minFontSize、maxFontSize属性展示了文本自适应字号的效果。


```

```TypeScript
### 示例10（文本扩展自定义菜单）

该示例通过editMenuOptions接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能。


```

```TypeScript
### 示例11（设置文本水平对齐/光标样式/选中背景色）

该示例通过textAlign、caretStyle、selectedBackgroundColor属性展示如何设置文本的水平对齐、光标样式和选中背景色。


```

```TypeScript
### 示例12（对输入的文本进行过滤）

该示例通过inputFilter属性展示如何对输入的文本进行内容的过滤，以限制输入内容。
```
