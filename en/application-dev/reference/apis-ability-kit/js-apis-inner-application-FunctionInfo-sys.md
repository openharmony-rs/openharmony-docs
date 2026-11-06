# FunctionInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @dsz2025-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=938bc44e514b9eed279585f3283eccb3aaf0ac72 translatedAt=2026-09-03T11:57:54.599Z pushedAt=2026-09-05T10:47:30.821Z -->

FunctionInfo describes the basic information of [Function](./js-apis-app-function-functionManager-sys.md), including the Function namespace, name, version, description, input and output modes, and so on.

**Since:** 26.0.0

> **NOTE**
>
> The APIs of this module are system APIs.

## Modules to Import

```ts
import { FunctionInfo } from '@kit.AbilityKit';
```

## FunctionInfo

Describes the basic information of a [Function](./js-apis-app-function-functionManager-sys.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name               | Type                                                   | Read-only | Optional | Description                                                  |
| ------------------ | ------------------------------------------------------ | --------- | -------- | ------------------------------------------------------------ |
| functionNamespace  | string                                                 | Yes       | No       | Namespace of the Function, used to classify and manage Functions in the system. A namespace helps organize and identify Functions in different functional domains. |
| functionName       | string                                                 | Yes       | No       | Name of the Function, used to uniquely identify a Function within the functionNamespace. |
| version            | string                                                 | Yes       | No       | Version number of the Function. It follows the semantic versioning specification (for example, "1.0.0"), and the format is defined by the provider. The version number is used to identify the functional iteration and compatibility changes of the Function. |
| description        | string                                                 | Yes       | No       | Functional description of the Function. This description should clearly explain the core functionality and purpose of the Function, helping users and AI Agents understand what the Function can do and assisting in decision-making. |
| inputSchema        | string                                                 | Yes       | Yes      | JSON Schema definition of the input parameters of the Function, describing the structure and types of the input parameters accepted by the Function. It must conform to the JSON Schema format definition. |
| outputSchema       | string                                                 | Yes       | Yes      | JSON Schema definition of the output result of the Function, describing the structure and types of the return value of the Function. It must conform to the JSON Schema format definition. |
