# MonitorDecorator

```TypeScript
declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator
```

Represents the actual type of the **@Monitor** decorator.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-unnamed-declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator--><!--Device-unnamed-declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [MonitorDecoratorOptions](arkts-arkui-common-comp-monitordecoratoroptions-i.md) | Yes | In versions earlier than API 26.0.0, this parameter indicates the path of the monitored variable name. The path is separated by dots (.) to indicate nested properties (for example, 'a.b.c'). The content is specified by you. The input value is of the string type when only a string is passed. Since API version 26.0.0, this parameter can also be an object of the **MonitorDecoratorOptions** type, which is used to configure the wildcard capability. |
| args | string[] | Yes | Array of paths of the state variables to monitor. The path uses dots (.) to separate nested properties (for example, 'a.b.c'), and its content is specified by you. When the developer has used MonitorDecoratorOptions or passed multiple strings, the input parameter is of this type. If this parameter is not passed, it defaults to empty. When value is of the string type, only the state variable path specified by the value parameter is monitored. When value is of the MonitorDecoratorOptions type, the state variable path to monitor must be specified through this parameter. If undefined is passed, the corresponding monitoring does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [MethodDecorator](../../apis-default/arkts-apis/arkts-methoddecorator-t.md) | Method decorator. You do not need to concern yourself with this return value. |
