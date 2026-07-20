# OnTrackChangeHandler

```TypeScript
type OnTrackChangeHandler = (index: number, isSelected: boolean) => void
```

track变更事件回调方法。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-media-type OnTrackChangeHandler = (index: int, isSelected: boolean) => void--><!--Device-media-type OnTrackChangeHandler = (index: int, isSelected: boolean) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 当前变更的track索引。  |
| isSelected | boolean | 是 | 当前变更的track索引是否被选中。true表示处于选中状态，false表示处于非选中状态。  |

