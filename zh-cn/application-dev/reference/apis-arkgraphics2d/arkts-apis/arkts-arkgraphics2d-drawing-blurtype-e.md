# BlurType

定义蒙版滤镜模糊中操作类型的枚举。 | 名称 | 值 | 说明 | 示意图 | | ------ | - | ------------------ | -------- | | NORMAL | 0 | 全面模糊，外圈边缘和内部实体一起模糊。 | !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ | | SOLID | 1 | 内部实体不变，只模糊外圈边缘部分。 | !\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ | | OUTER | 2 | 只有外圈边缘模糊，内部实体完全透明。 | !\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ | | INNER | 3 | 只有内部实体模糊，外圈边缘清晰。 | !\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_ |

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-drawing-enum BlurType--><!--Device-drawing-enum BlurType-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## NORMAL

```TypeScript
NORMAL = 0
```

Both the outer edges and the inner solid parts are blurred.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-BlurType-NORMAL = 0--><!--Device-BlurType-NORMAL = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SOLID

```TypeScript
SOLID = 1
```

The inner solid part remains unchanged, while only the outer edges are blurred.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-BlurType-SOLID = 1--><!--Device-BlurType-SOLID = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## OUTER

```TypeScript
OUTER = 2
```

Only the outer edges are blurred, with the inner solid part being fully transparent.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-BlurType-OUTER = 2--><!--Device-BlurType-OUTER = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INNER

```TypeScript
INNER = 3
```

Only the inner solid part is blurred, while the outer edges remain sharp.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-BlurType-INNER = 3--><!--Device-BlurType-INNER = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

