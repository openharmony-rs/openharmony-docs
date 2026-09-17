# FormInfoFilter

卡片信息过滤器，仅将符合过滤器内要求的卡片信息返回。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## bundleName

```TypeScript
bundleName?: string
```

选填，仅保留含bundleName与提供值相符的卡片信息，未填写时则不通过bundleName进行过滤。

**系统接口：** 此接口为系统接口。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## supportedDimensions

```TypeScript
supportedDimensions?: Array<number>
```

选填，仅保留含supportedDimensions提供值相符的卡片信息，未填写时则不通过supportedDimensions进行过滤。

**系统接口：** 此接口为系统接口。

**说明：** 最大长度为9，数值取值范围[1, 9]的整数的数组，数值5从API version 9开始支持，从API version 20开始废弃。

具体规格参考 [formInfo.FormDimension](arkts-form-forminfo-formdimension-e.md)。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## supportedShapes

```TypeScript
supportedShapes?: Array<number>
```

选填，仅保留含supportedShapes提供值相符的卡片信息，未填写时则不通过supportedShapes进行过滤。

**系统接口：** 此接口为系统接口。

**说明：** 只有1和2两个值。1代表方形，2代表圆形。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。
