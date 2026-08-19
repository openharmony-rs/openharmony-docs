# OperationItem

选择媒体文件的过滤配置。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export class OperationItem--><!--Device-photoAccessHelper-export class OperationItem-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## field

```TypeScript
field?: PhotoKeys
```

数据表中的列名。 当前仅支持如下关键字段：URI、PHOTO_TYPE、DISPLAY_NAME、SIZE、DURATION、WIDTH、HEIGHT、ORIENTATION、FAVORITE、TITLE、POSITION、 PHOTO_SUBTYPE、DYNAMIC_RANGE_TYPE、COVER_POSITION、BURST_KEY、LCD_SIZE、THM_SIZE、DETAIL_TIME、MEDIA_SUFFIX、 OWNER_ALBUM_ID、ASPECT_RATIO、DATE_TAKEN_MS&lt;sup&gt;24+&lt;/sup&gt; 通过[select](arkts-medialibrary-photoaccesshelper-photoviewpicker-c.md#select)接口配置此参数时，输入非法字段会抛出错误码401；通 过PhotoPickerComponent (PhotoPicker组件)配置此参数时，输入非法字段无 onPickerControllerReady回调。 非条件谓词如and、or、beginWrap、endWrap等不涉及该字段。

**类型：** [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperationItem-field?: PhotoKeys--><!--Device-OperationItem-field?: PhotoKeys-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## operationType

```TypeScript
operationType: OperationType
```

各类谓词的枚举。

**类型：** OperationType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperationItem-operationType: OperationType--><!--Device-OperationItem-operationType: OperationType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## value

```TypeScript
value?: Array<OperationValueType>
```

不同谓词所需匹配的值。 非条件谓词如and、or、beginWrap、endWrap等不涉及该字段。 限制最大长度为10，超出则取前10个值。

**类型：** Array&lt;[OperationValueType](arkts-medialibrary-photoaccesshelper-operationvaluetype-t.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperationItem-value?: Array<OperationValueType>--><!--Device-OperationItem-value?: Array<OperationValueType>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

