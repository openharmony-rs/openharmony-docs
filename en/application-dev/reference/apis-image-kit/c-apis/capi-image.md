# Image

## Overview

Provides APIs for obtaining pixel map data and information.

**Since**: 8

## Files

| Name | Description |
| -- | -- |
| [image_pixel_map_napi.h](capi-image-pixel-map-napi-h.md) | Declares the APIs that can lock, access, and unlock a pixel map. Need link <b>libpixelmap_ndk.z.so</b> |
| [image_packer_mdk.h](capi-image-packer-mdk-h.md) | Declares APIs for encoding image into data or file.<br> The packing image data module used to pack pixel data into a target.<br> The following steps are recommended for packing process: Create a image packer object by calling OH_ImagePacker_Create function. And then covert the image packer object to ImagePacker_Native by OH_ImagePacker_InitNative. Next using OH_ImagePacker_PackToData or OH_ImagePacker_PackToFile to pack source to target area with requird packing options. Finally, release the ImagePacker_Native by OH_ImagePacker_Release. |
| [image_pixel_map_mdk.h](capi-image-pixel-map-mdk-h.md) | Declares the APIs that can lock, access, and unlock a pixel map. |
| [image_mdk.h](capi-image-mdk-h.md) | Declares functions that access the image rectangle, size, format, and component data. Need link <b>libimagendk.z.so</b> |
| [image_source_mdk.h](capi-image-source-mdk-h.md) | Declares APIs for decoding an image source into a pixel map. |
| [image_mdk_common.h](capi-image-mdk-common-h.md) | Declares the common enums and structs used by the image interface. |
| [image_receiver_mdk.h](capi-image-receiver-mdk-h.md) | Declares the APIs for obtaining image data from the native layer. |
