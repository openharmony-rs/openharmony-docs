# CliInfo（系统接口）

表示CLI（Command Line Interface，命令行界面）信息。

**起始版本：** 26.0.0

<!--Device-abilityAccessCtrl-interface CliInfo--><!--Device-abilityAccessCtrl-interface CliInfo-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## cliName

```TypeScript
cliName: string
```

CLI名称。该字段不能为空，且长度不能超过256个字符。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliInfo-cliName: string--><!--Device-CliInfo-cliName: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## subCliName

```TypeScript
subCliName: string
```

CLI子命令名称。该字段可以为空，但长度不能超过256个字符。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliInfo-subCliName: string--><!--Device-CliInfo-subCliName: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

