# allocUninitialized

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## allocUninitialized

```TypeScript
function allocUninitialized(size: number): Buffer
```

创建指定大小未初始化的Buffer对象。内存不从缓冲池分配。创建的Buffer内容未知，需要使用[fill()](arkts-arkts-buffer-buffer-c.md#fill-1)函数来初始化Buffer对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function allocUninitialized(size: int): Buffer--><!--Device-buffer-function allocUninitialized(size: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 指定的Buffer对象长度，单位：字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 未初始化的Buffer实例。 |

**示例：**

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.allocUninitialized(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}

```

