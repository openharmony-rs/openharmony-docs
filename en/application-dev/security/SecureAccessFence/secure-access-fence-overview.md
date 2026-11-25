# Secure Access Fence Service Overview

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ee3646b2ac8dc8dfc90ec5c9facb07df160a93db translatedAt=2026-11-20T03:33:01.641Z pushedAt=2026-11-20T06:12:27.968Z nl=1 -->

Starting from API version 26.1.0, the Secure Access Fence Service is supported. The Secure Access Fence Service assists users in making access control decisions when using an agent operating system. It is responsible for the management and control of access behaviors to user-sensitive data and system capabilities, and manages the full lifecycle of access control policies and access records. The following independent capabilities are currently provided:

- **Obtaining CLI credentials:** The system provides a rich set of CLI command-line tools (such as `ohos-batteryManager total-energy`) for querying system capabilities such as battery information and device state. Third-party applications need to call these CLI tools in scenarios such as device management and O&M diagnosis. However, CLI tools involve system-level permissions. If an application executes them directly, permission escalation and security risks arise. The system issues verifiable ticket credentials to ensure that only user-authorized applications can call the related commands. For details, refer to [Obtaining CLI Credentials (Ticket)](secure-access-fence-guidelines.md).
- **Querying and requesting permission to control a target application:** The system provides system operation capabilities such as simulated clicks. With user authorization, an application can operate other applications to complete business logic. However, if capabilities such as simulated clicks are abused by malicious applications, sensitive operations (such as transfer confirmation and data deletion) may be silently executed without the user's awareness, causing property loss and privacy leakage. The system manages and controls the behavior of applications manipulating target applications through simulated clicks and other means, and provides a mechanism for querying and requesting control permission: an application can first query the control permission state of the target application. If the state is DENY, it then requests control authorization from the user, ensuring that only user-authorized applications can control the target application. For details, refer to [Querying and Requesting Permission to Control a Target Application](app-control-permission-guidelines.md).

## Related Capabilities

Compared with the capabilities provided by program access control (`@ohos.abilityAccessCtrl`), the program access control mechanism manages and controls the permissions for applications to access system resources (images, text, contacts, and so on) and system capabilities (camera, microphone, and so on). It targets the direct access of ordinary applications to system resources. The Secure Access Fence Service, however, focuses on agent scenarios. It manages and controls the system resources and tools that an agent calls during task execution, such as CLI command-line tools and control operations on other applications.

## Related APIs

For the definitions of the interfaces related to the Secure Access Fence Service, refer to [@ohos.abilityToolAccessCtrl](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md).
