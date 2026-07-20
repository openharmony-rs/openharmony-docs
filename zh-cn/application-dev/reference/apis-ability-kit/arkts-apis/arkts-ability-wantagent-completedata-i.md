# CompleteData

表示主动触发WantAgent返回的数据。

**起始版本：** 9

<!--Device-wantAgent-export interface CompleteData--><!--Device-wantAgent-export interface CompleteData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

## extraInfo

```TypeScript
extraInfo?: Record<string, Object>
```

额外数据。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-extraInfo?: Record<string, Object>--><!--Device-CompleteData-extraInfo?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## finalCode

```TypeScript
finalCode: number
```

触发wantAgent的返回码。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-finalCode: int--><!--Device-CompleteData-finalCode: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## finalData

```TypeScript
finalData: string
```

触发wantAgent的返回数据。返回**canceled**时表示触发失败，WantAgent实例已经被取消。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-finalData: string--><!--Device-CompleteData-finalData: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## info

```TypeScript
info: WantAgent
```

触发的wantAgent。

**类型：** WantAgent

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-info: WantAgent--><!--Device-CompleteData-info: WantAgent-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want: Want
```

触发wantAgent时实际使用的want信息。

**类型：** Want

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-want: Want--><!--Device-CompleteData-want: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

