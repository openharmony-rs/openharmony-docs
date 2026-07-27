# How to Properly Manage Media Assets
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @TristanMVP-->
<!--Designer: @AnakinJiang-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

[Media Library Kit](../photoAccessHelper-overview.md) provides media asset management capabilities, allowing you to access and modify media information in albums.

> **NOTE**
>
> Media Library Kit provides management capabilities only for images and videos. It does not manage audio files.

## Common Path Representations of Media Assets

Media assets can be represented in different path formats, each corresponding to different meanings and use cases. As unique identifiers of media assets, they can be used in some [media file operations](#standard-media-file-operation-process) during media asset management.

| Type | Format | Example | Description |
| :------------ | :------------ | :------------ | :------------ |
| URI  | file://media/Photo/&lt;ID&gt;/&lt;actual file name without extension&gt;/&lt;displayName&gt; | Image:<br>file://media/Photo/111/IMG\_1234567890\_123/A.jpg<br>Video:<br>file://media/Photo/222/VID\_1234567890\_321/B.mp4  | For details about the field definition and usage, see [Media File URI](../../../file-management/user-file-uri-intro.md#media-file-uri).|
| Path (media sandbox path) | /data/storage/el2/media/Photo/&lt;ID&gt;/&lt;actual file name without extension&gt;/&lt;displayName&gt; | Image:<br>/data/storage/el2/media/Photo/111/IMG\_1234567890\_123/A.jpg<br>Video:<br>/data/storage/el2/media/Photo/222/VID\_1234567890\_321/B.mp4<br> | The media sandbox path is used by third-party applications to access media assets. |
| Actual path | /storage/cloud/100/files/Photo/&lt;bucket directory&gt;/&lt;actual file name&gt; | Image:<br>/storage/cloud/100/files/Photo/1/IMG\_1234567890\_123.jpg<br>Video:<br>/storage/cloud/100/files/Photo/2/VID\_1234567890\_321.mp4  | Actual location where the media asset is stored in the device file system. |

## Standard Media File Operation Process

| Media File Operation | Standard Implementation |
| :------------ | :------------ |
| <!--DelRow-->Add (for system applications only) | [Create media assets](../photoAccessHelper-resource-guidelines.md#creating-a-media-asset) |
| <!--DelRow-->Delete (for system applications only) | [Move media assets to the trash](../photoAccessHelper-resource-guidelines.md#moving-a-media-asset-to-the-trash) |
| Obtain | [Obtain media assets](../photoAccessHelper-resource-guidelines.md#obtaining-media-assets)<br>[Obtain image and video thumbnails](../photoAccessHelper-resource-guidelines.md#obtaining-an-image-or-video-thumbnail)<br>[Select media assets using Picker](../photoAccessHelper-photoviewpicker.md) |
| Rename | [Rename media assets](../photoAccessHelper-resource-guidelines.md#renaming-a-media-asset) |
| Save to Gallery | [Save media assets](../photoAccessHelper-savebutton.md) |
| Operate on media files in user albums | [Add images and videos to user albums](../photoAccessHelper-userAlbum-guidelines.md#adding-images-or-videos-to-a-user-album)<br>[Obtain images and videos from user albums](../photoAccessHelper-userAlbum-guidelines.md#obtaining-images-and-videos-in-a-user-album)<br>[Remove images and videos from user albums](../photoAccessHelper-userAlbum-guidelines.md#removing-images-and-videos-from-a-user-album) |

## FAQs

### Can I add, delete, obtain, rename, or move files or folders by modifying generated media library paths or constructing media library paths manually?

No. Media library URIs and paths are virtual paths. They uniquely identify media files by combining certain attributes of media assets. They do not correspond to actual directory levels or physical files. Valid media file operations can be performed only through the internal addressing mechanism of the media library. Using modified or manually constructed media library paths to operate on media files may lead to unexpected file operation results. 

The following are common incorrect usage examples. The media library virtual path **/data/storage/el2/media/Photo/111/IMG_1234567890_123/A.jpg** is used as an example.

1. Truncate the generated media path.

   1.1 Delete directory levels from the end of the path. For example:

   - Delete the **displayName** part: **/data/storage/el2/media/Photo/111/IMG_1234567890_123/**
   - Delete the actual file name and **displayName** part: **/data/storage/el2/media/Photo/111/**
   - Delete other directory levels from the end of the path.

   All of these paths are invalid media library directories and cannot be used to represent the parent directory of a media asset.

   1.2 Delete directory levels from the path. For example:

   - Delete the actual file name: **/data/storage/el2/media/Photo/111/A.jpg**
   - Delete the ID part: **/data/storage/el2/media/Photo/IMG_1234567890_123/A.jpg**
   - Delete other directory levels.

   All of these paths are invalid media library directories and cannot represent adding or moving images under a specific directory level.

2. Modify the generated media path.

   2.1 Change **displayName** in the path. For example, replace **A.jpg** with **B.xxx** to obtain **/data/storage/el2/media/Photo/111/IMG_1234567890_123/B.xxx**. This is an invalid media library path and cannot be used to indicate that a new file **B.xxx** is created in the original directory.

   2.2 Change the ID in the path. For example, replace the ID **111** in the path with **1111** to obtain **/data/storage/el2/media/Photo/1111/IMG_1234567890_123/A.jpg**. This is also an invalid media library path and cannot be used to map **A.jpg** whose ID is **111** to another ID **1111**.

   2.3 Change other directory levels in the path.

Paths constructed by truncating or modifying media library directory levels are invalid media library paths. **If add, delete, update, or query APIs, such as fs.stat, fs.lstat, fs.access, fs.open, fs.close, fs.read, fs.write, and fs.unlink, are used on these invalid paths, unexpected results may occur.**

To ensure correctness and stability, always manage media files by following the [standard media file operation process](#standard-media-file-operation-process).
