# info

## 导入模块

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

<a id="info"></a>
## info

```TypeScript
function info(domain: number, tag: string, format: string, ...args: any[]): void
```

打印INFO级别的日志。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hilog-function info(domain: number, tag: string, format: string, ...args: any[]): void--><!--Device-hilog-function info(domain: number, tag: string, format: string, ...args: any[]): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domain | number | 是 | 日志对应的领域标识，范围是0x0~0xFFFF，超出范围则日志无法打印。<br/>建议开发者在应用内根据需要自定义划分。 |
| tag | string | 是 | 指定日志标识，可以为任意字符串，建议用于标识调用所在的类或者业务行为。tag长度最多为31字节，超出后会截断，不建议使用中文字符，可能出现乱码或者对齐问题。 |
| format | string | 是 | 格式字符串，用于日志的格式化输出。格式字符串中可以设置多个参数，参数需要包含参数类型、隐私标识。<br/>隐私标识分为{public}和{private}，缺省为{private}。标识{public}的内容明文输出，标识{private}的内容以<private>过滤回显。 |
| args | any[] | 是 | 与格式字符串format对应的可变长度参数列表。参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**示例：**

输出一条INFO信息，格式字符串为。其中变参为明文显示的字符串；为隐私的整型数。

```TypeScript
hilog.info(0x0001, "testTag", "%{public}s World %{private}d", "hello", 3);

```

字符串填入，整型数填入，输出日志：

```TypeScript
08-05 12:21:47.579  2695-2703  A00001/testTag  com.example.hilogDemo  I     hello World <private>

```

