# PatternOptions

输入法模式选项配置，用于定义键盘模式的切换选项。

**起始版本：** 11

<!--Device-unnamed-export interface PatternOptions--><!--Device-unnamed-export interface PatternOptions-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { Pattern, InputMethodListDialog, PatternOptions } from '@kit.IMEKit';
```

## action

```TypeScript
action: (index: number) => void
```

模式选项改变时的回调函数。

**使用场景：** 当需要在用户切换键盘模式时执行相应逻辑（如更新键盘布局、保存用户偏好等）时，需设置此回调。

**使用后效果：** 当用户在输入法切换列表弹窗中点击某个模式选项时，系统将调用此回调并传入选中模式在patterns数组中的索引值。

**说明：** 回调参数index为选中模式在patterns数组中的索引值，与defaultSelected的取值范围一致。回调中可根据index值更新defaultSelected，以保持下次打开弹窗时选中状态与用户选择一致。

**类型：** (index: number) =&gt; void

**起始版本：** 11

<!--Device-PatternOptions-action: (index: int) => void--><!--Device-PatternOptions-action: (index: int) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## defaultSelected

```TypeScript
defaultSelected?: number
```

默认选择的模式索引，对应patterns数组中的索引值。

**使用场景：** 当默认输入法需要预设一个初始选中的键盘模式时使用此参数。

**使用后效果：** 设置后，输入法列表弹窗打开时会默认选中该索引对应的模式选项。

**取值范围：** [0, patterns.length - 1]。超出此范围时不生效，弹窗打开时不选中任何模式选项。

**默认值：** 不设置时，弹窗打开时不选中任何模式选项。

**说明：** 该索引值必须在patterns数组的有效范围内，否则设置不生效。

**类型：** number

**起始版本：** 11

<!--Device-PatternOptions-defaultSelected?: int--><!--Device-PatternOptions-defaultSelected?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## patterns

```TypeScript
patterns: Array<Pattern>
```

模式选项资源数组，每个Pattern定义一个键盘模式的图标和选中状态图标。

**使用场景：** 当默认输入法需要提供多种键盘模式（如单手模式、全屏模式等）供用户选择时，需配置此参数。

**使用后效果：** 设置后，输入法切换列表弹窗中会在默认输入法区域展示该数组中定义的所有模式选项供用户选择。

**说明：** patterns数组中的每个Pattern的icon和selectedIcon均需为有效的[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)资源引用；建议至少配置2个模式选项以提供有意义的选择功能。

**类型：** Array&lt;Pattern&gt;

**起始版本：** 11

<!--Device-PatternOptions-patterns: Array<Pattern>--><!--Device-PatternOptions-patterns: Array<Pattern>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

