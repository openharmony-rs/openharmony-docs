# getImageSourceSupportedFormats

## getImageSourceSupportedFormats

```TypeScript
function getImageSourceSupportedFormats(): string[]
```

获取支持解码的图片格式，图片格式以mime type表示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function getImageSourceSupportedFormats(): string[]--><!--Device-image-function getImageSourceSupportedFormats(): string[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 支持解码的图片格式（mime type）列表。 |

## 示例

```TypeScript
async function GetImageSourceSupportedFormats() {
    let formats = image.getImageSourceSupportedFormats();
    console.info('formats:', formats);
}

async function IsSupportedTiffFormat() {
    let formats = image.getImageSourceSupportedFormats();
    return formats.includes("image/tiff");
}
```

