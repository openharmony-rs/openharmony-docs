# Sharing an Application File
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @gzhuangzhuang-->
<!--Designer: @wang_zhangjun; @chenxi0605-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=cc5502f4bd37e222f172b28bc0a5e060d5be809d translatedAt=2026-10-29T10:30:53.870Z pushedAt=2026-10-29T10:30:53.870Z nl=1 -->

An application can share a file with another application based on the uniform resource identifier (URI) of the file.

## Using startAbility to Start a File Application

Using [file picker (startAbility)](../application-models/file-processing-apps-startup.md), an application can share a single file and grant another application read-only or read/write permission through [wantConstant.Flags in ohos.app.ability.wantConstant](../reference/apis-ability-kit/js-apis-app-ability-wantConstant.md#flags). The receiving application can open the URI with [fileIo.open](../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen) to read or write the file.

## Shareable Application Directories

| Application Sandbox Path | Description &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; |
| ------- | ---- |
| /data/storage/el1/base | Application data directory protected by EL1 encryption. |
| /data/storage/el2/base | Application data directory protected by EL2 encryption. |
| /data/storage/el2/distributedfiles | Account-based distributed data directory protected by EL2 encryption. |

## File URI Specifications

The file URIs are in the following format:

  file://&lt;bundleName&gt;/&lt;path&gt;

- **file**: indicates a file URI.

- *bundleName*: specifies the owner of the file, that is, the application that shares the file.

- *path*: specifies the application sandbox path of the file.

> **NOTE**
>
> 1. URI processing involves encoding and decoding. The system cannot guarantee that URIs constructed by applications are usable.
> 2. Use system APIs to obtain URIs, such as [getUriFromPath()](../reference/apis-core-file-kit/js-apis-file-fileuri.md#fileurigeturifrompath).

## Samples

For application file sharing, the following sample is available:

- [SandboxShare (ArkTS) (API9)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/FileManagement/FileShare/SandboxShare)