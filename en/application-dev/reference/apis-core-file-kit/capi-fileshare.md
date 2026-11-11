# fileShare
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @leiyuqian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0547715d750965c950e08363cedf1ff726e5bd8a translatedAt=2026-11-10T05:05:58.642Z pushedAt=2026-11-10T07:29:18.525Z nl=1 -->

## Overview

This module provides file sharing capabilities, allowing the Uniform Resource Identifier (URI) of a file in a public directory to be authorized to other applications, so that other applications can access the corresponding file or directory according to the authorization. It is suitable for cross-application file sharing scenarios, managing file access permissions through the URI authorization mechanism.

**Since**: 12
## Files

| Name| Description|
| -- | -- |
| [oh_file_share.h](capi-oh-file-share-h.md) | Provides URI-based methods for persistent authorization of files and directories, cancellation of persistent authorization, permission activation, and permission query, applicable to cross-application file sharing scenarios. Persistent authorization is used to save access policies, and permission activation is used to make the persisted permissions take effect. |
