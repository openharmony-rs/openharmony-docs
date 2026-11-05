# @ohos.file.RecentPhotoComponent(最近图片组件)

RecentPhotoComponent是最近图片组件，应用可以在布局中嵌入最近图片组件，通过此组件，应用无需申请权限，即可指定配置访问公共目录中最近的一个照片或视频文件。授予的权限仅包含只读权限。该组件适用于需要快速展示或选择最近照
 片或视频的场景，如聊天应用发送照片、社交应用快速分享等。

最近图片组件不支持嵌套，且不应在该组件上覆盖设置overlay属性或更高层级组件，以免导致手势事件失效。

> **说明：**
 >
 > - 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 >
 > - 该组件不支持[同层渲染](../../../web/web-same-layer.md)。

## 属性

支持[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-comp.md)。

## 导入模块

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [RecentPhotoInfo](arkts-medialibrary-file-recentphotocomponent-recentphotoinfo-c.md) | 最近图片相关信息。 |
| [RecentPhotoOptions](arkts-medialibrary-file-recentphotocomponent-recentphotooptions-c.md) | 最近图片配置选项。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [RecentPhotoComponent](arkts-medialibrary-file-recentphotocomponent-recentphotocomponent-s.md) | RecentPhotoComponent({ recentPhotoOptions?: RecentPhotoOptions, onRecentPhotoCheckResult?: RecentPhotoCheckResultCallback, onRecentPhotoClick: RecentPhotoClickCallback, onRecentPhotoCheckInfo?: RecentPhotoCheckInfoCallback, }) |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RecentPhotoCheckInfoCallback](arkts-medialibrary-recentphotocheckinfocallback-t.md) | 最近图片是否存在查询结果以及最近图片相关信息的回调事件。 |
| [RecentPhotoCheckResultCallback](arkts-medialibrary-recentphotocheckresultcallback-t.md) | 最近图片查询结果回调事件。 |
| [RecentPhotoClickCallback](arkts-medialibrary-recentphotoclickcallback-t.md) | 用户点击最近图片组件时触发的回调事件，返回值无实际作用，可返回true或false。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PhotoSource](arkts-medialibrary-file-recentphotocomponent-photosource-e.md) | 枚举，图片或者视频数据的来源类型。 |

## 示例

```TypeScript
// xxx.ets
// 从API version 23开始，推荐使用统一导入方式，从'@kit.MediaLibraryKit'导入所需模块。
// 在API version 23之前的版本中，需要使用分别导入方式。
// import { RecentPhotoComponent, RecentPhotoOptions, PhotoSource, RecentPhotoInfo, RecentPhotoCheckResultCallback, RecentPhotoClickCallback, RecentPhotoCheckInfoCallback } from '@ohos.file.RecentPhotoComponent';
// import { BaseItemInfo } from '@ohos.file.PhotoPickerComponent';
// import { photoAccessHelper } from '@ohos.file.photoAccessHelper';
import {
  photoAccessHelper,
  RecentPhotoComponent, 
  RecentPhotoOptions, 
  PhotoSource, 
  RecentPhotoInfo, 
  RecentPhotoCheckResultCallback, 
  RecentPhotoClickCallback, 
  RecentPhotoCheckInfoCallback,
  BaseItemInfo
} from '@kit.MediaLibraryKit';

@Entry
@Component
struct PickerDemo {
  private recentPhotoOptions: RecentPhotoOptions = new RecentPhotoOptions();
  private recentPhotoCheckResultCallback: RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => this.onRecentPhotoCheckResult(recentPhotoExists);
  private recentPhotoClickCallback: RecentPhotoClickCallback = (recentPhotoInfo: BaseItemInfo): boolean => this.onRecentPhotoClick(recentPhotoInfo);
  private recentPhotoCheckInfoCallback: RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => this.onRecentPhotoCheckInfo(recentPhotoExists, info);

  aboutToAppear() {
    this.recentPhotoOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE;
    this.recentPhotoOptions.period = 30;
    this.recentPhotoOptions.photoSource = PhotoSource.ALL;
  }

  private onRecentPhotoCheckResult(recentPhotoExists: boolean): void {
    // 存在符合条件的照片或视频。
    if (recentPhotoExists) {
      console.info('The photo exists.');
    }
  }

  private onRecentPhotoClick(recentPhotoInfo: BaseItemInfo): boolean {
    // 照片或视频返回。
    if (recentPhotoInfo) {
      console.info('The photo uri is ' + recentPhotoInfo.uri);
      return true;
    }
    return true;
  }

  private onRecentPhotoCheckInfo(recentPhotoExists: boolean, info: RecentPhotoInfo): void {
    // 是否存在符合条件的照片或视频，若存在则可以拿到该照片或视频的相关信息。
  }

  build() {
    Stack() {
      RecentPhotoComponent({
        recentPhotoOptions: this.recentPhotoOptions,
        onRecentPhotoCheckResult: this.recentPhotoCheckResultCallback,
        onRecentPhotoClick: this.recentPhotoClickCallback,
        onRecentPhotoCheckInfo: this.recentPhotoCheckInfoCallback,
      }).height('100%').width('100%')
    }
  }
}
```
