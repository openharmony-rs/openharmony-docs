# OnSelectCallback

```TypeScript
declare type OnSelectCallback = (index: number, selectValue: string) => void
```

下拉菜单选中某一项的回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnSelectCallback = (index: number, selectValue: string) => void--><!--Device-unnamed-declare type OnSelectCallback = (index: number, selectValue: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 选中项的索引，索引从0开始。 |
| selectValue | string | 是 | 选中项的值。 |

