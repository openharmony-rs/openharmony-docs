# 应用内添加打印机

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

## 应用内添加打印机简介

本文档介绍应用内添加打印机的开发方法：开发者可在应用中调用addPrinter接口，将打印机直接添加到系统的打印机列表中，后续下发打印任务时可直接选择使用。addPrinter接口支持传入打印机名称、连接地址（URI）、PPD驱动名称和扩展选项，其中打印机名称和连接地址为必填参数。主要面向打印驱动、打印管理软件、三方打印管理软件、云打印等需要管理打印机的场景。

### 基本概念

在进行应用内添加打印机开发前，开发者应了解以下基本概念：

- **打印队列**

  打印服务中打印机对应的逻辑实体，应用将打印任务提交到队列，由队列对应的打印机完成输出。自定义队列即开发者通过addPrinter接口主动创建的打印队列。

- **PPD驱动**

  PPD（PostScript Printer Description）是一种描述打印机能力（如支持的纸张尺寸、色彩模式等）的驱动文件。指定PPD驱动名称时，打印服务使用该驱动描述打印机能力。

- **IPP Everywhere**

  一种自动驱动模式，打印服务通过IPP协议查询打印机能力并自动生成驱动配置，无需手动指定驱动文件，大多数现代网络打印机均支持此模式。

### 接口说明

