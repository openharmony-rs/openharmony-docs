# AntiAliasingLevel

缩放时的插值算法。可根据缩放质量和性能需求选择合适的级别。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## NONE

```TypeScript
NONE = 0
```

最近邻插值算法。

速度最快，放大时会有明显的马赛克/锯齿感，适合对性能要求高、对画质要求低的快速缩放场景。

**起始版本：** 12

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## LOW

```TypeScript
LOW = 1
```

双线性插值算法。

适合一般缩放场景。

**起始版本：** 12

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## MEDIUM

```TypeScript
MEDIUM = 2
```

双线性插值算法，同时开启Mipmap。

适合缩小图片的场景，能极好地消除大幅缩小时的混叠与纹理闪烁。

**起始版本：** 12

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## HIGH

```TypeScript
HIGH = 3
```

三次卷积插值算法。

适合对画质要求较高的放大场景。

**起始版本：** 12

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

