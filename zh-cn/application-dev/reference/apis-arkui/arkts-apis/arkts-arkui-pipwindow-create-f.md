# create

## 导入模块

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## create

```TypeScript
function create(config: PiPConfiguration): Promise<PiPController>
```

创建画中画控制器，使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindow-function create(config: PiPConfiguration): Promise<PiPController>--><!--Device-PiPWindow-function create(config: PiPConfiguration): Promise<PiPController>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [PiPConfiguration](arkts-arkui-pipwindow-pipconfiguration-i.md) | 是 | 创建画中画控制器的参数。该参数不能为空，并且构造该参数的context和componentController不能为空。构造该参数时，如果指定了templateType，需保证templateType是[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md)类型；如果指定了controlGroups，需保证controlGroups与templateType匹配，详见[PiPControlGroup](arkts-arkui-pipwindow-pipcontrolgroup-t.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PiPController> | Promise对象。返回当前创建的画中画控制器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { BuilderNode, FrameNode, NodeController, UIContext } from '@kit.ArkUI';

class Params {
  text: string = '';
  constructor(text: string) {
    this.text = text;
  }
}

// 开发者可以通过@Builder装饰器实现布局构建
@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(20)
      .fontColor(Color.Red)
  }
  .width('100%') // 宽度方向充满画中画窗口
  .height('100%') // 高度方向充满画中画窗口
}

// 开发者可通过继承NodeController实现自定义UI控制器
class TextNodeController extends NodeController {
  private message: string;
  private textNode: BuilderNode<[Params]> | null = null;
  constructor(message: string) {
    super();
    this.message = message;
  }

  // 通过BuilderNode加载自定义布局
  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode(context);
    this.textNode.build(wrapBuilder<[Params]>(buildText), new Params(this.message));
    return this.textNode.getFrameNode();
  }

  // 开发者可自定义该方法实现布局更新
  update(message: string) {
    console.info(`update message: ${message}`);
    if (this.textNode !== null) {
      this.textNode.update(new Params(message));
    }
  }
}

@Entry
@Component
struct Index {
    private message: string = 'createPiP';
    private pipController: PiPWindow.PiPController | undefined = undefined;
    private mXComponentController: XComponentController = new XComponentController(); // 开发者应使用该mXComponentController初始化XComponent: XComponent( {id: 'video', type: 'surface', controller: mXComponentController} )，保证XComponent的内容可以被迁移到画中画窗口。
    private nodeController: TextNodeController = new TextNodeController('this is custom UI');
    private navId: string = "page_1"; // 假设当前页面的导航id为page_1，详见PiPConfiguration定义，具体导航名称由开发者自行定义。
    private contentWidth: number = 800; // 假设当前内容宽度800px。
    private contentHeight: number = 600; // 假设当前内容高度600px。
    private pageId: number = this.getUniqueId(); // 获取当前页面Id。
    private para: Record<string, number> = { 'PropA': 47 };
    private localStorage: LocalStorage = new LocalStorage(this.para);
    private res: boolean = this.localStorage.setOrCreate('PropB', 121);
    private defaultWindowSizeType: number = 1; // 指定画中画第一次拉起窗口为小窗口。
    private cornerAdsorptionEnabled: boolean = true;
    private config: PiPWindow.PiPConfiguration = {
        context: this.getUIContext().getHostContext() as Context,
        componentController: this.mXComponentController,
        navigationId: this.navId,
        handleId: this.pageId,
        templateType: PiPWindow.PiPTemplateType.VIDEO_PLAY,
        contentWidth: this.contentWidth,
        contentHeight: this.contentHeight,
        controlGroups: [PiPWindow.VideoPlayControlGroup.VIDEO_PREVIOUS_NEXT],
        customUIController: this.nodeController, // 可选，如果需要在画中画显示内容上方展示自定义UI，可设置该参数。
        localStorage: this.localStorage, // 可选，如果需要跟踪主窗实例，可设置此参数。
        defaultWindowSizeType: this.defaultWindowSizeType, // 可选，如果需要配置默认启动窗口档位，可设置此参数。
        cornerAdsorptionEnabled: this.cornerAdsorptionEnabled, // 可选，默认为true，如果不需要画中画窗口四角吸附，可设置此参数为false。
    };

    createPiP() {
        let promise: Promise<PiPWindow.PiPController> = PiPWindow.create(this.config);  // 创建画中画控制器
        promise.then((data: PiPWindow.PiPController) => {
            this.pipController = data;
            console.info(`Succeeded in creating pip controller. Data:${data}`);
        }).catch((err: BusinessError) => {
            console.error(`Failed to create pip controller. Cause:${err.code}, message:${err.message}`);
        });
    }

    // 仅用于功能测试，实际开发过程中开发者按功能需求设计组件
    build() {
        RelativeContainer() {
            Button(this.message)
                .onClick(() => {
                    this.createPiP();
                })
        }
    }
}

```


## create

```TypeScript
function create(config: PiPConfiguration, contentNode: typeNode.XComponent): Promise<PiPController>
```

创建画中画控制器，使用typeNode为画中画添加自定义UI节点。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindow-function create(config: PiPConfiguration, contentNode: typeNode.XComponent): Promise<PiPController>--><!--Device-PiPWindow-function create(config: PiPConfiguration, contentNode: typeNode.XComponent): Promise<PiPController>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [PiPConfiguration](arkts-arkui-pipwindow-pipconfiguration-i.md) | 是 | 创建画中画控制器的参数。该参数不能为空，并且构造该参数的context不能为空。构造该参数时，如果指定了templateType，需保证templateType是[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md)类型；如果指定了controlGroups，需保证controlGroups与templateType匹配，详见[PiPControlGroup](arkts-arkui-pipwindow-pipcontrolgroup-t.md)。 |
| contentNode | typeNode.XComponent | 是 | 用于渲染画中画窗口中的内容。该参数不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PiPController> | Promise对象。返回当前创建的画中画控制器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { PiPWindow, typeNode, UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
    private message = 'createPiP'
    private pipController: PiPWindow.PiPController | undefined = undefined;
    private xComponentController: XComponentController = new XComponentController();
    private context: UIContext | undefined = this.getUIContext(); // 可传入UIContext或在布局中通过this.getUIContext()为context赋有效值
    private contentWidth: number = 800; // 假设当前内容宽度800px。
    private contentHeight: number = 600; // 假设当前内容高度600px。
    private config: PiPWindow.PiPConfiguration = {
        context: this.getUIContext().getHostContext() as Context,
        componentController: this.xComponentController,
        templateType: PiPWindow.PiPTemplateType.VIDEO_PLAY,
        contentWidth: this.contentWidth,
        contentHeight: this.contentHeight,
    };
    private options: XComponentOptions = {
        type: XComponentType.SURFACE,
        controller: this.xComponentController
    }
    private xComponent = typeNode.createNode(this.context, 'XComponent', this.options); // 创建XComponent节点用于渲染画中画内容

    createPiP() {
        let promise: Promise<PiPWindow.PiPController> = PiPWindow.create(this.config, this.xComponent); // 使用typeNode创建画中画控制器
        promise.then((data: PiPWindow.PiPController) => {
            this.pipController = data;
            console.info(`Succeeded in creating pip controller. Data:${data}`);
        }).catch((err: BusinessError) => {
            console.error(`Failed to create pip controller. Cause:${err.code}, message:${err.message}`);
        });
    }

    // 仅用于功能测试，实际开发过程中开发者按功能需求设计组件
    build() {
        RelativeContainer() {
            Button(this.message)
                .onClick(() => {
                    this.createPiP();
                })
        }
    }
}

```

