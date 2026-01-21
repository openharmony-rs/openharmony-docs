# CryptoExtensionAbility Extension Capability Overview

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

**CryptoExtensionAbility** is a derived class of [ExtensionAbility](../../application-models/extensionability-overview.md) in the stage model.

**CryptoExtensionAbility** provides the API definitions required for external key management extension capabilities for driver vendors, including APIs for resource opening or closing, PIN code authentication, signing and signature verification, and certificate export.

**CryptoExtensionAbility** can isolate the implementation differences of underlying hardware (Ukey driver) vendors.

If a third-party driver HAP needs to define its external key management extension capabilities, the following steps are required:

First, the HAP inherits **CryptoExtensionAbility** and implements the related APIs. Then, it registers the capabilities using the Provider registration API. Finally, HUKS and certificate management open the key management extension capabilities for applications.

## Core Capability Implementation

**CryptoExtensionAbility** provides the following capabilities:

1. Device management: A single **ExtensionAbility** can connect to multiple Ukey devices, and the maximum number of Ukey devices is 10.
2. Handle management: Application-based handle resource management is supported for the same Ukey resource (for example, the keys in a container).
   - Multiple OpenHarmony applications can access the same Ukey key resource. For example, after OpenHarmony application 1 opens container A, OpenHarmony application 2 can also open container A.
   - Multiple OpenHarmony applications can perform operations on the same Ukey key resource. For example, after OpenHarmony application 1 performs private key signing on container A, OpenHarmony application 2 can also perform private key signing on container A after verifying the PIN. The two applications do not affect each other.
3. Key session management: Three-segment key management is supported. A single signature verification requires the cooperation of three functions [onInitSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityoninitsession), [onUpdateSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonupdatesession), and [onFinishSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonfinishsession) in three steps, and session management and key session status caching also need to be supported.
   - **init**: Initializes the key session and returns the session handle information.
   - **update**: Passes group data, performs cryptographic operations on the group data, updates the key session information, and returns the intermediate data (if any).
   - **finish**: Passes the last group of data, returns the key, ends the key session, and returns the final result.
4. Authentication state management: Application-based authentication state management is supported. For application A in the same UKey, after OpenHarmony application 1 verifies the PIN of application A, OpenHarmony application 2 needs to verify the PIN again if it wants to access application A.
5. Certificate query: Enumeration of all certificates and query of certificates in a single container based on certificate type are supported.
