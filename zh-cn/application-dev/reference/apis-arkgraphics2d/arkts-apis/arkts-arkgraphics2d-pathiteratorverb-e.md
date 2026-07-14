# PathIteratorVerb

迭代器包含的路径操作类型枚举，可用于读取path的操作指令。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## MOVE

```TypeScript
MOVE = 0
```

设置起始点。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## LINE

```TypeScript
LINE = 1
```

添加线段。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## QUAD

```TypeScript
QUAD = 2
```

添加二阶贝塞尔圆滑曲线。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## CONIC

```TypeScript
CONIC = 3
```

添加圆锥曲线。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## CUBIC

```TypeScript
CUBIC = 4
```

添加三阶贝塞尔圆滑曲线。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## CLOSE

```TypeScript
CLOSE = 5
```

路径闭合。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## DONE

```TypeScript
DONE = CLOSE + 1
```

路径设置完成。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

