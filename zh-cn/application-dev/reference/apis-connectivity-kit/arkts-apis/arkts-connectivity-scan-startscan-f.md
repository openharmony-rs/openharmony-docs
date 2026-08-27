# startScan

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## startScan

```TypeScript
function startScan(filters: ScanFilters[] | null, options?: ScanOptions): Promise<void>
```

发起星闪扫描。使用Promise异步回调。需先调用[scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md)订阅扫描结果回调，本接口发起扫描后，扫描到的设备信息通过 [scan.onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md)回调上报。扫描完成后可调用[scan.stopScan](arkts-connectivity-scan-stopscan-f.md)停止扫描。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filters | [ScanFilters](arkts-connectivity-scan-scanfilters-i.md)[] \| null | 是 | 扫描星闪广播的过滤条件集合，符合过滤条件的设备会被上报。若不使能过滤器则传入null。 若该参数设置为null，将扫描所有可发现的周边星闪设备，但是不建议使用此方式，可能扫描到非预期设备，并增加功耗。 |
| options | [ScanOptions](arkts-connectivity-scan-scanoptions-i.md) | 否 | 表示扫描选项。默认为低功耗模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-整数超出范围) | Integer out of range. |
| [36100041](../errorcode-nearlink-service.md#36100041-无效地址) | Invalid address. |
| [36100042](../errorcode-nearlink-service.md#36100042-数组为空) | Empty array. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
