# IsolatedOptions（系统接口）

用于在IsolatedComponent构造时传递构造参数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface IsolatedOptions--><!--Device-unnamed-declare interface IsolatedOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

要加载的Abc信息。 Want对象的parameters中需包含以下字段： \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_resourcePath：资源路径，需为.hap文件路径； \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_abcPath：经verifyAbc校验后的Abc文件路径，需以'/abcs'开头； \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_entryPoint：Abc入口，格式为'bundleName/页面路径'。

**类型：** Want

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IsolatedOptions-want: Want--><!--Device-IsolatedOptions-want: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## worker

```TypeScript
worker: RestrictedWorker
```

运行Abc的受限Worker。

**类型：** RestrictedWorker

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IsolatedOptions-worker: RestrictedWorker--><!--Device-IsolatedOptions-worker: RestrictedWorker-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

