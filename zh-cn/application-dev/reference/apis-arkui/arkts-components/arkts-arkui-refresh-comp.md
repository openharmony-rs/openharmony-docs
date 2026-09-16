# Refresh

Refresh是提供下拉刷新交互的容器组件，适用于列表数据刷新、页面内容更新等需要用户触发数据更新的场景。它支持自定义刷新区域显示内容和文本、设置下拉偏移量和跟手系数、控制最大下拉距离等，可灵活适配不同应用的下拉刷新需求，提供一致且流畅的刷新体验。

> **说明：** > > - 该组件从API version 12开始支持与垂直滚动的Swiper和 > Web的联动。当Swiper设置 > loop属性为true时，Refresh无法和Swiper产生联动。 > > - Refresh和内容大小小于组件自身的List组件嵌套使用并且中间还有其他组件时，手势可能会被中间组件响应，导致Refresh未产生下拉刷新效果。此时可以将 > [alwaysEnabled](arkts-arkui-edgeeffectoptions-i.md)参数设为true，List会响应手势并通过嵌套滚动带动Refresh组件产生下拉刷新效果。具体可以参考 > 示例9（不满一屏场景实现下拉刷新）。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。 > > - 组件无法通过鼠标按下拖动操作进行下拉刷新。

## 子组件

支持单个子组件。

从API version 11开始，Refresh子组件会跟随手势下拉而下移。

## Refresh

```TypeScript
Refresh(value: RefreshOptions)
```

创建Refresh容器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 是 | 刷新组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 用于设置Refresh组件参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RefreshStatus](arkts-arkui-refreshstatus-e.md) | RefreshStatus刷新状态枚举。 |

## 示例

```TypeScript
### 示例1（默认刷新样式）

刷新区域使用默认刷新样式。


```

```TypeScript
### 示例2（设置刷新区域显示文本）

通过[promptText](#refreshoptions对象说明)参数设置刷新区域显示文本。


```

```TypeScript
### 示例3（自定义刷新区域显示内容-builder）

通过[builder](#refreshoptions对象说明)参数自定义刷新区域显示内容。


```

```TypeScript
### 示例4（自定义刷新区域显示内容-refreshingContent）

通过[refreshingContent](#refreshoptions对象说明)参数自定义刷新区域显示内容。


```

```TypeScript
### 示例5（实现最大下拉距离）

通过[pullDownRatio](arkts-arkui-refresh-comp-attribute.md#pulldownratio)属性和[onOffsetChange](#onoffsetchange12)事件实现最大下拉距离。


```

```TypeScript
### 示例6（实现下拉刷新上拉加载更多）

Refresh组件与[List](ts-container-list.md)组件组合实现下拉刷新上拉加载更多效果。


```

```TypeScript
### 示例7（设置最大下拉距离）

从API version 20开始，通过[maxPullDownDistance](arkts-arkui-refresh-comp-attribute.md#maxpulldowndistance)属性设置最大下拉距离。


```

```TypeScript
### 示例8（禁止下拉刷新）

通过[pullDownRatio](arkts-arkui-refresh-comp-attribute.md#pulldownratio)属性禁止下拉刷新。


```

```TypeScript
### 示例9（不满一屏场景实现下拉刷新）

调用[edgeEffect](ts-container-scrollable-common.md#edgeeffect11)时，将options参数的[alwaysEnabled](ts-container-scrollable-common.md#edgeeffectoptions11对象说明)设置为true，可以在不满一屏的情况下实现Refresh组件的下拉刷新效果。


```

```TypeScript
### 示例10（上滑不取消刷新）

该示例通过[pullUpToCancelRefresh](arkts-arkui-refresh-comp-attribute.md#pulluptocancelrefresh)接口设置上滑不取消刷新。

从API version 23开始，新增pullUpToCancelRefresh接口。
```
