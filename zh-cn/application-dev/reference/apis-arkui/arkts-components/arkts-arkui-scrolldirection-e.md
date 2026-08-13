# ScrollDirection

滚动方向枚举。 FREE（自由滚动）模式下支持的能力： > **说明：** > > - `edgeEffect`属性仅支持`Spring`和`None`边缘滑动效果。 > > - `onWillScroll`回调仅支持在跟手滑动阶段重载偏移量。 > > - `onScrollEdge`回调只在到达边缘时触发一次，回弹后不会重复触发。 > > - 在抛滑动画过程中切换边缘模式不会打断动画。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare enum ScrollDirection--><!--Device-unnamed-declare enum ScrollDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Vertical

```TypeScript
Vertical
```

仅支持竖直方向滚动。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollDirection-Vertical--><!--Device-ScrollDirection-Vertical-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Horizontal

```TypeScript
Horizontal
```

仅支持水平方向滚动。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollDirection-Horizontal--><!--Device-ScrollDirection-Horizontal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Free

```TypeScript
Free
```

支持水平和垂直方向滚动

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [FREE](#FREE)

<!--Device-ScrollDirection-Free--><!--Device-ScrollDirection-Free-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

不可滚动。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollDirection-None--><!--Device-ScrollDirection-None-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FREE

```TypeScript
FREE = 4
```

自由滚动。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollDirection-FREE = 4--><!--Device-ScrollDirection-FREE = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

