# OnTabsContentDidScrollCallback

```TypeScript
export type OnTabsContentDidScrollCallback = (selectedIndex: int, index: int, position: double, mainAxisLength: double) => void
```

Tabs滑动时触发的回调。 > **说明：** > > - 例如，当前选中的页签索引为0，从第0页切换到第1页的动画过程中，每帧都会对视窗内所有页面触发回调，当视窗内有第0页和第1页两页时，每帧会触发两次回调。其中，第一次回调的selectedIndex为0、index为0、 > position为当前帧第0页相对于动画开始前第0页的移动比例，mainAxisLength为主轴方向上第0页的长度。第二次回调的selectedIndex仍为0、index为1、position为当前帧第1页相对于动画开始前第0 > 页的移动比例，mainAxisLength为主轴方向上第1页的长度。 > > - 若动画曲线为弹簧插值曲线，从第0页切换到第1页的动画过程中，可能会因为离手时的位置和速度，先过滑到第2页，再回弹到第1页，该过程中每帧会对视窗内第1页和第2页触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnTabsContentDidScrollCallback = (selectedIndex: int, index: int, position: double, mainAxisLength: double) => void--><!--Device-unnamed-export type OnTabsContentDidScrollCallback = (selectedIndex: int, index: int, position: double, mainAxisLength: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndex | int | 是 | 当前选中页面的索引。例如，当前选中的页签索引为0，从第0页切换到第1页的动画过程中，每一次回调的selectedIndex都为0。 取值范围为全体整数 取值限定为整数。 |
| index | int | 是 | 视窗内页面的索引。例如，页面滑动过程中，视窗内有第0页和第1页两页时，每帧会触发两次回调。其中，第一次回调的index为0，第二次回调的index为1。 取值范围为全体整数 取值限定为整数。 |
| position | double | 是 | index页面相对于Tabs主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。例如，一个横向Tabs中，当前选中的页签索引为0，从第0页往左切换到第1页的 动画过程中，若刚好有一帧第0页和第1页分别占用视窗的30%和70%时，当前帧会触发两次回调。其中，第一次回调的position为-0.7，表示当前帧第0页在Tabs主轴起始位置的左侧，且第0页左侧位置距离Tabs主轴起始位置为 视窗的70%，即第0页往左移动了视窗70%的距离。第二次回调的position为0.3，表示当前帧第1页在Tabs主轴起始位置的右侧，且第1页左侧位置距离Tabs主轴起始位置为视窗的30%，实际上第1页也是往左移动了视窗70% 的距离。 |
| mainAxisLength | double | 是 | index页面相对于Tabs主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。例如，一个横向Tabs中，当前选中的页签索引为0，从第0页往左切换到第1页的 动画过程中，若刚好有一帧第0页和第1页分别占用视窗的30%和70%时，当前帧会触发两次回调。其中，第一次回调的position为-0.7，表示当前帧第0页在Tabs主轴起始位置的左侧，且第0页左侧位置距离Tabs主轴起始位置为 视窗的70%，即第0页往左移动了视窗70%的距离。第二次回调的position为0.3，表示当前帧第1页在Tabs主轴起始位置的右侧，且第1页左侧位置距离Tabs主轴起始位置为视窗的30%，实际上第1页也是往左移动了视窗70% 的距离。 |

