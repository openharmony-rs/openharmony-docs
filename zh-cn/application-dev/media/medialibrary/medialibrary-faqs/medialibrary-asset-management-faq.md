# 如何正确管理媒体资源
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @TristanMVP-->
<!--Designer: @AnakinJiang-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

[Media Library Kit](../photoAccessHelper-overview.md)（媒体文件管理服务）提供了媒体资源的管理能力，开发者可以访问和修改相册中的媒体信息。

> **注意：**
>
> Media Library Kit仅提供图片和视频的管理能力，不涉及音频文件的管理。

## 媒体资源的常用路径表示

有多种路径形式来表示媒体资源，对应了不同的含义和使用场景，作为媒体资源的唯一标识，可在媒体资源管理过程中的部分[媒体文件操作](#标准媒体文件操作流程)中被使用。

| 类型  | 形式  | 举例  | 说明  |
| :------------ | :------------ | :------------ | :------------ |
| URI  | file://media/Photo/&lt;id&gt;/&lt;真实文件名(无后缀)&gt;/&lt;displayName&gt;  | 图片：<br>file://media/Photo/111/IMG\_1234567890\_123/A.jpg<br>视频：<br>file://media/Photo/222/VID\_1234567890\_321/B.mp4  | 字段定义与使用方式详见[媒体文件URI](../../../file-management/user-file-uri-intro.md#媒体文件uri)。|
| Path(媒体沙箱路径)  | /data/storage/el2/media/Photo/&lt;id&gt;/&lt;真实文件名(无后缀)&gt;/&lt;displayName&gt;  | 图片：<br>/data/storage/el2/media/Photo/111/IMG\_1234567890\_123/A.jpg<br>视频：<br>/data/storage/el2/media/Photo/222/VID\_1234567890\_321/B.mp4<br>  | 媒体沙箱路径用于三方应用访问媒体资源。  |
| 真实路径  | /storage/cloud/100/files/Photo/&lt;所在桶目录&gt;/&lt;真实文件名&gt;  | 图片：<br>/storage/cloud/100/files/Photo/1/IMG\_1234567890\_123.jpg<br>视频：<br>/storage/cloud/100/files/Photo/2/VID\_1234567890\_321.mp4  | 媒体资源在设备文件系统内实际保存的位置。  |

## 标准媒体文件操作流程

| 媒体文件操作  | 标准实现方式  |
| :------------ | :------------ |
| <!--DelRow--> 新增（仅系统应用）  | [创建媒体资源](../photoAccessHelper-resource-guidelines.md#创建媒体资源)  |
| <!--DelRow--> 删除（仅系统应用）  | [将文件放入回收站](../photoAccessHelper-resource-guidelines.md#将文件放入回收站)  |
| 获取  | [获取指定媒体资源](../photoAccessHelper-resource-guidelines.md#获取指定媒体资源)<br>[获取图片和视频缩略图](../photoAccessHelper-resource-guidelines.md#获取图片和视频缩略图)<br>[使用Picker选择媒体库资源](../photoAccessHelper-photoviewpicker.md)  |
| 重命名  | [重命名媒体资源](../photoAccessHelper-resource-guidelines.md#重命名媒体资源)  |
| 保存到图库  | [保存媒体库资源](../photoAccessHelper-savebutton.md)  |
| 对用户相册内媒体文件进行操作  | [添加图片和视频到用户相册中](../photoAccessHelper-userAlbum-guidelines.md#添加图片和视频到用户相册中)<br>[获取用户相册中的图片和视频](../photoAccessHelper-userAlbum-guidelines.md#获取用户相册中的图片和视频)<br>[从用户相册中移除图片和视频](../photoAccessHelper-userAlbum-guidelines.md#从用户相册中移除图片和视频)  |

## 常见问题

### 能否通过修改生成或自行构造的媒体库路径来新增、删除、获取、重命名、移动文件或文件夹

不可以。因为媒体库URI和Path为虚拟路径，是通过组合媒体资源的部分属性来对媒体文件进行唯一标识，并非实际存在对应目录层级，也不存在真实的物理文件，需要通过媒体库内部的寻址方式才能进行有效的媒体文件操作。若使用修改生成或自行构造的媒体库路径对媒体文件进行操作，可能会造成非预期的文件操作结果，为确保正确性与稳定性，请务必通过[标准媒体文件操作流程](#标准媒体文件操作流程)进行媒体文件管理。