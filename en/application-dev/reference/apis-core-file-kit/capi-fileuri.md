# fileUri
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0547715d750965c950e08363cedf1ff726e5bd8a translatedAt=2026-11-10T05:06:01.892Z pushedAt=2026-11-10T07:29:25.137Z nl=1 -->

## Overview

File Uniform Resource Identifier (fileUri).<br> Supports conversion between fileUri and paths, as well as format validation of fileUri. This module is mainly used for URI format validation and URI conversion. URIs are used in file sharing scenarios between applications. An application sandbox path can be converted into a URI according to system rules, avoiding direct transfer of the sandbox path. Callers must ensure the validity of all API input parameters. The APIs convert and output results according to fixed rules and do not check whether the corresponding file or directory exists.

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [oh_file_uri.h](capi-oh-file-uri-h.md) | Provides methods for mutual conversion between URIs and paths, directory URI retrieval, and URI format validation, applicable to URI conversion and validation in file sharing scenarios. |
