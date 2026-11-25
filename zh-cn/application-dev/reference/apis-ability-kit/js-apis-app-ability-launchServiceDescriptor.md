# LaunchServiceDescriptor

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

描述LaunchService的所属应用、模块、服务名称，以及用户和应用分身信息。作为[register](js-apis-app-ability-launchServiceManager.md#launchservicemanagerregister)、[unregister](js-apis-app-ability-launchServiceManager.md#launchservicemanagerunregister)、[start](js-apis-app-ability-launchServiceManager.md#launchservicemanagerstart)、[stop](js-apis-app-ability-launchServiceManager.md#launchservicemanagerstop)、[getInformation](js-apis-app-ability-launchServiceManager.md#launchservicemanagergetinformation)接口的descriptor参数，用于指定要操作或查询的LaunchService。

**起始版本**：26.1.0

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```ts
import { launchServiceManager } from '@kit.AbilityKit';
```

## LaunchServiceDescriptor

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| bundleName | string | 否 | 否 | 拥有LaunchService的应用程序的包名，对应[app.json5配置文件](../../quick-start/app-configuration-file.md#配置文件标签)中的bundleName。 |
| moduleName | string | 否 | 否 | 声明LaunchService的模块名，对应[module.json5配置文件](../../quick-start/module-configuration-file.md#配置文件标签)中的name。 |
| serviceName | string | 否 | 否 | LaunchService的名称，对应module.json5配置文件中[launchServices标签](../../quick-start/module-configuration-file.md#launchservices标签)的name。 |
| userId | number | 否 | 是 | 用户ID。如果不指定该参数，则默认使用当前用户。<br>取值限定为非负整数。 |
| appIndex | number | 否 | 是 | 应用分身的索引。取值范围是[0, 1000]，默认值0表示主应用。<br>取值限定为非负整数。 |
