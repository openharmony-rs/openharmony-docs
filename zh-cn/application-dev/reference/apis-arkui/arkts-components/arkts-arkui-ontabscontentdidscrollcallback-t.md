# OnTabsContentDidScrollCallback

```TypeScript
declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void
```

Tabs滑动时触发的回调。  
> **说明：**  
> - 例如，当前选中的页签索引为0，从第0页切换到第1页的动画过程中，每帧都会对视窗内所有页面触发回调，当视窗内有第0页和第1页两页时，每帧会触发两次回调。其中，第一次回调的selectedIndex为0、index为0、  
> position为当前帧第0页相对于动画开始前第0页的移动比例，mainAxisLength为主轴方向上第0页的长度。第二次回调的selectedIndex仍为0、index为1、position为当前帧第1页相对于动画开始前第0  
> 页的移动比例，mainAxisLength为主轴方向上第1页的长度。  
>  
> - 若动画曲线为弹簧插值曲线，从第0页切换到第1页的动画过程中，可能会因为离手时的位置和速度，先过滑到第2页，再回弹到第1页，该过程中每帧会对视窗内第1页和第2页触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void--><!--Device-unnamed-declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndex | number | 是 | 当前选中页面的索引。例如，当前选中的页签索引为0，从第0页切换到第1页的动画过程中，每一次回调的selectedIndex都为0。  |
| index | number | 是 | 视窗内页面的索引。例如，页面滑动过程中，视窗内有第0页和第1页两页时，每帧会触发两次回调。其中，第一次回调的index为0，第二次回调的index为1。  |
| position | number | 是 | 视窗内页面的索引。例如，页面滑动过程中，视窗内有第0页和第1页两页时，每帧会触发两次回调。其中，第一次回调的index为0，第二次回调的index为1。  |
| mainAxisLength | number | 是 | 视窗内页面的索引。例如，页面滑动过程中，视窗内有第0页和第1页两页时，每帧会触发两次回调。其中，第一次回调的index为0，第二次回调的index为1。  |

