# AVImageQueryOptions

```TypeScript
enum AVImageQueryOptions
```

Enumerates the relationship between the video frame and the time at which the video thumbnail is obtained.

The time passed in for obtaining the thumbnail may be different from the time of the video frame for which the thumbnail is actually obtained. Therefore, you need to specify their relationship.

**Since:** 12

<!--Device-media-enum AVImageQueryOptions--><!--Device-media-enum AVImageQueryOptions-End-->

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_CLOSEST

```TypeScript
AV_IMAGE_QUERY_CLOSEST
```

The frame (not necessarily a key frame) closest to the specified time is selected.

**Since:** 12

<!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_CLOSEST--><!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_CLOSEST-End-->

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_CLOSEST_SYNC

```TypeScript
AV_IMAGE_QUERY_CLOSEST_SYNC
```

The key frame closest to the specified time is selected.

**Since:** 12

<!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_CLOSEST_SYNC--><!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_CLOSEST_SYNC-End-->

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_NEXT_SYNC

```TypeScript
AV_IMAGE_QUERY_NEXT_SYNC = 0
```

The key frame at or next to the specified time is selected.

**Since:** 12

<!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_NEXT_SYNC = 0--><!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_NEXT_SYNC = 0-End-->

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_PREVIOUS_SYNC

```TypeScript
AV_IMAGE_QUERY_PREVIOUS_SYNC
```

The key frame at or prior to the specified time is selected.

**Since:** 12

<!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_PREVIOUS_SYNC--><!--Device-AVImageQueryOptions-AV_IMAGE_QUERY_PREVIOUS_SYNC-End-->

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator
