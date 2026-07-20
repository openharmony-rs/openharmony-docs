# alloc

## 导入模块

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

<a id="alloc"></a>
## alloc

```TypeScript
function alloc(size: number, fill?: string | FastBuffer | number, encoding?: BufferEncoding): FastBuffer
```

创建指定字节长度的FastBuffer对象并初始化。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function alloc(size: number, fill?: string | FastBuffer | number, encoding?: BufferEncoding): FastBuffer--><!--Device-fastbuffer-function alloc(size: number, fill?: string | FastBuffer | number, encoding?: BufferEncoding): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 指定的FastBuffer对象长度，单位：字节。取值范围：0 <= size <= UINT32_MAX。 |
| fill | string \| FastBuffer \| number | 否 | 填充至新缓存区的值，默认值：0。 |
| encoding | [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 否 | 编码格式（当`fill`为string时，才有意义）。默认值：'utf8'。传入无法识别的encoding会抛出TypeError。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | 返回一个FastBuffer对象。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

// 创建长度为5的FastBuffer对象，默认填充0
let buf1 = fastbuffer.alloc(5);
console.info(buf1.toString());
// 输出结果：00000
// 创建长度为5的FastBuffer对象，填充字符'a'
let buf2 = fastbuffer.alloc(5, 'a');
// 创建长度为11的FastBuffer对象，使用base64编码填充
let buf3 = fastbuffer.alloc(11, 'aGVsbG8gd29ybGQ=', 'base64');
console.info(buf2.toString());
// 输出结果：aaaaa
console.info(buf3.toString());
// 输出结果：hello world

```

