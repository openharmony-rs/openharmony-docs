# CropAndScaleStrategy

表示裁剪与缩放的先后策略的枚举。

如果在配置解码选项[DecodingOptions](arkts-image-image-decodingoptions-i.md)时，未填入参数cropAndScaleStrategy，并且同时设置了参数desiredRegion和desiredSize，由于系统对于不同图片格式采用的解码算法不同，最终解码效果将略有差异。

例如原始图片大小为200x200，传入desiredSize:{width: 150, height: 150}，desiredRegion:{x: 0, y: 0, width: 100, height: 100}，即预期解码原图左上角1/4区域，最终将pixelMap大小缩放至150x150返回。

对于jpeg、webp图片（部分dng图片解码时会优先解码图片中的jpeg预览图，在此场景下也会被视为jpeg图片格式）会先进行下采样，例如按照7/8下采样，再基于175x175的图片大小进行区域裁剪，因此最终的区域内容稍大于原图的左上角1/4区域。

对于svg图片，由于是矢量图，可以任意缩放不损失清晰度，在解码时会根据desiredSize与原图Size的比例选择缩放比例，再基于缩放后的图片大小进行区域裁剪，因此最终返回的解码区域会有所差异。

针对该场景，建议在解码选项同时设置了desiredRegion与desiredSize时，参数cropAndScaleStrategy应传入CROP_FIRST保证效果一致。

**起始版本：** 18

<!--Device-image-enum CropAndScaleStrategy--><!--Device-image-enum CropAndScaleStrategy-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCALE_FIRST

```TypeScript
SCALE_FIRST = 1
```

解码参数如果同时设置desiredRegion与desiredSize，先根据desiredSize进行缩放，再根据desiredRegion进行区域裁剪。

**起始版本：** 18

<!--Device-CropAndScaleStrategy-SCALE_FIRST = 1--><!--Device-CropAndScaleStrategy-SCALE_FIRST = 1-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## CROP_FIRST

```TypeScript
CROP_FIRST = 2
```

解码参数如果同时设置desiredRegion与desiredSize，先根据desiredRegion进行区域裁剪，再根据desiredSize进行缩放。

**起始版本：** 18

<!--Device-CropAndScaleStrategy-CROP_FIRST = 2--><!--Device-CropAndScaleStrategy-CROP_FIRST = 2-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

