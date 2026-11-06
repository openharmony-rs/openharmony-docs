---
kits: ["Drm Kit / Digital Rights Management Services"]
description: "Defines core DRM Kit concepts, including CencInfo, content protection levels, DRM certificates, MediaKeySystem, and MediaKeySession."
keywords: [DRM, terms, CencInfo, content protection level, DRM certificate, MediaKeySystem, MediaKeySession, media keys, PSSH]
doctype: glossary
status: active
---
# Glossary

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=92b708fb842b7fe0ab4ee9b86fb422e92c237d46 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## C

### CencInfo

Describes encryption of audio/video frames, including the encryption algorithm and mode, key ID (KeyId), initialization vector (IV), and subsample encryption information. When using AVCodec Kit, set this information in the AVBuffer CencInfo so that audio/video frames are decrypted and decoded accordingly when PushInputBuffer is called.

### Content Protection Level

The security level supported by a DRM solution for content decryption, decoding, and rendering. Common levels include unknown (CONTENT_PROTECTION_LEVEL_UNKNOWN), software (CONTENT_PROTECTION_LEVEL_SW_CRYPTO), hardware (CONTENT_PROTECTION_LEVEL_HW_CRYPTO), enhanced hardware (CONTENT_PROTECTION_LEVEL_ENHANCED_HW), and maximum (CONTENT_PROTECTION_LEVEL_MAX) content protection.

## D

### DRM Certificate

A device certificate required by a DRM solution to verify device authenticity and security. Different DRM solutions use different device certificates. Generally, the DRM system automatically provisions the certificate during device registration, with no app-level handling required.

### DRM Content Authorization

Supports online license requests and processing, offline license loading, and media key status queries, and authorizes DRM content according to license permissions. Permission policies include security levels, output control, and playback start and end times.

### DRM Content Decryption

The process of decrypting DRM-encrypted content. DRM Kit supports HLS and DASH media protocols, MP4 and TS containers, H.264 video encoding, and AAC audio encoding.

### DRM Content License

A DRM solution uses licenses to authorize devices. A license contains content keys and permission control information, including security levels, output control, and playback start and end times. License formats and supported permission policies vary by DRM solution.

### DRM Kit

Digital Rights Management Kit provides authorization and decryption of DRM-encrypted content, including DRM plugin management, certificate management, license management, content authorization, and content decryption. It supports DRM solution integration, certificate provisioning, and content authorization and decryption.

### DRM MediaKeySystemInfo

Describes DRM content encryption, including the DRM solution UUID and pssh data. Apps can obtain this information from the DRM description provided by their service, or through the mediaKeySystemInfoUpdate event in ArkTS or the MediaKeySystemInfo callback in C/C++ provided by Media Kit or AVCodec Kit.

### DRM Plugin

A DRM solution driver integrated into the system that implements DRM HDI APIs. It is generally implemented by the DRM solution provider using the HDI APIs provided by DRM Kit to support different DRM solutions.

### DRM Provision

The process through which a DRM solution obtains a device certificate. Provisioning procedures vary by DRM solution. Certificates are generally preinstalled at the factory or automatically provisioned by the DRM system, with no additional app-level handling required. To trigger provisioning from an app, obtain the certificate management API documentation from the DRM solution provider.

### DRM Solution

A system or service that provides digital rights protection. Each solution has its own UUID, certificate system, license format, and permission policies. Common solutions include Widevine, FairPlay, and PlayReady.

## M

### Media Key

A key used to decrypt DRM-protected content. Online media keys are used for real-time streaming playback, whereas offline media keys can be stored persistently for offline playback.

### MediaKeySession

A session object for license management and media content decryption, with its lifecycle managed by MediaKeySystem. Supports requesting, processing, updating, and deleting licenses, and works with Media Kit or AVCodec Kit to decrypt DRM content.

### MediaKeySystem

The core DRM Kit object for DRM certificate and MediaKeySession management. Manages the lifecycle of a DRM solution, certificate provisioning, and session creation.

## O

### Offline Media Key

A media key that can be stored persistently on the device for offline playback. Managed through an offline media key ID, with support for restoration, status queries, and deletion.

## P

### Protection System Specific Header Box (PSSH)

Data used by a DRM solution to describe how content is encrypted. Included in DRM information and used as initialization data when generating a license request.

### Provision Request

A request generated during device DRM certificate provisioning. Contains device information and certificate request data and must be sent to the DRM provisioning server to obtain a certificate response.

## S

### Secure Decoder

Decoding in a protected hardware environment to prevent unauthorized access to decrypted content. When secure decoding is required, decrypted content is decoded directly in secure hardware without being exposed to a non-secure environment.

### Secure Video Path

A complete video processing path for secure decryption, decoding, rendering, and output. Prevents unauthorized access to content throughout processing and depends on the hardware security capabilities of the DRM solution and operating system.

## U

### Universally Unique Identifier (UUID)

Identifies a DRM solution. Each solution has a unique UUID, which apps use to identify the solution and create the corresponding MediaKeySystem instance.