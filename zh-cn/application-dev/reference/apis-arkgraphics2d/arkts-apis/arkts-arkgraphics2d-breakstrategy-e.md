# BreakStrategy

断行策略枚举。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## GREEDY

```TypeScript
GREEDY = 0
```

尽可能将当前行填满，不会自动添加连词符。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## HIGH_QUALITY

```TypeScript
HIGH_QUALITY = 1
```

布局优化，必要时会自动添加连词符。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## BALANCED

```TypeScript
BALANCED = 2
```

保证一个段落的每一行的宽度相同，必要时会添加连词符。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

