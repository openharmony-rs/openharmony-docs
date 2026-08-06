# TabBarOptions

页签容器数组。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-export declare class TabBarOptions--><!--Device-unnamed-export declare class TabBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,
    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)
```

TabBarOptions的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabBarOptions-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)--><!--Device-TabBarOptions-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr,    unselectedColor?: ResourceColor, selectedColor?: ResourceColor)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| TabBarSymbol | 是 | 页签内的图片内容。 |
| text | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 页签内的文字内容。 |
| unselectedColor | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 未选择时的页签颜色，默认值：#99182431。 |
| selectedColor | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 被选择时的页签颜色，默认值：#FF007DFF。 |

