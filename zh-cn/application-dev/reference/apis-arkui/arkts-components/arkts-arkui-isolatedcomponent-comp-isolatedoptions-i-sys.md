# IsolatedOptions（系统接口）

```TypeScript
declare interface IsolatedOptions
```

用于在IsolatedComponent构造时传递构造参数。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

要加载的Abc信息。Want对象的parameters中需包含以下字段：<br>resourcePath：资源路径，需为.hap文件路径；<br>abcPath：经verifyAbc校验后的Abc文件路径，需以'/abcs'开头；<br>entryPoint：Abc入口，格式为'bundleName/页面路径'。

**类型：** [Want](arkts-arkui-isolatedcomponent-comp-want-t-sys.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## worker

```TypeScript
worker: RestrictedWorker
```

运行Abc的受限Worker。

**类型：** [RestrictedWorker](arkts-arkui-isolatedcomponent-comp-restrictedworker-t-sys.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
