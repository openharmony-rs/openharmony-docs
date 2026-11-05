# Module Description

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=82dc1fd26a15c359a60162968b248e32427fed86 translatedAt=2026-11-04T04:15:02.890Z pushedAt=2026-11-04T10:12:50.070Z nl=1 -->

The DRM (Digital Rights Management) framework component adopts a plug-in architecture and connects to different DRM solutions through unified plug-in interfaces, supporting the development of digital rights management functions for audio and video media services. It applies to business scenarios that require copyright protection, such as online video playback, music applications, and e-books, effectively preventing content piracy and unauthorized access, protecting the rights and interests of content providers, and ensuring secure playback of audio and video content. Developers can call the DRM plug-ins provided by the system to implement the following functions:
- DRM certificate management: Generate certificate requests and set certificate responses to implement certificate Provision (download and installation). Use scenario: online video platforms, music applications, and other audio and video playback services that need to obtain licenses.
- DRM media key management: Generate media key requests, manage media key responses, and handle offline media keys.
- DRM content authorization: Support DRM plug-ins to authorize DRM content based on media keys.
- DRM content decryption: Support media playback decryption calls to decrypt DRM content.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { drm } from '@kit.DrmKit';
```
