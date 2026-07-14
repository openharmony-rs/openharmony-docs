# PackingOptionsForSequence

描述动图编码参数的选项。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## delayTimeList

```TypeScript
delayTimeList: Array<number>
```

GIF编码中设定每帧输出图像的延迟时间，取值需大于0。

- 单位：10毫秒（ms）。例如，取值为10时，实际单帧延迟是100毫秒。
- 如果长度小于frameCount，不足的部分将使用delayTimeList中的最后一个值进行填充。

**类型：** Array<number>

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## disposalTypes

```TypeScript
disposalTypes?: Array<number>
```

GIF编码中设定每帧输出图像的帧过渡模式，如果长度小于frameCount，不足的部分将使用disposalTypes中的最后一个值进行填充，可取值如下：

- 0：不需要任何操作。
- 1：保持图形不变。
- 2：恢复背景色。
- 3：恢复到之前的状态。

**类型：** Array<number>

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## frameCount

```TypeScript
frameCount: number
```

GIF编码中指定的帧数。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## loopCount

```TypeScript
loopCount?: number
```

表示在GIF编码中输出图片循环播放次数，取值范围为[0，65535]。

0表示无限循环；若无此字段，则表示不循环播放。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

