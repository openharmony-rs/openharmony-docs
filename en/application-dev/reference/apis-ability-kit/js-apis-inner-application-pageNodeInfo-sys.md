# PageNodeInfo (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2e4d688beb0becfa2a64d71411845578aee3b47 translatedAt=2026-09-03T12:01:39.040Z pushedAt=2026-09-05T10:47:30.852Z -->

PageNodeInfo describes the page node information in auto-fill scenarios, including system API fields such as node depth, tag, password generation rules, auto-fill flag, and metadata.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [PageNodeInfo](js-apis-inner-application-pageNodeInfo.md).

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## PageNodeInfo

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | -------------------- | ----| ---- | ------------------------------------------------------------ |
| depth    | number              | No  | No  | Depth of the page node, in px.                              |
| tag    | string              | No   | No   | Tag name of the page node, used to identify the component type of the node.                 |
| passwordRules    | string              | No   | Yes   | Rule for auto-generating a password, used to specify the format and constraints of the generated password (such as length and character types). It takes effect only when the auto-fill type is password.   |
| enableAutoFill    | boolean              | No  | No  | Status of the auto-fill feature. **true** if enabled, **false** otherwise.           |
| metadata<sup>12+</sup>    | string              | No   | Yes   | Metadata of the page node, used to carry custom attributes or configuration information of the node to help the auto-fill service perform more precise matching and filling. The default value is an empty string.     |
