# ToneMappingType

色调映射类型枚举。@enum { number }

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## ACES

```TypeScript
ACES = 0
```

ACES色调映射类型，基于Academy Color Encoding System标准，将高动态范围（HDR）图像映射到低动态范围（LDR），适用于追求电影级色彩还原的场景。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## ACES_2020

```TypeScript
ACES_2020 = 1
```

ACES_2020色调映射类型，基于ACES 2020标准，提供更广的色域支持，适用于需要高色彩精度的HDR渲染场景。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## FILMIC

```TypeScript
FILMIC = 2
```

FILMIC色调映射类型，模拟胶片曝光响应曲线，高光过渡柔和自然，适用于追求写实风格和电影质感的一般3D场景。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D
