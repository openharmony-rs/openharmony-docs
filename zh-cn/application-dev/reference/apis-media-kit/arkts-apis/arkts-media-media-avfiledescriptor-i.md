# AVFileDescriptor

媒体文件描述符。调用者需要确保fd有效，并且偏移量和长度是正确的。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## fd

```TypeScript
fd: number
```

来自文件系统的音频或视频源的文件描述符。调用者负责关闭该文件描述符。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## length

```TypeScript
length?: number
```

读取的数据的字节长度。默认情况下，长度是从偏移量开始文件中剩余的字节数。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## offset

```TypeScript
offset?: number
```

读取的数据在文件中的偏移量，单位字节。默认情况下，偏移量是零。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core
