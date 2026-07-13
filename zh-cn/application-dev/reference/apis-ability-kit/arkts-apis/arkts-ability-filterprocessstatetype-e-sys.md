# FilterProcessStateType（系统接口）

表示要监听的进程状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appstatefilter-i-sys.md)过滤想要监听的进程状态。

**起始版本：** 21

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## CREATE

```TypeScript
CREATE = 1 << 0
```

进程刚创建完成，对应[ProcessData](../../../../reference/apis-ability-kit/js-apis-inner-application-processData.md#属性)中state取值
为0的状态。

**起始版本：** 21

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

进程处于前台，对应[ProcessData](../../../../reference/apis-ability-kit/js-apis-inner-application-processData.md#属性)中state取值为
2的状态。

**起始版本：** 21

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

进程处于后台，对应[ProcessData](../../../../reference/apis-ability-kit/js-apis-inner-application-processData.md#属性)中state取值为
4的状态。

**起始版本：** 21

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

进程已终止，对应[ProcessData](../../../../reference/apis-ability-kit/js-apis-inner-application-processData.md#属性)中state取值为5
的状态。

**起始版本：** 21

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

