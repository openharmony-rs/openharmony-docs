# @ohos.app.function.functionManager

Function是定义在应用包中的一个业务逻辑单元，可以接收大模型提供的结构化数据来完成应用定义的功能，例如查询实时天气信息、打开指定应用页面等。

本模块提供Function的管理和调用能力，可以查询可用的Function信息、调用指定的Function执行业务逻辑。

@namespace functionManager

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { functionManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [invokeFunction](arkts-ability-functionmanager-invokefunction-f-sys.md) | 根据Function命名空间和Function名称调用指定的Function，使用Promise异步回调。 |
| [queryFunctions](arkts-ability-functionmanager-queryfunctions-f-sys.md) | 查询所有可用的Function信息，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InvokeOptions](arkts-ability-functionmanager-invokeoptions-i-sys.md) | Function调用的可选参数。包含Function调用时的应用上下文信息。 |
| [InvokeResult](arkts-ability-functionmanager-invokeresult-i-sys.md) | Function调用的结果。包含Function调用成功时返回的数据，调用失败时的错误码和错误信息。 |
<!--DelEnd-->