| 接口名称 | 描述 | 起始API版本 |
| -------- | ------- | ------ |
| [addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise&lt;boolean&gt;](../../reference/apis-basic-services-kit/js-apis-print.md#printaddprinter24) | 在系统中添加打印机，创建自定义队列 | 24 |

### 约束与限制

| 约束项 | 说明 |
| -------- | -------- |
| 模型约束 | 仅支持Stage模型 |
| 权限要求 | ohos.permission.PRINTER_DRIVER（system_basic级别，system_grant授权） |
| 参数约束 | 详见[print.addPrinter](../../reference/apis-basic-services-kit/js-apis-print.md#printaddprinter24)接口参数说明 |
| 连接协议 | 支持IPP、IPPS（加密）、Socket、LPD等常见打印协议。网络协议的URI格式可参考：{协议}://{IP地址}:{端口}/{队列名}，例如：ipp://192.168.1.100:631/ipp/print |

| 协议 | 连接地址示例 |
| -------- | -------- |
| IPP | ipp://192.168.1.100:631/ipp/print |
| IPPS（加密） | ipps://192.168.1.100:631/ipp/print |
| Socket | socket://192.168.1.100:9100 |
| LPD | lpd://192.168.1.100:515/queue |

> **说明：** 
> 网络协议连接地址的格式可参考：{协议}://{IP地址}:{端口}/{队列名}，队列名因协议而异：IPP/IPPS末尾路径为打印机IPP端点，常见取值为/ipp/print，以打印机实际支持为准；Socket无队列名；LPD末尾为打印机实际队列名。
## 应用内添加打印机开发指导

### 开发准备

**环境与工具：**

- 已安装DevEco Studio，并配置支持API 24的SDK（版本配套关系以DevEco Studio官方说明为准）。
- 真机调试可使用hdc工具连接设备。

**设备要求：**

- OpenHarmony真机（API版本24及以上）。
- 目标打印机支持网络打印或USB连接；网络打印机需与设备处于同一局域网，USB打印机需已连接到设备。

**前置操作：**

- 获取目标打印机的连接地址（URI），格式参见[约束与限制](#约束与限制)中的协议表。
- 若需指定PPD驱动（ppdName），确认对应的厂商PPD驱动已安装到设备，并向驱动厂商获取PPD名称（命名格式为“包名_模块名_文件名”）。

### 开发流程

应用内添加打印机的整体开发流程如下表所示：

| 序号 | 阶段 | 关键动作 | 关键点 |
| -------- | -------- | -------- | -------- |
| 1 | 准备 | 导入print模块 | - |
| 2 | 准备 | 声明PRINTER_DRIVER权限 | 不可遗漏 |
| 3 | 选型 | 选择驱动模式：自动驱动或指定PPD驱动 | 指定PPD驱动的前提是PPD驱动已安装到设备 |
| 4 | 开发 | 调用addPrinter创建自定义队列 | 打印机名称、uri为必填参数，约束见[addPrinter](../../reference/apis-basic-services-kit/js-apis-print.md#printaddprinter24)接口参数说明 |
| 5 | 验证 | 真机运行验证 | 部署完整示例到真机运行，确认接口返回true，且新增打印机出现在系统打印机列表中 |

### 步骤1：导入模块

``` TypeScript
import { print, BusinessError } from '@kit.BasicServicesKit';
```

### 步骤2：声明权限

在module.json5中声明ohos.permission.PRINTER_DRIVER权限。

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

### 步骤3：选择驱动模式

创建自定义队列时支持两种驱动模式，建议按以下方式选型：

| 驱动模式 | 传参方式 | 适用场景 |
| -------- | -------- | -------- |
| 自动驱动（IPP Everywhere） | 不传入ppdName | 打印机支持IPP Everywhere（典型为ipp://、ipps://连接地址），且无需特定能力配置 |
| 指定PPD驱动 | 传入厂商PPD驱动名称 | 打印机不支持IPP Everywhere（如连接地址为socket://、lpd://、usb://等格式），或需要特定纸张尺寸、色彩模式等能力配置；前提是PPD驱动已安装到设备 |

> **说明：**
> 自动驱动依赖打印机支持IPP能力查询，普通USB打印机（usb://连接地址）通常不支持自动驱动，需指定PPD驱动名称；打印机是否支持IPP Everywhere以其自身能力为准。

### 步骤4：创建自定义队列

**方式一：仅传入必填参数（自动驱动）**

连接地址为ipp://或ipps://格式的现代网络打印机大多支持IPP Everywhere自动驱动模式，只需传入打印机名称和连接地址即可创建队列：

``` TypeScript
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

**方式二：指定PPD驱动**

当自动驱动模式无法满足需求时（如需要特定纸张尺寸、色彩模式等），可传入ppdName指定PPD驱动。ppdName为设备安装厂商驱动后生成的PPD文件名称，命名格式为“包名_模块名_文件名”，具体名称需向驱动厂商获取：

``` TypeScript
let printerName: string = 'MyPrinter';
let uri: string = 'ipp://192.168.1.100:631/ipp/print';
let ppdName: string = 'ppdName';

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

**方式三：传入全部参数**

传入ppdName和options，其中options当前为预留扩展字段，传入空字符串即可：

``` TypeScript
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

``` TypeScript
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

### 完整示例

以下示例展示了应用内添加打印机的完整开发流程：用户输入打印机名称和连接地址（可选填PPD驱动名称）后调用addPrinter创建自定义队列，并根据接口返回值与错误码（如201、13100003）展示结果及排查提示。示例仅添加打印机，不执行打印。在已完成步骤2权限声明的工程中，将entry模块页面目录（./entry/src/main/ets/pages）下的Index.ets替换为以下代码。页面文本使用$r资源引用，中英文资源定义在同源工程entry/src/main/resources目录（base、zh_CN、en_US）的element/string.json中：

<!-- @[add_printer_page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/AddPrinterInApp/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { print, BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State printerName: string = 'DemoPrinter';
  @State uri: string = '';
  @State ppdName: string = '';
  @State isAdding: boolean = false;
  @State resultTitle: Resource = $r('app.string.result_wait_title');
  @State resultDetail: Resource = $r('app.string.result_wait_detail');

  private async addPrinter(): Promise<void> {
    if (this.isAdding) {
      return;
    }

    const name = this.printerName.trim();
    const uri = this.uri.trim();
    const ppd = this.ppdName.trim();
    if (name.length === 0 || uri.length === 0) {
      this.resultTitle = $r('app.string.result_incomplete_title');
      this.resultDetail = name.length === 0
        ? $r('app.string.result_name_empty_detail')
        : $r('app.string.result_uri_empty_detail');
      return;
    }

    this.isAdding = true;
    this.resultTitle = $r('app.string.adding');
    this.resultDetail = $r('app.string.result_adding_detail');
    try {
      const added = ppd.length === 0
        ? await print.addPrinter(name, uri)
        : await print.addPrinter(name, uri, ppd);
      this.resultTitle = added ? $r('app.string.result_success_title') : $r('app.string.result_fail_title');
      this.resultDetail = added
        ? $r('app.string.result_success_detail', name)
        : $r('app.string.result_fail_detail');
    } catch (cause) {
      const error = cause as BusinessError;
      this.resultTitle = $r('app.string.result_fail_title');
      if (typeof cause === 'number') {
        this.resultDetail = $r('app.string.error_detail_code_only', String(cause));
      } else {
        const code = typeof error.code === 'number' ? String(error.code) : '';
        const message = error.message || String(cause);
        if (code === '201') {
          this.resultDetail = $r('app.string.error_detail_201', message);
        } else if (code === '13100003') {
          this.resultDetail = $r('app.string.error_detail_13100003', message);
        } else if (code === '') {
          this.resultDetail = $r('app.string.error_detail_unknown_code', message);
        } else {
          this.resultDetail = $r('app.string.error_detail', code, message);
        }
      }
    } finally {
      this.isAdding = false;
    }
  }

  build() {
    Scroll() {
      Column({ space: 16 }) {
        Text($r('app.string.page_title'))
          .fontSize(28)
          .fontWeight(FontWeight.Bold)
        Text('addPrinter · API 24+')
          .fontSize(14)

        Text($r('app.string.printer_name_label'))
          .fontSize(16)
        TextInput({ text: this.printerName, placeholder: 'DemoPrinter' })
          .id('printerNameInput')
          .accessibilityText($r('app.string.printer_name_a11y'))
          .enabled(!this.isAdding)
          .onChange((value: string) => {
            this.printerName = value;
          })

        Text($r('app.string.printer_uri_label'))
          .fontSize(16)
        TextInput({ text: this.uri, placeholder: $r('app.string.printer_uri_placeholder') })
          .id('printerUriInput')
          .accessibilityText($r('app.string.printer_uri_a11y'))
          .enabled(!this.isAdding)
          .onChange((value: string) => {
            this.uri = value;
          })
        Text($r('app.string.printer_uri_hint'))
          .fontSize(14)

        Text($r('app.string.ppd_name_label'))
          .fontSize(16)
        TextInput({ text: this.ppdName, placeholder: $r('app.string.ppd_placeholder') })
          .id('ppdNameInput')
          .accessibilityText($r('app.string.ppd_name_a11y'))
          .enabled(!this.isAdding)
          .onChange((value: string) => {
            this.ppdName = value;
          })
        Text($r('app.string.ppd_hint'))
          .fontSize(14)

        Button(this.isAdding ? $r('app.string.adding') : $r('app.string.button_add'))
          .id('addPrinterButton')
          .width('100%')
          .enabled(!this.isAdding)
          .onClick(() => {
            this.addPrinter();
          })

        Column({ space: 8 }) {
          Text(this.resultTitle)
            .id('resultTitle')
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          Text(this.resultDetail)
            .id('resultDetail')
            .fontSize(16)
            .copyOption(CopyOptions.InApp)
        }
        .alignItems(HorizontalAlign.Start)
        .width('100%')
        .padding({ top: 12, bottom: 12 })

        Text($r('app.string.footer_note'))
          .fontSize(14)
      }
      .alignItems(HorizontalAlign.Start)
      .width('100%')
      .constraintSize({ maxWidth: 680 })
      .padding(24)
    }
    .height('100%')
    .width('100%')
  }
}
```

## 相关文档

- [@ohos.print (打印)](../../reference/apis-basic-services-kit/js-apis-print.md)
- [打印服务错误码](../../reference/apis-basic-services-kit/errorcode-print.md)
- [通用错误码](../../reference/errorcode-universal.md)
