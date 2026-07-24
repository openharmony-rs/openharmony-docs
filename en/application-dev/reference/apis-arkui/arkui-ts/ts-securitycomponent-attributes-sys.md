# Security Component Universal Attributes (System API)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## Overview

This set of system APIs provides universal attributes for security components. It is used to set unique identifiers for security components during testing and debugging, enabling precise positioning and validation of their attribute configurations and interactive behaviors.

This module applies to the following scenarios:

- Set additional unique IDs for security components in testing or debugging scenarios to locate target component instances by ID.
- Track and verify attribute configurations and interactive behaviors via unique IDs to troubleshoot issues efficiently.

> **NOTE**
>
> This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [Security Component Universal Attributes](ts-securitycomponent-attributes.md).

## Key Classes and APIs

### Key APIs

- **SecurityComponentMethod&lt;T&gt;:** A collection of universal attribute methods for security components, which holds system-extended attributes beyond public attributes.

### Key Functions

- [key](#key): Unique ID of the component. Intended solely for validating attribute configurations and interactive behaviors of security components.

## key

key(value: string): T

Sets the unique ID for the component. You shall guarantee its uniqueness. Upon successful invocation, the component is assigned the specified ID for precise positioning of the component instance during testing. If this API is used together with [id](ts-securitycomponent-attributes.md#id15), the value set later overrides the value set earlier. You are advised to set only **id**.

This API is intended exclusively for app testing to verify attribute configurations and interactive behaviors of security components. In production environments, use the public API [id](ts-securitycomponent-attributes.md#id15).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Parameter| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | string | Yes| Unique ID for the component. You shall guarantee its uniqueness. This parameter is used to accurately locate security component instances by ID in test scenarios.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|
