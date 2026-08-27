# @ohos.annotation(Annotation)

本模块定义了OpenHarmony ArkTS API的注解类型，如生命周期最小可用版本、API告警屏蔽等，用于帮助开发者标识和管理API的兼容性、告警抑制等特性。
 该模块解决了开发者在跨版本开发、第三方SDK集成等场景中遇到的版本兼容性告警、权限告警、多设备适配告警等问题，通过注解方式抑制不必要的告警干扰，提高代码的可维护性和开发效率。
 > **说明**
 >
 > - 本模块首批接口从 API version 22 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```TypeScript
import { Available, SuppressWarnings, SuppressWarningsType } from '@kit.BasicServicesKit';
```

## 汇总

### 注解

| 名称 | 说明 |
| --- | --- |
| [Available](arkts-basicservices-annotation-available-a.md) | 提供API注解能力，用于标记API支持的最低可用版本。 此注解可以标注在类、接口、函数、变量、类型、模块、枚举上。 在源码定义处添加注解后，编译工具会在使用处检查潜在的兼容性问题。 当minApiVersion大于build-profile.json5中指定的compatibleSdkVersion字段，会生成兼容性警告。 |
| [SuppressWarnings](arkts-basicservices-annotation-suppresswarnings-a.md) | 系统提供的API告警屏蔽功能，允许开发者通过注解的方式抑制API调用时产生的告警。 该功能可应用于类、函数、变量、类型、接口等API元素上。 在源码中添加相应标注后，编译器会根据预设规则自动屏蔽对应的告警信息。 预设规则包括：当API调用版本高于兼容版本时产生的兼容性告警、当设备不支持某系统能力时产生的多设备告警、当缺少权限配置时产生的权限告警等。 适用于需要在特定场景下暂时忽略某些告警、避免编译器产生干扰性警告的情况，帮助开发者专注于关键问题，提高开发效率。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SuppressWarningsType(Annotation)](arkts-basicservices-annotation-suppresswarningstype-e.md) | 支持消除告警的规则。帮助开发者根据实际需求选择性地屏蔽兼容性告警、多设备告警、权限告警等，在确保代码质量的同时减少不必要的告警干扰，提升开发体验。 |
