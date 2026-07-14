# ColorSpace

色域类型枚举。

**起始版本：** 9

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知的色域类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## ADOBE_RGB_1998

```TypeScript
ADOBE_RGB_1998 = 1
```

RGB色域为Adobe RGB(1998)类型。

转换函数为Adobe RGB(1998)类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DCI_P3

```TypeScript
DCI_P3 = 2
```

RGB色域为DCI-P3类型。

转换函数为Gamma 2.6类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3

```TypeScript
DISPLAY_P3 = 3
```

RGB色域为DCI-P3类型。

转换函数为Gamma 2.6类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## SRGB

```TypeScript
SRGB = 4
```

RGB色域为SRGB类型。

转换函数为SRGB类型。

编码范围为Full类型。

系统默认色域类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT709

```TypeScript
BT709 = 6
```

RGB色域为BT709类型。

转换函数为BT709类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_EBU

```TypeScript
BT601_EBU = 7
```

RGB色域为BT601_P类型。

转换函数为BT709类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_SMPTE_C

```TypeScript
BT601_SMPTE_C = 8
```

RGB色域为BT601_N类型。

转换函数为BT709类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_HLG

```TypeScript
BT2020_HLG = 9
```

RGB色域为BT2020类型。

转换函数为HLG类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_PQ

```TypeScript
BT2020_PQ = 10
```

RGB色域为BT2020类型。

转换函数为PQ类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_HLG

```TypeScript
P3_HLG = 11
```

RGB色域为Display P3类型。

转换函数为HLG类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_PQ

```TypeScript
P3_PQ = 12
```

RGB色域为Display P3类型。

转换函数为PQ类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## ADOBE_RGB_1998_LIMIT

```TypeScript
ADOBE_RGB_1998_LIMIT = 13
```

RGB色域为Adobe RGB(1998)类型。

转换函数为Adobe RGB(1998)类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_LIMIT

```TypeScript
DISPLAY_P3_LIMIT = 14
```

RGB色域为Display P3类型。

转换函数为SRGB类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## SRGB_LIMIT

```TypeScript
SRGB_LIMIT = 15
```

RGB色域为SRGB类型。

转换函数为SRGB类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT709_LIMIT

```TypeScript
BT709_LIMIT = 16
```

RGB色域为BT709类型。

转换函数为BT709类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_EBU_LIMIT

```TypeScript
BT601_EBU_LIMIT = 17
```

RGB色域为BT601_P类型。

转换函数为BT709类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_SMPTE_C_LIMIT

```TypeScript
BT601_SMPTE_C_LIMIT = 18
```

RGB色域为BT601_N类型。

转换函数为BT709类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_HLG_LIMIT

```TypeScript
BT2020_HLG_LIMIT = 19
```

RGB色域为BT2020类型。

转换函数为HLG类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_PQ_LIMIT

```TypeScript
BT2020_PQ_LIMIT = 20
```

RGB色域为BT2020类型。

转换函数为PQ类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_HLG_LIMIT

```TypeScript
P3_HLG_LIMIT = 21
```

RGB色域为Display P3类型。

转换函数为HLG类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_PQ_LIMIT

```TypeScript
P3_PQ_LIMIT = 22
```

RGB色域为Display P3类型。

转换函数为PQ类型。

编码范围为Limit类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_P3

```TypeScript
LINEAR_P3 = 23
```

RGB色域为Display P3类型。

转换函数为Linear类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_SRGB

```TypeScript
LINEAR_SRGB = 24
```

RGB色域为SRGB类型。

转换函数为Linear类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_BT709

```TypeScript
LINEAR_BT709 = LINEAR_SRGB
```

与LINEAR_SRGB相同。

RGB色域为BT709类型。

转换函数为Linear类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_BT2020

```TypeScript
LINEAR_BT2020 = 25
```

RGB色域为BT2020类型。

转换函数为Linear类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_SRGB

```TypeScript
DISPLAY_SRGB = SRGB
```

与SRGB相同。

RGB色域为SRGB类型。

转换函数为SRGB类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_SRGB

```TypeScript
DISPLAY_P3_SRGB = DISPLAY_P3
```

与DISPLAY_P3相同。

RGB色域为Display P3类型。

转换函数为SRGB类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_HLG

```TypeScript
DISPLAY_P3_HLG = P3_HLG
```

RGB色域为Display P3类型。

转换函数为HLG类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_PQ

```TypeScript
DISPLAY_P3_PQ = P3_PQ
```

与P3_PQ相同。

RGB色域为Display P3类型。

转换函数为PQ类型。

编码范围为Full类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## H_LOG

```TypeScript
H_LOG = 26
```

RGB色域为BT2020类型。

转换函数为LOG类型。

**起始版本：** 18

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_BT2020_SRGB

```TypeScript
DISPLAY_BT2020_SRGB = 27
```

RGB色域为DISPLAY BT2020类型。

转换函数为SRGB类型。

编码范围为Full类型。

**起始版本：** 20

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## CUSTOM

```TypeScript
CUSTOM = 5
```

用户自定义色域类型。

从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

