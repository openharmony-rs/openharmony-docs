# getImagePackerSupportedFormats

## getImagePackerSupportedFormats

```TypeScript
function getImagePackerSupportedFormats(): string[]
```

获取支持编码的图片格式，图片格式以mime type表示。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 支持编码的图片格式（mime type）列表。 |

**示例：**

```TypeScript
async function GetImagePackerSupportedFormats() {
    let formats = image.getImagePackerSupportedFormats();
    console.info('formats:', formats);
}

```

