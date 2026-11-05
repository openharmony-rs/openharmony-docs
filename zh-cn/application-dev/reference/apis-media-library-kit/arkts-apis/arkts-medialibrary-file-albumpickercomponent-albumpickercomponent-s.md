# AlbumPickerComponent

```TypeScript
export declare struct AlbumPickerComponent
```

AlbumPickerComponent({albumPickerOptions?: AlbumPickerOptions, onAlbumClick?: (albumInfo: AlbumInfo) =&gt; boolean, onEmptyAreaClick?: EmptyAreaClickCallback, albumPickerController?: AlbumPickerController })

应用可以在布局中嵌入相册选择组件，通过此组件，应用无需申请权限，即可访问公共目录中的相册列表。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AlbumPickerComponent--><!--Device-unnamed-export declare struct AlbumPickerComponent-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## onAlbumClick

```TypeScript
onAlbumClick?: (albumInfo: AlbumInfo) => boolean
```

用户选择某个相册时产生的回调事件，将相册uri给到应用。不对返回值做特殊处理。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerComponent-onAlbumClick?: (albumInfo: AlbumInfo) => boolean--><!--Device-AlbumPickerComponent-onAlbumClick?: (albumInfo: AlbumInfo) => boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| albumInfo | [AlbumInfo](arkts-medialibrary-file-albumpickercomponent-albuminfo-c.md) | 是 |  |

## onEmptyAreaClick

```TypeScript
onEmptyAreaClick?: EmptyAreaClickCallback
```

点击相册组件空白区域时产生的回调事件，并将该次点击通知给应用。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerComponent-onEmptyAreaClick?: EmptyAreaClickCallback--><!--Device-AlbumPickerComponent-onEmptyAreaClick?: EmptyAreaClickCallback-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumPickerController

```TypeScript
albumPickerController?: AlbumPickerController
```

应用可通过AlbumPickerController向组件发送数据。

**类型：** [AlbumPickerController](arkts-medialibrary-file-albumpickercomponent-albumpickercontroller-c.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerComponent-albumPickerController?: AlbumPickerController--><!--Device-AlbumPickerComponent-albumPickerController?: AlbumPickerController-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumPickerOptions

```TypeScript
albumPickerOptions?: AlbumPickerOptions
```

AlbumPicker的配置信息。

**类型：** [AlbumPickerOptions](arkts-medialibrary-file-albumpickercomponent-albumpickeroptions-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerComponent-albumPickerOptions?: AlbumPickerOptions--><!--Device-AlbumPickerComponent-albumPickerOptions?: AlbumPickerOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
