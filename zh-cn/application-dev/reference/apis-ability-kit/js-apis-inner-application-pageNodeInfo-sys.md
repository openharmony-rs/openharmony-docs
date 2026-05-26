# PageNodeInfo (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

用于自动填充的页面节点信息。

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
| tag                    | string  | 否   | 否   | 页面节点的标签。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| passwordRules          | string  | 否   | 是   | 生成密码的规则。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| enableAutoFill         | boolean | 否   | 否   | 自动填充标志。true表示已开启自动填充，false表示未开启自动填充。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| metadata<sup>12+</sup> | string  | 否   | 是   | 页面节点的元数据。<br>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
