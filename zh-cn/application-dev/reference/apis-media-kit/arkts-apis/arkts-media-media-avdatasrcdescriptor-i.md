# AVDataSrcDescriptor

定义音频和视频文件的描述符，用于DataSource播放模式。 使用场景：一个应用可以在下载完音频和视频资源之前创建播放实例并开始播放。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## callback

```TypeScript
callback: (buffer: ArrayBuffer, length: number, pos?: number) => number
```

用户实现的回调函数，用来填充数据。 buffer - 缓冲区需要填充。 length - 播放需要获得的流长度。 pos - 播放获取流的起始位置，可选参数。 当fileSize设置为-1时，该参数不会被使用。 返回要填充的数据的长度，返回-1表示已到达流的末尾，返回-2表示遇到了不可恢复的错误。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 |  |
| length | number | 是 |  |
| pos | number | 否 |  |

## fileSize

```TypeScript
fileSize: number
```

文件大小，-1表示文件大小未知，在这种情况下，seek和setSpeed无法执行，loop不能设置，也无法重播。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer
