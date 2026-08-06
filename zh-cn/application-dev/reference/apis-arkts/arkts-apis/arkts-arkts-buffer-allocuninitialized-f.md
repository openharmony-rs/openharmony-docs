# allocUninitialized

## allocUninitialized

```TypeScript
function allocUninitialized(size: int): Buffer
```

创建指定大小未初始化的Buffer对象。内存不从缓冲池分配，适用于需要创建较大Buffer或希望精确控制内存分配的场景，如一次性分配较大内存区域（避免缓冲池可能导致的内存碎片累积和缓存性能损耗）。 创建的Buffer的内容未知，需要使用[fill]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_函数来初始化Buffer对象。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function allocUninitialized(size: int): Buffer--><!--Device-buffer-function allocUninitialized(size: int): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的Buffer对象长度，单位：字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 未初始化的Buffer实例。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.allocUninitialized(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```

ArkTS-Sta示例：

```TypeScript
import { buffer } from '@kit.ArkTS';

let buf = buffer.allocUninitialized(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```

