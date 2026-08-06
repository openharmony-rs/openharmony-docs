# ContentDidScrollCallback

```TypeScript
export type ContentDidScrollCallback = (selectedIndex: int, index: int, position: double,
  mainAxisLength: double) => void
```

Swiper滑动时触发的回调，参数可参考[SwiperContentTransitionProxy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ContentDidScrollCallback = (selectedIndex: int, index: int, position: double,  mainAxisLength: double) => void--><!--Device-unnamed-export type ContentDidScrollCallback = (selectedIndex: int, index: int, position: double,  mainAxisLength: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndex | int | 是 | 当前选中页面的索引。 取值范围为全体整数 取值限定为整数。  |
| index | int | 是 | 视窗内页面的索引。 取值范围为全体整数 取值限定为整数。  |
| position | double | 是 | index页面相对于Swiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。  |
| mainAxisLength | double | 是 | index页面相对于Swiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。  |

