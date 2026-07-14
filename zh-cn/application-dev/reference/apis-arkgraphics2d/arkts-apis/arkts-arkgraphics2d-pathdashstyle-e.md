# PathDashStyle

路径效果的绘制样式枚举。
| 名称 | 值 | 说明 |
| ------ | - | ------------------ |
| TRANSLATE | 0 | 不会随着路径旋转，只会平移。 |
| ROTATE | 1 | 随着路径的旋转而旋转。 |
| MORPH | 2 | 随着路径的旋转而旋转，并在转折处进行拉伸或压缩等操作以增加平滑度。 |

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## TRANSLATE

```TypeScript
TRANSLATE = 0
```

Translates only, not rotating with the path.

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## ROTATE

```TypeScript
ROTATE = 1
```

Rotates with the path.

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## MORPH

```TypeScript
MORPH = 2
```

Rotates with the path and stretches or compresses at turns to enhance smoothness.

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

