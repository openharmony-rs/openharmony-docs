# MediaLibrary_RequestId
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=2ab5b998917bb062294cfbc0e7284f8431e10efc translatedAt=2026-11-03T07:14:19.262Z pushedAt=2026-11-04T03:11:19.977Z nl=1 -->

```c
typedef struct MediaLibrary_RequestId {...} MediaLibrary_RequestId
```

## Overview

Defines a struct for the request ID.

A value of this type is returned when a media asset is requested.

The request ID can be used to cancel the corresponding media asset request.

If the request fails, this field is an all-zero string, for example, "00000000-0000-0000-0000-000000000000".

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

**Header file**: [media_asset_base_capi.h](capi-media-asset-base-capi-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char requestId[UUID_STR_MAX_LENGTH] | Request ID, which identifies a media library resource request and can be used to cancel the request. |


