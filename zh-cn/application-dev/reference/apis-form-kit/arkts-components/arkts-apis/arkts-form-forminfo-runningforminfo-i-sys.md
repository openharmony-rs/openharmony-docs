# RunningFormInfo

已经添加到桌面的卡片信息。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## extraData

```TypeScript
readonly extraData?: Record<string, Object>
```

卡片的额外数据。

**类型：** Record&lt;string, Object&gt;

**默认值：** -

**起始版本：** 12

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formDescription

```TypeScript
readonly formDescription: string
```

提供方卡片配置文件中的描述信息。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## formUsageState

```TypeScript
readonly formUsageState: FormUsageState
```

卡片当前使用状态枚举。默认值为FormUsageState.USED

**类型：** [FormUsageState](arkts-form-forminfo-formusagestate-e-sys.md)

**默认值：** FormUsageState.USED

**起始版本：** 11

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## hostBundleName

```TypeScript
readonly hostBundleName: string
```

使用方卡片所属包的Bundle名称。

**类型：** string

**默认值：** -

**起始版本：** 10

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## visibilityType

```TypeScript
readonly visibilityType: VisibilityType
```

卡片当前可见类型枚举。

**类型：** [VisibilityType](arkts-form-forminfo-visibilitytype-e.md)

**默认值：** -

**起始版本：** 10

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。
