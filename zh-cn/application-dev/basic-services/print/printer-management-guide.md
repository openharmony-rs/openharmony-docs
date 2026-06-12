# 打印机添加管理

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @fang-jinxu-->

## 概述

开发者可通过打印框架接口将打印机添加到系统中，供后续打印任务使用。主要提供以下两种添加方式：

- **直接添加**：已知打印机的名称和连接地址（URI）时，通过[addPrinter](#步骤2添加打印机)接口直接添加，适用于大多数网络打印机场景。
- **发现添加**：需要将自定义打印机信息展示在系统的打印机发现界面中时，通过addPrinterToDiscovery接口上报打印机信息，适用于[打印扩展能力](printExtensionAbilityGuide.md)的开发场景。

> **说明：**
>
> 使用addPrinter接口，需声明权限：ohos.permission.MANAGE_PRINT_JOB或ohos.permission.PRINTER_DRIVER。
>
> 使用打印机发现、查询、监听等接口，需声明权限：ohos.permission.PRINT。

## 接口说明

| 接口名称 | 描述 | 起始API版本 |
| -------- | ------- | ------ |
| [addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise&lt;boolean&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printaddprinter24) | 添加打印机到系统中 | 24 |
| [queryAllPrinterPpds(): Promise&lt;Array&lt;PpdInfo&gt;&gt;](../../reference/apis-basic-services-kit/js-apis-print-sys.md) | 查询系统中所有PPD驱动信息（系统接口） | 24 |

以下为打印机添加管理中可能用到的其他接口，开发者可按需参考API文档使用：

| 接口名称 | 描述 | 起始API版本 |
| -------- | ------- | ------ |
| [addPrinterToDiscovery(printerInformation: PrinterInformation): Promise&lt;void&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printaddprintertodiscovery14) | 将打印机信息添加到发现列表 | 14 |
| [updatePrinterInDiscovery(printerInformation: PrinterInformation): Promise&lt;void&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printupdateprinterindiscovery14) | 更新发现列表中的打印机信息 | 14 |
| [removePrinterFromDiscovery(printerId: string): Promise&lt;void&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printremoveprinterfromdiscovery14) | 从发现列表中移除打印机 | 14 |
| [onPrinterChange(callback: printerChangeCallback): void](../../reference/apis-basic-services-kit/js-apis-print.md#printonprinterchange14) | 监听打印机列表变化事件 | 14 |
| [getPrinterInformationById(printerId: string): Promise&lt;PrinterInformation&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printgetprinterinformationbyid14) | 根据打印机ID查询打印机信息 | 14 |
| [updatePrinterInformation(printerInformation: PrinterInformation): Promise&lt;void&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printupdateprinterinformation24) | 更新打印机的属性信息 | 24 |

## 参数约束与错误码

### addPrinter参数约束

| 参数 | 约束规则 | 违反时错误码 |
| -------- | -------- | -------- |
| printerName | 长度不超过124个字符，不允许为空 | 401（参数错误） |
| printerName | 不允许包含以下字符：空格、不可见控制字符、`/`、`\`、`?`、`'`、`"`、`#` | 401（参数错误） |
| uri | 长度不超过128个字符，不允许为空 | 401（参数错误） |
| uri | 必须为合法的打印机连接地址格式（如ipp://192.168.1.100:631/ipp/print），主机地址须为有效IP | 13100005（无效的打印机） |
| ppdName | 为空或"everywhere"时使用自动驱动模式；否则须为系统中已安装的PPD驱动名称，可通过queryAllPrinterPpds查询获取 | 401（参数错误） |
| options | 须为合法的JSON字符串 | 401（参数错误） |

> **说明：**
>
> 若系统中已存在同名打印机，打印服务会自动在名称后追加序号（如"MyPrinter 1"），不会因重名报错。

### addPrinterToDiscovery参数约束

传入的PrinterInformation对象须满足以下约束：

| 参数 | 约束规则 | 违反时错误码 |
| -------- | -------- | -------- |
| printerId | 必填，不允许为空 | 401（参数错误） |
| printerName | 必填，不允许为空 | 401（参数错误） |
| printerStatus | 必填，须为合法的[PrinterStatus](../../reference/apis-basic-services-kit/js-apis-print.md#printerstatus14)枚举值 | 401（参数错误） |

### 错误码汇总

以下为打印机添加管理接口可能返回的错误码，完整说明请参考[打印服务错误码](../../reference/apis-basic-services-kit/errorcode-print.md)及[通用错误码](../../reference/apis-basic-services-kit/errorcode-universal.md)。

| 错误码ID | 错误信息 | 触发场景 |
| -------- | -------- | -------- |
| 201 | Permission denied. | 未声明或未获取所需权限 |
| 202 | Not system app. | 非系统应用调用了系统接口（如queryAllPrinterPpds） |
| 401 | Parameter error. | 参数类型错误、必填参数缺失、参数值不符合约束 |
| 13100001 | Generic failure. | 打印服务内部异常 |
| 13100002 | RPC failure. | 打印服务通信异常 |
| 13100003 | Print service failure. | 打印服务异常或打印机连接失败 |
| 13100005 | Invalid printer. | 打印机连接地址不合法、打印机不存在 |

## 开发步骤

### 前置准备：导入模块与声明权限

1. 在工程entry Module对应的ets目录（./entry/src/main/ets）下新建页面文件。

2. 导入打印模块。

   ```ts
   import { print } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

3. 在module.json5中声明所需权限。

   使用addPrinter时需声明ohos.permission.MANAGE_PRINT_JOB或ohos.permission.PRINTER_DRIVER权限：

   ```json
   {
       "module": {
           "requestPermissions": [
               {
                   "name": "ohos.permission.MANAGE_PRINT_JOB"
               }
           ]
       }
   }
   ```

   使用打印机发现、查询、监听等接口时需声明ohos.permission.PRINT权限：

   ```json
   {
       "module": {
           "requestPermissions": [
               {
                   "name": "ohos.permission.PRINT"
               }
           ]
       }
   }
   ```

   > **说明：** ohos.permission.PRINTER_DRIVER为system_basic级别权限（system_grant）；ohos.permission.MANAGE_PRINT_JOB和ohos.permission.PRINT为normal级别权限（user_grant）。

### 步骤1：查询PPD驱动列表

如需指定PPD驱动（步骤2中传入ppdName参数），可先通过queryAllPrinterPpds查询系统中可用的PPD驱动名称列表，从中选取与目标打印机匹配的驱动。

> **说明：** queryAllPrinterPpds为系统接口，仅系统应用可调用。如果不需要指定PPD驱动，可跳过此步骤，addPrinter会自动适配驱动。

```ts
print.queryAllPrinterPpds().then((ppdList: print.PpdInfo[]) => {
  for (let i = 0; i < ppdList.length; i++) {
    console.info('PPD名称: ' + ppdList[i].ppdName + ', 厂商: ' + ppdList[i].manufacturer);
  }
}).catch((error: BusinessError) => {
  console.error('queryAllPrinterPpds error : ' + JSON.stringify(error));
});
```

返回的PpdInfo包含以下字段：
- **ppdName**：PPD驱动的名称，即addPrinter中ppdName参数应传入的值。
- **manufacturer**：打印机厂商名称，可用于筛选与目标打印机匹配的驱动。
- **nickName**：驱动的显示别名。

### 步骤2：添加打印机

通过addPrinter接口将打印机添加到系统中。printerName和uri为必填参数，ppdName和options为可选参数。

#### 仅传入必填参数

大多数现代网络打印机支持IPP Everywhere自动驱动模式，只需传入打印机名称和连接地址即可添加：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';

print.addPrinter(printerName, uri).then((result: boolean) => {
  if (result) {
    console.info('addPrinter success');
  } else {
    console.error('addPrinter failed');
  }
}).catch((error: BusinessError) => {
  console.error('addPrinter error : ' + JSON.stringify(error));
});
```

#### 传入ppdName指定驱动

当自动驱动模式无法满足需求时（如需要特定纸张尺寸、色彩模式等），可从步骤1的查询结果中选取ppdName传入：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let ppdName: string = 'com.epson.printandscan_entry_Epson-L3250_Series-epson-escpr-en.ppd';

print.addPrinter(printerName, uri, ppdName).then((result: boolean) => {
  if (result) {
    console.info('addPrinter success');
  } else {
    console.error('addPrinter failed');
  }
}).catch((error: BusinessError) => {
  console.error('addPrinter error : ' + JSON.stringify(error));
});
```

#### 传入ppdName和options

options为JSON字符串，用于指定打印机的高级配置选项：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let ppdName: string = 'everywhere';
let options: string = '{"device-uri":"ipp://192.168.1.100:631/ipp/print"}';

print.addPrinter(printerName, uri, ppdName, options).then((result: boolean) => {
  if (result) {
    console.info('addPrinter success');
  } else {
    console.error('addPrinter failed');
  }
}).catch((error: BusinessError) => {
  console.error('addPrinter error : ' + JSON.stringify(error));
});
```

#### 仅传入options（不指定驱动）

ppdName传undefined即可跳过驱动指定：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let options: string = '{"device-uri":"ipp://192.168.1.100:631/ipp/print"}';

print.addPrinter(printerName, uri, undefined, options).then((result: boolean) => {
  if (result) {
    console.info('addPrinter success');
  } else {
    console.error('addPrinter failed');
  }
}).catch((error: BusinessError) => {
  console.error('addPrinter error : ' + JSON.stringify(error));
});
```

> **说明：**
>
> - ppdName为空或传入"everywhere"时，打印服务使用IPP Everywhere自动驱动模式，大多数现代网络打印机均支持此模式。
> - uri须为合法的打印机连接地址，常见格式如下：
>
> | 协议 | 连接地址示例 |
> | -------- | -------- |
> | IPP | ipp://192.168.1.100:631/ipp/print |
> | IPPS（加密） | ipps://192.168.1.100:631/ipp/print |
> | Socket | socket://192.168.1.100:9100 |
> | LPD | lpd://192.168.1.100:515 |

## 完整示例

以下示例展示了添加打印机的典型开发流程：页面加载时查询PPD驱动列表，用户输入打印机信息后调用addPrinter添加打印机。

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { promptAction } from '@kit.ArkUI';

@Entry
@Component
struct AddPrinterDemo {
  @State printerName: string = '192.168.4.26';
  @State uri: string = 'ipp://192.168.4.26:631/ipp/print';
  @State ppdName: string = '';
  @State options: string = '{}';
  @State isLoading: boolean = false;
  @State result: string = '';
  @State showResult: boolean = false;
  @State isSuccess: boolean = false;
  @State ppdList: print.PpdInfo[] = [];

  aboutToAppear(): void {
    this.loadPpdList();
  }

  async loadPpdList(): Promise<void> {
    try {
      this.ppdList = await print.queryAllPrinterPpds();
    } catch (error) {
      console.error('queryAllPrinterPpds error : ' + JSON.stringify(error));
    }
  }

  async handleAddPrinter(): Promise<void> {
    if (this.printerName.trim().length === 0) {
      promptAction.showToast({ message: '请输入打印机名称', duration: 2000 });
      return;
    }
    if (this.uri.trim().length === 0) {
      promptAction.showToast({ message: '请输入打印机URI', duration: 2000 });
      return;
    }

    this.isLoading = true;
    this.showResult = false;
    try {
      const hasPpdName = this.ppdName.trim().length > 0;
      const hasOptions = this.options.trim().length > 0 && this.options.trim() !== '{}';

      let result: boolean;
      if (!hasPpdName && !hasOptions) {
        result = await print.addPrinter(this.printerName, this.uri);
      } else if (hasPpdName && !hasOptions) {
        result = await print.addPrinter(this.printerName, this.uri, this.ppdName);
      } else if (!hasPpdName && hasOptions) {
        result = await print.addPrinter(this.printerName, this.uri, undefined, this.options);
      } else {
        result = await print.addPrinter(this.printerName, this.uri, this.ppdName, this.options);
      }

      this.isSuccess = result;
      this.result = result ? '打印机添加成功' : '打印机添加失败';
    } catch (error) {
      this.isSuccess = false;
      this.result = '添加错误: ' + JSON.stringify(error);
    }
    this.isLoading = false;
    this.showResult = true;
  }

  build() {
    Column() {
      TextInput({ placeholder: '请输入打印机名称', text: this.printerName })
        .width('100%')
        .onChange((value: string) => { this.printerName = value; })
        .margin({ bottom: 12 })

      TextInput({ placeholder: '请输入打印机URI', text: this.uri })
        .width('100%')
        .onChange((value: string) => { this.uri = value; })
        .margin({ bottom: 12 })

      TextInput({ placeholder: '请输入PPD名称（可选）', text: this.ppdName })
        .width('100%')
        .onChange((value: string) => { this.ppdName = value; })
        .margin({ bottom: 12 })

      TextInput({ placeholder: '请输入options（JSON格式，可选）', text: this.options })
        .width('100%')
        .onChange((value: string) => { this.options = value; })
        .margin({ bottom: 20 })

      if (this.isLoading) {
        LoadingProgress().width(24).height(24).color('#FFFFFF')
      } else {
        Button('添加打印机')
          .width('100%')
          .onClick(() => { this.handleAddPrinter(); })
      }

      if (this.showResult) {
        Text(this.result)
          .fontSize(16)
          .fontColor(this.isSuccess ? '#4CAF50' : '#F44336')
          .margin({ top: 16 })
      }

      if (this.ppdList.length > 0) {
        Text('可用PPD驱动:')
          .fontSize(16)
          .fontWeight(FontWeight.Medium)
          .margin({ top: 20 })
        List() {
          ForEach(this.ppdList, (item: print.PpdInfo) => {
            ListItem() {
              Text(item.ppdName + ' - ' + item.manufacturer)
                .fontSize(14)
                .padding({ left: 16, right: 16, top: 8, bottom: 8 })
                .onClick(() => { this.ppdName = item.ppdName; })
            }
          })
        }
        .width('100%')
        .height(200)
      }
    }
    .width('100%')
    .padding(20)
  }
}
```

## 相关文档

- [文件打印（C/C++）](native-print-file.md)
- [打印扩展能力](printExtensionAbilityGuide.md)
- [@ohos.print（打印）](../../reference/apis-basic-services-kit/js-apis-print.md)
- [@ohos.print（打印系统接口）](../../reference/apis-basic-services-kit/js-apis-print-sys.md)