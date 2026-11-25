# CryptoExtensionAbility Extension Capability Overview

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=643ff082fb4d2e3376315b4c787c640f6b6e022e translatedAt=2026-11-03T05:21:16.390Z pushedAt=2026-11-03T06:56:33.858Z nl=1 -->

As a derived class of the extension component [ExtensionAbility](../../application-models/extensionability-overview.md) in the Stage model, CryptoExtensionAbility adapts to the implementation differences of the underlying external key management capabilities, integrates external key management capabilities into the HUKS framework, and provides upper-layer applications with capabilities such as signing and signature verification, key usage, certificate query, and PIN authentication.


This document is intended for **key management extension application developers** (implementers) and describes the interfaces, state management, and constraints that key management extension applications need to pay attention to when implementing CryptoExtensionAbility. For detailed API parameters and the recommended error codes returned by each interface, see [@ohos.security.CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md).

## Overall Process

The complete lifecycle of a key management extension application, from development and registration to deregistration, consists of three phases:

1. Interface implementation: Inherit CryptoExtensionAbility, implement the callback interfaces in [Core Capability Implementation](#core-capability-implementation) as required by the business, and encapsulate calls to the underlying external key management backend.

2. Registration with HUKS: When the key management extension device/service is available, call [registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider) to register CryptoExtensionAbility with HUKS. After successful registration, HUKS and certificate management expose the corresponding key management extension capabilities to applications.

3. Deregistration and offline: In unavailable scenarios such as device removal or service stop, call [unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider) to deregister the registered capabilities and avoid resource residue.

## Access Capabilities

A key management extension application must implement the following mechanisms so that a single ExtensionAbility instance can securely manage one or more external key management resources (such as UKey physical devices and software resources).

Before introducing the specific mechanisms, two core concepts must be clarified:

- Provider: Represents the logical ownership of an external key management driver and is used to uniquely identify the driver in HUKS. Generally, a key management extension application registers one Provider. The naming is recommended to include information about the external key management capability provider to ensure global uniqueness.

- Ability: Represents the extension capability customized by developers for each business scenario and identifies the logical name of a CryptoExtensionAbility instance. Multiple Abilities can be registered under one Provider, corresponding to different CryptoExtensionAbility subclass instances in the key management extension application, to distinguish different business scenarios under the same driver.

The following sections introduce availability detection, Provider/Ability constraints, device-level resource isolation, and customized authentication UI association in sequence.

### Availability Detection and Registration/Unregistration Timing

A key management extension application must detect availability based on the device or service form it integrates with. When the device or service is available, call the [registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider) API to register the CryptoExtensionAbility; when it is unavailable, call the [unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider) API to unregister the CryptoExtensionAbility. For details, see [CryptoExtensionAbility Registration and Unregistration](huks-extension-registration-and-unregistration-arkts-ndk.md).

The detection mechanism varies by device form:
- UKey physical device: listen for USB plug-in and plug-out events.
- Other forms: implement detection based on service availability.

### Provider and Ability Management

A Provider can be associated with multiple CryptoExtensionAbilities. It is recommended to match them one-to-one during use.

- The maximum length of a Provider name is 128 bytes. It is recommended to include information about the external key management capability provider to ensure global uniqueness.
- The entire system supports registering at most **10** CryptoExtensionAbility Providers. When the limit is exceeded, the registerProvider interface returns HUKS_ERR_CODE_EXCEED_LIMIT.
- During registration, the `(providerName, abilityName, bundleName)` triple serves as the unique identifier.

### Device-Level Resource Isolation

It is recommended that the key management extension application ensure that device handles, resource mappings, session states, and authentication states of different external key management resources remain independent of one another.

### Customized Authentication UI

The system provides the PIN authentication dialog capability, allowing upper-layer applications to bring up the UKey PIN authentication UI when needed. If the system default dialog does not meet business requirements, a key management extension application can register a customized authentication UI, associate it when registering the Provider, and bring it up by calling the certificate management APIs when needed.

Starting from API version 26.0.0, registering a [UIAbility](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) as the customized authentication UI is supported, and developers implement the UI layout and interaction logic on their own. This method only supports being brought up by an upper-layer application and depends on the caller holding context information.

Starting from API version 26.0.1, registering a [UkeyAuthExtensionAbility](../../reference/apis-device-certificate-kit/js-apis-UkeyAuthExtensionAbility.md#ukeyauthextensionability) as the customized authentication UI is newly supported. Developers inherit it and implement the UI layout and interaction logic on their own. This method supports two bring-up paths: one is brought up by an upper-layer application, which depends on the caller holding context information; the other is actively brought up by the UKey driver application, which does not depend on the upper-layer application holding context information.

- Quantity limit: For resources corresponding to the same resourceId field, only one type of customized authentication UI (UIAbility or UkeyAuthExtensionAbility) can be associated, and both types cannot be registered at the same time. One CryptoExtensionAbility can be associated with at most **10** customized authentication UIs. If the limit is exceeded, registerProvider returns HUKS_ERR_CODE_EXCEED_LIMIT.
- Field description: When registering the key management extension, register the corresponding customized authentication UI dialog at the same time, and pass in a JSON string through [HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). The abilityName field corresponds to the name field in module.json5, with a maximum length of 127 bytes. The index field corresponds to the customized resource identifier, with a maximum length of 512 bytes, and is used to route the customized authentication UI to a specific resource.
- Typical scenarios: customized PIN input boxes, customized certificate selection UIs, customized user confirmation dialogs, and so on.

The differences between the two methods are as follows:

| Dimension | UIAbility (26.0.0+) | UkeyAuthExtensionAbility (26.0.1+) |
| --- | --- | --- |
| Implementation | Developers implement UIAbility on their own. | Developers inherit UkeyAuthExtensionAbility and implement it on their own. |
| abilityType | 0 (or not passed, processed as UIAbility by default) | 1 |
| Bring-up party | Upper-layer application. | Upper-layer application or UKey driver application. |
| Bring-up API | [openUkeyAuthDialog()](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenukeyauthdialog22) | [openUkeyAuthDialog()](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenukeyauthdialog22) or [openAuthDialogForUkeyProvider()](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthdialogforukeyprovider) |
| Context dependency | Depends on the caller holding context information. | Depends on context (brought up by an upper-layer application) or does not depend on context (brought up by a UKey driver application). |
| Dialog behavior | A normal application window that supports foreground/background switching and can be switched to the background. | A system modal dialog. Before the user completes the interaction, the entire system enters a modal state and cannot be switched to the background or closed. |

## Core Capability Implementation

A key management extension application can implement some of these APIs on demand based on its business needs.

The CryptoExtensionAbility interfaces can be divided into seven capability domains by responsibility, and some capability domains have explicit dependencies when implemented.

- [Resource Identifier](#resource-identifier) and [Handle Management](#handle-management) together form the resource access entry. An upper-layer application can obtain a resourceId in two ways: first, by invoking the certificate management capability to bring up the certificate selection dialog, where the keyUri (that is, the resourceId) is obtained after the user selects a certificate; second, by calling the getResourceId interface of CryptoExtensionAbility to obtain the resourceId based on a business identifier. After obtaining the resourceId, the handle is obtained through openResource. It is recommended that the key management extension application maintain the mapping between application-level handles and underlying device handles using the (UID, handle) pair.
- [Authentication State Management](#authentication-state-management) is used for access control of PIN-protected resources: operations involving private keys (typical scenarios such as signing and decryption) usually require PIN authentication to be completed first. Whether it is mandatory is determined by the key management extension application based on business needs.
- Common operations ([Property Query and Setting](#property-query-and-setting), [Certificate Query and Import](#certificate-query-and-import), and [Key Generation/Import/Export](#key-generationimportexport)) usually do not require PIN authentication.
- [Key Session Management](#key-session-management) processes the intermediate states of signing/verification through a three-phase protocol (initSession/updateSession/finishSession). Typical scenarios include signing/verification, encryption/decryption, and so on.

> **Note:**
>
> 1. The params of all CryptoExtensionAbility interfaces carry the caller identity information (identified by the HUKS_EXT_CRYPTO_TAG_UID tag). The key management extension application can decide whether to use it based on business needs, for example, performing isolation and verification based on the UID in scenarios such as handle management, session management, and authentication management.
> 2. The resultCode of interface functions does not support customization and must be returned according to the error codes defined in the [HuksCryptoExtensionResultCode](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensionresultcode) enumeration; otherwise, exceptions may occur.
> 3. Starting from API version 26.0.0, if a vendor needs to pass custom fine-grained error information, it can be passed in through the errInfo field of the return value. errInfo is of the [HuksExternalErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalerrorinfo) type. The upper-layer application can obtain it through the [huksExternalCrypto.getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo) interface.

### Handle Management

For the same key management extension resource (for example, a key under a container), handle management is required to control the lifecycle of resource access.

- Open a resource: Open the resource identified by resourceId through the [onOpenResource](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onopenresource) API.

   The key management extension application must internally establish a mapping between resourceId and a new handle (the specific implementation is determined by the connected device/service, such as opening a session on a UKey or starting a service on a digital shield), and return the handle to HUKS. The handle value is generated by the key management extension application itself and must be unique.

   The caller identity is carried by HUKS_EXT_CRYPTO_TAG_UID in the params parameter. It is recommended that the key management extension application store handle resources in isolation based on this UID.

- Close a resource: Close the resource corresponding to the handle through the [onCloseResource](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#oncloseresource) API. The key management extension application must internally release the mapping between resourceId and the handle (the specific implementation is determined by the connected device/service, such as closing a session on a UKey), and notify HUKS that the resource has been closed.

- Handle mapping:
  - It is recommended that multiple OpenHarmony applications be allowed to open/close the same resource simultaneously, with each application obtaining an independent mapped handle. For example, after OpenHarmony application 1 opens resource A, OpenHarmony application 2 can also open resource A again.
  - It is recommended that multiple applications operating on the same resource (for example, signing) do not affect each other, with each maintaining an independent handle and session. For example, after OpenHarmony application 1 signs with a private key, OpenHarmony application 2 can also sign with the private key after completing PIN authentication, without affecting each other.

> **Note:**
>
> It is recommended that the key for handle resource storage be the `(UID, handle)` tuple to avoid handle conflicts between different applications.

### Authentication State Management

Supports application-level PIN authentication state management (authentication/query/reset). Each OpenHarmony application must complete PIN authentication independently.

- Authentication state dimension: It is recommended that PIN authentication be performed with the Application defined in GM/T 0016-2023 as the unit, and different Applications must be authenticated independently. After OpenHarmony application 1 completes PIN authentication for Application A, OpenHarmony application 2 still needs independent authentication to access Application A. When the same application accesses different Applications, authentication must also be performed separately.

- PIN encrypted transmission: The PIN passed in by the caller is the ciphertext encrypted with the public key exported in [onGetProperty](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetproperty). The key management extension application must first decrypt it with the corresponding private key in [onAuthUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onauthukeypin), and then call the underlying driver for verification. [onGetUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetukeypinauthstate) is used to query the PIN authentication state.

- Reset authentication state scope: [onClearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onclearukeypinauthstate) is used to clear the application-level authentication state (without releasing the external key management capability or the PIN lock of the device itself). For example, unlocking the UKey physical PIN must be completed through the UKey physical button or a vendor-private channel, and is not exposed through the CryptoExtensionAbility interface.

### Key Generation/Import/Export

Starting from API version 26.0.0, the capabilities of key generation, public key export, and encrypted wrapped key import are provided (keys are stored within the external key management capability).

- Generate a key: Use the [onGenerateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongeneratekeyitem) API to generate a key pair in the key management extension service. The input parameters support specifying the algorithm, key length, and purpose. The key management extension application must set reasonable default values (for example, RSA-2048 and the signing purpose). A successful return indicates that the key pair has been generated.

- Export a public key: Use the [onExportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onexportkeyitem) API to export a public key from the key management extension service. It is recommended to pass the key purpose parameter to export the public key for the specified purpose. If the purpose is not specified, the signing purpose is used by default. The exported public key data is returned through result.outData.

- Import a wrapped key: Use the [onImportWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onimportwrappedkeyitem) API to import an encrypted wrapped key pair into the key management extension service. It must be used together with the transport key (wrappingHandle) within the key management extension service. The wrappedKey data format is defined by the key management extension application. Typical scenario: securely import an externally generated key pair through the transport key within the key management extension service.

### Key Session Management

Signing/verification, encryption/decryption, and other operations are completed using a three-phase protocol.

- Session model:
  - [onInitSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#oninitsession): Initializes a key session and returns a new session handle.
  - [onUpdateSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onupdatesession): Passes segmented data (may be called zero or more times) and performs intermediate cryptographic operations.
  - [onFinishSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onfinishsession): Passes the final segment of data, performs the final cryptographic operation, ends the session, and returns the final result.

- State caching: Vendors must cache the session state, which should at least include the mapping between the session handle and the underlying session, the accumulated intermediate data, and the business identity (passed in through HUKS_EXT_CRYPTO_TAG_UID).

- Lifecycle: When the underlying resources become unavailable or the ExtensionAbility is destroyed, all unfinished sessions should be proactively cleaned up.

### Certificate Query and Import

A key management extension application can support querying, enumerating, and importing certificates by certificate purpose [HUKS_EXT_CRYPTO_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). If not specified, the key management extension application must set a reasonable default value (for example, a certificate for signing purposes).

- Certificate purpose filtering: specified through the `HUKS_EXT_CRYPTO_TAG_PURPOSE` parameter. The following values are recommended:
  - `0`: default purpose
  - `1`: query all credentials
  - `2`: credential signing
  - `3`: credential encryption
  - When not specified, the signing certificate is obtained by default

- Certificate query: [onExportCertificate](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onexportcertificate) queries a single certificate under a resourceId.

- Certificate enumeration: [onEnumCertificates](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onenumcertificates) enumerates all certificates under the current CryptoExtensionAbility.

- Return structure: returned through result.certs, with the element type being Array<[HuksCryptoExtensionCertInfo](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensioncertinfo)>.

- Certificate import (supported since API version 26.0.0): imports a certificate into the key management extension service through the [onImportCertificate](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onimportcertificate) interface.

### Property Query and Setting

A key management extension application can support querying and setting information of the key management extension service.

Properties such as device information and public keys can be queried through the [onGetProperty](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetproperty) interface. After API version 26.0.0, properties can be set through the [onSetProperty](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onsetproperty) interface.

- propertyId naming convention: propertyId is the invocation contract between the upper-layer application and the key management extension application, and its length must be between 1 and 100 bytes. The upper-layer application specifies the propertyId when invoking, and the key management extension application identifies the propertyId in onGetProperty/onSetProperty and performs the corresponding operation. The two ends must agree on the following three items:
  - Function name set: which propertyIds the driver supports and which ones the upper-layer application can invoke.
  - Parameter format: the input parameter structure corresponding to each propertyId.
  - Return format: the return value structure corresponding to each propertyId.

- Required property: In the PIN authentication process, the HUKS framework passes in a propertyId (SKF_ExportPublicKey) and invokes onGetProperty to obtain the public key, which is used to encrypt the PIN passed in subsequently. The key management extension application must implement the SKF_ExportPublicKey property.

> **Note:**
>
> It is recommended to use the SKF standard function names defined in GM/T 0016-2023 as propertyIds to ensure interoperability between different vendors.

### Resource Identifier

Starting from API version 26.0.0, the [onGetResourceId](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetresourceid) interface is provided. Based on parameters such as the Provider/Ability/Bundle names customized by the key management extension application and the caller UID, it returns the corresponding resourceId.

- Interface responsibility: The key management extension application returns the corresponding resourceId based on the business identifier passed in by the upper-layer application, so that the upper-layer application can subsequently access the resource through interfaces such as openResource.

- Implementation points: When the upper-layer application invokes the interface, it carries parameters such as the Ability name, Bundle name, and business identifier (passed in through [HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)) in params. The key management extension application must distinguish the resource to be accessed by the upper-layer application based on the business identifier, and map that business identifier to the corresponding resourceId. The specific form of the business identifier is defined by the key management extension application according to its underlying resource management approach.

- Return structure: On success, the resource ID is returned through the result.resourceId field, identifying a specific resource in the key management extension service, which can be used by the upper-layer application as an input parameter for subsequent interfaces such as openResource.

## Typical Scenario

The CryptoExtensionAbility interfaces are divided into two groups by starting API version: API version 22 provides basic capabilities, and API version 26.0.0 extends enhanced capabilities on this basis. The key management extension application must evaluate the implementation scope according to the target API version.

Browser mutual SSL login can be implemented in API version 22; if it is necessary to support "generating a new certificate on the UKey and automatically importing it" within the same extension, the application must upgrade to API version 26.0.0 and implement onGenerateKeyItem and onImportCertificate.

### Basic Capabilities

API version 22 provides the following interfaces, supporting typical scenarios such as browser-based mutual SSL login, client certificate authentication, and signing.

| Capability Domain | API | Initial Version |
| --- | --- | --- |
| Handle management | onOpenResource, onCloseResource | 22+ |
| Authentication state management | onAuthUkeyPin, onGetUkeyPinAuthState, onClearUkeyPinAuthState | 22+ |
| Key session | onInitSession, onUpdateSession, onFinishSession | 22+ |
| Certificate query and import | onExportCertificate, onEnumCertificates | 22+ |
| Property query and setting | onGetProperty | 22+ |

Typical scenarios supported:

- [Browser-based mutual SSL login](huks-extension-ability-best-dev.md): certificate selection → open resource → PIN authentication → sign and verify → close resource.
- Client certificate authentication: identify available certificates through certificate enumeration and query.
- Signing: three-stage session signing based on resource handles.

### Enhanced Capabilities

API version 26.0.0 adds the following interfaces on top of API version 22, supporting more flexible resource identification, localized key generation, key migration, and other scenarios.

| Capability Domain | API | Initial Version |
| --- | --- | --- |
| Resource identification | onGetResourceId | 26.0.0+ |
| Key generation/import/export | onGenerateKeyItem, onExportKeyItem, onImportWrappedKeyItem | 26.0.0+ |
| Certificate query and import | onImportCertificate | 26.0.0+ |
| Property query and setting | onSetProperty | 26.0.0+ |

Scenarios additionally supported on top of API version 22:

- Custom business identifier: Through onGetResourceId, upper-layer applications can obtain a resourceId based on a business identifier (such as a certificate serial number, container name, or key alias), no longer limited to obtaining it through the certificate management dialog.
- Localized key generation: Through onGenerateKeyItem, a key pair is generated directly within the external key management resource, preventing key leakage during transmission.
- Key migration: Through onImportWrappedKeyItem, in conjunction with the transport key (wrappingHandle) within the external key management resource, an externally generated key pair is securely imported, supporting scenarios such as new device initialization and key backup and recovery.
- Localized certificate management: Through onImportCertificate, certificates are imported into the external key management resource for centralized management.
- Property configuration: Through onSetProperty, configurable properties of the key management extension service are set (not limited to querying).

<!--no_check-->