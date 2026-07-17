# BlurOptions

灰阶模糊参数。

**起始版本：** 12

<!--Device-unnamed-declare interface BlurOptions--><!--Device-unnamed-declare interface BlurOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## grayscale

```TypeScript
grayscale: [number, number]
```

灰阶模糊参数，两参数取值范围均为[0,127] 。对图像中的黑白色进行色阶调整，使其趋于灰色更为柔和美观，对图像中的彩色调整没有效果。参数一表示对黑色的提亮程度，参数二表示对白色的压暗程度，参数值越大调整效果越明显（黑白色变得越灰），有效值范围0-127。例如：设置参数为（20,20），图片中的黑色像素RGB:[0, 0, 0]会调整为[20,20,20]，白色像素RGB:[255,255,255]会调整为[235,235,235]（255-20），图像中的彩色像素维持不变。

**类型：** [number, number]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BlurOptions-grayscale: [number, number]--><!--Device-BlurOptions-grayscale: [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

