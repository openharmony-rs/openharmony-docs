# FoldStatus

当前可折叠设备的折叠状态枚举。如果是双折轴设备，则在充电口朝下的状态下，从右到左分别是折轴一和折轴二。
> **说明：**
> 只有一个折轴的产品包含FOLD_STATUS_EXPANDED、FOLD_STATUS_FOLDED、FOLD_STATUS_HALF_FOLDED三种折叠状态。
> 具有两个折轴的产品包含上表除FOLD_STATUS_UNKNOWN以外的九种折叠状态。
> FOLD_STATUS_UNKNOWN是一种不可用的折叠状态。

**起始版本：** 10

<!--Device-display-enum FoldStatus--><!--Device-display-enum FoldStatus-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_UNKNOWN

```TypeScript
FOLD_STATUS_UNKNOWN = 0
```

表示设备当前折叠状态无法确定或设备本身不可折叠。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_UNKNOWN = 0--><!--Device-FoldStatus-FOLD_STATUS_UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_EXPANDED

```TypeScript
FOLD_STATUS_EXPANDED = 1
```

表示设备当前折叠状态为完全展开。如果是双折轴设备，则表示折轴一折叠状态为完全展开，折轴二折叠状态为折叠。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_EXPANDED = 1--><!--Device-FoldStatus-FOLD_STATUS_EXPANDED = 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_FOLDED

```TypeScript
FOLD_STATUS_FOLDED = 2
```

表示设备当前折叠状态为折叠。如果是双折轴设备，则表示折轴一和折轴二的折叠状态均为折叠。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_FOLDED = 2--><!--Device-FoldStatus-FOLD_STATUS_FOLDED = 2-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_HALF_FOLDED

```TypeScript
FOLD_STATUS_HALF_FOLDED = 3
```

表示设备当前折叠状态为半折叠。半折叠指完全展开和折叠之间的状态。如果是双折轴设备，则表示折轴一折叠状态为半折叠，折轴二折叠状态为折叠。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_HALF_FOLDED = 3--><!--Device-FoldStatus-FOLD_STATUS_HALF_FOLDED = 3-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_EXPANDED_WITH_SECOND_EXPANDED

```TypeScript
FOLD_STATUS_EXPANDED_WITH_SECOND_EXPANDED = 11
```

表示双折轴设备折轴一和折轴二的折叠状态均为完全展开。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_EXPANDED_WITH_SECOND_EXPANDED = 11--><!--Device-FoldStatus-FOLD_STATUS_EXPANDED_WITH_SECOND_EXPANDED = 11-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_EXPANDED_WITH_SECOND_HALF_FOLDED

```TypeScript
FOLD_STATUS_EXPANDED_WITH_SECOND_HALF_FOLDED = 21
```

表示双折轴设备折轴一折叠状态为完全展开，折轴二折叠状态为半折叠。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_EXPANDED_WITH_SECOND_HALF_FOLDED = 21--><!--Device-FoldStatus-FOLD_STATUS_EXPANDED_WITH_SECOND_HALF_FOLDED = 21-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_FOLDED_WITH_SECOND_HALF_FOLDED

```TypeScript
FOLD_STATUS_FOLDED_WITH_SECOND_HALF_FOLDED = 22
```

表示双折轴设备折轴一折叠状态为折叠，折轴二折叠状态为半折叠。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_FOLDED_WITH_SECOND_HALF_FOLDED = 22--><!--Device-FoldStatus-FOLD_STATUS_FOLDED_WITH_SECOND_HALF_FOLDED = 22-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_HALF_FOLDED_WITH_SECOND_HALF_FOLDED

```TypeScript
FOLD_STATUS_HALF_FOLDED_WITH_SECOND_HALF_FOLDED = 23
```

表示双折轴设备折轴一和折轴二的折叠状态均为半折叠。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_HALF_FOLDED_WITH_SECOND_HALF_FOLDED = 23--><!--Device-FoldStatus-FOLD_STATUS_HALF_FOLDED_WITH_SECOND_HALF_FOLDED = 23-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_FOLDED_WITH_SECOND_EXPANDED

```TypeScript
FOLD_STATUS_FOLDED_WITH_SECOND_EXPANDED = 12
```

表示双折轴设备折轴一折叠状态为折叠，折轴二折叠状态为完全展开。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_FOLDED_WITH_SECOND_EXPANDED = 12--><!--Device-FoldStatus-FOLD_STATUS_FOLDED_WITH_SECOND_EXPANDED = 12-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLD_STATUS_HALF_FOLDED_WITH_SECOND_EXPANDED

```TypeScript
FOLD_STATUS_HALF_FOLDED_WITH_SECOND_EXPANDED = 13
```

表示双折轴设备折轴一折叠状态为半折叠，折轴二折叠状态为完全展开。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatus-FOLD_STATUS_HALF_FOLDED_WITH_SECOND_EXPANDED = 13--><!--Device-FoldStatus-FOLD_STATUS_HALF_FOLDED_WITH_SECOND_EXPANDED = 13-End-->

**系统能力：** SystemCapability.Window.SessionManager

