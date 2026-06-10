# 媒体库变更说明

## cl.medialibrary.1 ohos.permission.READ_IMAGEVIDEO权限变更

**访问级别**

公共能力

**变更原因**

限制网盘等应用访问云上的图片或视频，避免因为访问云上资产导致隐私安全与设备功耗高、发热等问题。

**变更影响**

此变更涉及应用适配。

变更前：应用通过ohos.permission.READ_IMAGEVIDEO权限，调用Media Library Kit接口可以获取云上和本地图片或视频。

变更后：应用通过ohos.permission.READ_IMAGEVIDEO权限，调用Media Library Kit接口仅可以获取本地图片或视频。


**起始 API Level**

API 9

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

```typescript
PhotoAccessHelper.getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void;

PhotoAccessHelper.getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>;

PhotoAccessHelper.getBurstAssets(burstKey: string, options: FetchOptions): Promise<FetchResult<PhotoAsset>>;

AbsAlbum.getAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<PhotoAsset>>): void;

AbsAlbum.getAssets(options: FetchOptions): Promise<FetchResult<PhotoAsset>>;

fileIo.open(path: string, mode?: number): Promise<File>;

fileIo.open(path: string, callback: AsyncCallback<File>): void;

fileIo.open(path: string, mode: number, callback: AsyncCallback<File>): void;

fileIo.openSync(path: string, mode?: number): File;
```

**适配指导**

涉及默认行为变更：变更前应用能访问云上和本地图片或视频，变更后应用仅能访问本地图片或视频。

如果应用需要访问云上的图片或视频，请通过PhotoViewPicker进行访问。
