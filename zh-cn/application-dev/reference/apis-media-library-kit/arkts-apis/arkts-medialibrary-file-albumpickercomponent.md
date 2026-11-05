# @ohos.file.AlbumPickerComponent(Album Picker组件)

AlbumPickerComponent是相册选择组件，相册选择组件适用于需要在应用内展示相册列表让用户选择相册浏览图片或视频的场景，例如社交媒体应用中让用户选择相册进行照片上传。通过此组件，应用无需申请相册访问权限即可访问公共目录中
 的相册列表，做到了简化权限申请流程、降低开发成本，从而提升了用户体验。

相册选择组件需配合图片选择器组件一起使用。当用户选择相册后，系统触发onAlbumClick回调并将AlbumInfo（包含相册URI和名称）传递给应用。应用需通过PickerController将URI传递给图片选择器组件以刷新显示
 对应相册的图片和视频。详细协作机制请参见文档[@ohos.file.PhotoPickerComponent (PhotoPicker组件)](arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md)。

相册选择组件不支持嵌套，且不应在该组件上覆盖设置overlay属性或更高层级组件，以免导致手势事件失效。

> **说明：**
 >
 > - 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 >
 > - 该组件不支持[同层渲染](../../../web/web-same-layer.md)。

## 属性

支持[通用属性](../../apis-arkui/arkts-components/arkts-arkui-common-comp.md)。

## 导入模块

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AlbumInfo](arkts-medialibrary-file-albumpickercomponent-albuminfo-c.md) | 相册相关信息。 |
| [AlbumPickerController](arkts-medialibrary-file-albumpickercomponent-albumpickercontroller-c.md) | 应用可通过AlbumPickerController向组件发送数据。 |
| [AlbumPickerOptions](arkts-medialibrary-file-albumpickercomponent-albumpickeroptions-c.md) | Album Picker配置选项。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AlbumPickerComponent](arkts-medialibrary-file-albumpickercomponent-albumpickercomponent-s.md) | AlbumPickerComponent({albumPickerOptions?: AlbumPickerOptions, onAlbumClick?: (albumInfo: AlbumInfo) =&gt; boolean, onEmptyAreaClick?: EmptyAreaClickCallback, albumPickerController?: AlbumPickerController }) |

### 类型

| 名称 | 说明 |
| --- | --- |
| [EmptyAreaClickCallback](arkts-medialibrary-emptyareaclickcallback-t.md) | 点击相册组件空白区域时产生的回调事件。 |

## 示例

```TypeScript
// xxx.ets
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, PickerColorMode, photoAccessHelper, EmptyAreaClickCallback } from '@kit.MediaLibraryKit';

@Entry
@Component
struct PickerDemo {
  albumPickerOptions: AlbumPickerOptions = new AlbumPickerOptions();
  private emptyAreaClickCallback: EmptyAreaClickCallback = (): void => this.onEmptyAreaClick();

  aboutToAppear() {
    this.albumPickerOptions.themeColorMode = PickerColorMode.AUTO;
    this.albumPickerOptions.filterType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE;
  }
  
  private onAlbumClick(albumInfo: AlbumInfo): boolean {
    if (albumInfo?.uri) {
      // 通过pickerController向PhotoPickerComponent发送消息，通知其刷新。
    }
    if (albumInfo?.albumName) {
      // 基于获取到的albumName后续逻辑处理。
    }
    return true;
  }
  
  private onEmptyAreaClick(): void {
    // 点击组件空白区域回调。
  }

  build() {
    Stack() {
      AlbumPickerComponent({
        albumPickerOptions: this.albumPickerOptions,
        onAlbumClick: (albumInfo: AlbumInfo): boolean => this.onAlbumClick(albumInfo),
        onEmptyAreaClick: this.emptyAreaClickCallback,
      }).height('100%').width('100%')
    }
  }
}
```
