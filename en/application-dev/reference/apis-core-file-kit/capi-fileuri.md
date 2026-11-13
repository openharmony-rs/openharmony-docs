# fileUri
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=77ffbb47e835fe530737feb44b30ade95bf4c07d translatedAt=2026-11-03T03:47:26.803Z pushedAt=2026-11-04T03:11:33.467Z nl=1 -->

## Overview

File Uniform Resource Identifier.<br>Supports conversion between fileUri and paths, as well as format validation of fileUri. This module is mainly used for URI format validation and URI conversion. URIs are used in file sharing scenarios between applications. An application sandbox path can be converted into a URI according to system rules, avoiding direct passing of the sandbox path. The caller must ensure the validity of all interface input parameters. The interfaces convert and output results according to fixed rules and do not check whether the corresponding file or directory exists.

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [oh_file_uri.h](capi-oh-file-uri-h.md) | Provides methods for mutual conversion between URIs and paths, directory URI retrieval, and URI format validation. |
