# startScan

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

<a id="startscan"></a>
## startScan

```TypeScript
function startScan(filters: ScanFilters[] | null, options?: ScanOptions): Promise<void>
```

开始使用过滤器扫描指定的NearLink设备。如果不想使用过滤器，可以将过滤器参数设置为{@code null}。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-scan-function startScan(filters: ScanFilters[] | null, options?: ScanOptions): Promise<void>--><!--Device-scan-function startScan(filters: ScanFilters[] | null, options?: ScanOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filters | ScanFilters[] \| null | 是 | 过滤器列表，必选。如果不需要使用filter，可以设置为{@code null}。如果要使用过滤器，至少要设置一个过滤器。 |
| options | [ScanOptions](arkts-connectivity-scan-scanoptions-i.md) | 否 | 扫描的参数。默认为低功率模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100040](../errorcode-nearlink.md#36100040-整数超出范围) | Integer out of range. |
| [36100041](../errorcode-nearlink.md#36100041-无效地址) | Invalid address. |
| [36100042](../errorcode-nearlink.md#36100042-数组为空) | Empty array. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

