# DaltonizationColorFilter（系统接口）

```TypeScript
type DaltonizationColorFilter = 'Normal' | 'Protanomaly' | 'Deuteranomaly' | 'Tritanomaly'
```

用于不同色弱类型的校正颜色滤镜。

色彩校正功能启用时（[daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate)设置为true）配置生效；色彩校正功能未启用时（[daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate)设置为false）显示为正常类型。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'Normal' | 表示正常类型。 |
| 'Protanomaly' | 表示红色弱类型。 |
| 'Deuteranomaly' | 表示绿色弱类型。 |
| 'Tritanomaly' | 表示蓝色弱类型。 |
