# AutoFillRect (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

用于自动填充的矩形区域。

> **说明：**
> 
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> 本模块接口均为系统接口。
> 本模块接口仅可在Stage模型下使用。

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

| 名称   | 类型   | 只读 | 可选 | 说明                                     |
| ------ | ----- | ---- | ---- | ---------------------------------------- |
| left   | number | 否   | 否   | AutoFill表单或页面节点与页面左边界的距离。|
| top    | number | 否   | 否   | AutoFill表单或页面节点与页面上边界的距离。|
| height | number | 否   | 否   | AutoFill表单或页面节点的高度。            |
| width  | number | 否   | 否   | AutoFill表单或页面节点的宽度。            |
