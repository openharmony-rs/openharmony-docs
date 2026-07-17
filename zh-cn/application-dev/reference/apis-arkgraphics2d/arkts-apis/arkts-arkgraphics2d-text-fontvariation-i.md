# FontVariation

可变字体属性。

**起始版本：** 12

<!--Device-text-interface FontVariation--><!--Device-text-interface FontVariation-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## axis

```TypeScript
axis: string
```

可变字体属性键值对中的关键字标识的字符串。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontVariation-axis: string--><!--Device-FontVariation-axis: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## isNormalized

```TypeScript
isNormalized?: boolean
```

是否归一化。值为true时，value字段取值范围为-1~1，映射字体文件中配置的最小值到最大值范围，0表示字体文件中配置的默认值；值为false时，value字段取值范围为字体文件本身支持调节的范围；默认为false。

**类型：** boolean

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-FontVariation-isNormalized?: boolean--><!--Device-FontVariation-isNormalized?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## value

```TypeScript
value: number
```

可变字体属性键值对的值。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontVariation-value: double--><!--Device-FontVariation-value: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

