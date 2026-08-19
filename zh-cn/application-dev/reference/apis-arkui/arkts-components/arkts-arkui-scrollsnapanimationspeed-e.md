# ScrollSnapAnimationSpeed

设置列表项滚动限位动画速度。

**起始版本：** 22

<!--Device-unnamed-declare enum ScrollSnapAnimationSpeed--><!--Device-unnamed-declare enum ScrollSnapAnimationSpeed-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

默认列表限位动画速度，适用于列表项主轴方向尺寸较大（如接近列表视口主轴尺寸），每次划动仅滚动一个列表项的场景。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollSnapAnimationSpeed-NORMAL = 0--><!--Device-ScrollSnapAnimationSpeed-NORMAL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLOW

```TypeScript
SLOW = 1
```

列表限位动画速度低于NORMAL，适用于列表项主轴方向尺寸较小（如远小于列表视口主轴尺寸），每次划动需滚动多个列表项的场景。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollSnapAnimationSpeed-SLOW = 1--><!--Device-ScrollSnapAnimationSpeed-SLOW = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

