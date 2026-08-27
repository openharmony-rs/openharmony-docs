# isNfcOpen

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## isNfcOpen

```TypeScript
function isNfcOpen(): boolean
```

查询NFC是否打开。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: NFC是打开的， false: NFC是关闭的。 |
