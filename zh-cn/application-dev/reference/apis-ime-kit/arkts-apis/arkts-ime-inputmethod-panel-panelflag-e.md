# PanelFlag

输入法面板状态类型枚举。定义面板的显示状态形态，决定面板是固定态、悬浮态还是候选词态。   
> **说明：**
   
> 
   
> 目前仅用于SOFT_KEYBOARD类型的面板。对STATUS_BAR类型的面板设置PanelFlag不产生实际效果。
   
> PanelFlag使用建议：
   
- 选取原则：   
 - 默认场景优先选择`FLAG_FIXED`(0)，这是最常用的面板状态，系统自动管理显隐，开发者无需额外处理。   
 - 需要灵活布局（如横屏模式、多窗口）时选择`FLAG_FLOATING`(1)，可通过`Panel.moveTo()`调整面板位置。   
 - 需要独立候选词展示时选择`FLAG_CANDIDATE`(2)，但需开发者自行管理显隐逻辑。   
- 缺省配置：默认值为`FLAG_FIXED`(0)。在`PanelInfo`中不设置`flag`时，面板默认为固定态。   
- 注意事项：选择`FLAG_CANDIDATE`时，开发者必须自行实现候选词面板的显隐管理逻辑，否则面板将不会自动显示或隐藏。建议在用户开始输入时显示、在输入结束或选择候选词后隐藏。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_FIXED

```TypeScript
FLAG_FIXED = 0
```

固定态面板类型。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_FLOATING

```TypeScript
FLAG_FLOATING
```

悬浮态面板类型。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_CANDIDATE

```TypeScript
FLAG_CANDIDATE
```

候选词态面板类型。   
- 当输入面板为候选词态时，面板为显示用户输入候选词的窗口。   
- 系统不会主动控制候选词态面板的显示和隐藏，需要开发者根据应用场景自行控制候选词态面板的显示和隐藏。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
