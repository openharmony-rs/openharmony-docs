# AlbumPickerController

```TypeScript
export declare class AlbumPickerController
```

应用可通过AlbumPickerController向组件发送数据。

**起始版本：** 20

**装饰器类型：** @Observed

<!--Device-unnamed-export declare class AlbumPickerController--><!--Device-unnamed-export declare class AlbumPickerController-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { AlbumPickerComponent, AlbumPickerOptions, AlbumInfo, EmptyAreaClickCallback, AlbumPickerController } from '@kit.MediaLibraryKit';
```

## setFontSize

```TypeScript
setFontSize(fontSize: number | string): void
```

应用可通过该接口设置相册列表的字体大小。需要在创建相册选择组件时传入albumPickerController参数。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-AlbumPickerController-setFontSize(fontSize: number | string): void--><!--Device-AlbumPickerController-setFontSize(fontSize: number | string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontSize | number &#124; string | 是 | 字体大小，取值范围参考[fontSize](../../apis-arkui/arkts-components/arkts-arkui-text-comp-attribute.md#fontsize)。 |
