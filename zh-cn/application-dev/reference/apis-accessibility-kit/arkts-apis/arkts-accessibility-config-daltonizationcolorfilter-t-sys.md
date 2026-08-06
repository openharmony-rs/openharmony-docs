# DaltonizationColorFilter（系统接口）

```TypeScript
type DaltonizationColorFilter = 'Normal' | 'Protanomaly' | 'Deuteranomaly' | 'Tritanomaly'
```

颜色滤镜功能开启时（[daltonizationState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_设置为true)，颜色滤镜的配置(即设置的DaltonizationColorFilter的值)生效；颜色滤镜功能关闭 时（[daltonizationState]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_设置为false)，显示为正常类型。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-config-type DaltonizationColorFilter = 'Normal' | 'Protanomaly' | 'Deuteranomaly' | 'Tritanomaly'--><!--Device-config-type DaltonizationColorFilter = 'Normal' | 'Protanomaly' | 'Deuteranomaly' | 'Tritanomaly'-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'Normal' | 表示正常类型。 |
| 'Protanomaly' | 表示红色弱视类型。 |
| 'Deuteranomaly' | 表示绿色弱视类型。 |
| 'Tritanomaly' | 表示蓝色弱视类型。 |

