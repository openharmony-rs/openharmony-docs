# TabBarOptions(Provides an advanced struct of tabs for atomic services)

页签选项。

**起始版本：** 12

<!--Device-unnamed-export declare class TabBarOptions--><!--Device-unnamed-export declare class TabBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, TabContentBuilder, OnContentWillChangeCallback } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,
    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)
```

TabBarOptions的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabBarOptions-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)--><!--Device-TabBarOptions-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | ResourceStr \| TabBarSymbol | 是 | 页签内的图标内容。 |
| text | ResourceStr | 是 | 页签内的文字内容。 |
| unselectedColor | ResourceColor | 否 | 未选择时的页签颜色，默认值为#99182431。 |
| selectedColor | ResourceColor | 否 | 已选择时的页签颜色，默认值为#FF007DFF。 |

