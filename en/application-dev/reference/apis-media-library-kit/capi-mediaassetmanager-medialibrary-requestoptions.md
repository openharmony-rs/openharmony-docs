# MediaLibrary_RequestOptions
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct MediaLibrary_RequestOptions {...} MediaLibrary_RequestOptions
```

## Overview

The struct defines how media assets are requested and processed.

You can use this struct to set options related to the media asset quality, delivery mode, and more.

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

**Header file**: [media_asset_base_capi.h](capi-media-asset-base-capi-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [MediaLibrary_DeliveryMode](capi-media-asset-base-capi-h.md#medialibrary_deliverymode) deliveryMode | Delivery mode of the requested media asset.|
