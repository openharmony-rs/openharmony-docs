# OverflowRequest（系统接口）

互动卡片动效请求信息。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## formId

```TypeScript
formId: string
```

卡片id。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isOverflow

```TypeScript
isOverflow: boolean
```

动效请求类型标记，true 表示互动卡片请求触发动效，false 表示互动卡片请求取消动效。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## overflowInfo

```TypeScript
overflowInfo?: OverflowInfo
```

动效请求参数信息，包括动效时长（单位：ms）和动效区域（动效区域范围以卡片左上角为原点，单位为vp），默认值为空。

**类型：** [OverflowInfo](arkts-form-forminfo-overflowinfo-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。
