# FormParam

卡片参数枚举。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

## IDENTITY_KEY

```TypeScript
IDENTITY_KEY = "ohos.extra.param.key.form_identity"
```

卡片标识。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## DIMENSION_KEY

```TypeScript
DIMENSION_KEY = "ohos.extra.param.key.form_dimension"
```

卡片规格，规格尺寸参考[FormDimension](arkts-form-forminfo-formdimension-e.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## NAME_KEY

```TypeScript
NAME_KEY = "ohos.extra.param.key.form_name"
```

卡片名称。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## MODULE_NAME_KEY

```TypeScript
MODULE_NAME_KEY = "ohos.extra.param.key.module_name"
```

卡片所属模块名称。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## WIDTH_KEY

```TypeScript
WIDTH_KEY = "ohos.extra.param.key.form_width"
```

卡片宽度。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## HEIGHT_KEY

```TypeScript
HEIGHT_KEY = "ohos.extra.param.key.form_height"
```

卡片高度。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## TEMPORARY_KEY

```TypeScript
TEMPORARY_KEY = "ohos.extra.param.key.form_temporary"
```

临时卡片。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## BUNDLE_NAME_KEY

```TypeScript
BUNDLE_NAME_KEY = "ohos.extra.param.key.bundle_name"
```

Bundle名称。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## ABILITY_NAME_KEY

```TypeScript
ABILITY_NAME_KEY = "ohos.extra.param.key.ability_name"
```

Ability名称。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## LAUNCH_REASON_KEY

```TypeScript
LAUNCH_REASON_KEY = "ohos.extra.param.key.form_launch_reason"
```

卡片创建原因。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## PARAM_FORM_CUSTOMIZE_KEY

```TypeScript
PARAM_FORM_CUSTOMIZE_KEY = "ohos.extra.param.key.form_customize"
```

自定义数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## FORM_LOCATION_KEY

```TypeScript
FORM_LOCATION_KEY = 'ohos.extra.param.key.form_location'
```

卡片位置。 具体可选位置参考[FormLocation](arkts-form-forminfo-formlocation-e.md)。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.Form

## FORM_RENDERING_MODE_KEY

```TypeScript
FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'
```

卡片渲染模式。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## HOST_BG_INVERSE_COLOR_KEY

```TypeScript
HOST_BG_INVERSE_COLOR_KEY = 'ohos.extra.param.key.host_bg_inverse_color'
```

卡片使用方的背景反色颜色值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## FORM_PERMISSION_NAME_KEY

```TypeScript
FORM_PERMISSION_NAME_KEY = 'ohos.extra.param.key.permission_name'
```

用户授权权限名称。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## FORM_PERMISSION_GRANTED_KEY

```TypeScript
FORM_PERMISSION_GRANTED_KEY = 'ohos.extra.param.key.permission_granted'
```

用户是否授权。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## ORIGINAL_FORM_KEY

```TypeScript
ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'
```

用groupId关联的一组卡片，在调整大小时，会先创建新尺寸的卡片，再删除旧尺寸的卡片。新尺寸卡片创建时want参数会通过该key传递旧尺寸卡片的卡片id。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## EDIT_FORM_KEY

```TypeScript
EDIT_FORM_KEY = 'ohos.extra.param.key.edit_form_id'
```

在半模态页面的卡片编辑中，通过onAddForm回调函数传递该key表示被编辑的卡片id，用来确保预览卡片与被编辑卡片信息同步。如果卡片onAddForm回调函数中携带了该key，则说明当前卡片为半模态页面中的预览卡片，需要基 于被编辑卡片来筛选预览卡片内容。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

## UPDATE_FORM_REASON_KEY

```TypeScript
UPDATE_FORM_REASON_KEY = 'ohos.extra.param.key.update_form_reason'
```

Indicates the key specifying the reason for the form update. which is represented as want: {"parameters": {UPDATE_FORM_REASON_KEY: FormUpdateReason.FORM_NODE_REUSE}}.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form
