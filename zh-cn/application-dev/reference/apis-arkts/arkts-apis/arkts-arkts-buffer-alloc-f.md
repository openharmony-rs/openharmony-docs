# alloc

## 导入模块

```TypeScript
```

## alloc

```TypeScript
function alloc(size: number, fill?: string | Buffer | number | number | number, encoding?: BufferEncoding): Buffer
```

创建指定字节长度的Buffer对象，并使用指定值进行初始化填充（默认填充0）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 指定的Buffer对象长度，单位：字节。取值为正整数，最大值为2^32-1，即4294967295。 |
| fill | string \| Buffer \| number \| number \| number | 否 | 填充至新缓冲区的值。默认值：0。<br>**起始版本：** 9 - 10 |
| encoding | BufferEncoding | 否 | 编码格式（当fill为string时，才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Buffer | 返回一个Buffer对象。 |

**示例**

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf1 = buffer.alloc(5);
console.info(JSON.stringify(buf1)); // {"type":"Buffer","data":[0,0,0,0,0]}

let buf2 = buffer.alloc(5, 'a');
console.info(JSON.stringify(buf2)); // {"type":"Buffer","data":[97,97,97,97,97]}

let buf3 = buffer.alloc(11, 'aGVsbG8gd29ybGQ=', 'base64');
console.info(JSON.stringify(buf3)); // {"type":"Buffer","data":[104,101,108,108,111,32,119,111,114,108,100]}
```
