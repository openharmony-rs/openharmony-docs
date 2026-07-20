# alloc

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

<a id="alloc"></a>
## alloc

```TypeScript
function alloc(size: number, fill?: string | Buffer | number | number | number, encoding?: BufferEncoding): Buffer
```

创建指定字节长度的Buffer对象并初始化。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function alloc(size: int, fill?: string | Buffer | int | double | long, encoding?: BufferEncoding): Buffer--><!--Device-buffer-function alloc(size: int, fill?: string | Buffer | int | double | long, encoding?: BufferEncoding): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 指定的Buffer对象长度，单位：字节。 |
| fill | string \| Buffer \| number \| number \| number | 否 | 填充至新缓存区的值。默认值：0。<br>**起始版本：** 9 - 10 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 编码格式（当fill为string时，才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回一个Buffer对象。 |

