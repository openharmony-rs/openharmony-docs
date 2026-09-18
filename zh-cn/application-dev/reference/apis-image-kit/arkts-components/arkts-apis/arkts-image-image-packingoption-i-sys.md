# PackingOption

表示图片编码选项。

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## c2paDataSize

```TypeScript
c2paDataSize?: number
```

编码时为C2PA数据预留的空间大小，单位为字节。默认值为0，表示不添加预留空间。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**系统接口：** 此接口为系统接口。
