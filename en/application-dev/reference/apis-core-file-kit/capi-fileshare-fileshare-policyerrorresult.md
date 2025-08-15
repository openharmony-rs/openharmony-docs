# FileShare_PolicyErrorResult
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie; @hongjin-li_admin-->
<!--SE: @chenxi0605; @JerryH1011-->
<!--TSE: @leiyuqian-->

## Overview

Represents the permission policy error result.

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

**Header file**: [oh_file_share.h](capi-oh-file-share-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* uri | Pointer to the URI, on which the permission fails to be granted or activated.|
| FileShare_PolicyErrorCode code | Error code corresponding to the URI.|
| char* message | Pointer to the error message.|
