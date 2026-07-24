# PageNodeInfo (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

PageNodeInfo用于描述自动填充场景下的页面节点信息，包含节点深度、标签、密码生成规则、自动填充标志及元数据等系统接口字段。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[PageNodeInfo](js-apis-inner-application-pageNodeInfo.md)。

## PageNodeInfo

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

| 名称                   | 类型                                 | 只读 | 可选 | 说明                                                         |
| ---------------------- | ------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| depth                  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否   | 否   | 页面节点的深度（单位：px）。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| tag                    | string  | 否   | 否   | 页面节点的标签名称，用于标识节点的组件类型。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| passwordRules          | string  | 否   | 是   | 自动生成密码时的规则，用于指定生成密码的格式和约束（如长度、字符类型等）。仅当自动填充类型为密码时生效。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| enableAutoFill         | boolean | 否   | 否   | 自动填充标志。true表示已开启自动填充，false表示未开启自动填充。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| metadata<sup>12+</sup> | string  | 否   | 是   | 页面节点的元数据，用于携带节点的自定义属性或配置信息，辅助自动填充服务进行更精确的匹配和填充。默认值为空字符串。<br>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
