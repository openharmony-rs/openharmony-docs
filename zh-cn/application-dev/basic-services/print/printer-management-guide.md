# 打印机添加管理

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @fang-jinxu-->

## 概述

开发者可通过addPrinter接口将打印机添加到系统中，供后续打印任务使用。该接口支持传入打印机名称、连接地址（URI）、PPD驱动名称和扩展选项等参数，其中打印机名称和连接地址为必填参数。

> **说明：**
>
> 使用addPrinter接口，需声明权限：ohos.permission.PRINTER_DRIVER。

## 接口说明

| 接口名称 | 描述 | 起始API版本 |
| -------- | ------- | ------ |
| [addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise&lt;boolean&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printaddprinter24) | 添加打印机到系统中 | 24 |

## 参数约束

| 参数 | 约束规则 |
| -------- | -------- |
| printerName | 不允许为空，长度不超过124个字符，不允许包含空格、不可见控制字符、`/`、`\`、`?`、`'`、`"`、`#` |
| uri | 不允许为空，长度不超过128个字符，必须为合法的打印机连接地址格式，主机地址须为有效IP地址（如ipp://192.168.1.100:631/ipp/print） |
| ppdName | 为空或"everywhere"时使用自动驱动模式；否则须为系统中已安装的PPD驱动名称 |
| options | 预留扩展字段，当前版本不使用此参数的具体内容，传入空字符串即可 |

> **说明：**
>
> ppdName用于指定打印机的PPD驱动，驱动决定了打印机的功能描述（如支持的纸张尺寸、色彩模式等）。ppdName为空或传入"everywhere"时，打印服务使用IPP Everywhere自动驱动模式，大多数现代网络打印机均支持此模式，无需手动指定驱动。
>
> 若系统中已存在同名打印机，打印服务会自动在名称后追加序号（如"MyPrinter 1"），不会因重名报错。

## 开发步骤

### 前置准备：导入模块与声明权限

1. 在工程entry Module对应的ets目录（./entry/src/main/ets）下新建页面文件。

2. 导入打印模块。

   ```ts
   import { print } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

3. 在module.json5中声明ohos.permission.PRINTER_DRIVER权限。

   ```json
   {
       "module": {
           "requestPermissions": [
               {
                   "name": "ohos.permission.PRINTER_DRIVER"
               }
           ]
       }
   }
   ```

   > **说明：** ohos.permission.PRINTER_DRIVER为system_basic级别权限，通过系统授权（system_grant）方式获取。

### 步骤1：添加打印机（仅传入必填参数）

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

### 步骤2：添加打印机（指定PPD驱动）

当自动驱动模式无法满足需求时（如需要特定纸张尺寸、色彩模式等），可传入ppdName指定PPD驱动：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let ppdName: string = 'everywhere';

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

### 步骤3：添加打印机（传入全部参数）

传入ppdName和options，其中options当前为预留扩展字段，传入空字符串即可：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let ppdName: string = 'everywhere';
let options: string = '';

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

仅传入options（不指定驱动）时，ppdName传undefined：

```ts
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let options: string = '';

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
> - uri须为合法的打印机连接地址，常见格式如下：
>
> | 协议 | 连接地址示例 |
> | -------- | -------- |
> | IPP | ipp://192.168.1.100:631/ipp/print |
> | IPPS（加密） | ipps://192.168.1.100:631/ipp/print |
> | Socket | socket://192.168.1.100:9100 |
> | LPD | lpd://192.168.1.100:515 |

## 完整示例

以下示例展示了添加打印机的典型开发流程：用户输入打印机名称和连接地址后调用addPrinter添加打印机，支持可选的PPD驱动指定。

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
  @State options: string = '';
  @State isLoading: boolean = false;
  @State result: string = '';
  @State showResult: boolean = false;
  @State isSuccess: boolean = false;

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
      const hasOptions = this.options.trim().length > 0;

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

      TextInput({ placeholder: '请输入PPD驱动名称（可选，空则自动适配）', text: this.ppdName })
        .width('100%')
        .onChange((value: string) => { this.ppdName = value; })
        .margin({ bottom: 12 })

      TextInput({ placeholder: '请输入options（预留扩展字段，可选）', text: this.options })
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