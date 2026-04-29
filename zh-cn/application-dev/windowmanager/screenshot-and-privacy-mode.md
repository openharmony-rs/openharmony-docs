# 截图与隐私模式

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin qianjiaxing@huawei.com-->
<!--Designer: @nyankomiya wanghaofan@huawei.com-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 场景介绍

截图包含窗口截图、屏幕截图和组件截图。其中窗口截图和屏幕截图都受到[隐私模式](#隐私模式)限制。不同截图能力的范围和适用场景不同：

- 窗口截图以应用窗口为单位，获取当前窗口的可见内容，适用于当前应用页面采集等。

- 屏幕截图以设备屏幕为单位，可获取整屏，指定显示屏和用户框选区域内容，适用于整屏截图、区域截图等场景。

- 组件截图以单个组件为场景，仅获取指定组件的内容，适用于分享卡片生成等场景。

## 隐私模式

设置为隐私模式的窗口（称为隐私窗口），窗口内容将无法被截屏/录屏/投屏，主要用于禁止截屏/录屏/投屏的场景，一般用于带有密码等敏感信息的页面。

隐私窗口用于保护窗口中的敏感内容，避免窗口内容在截图、预览等场景下被非预期获取。对于包含个人信息、支付信息、会话内容或其他敏感数据的窗口，建议按业务需要设置隐私模式。

### 规格表现

- 当未调用相关接口设置隐私模式时，窗口默认不开启隐私模式，可以被截屏或录屏。

- 当隐私窗口处于前台时，此时在投屏、录屏等[虚拟屏](../displaymanager/display-terminology.md)显示场景下，系统会对隐私内容进行保护，隐私窗口显示黑色或隐私窗口所在屏幕显示黑色； 当主窗或子窗为隐私窗口时，退后台在多任务卡片中显示为白色蒙层或模糊蒙层。针对隐私窗口进行截图（屏幕截图和窗口截图）的表现如下：

  - 通过[snapshot()](../reference/apis-arkui/arkts-apis-window-Window.md#snapshot9-1)/[snapshotSync()](../reference/apis-arkui/arkts-apis-window-Window.md#snapshotsync20)接口获取到的窗口截图结果为白屏。

  - 在Phone或Tablet设备上，将不允许用户通过下拉控制中心的截屏按钮或指关节敲击截屏，会提示类似“当前界面涉及隐私，不允许截图”的相关信息。

  - 在2in1设备上，允许用户通过控制中心的截屏按钮进行截屏，但是设置隐私模式的窗口将显示为黑屏，其他窗口正常显示。

- 当业务场景明确需要对隐私窗口进行有效截图时，可以使用[snapshotIgnorePrivacy()](../reference/apis-arkui/arkts-apis-window-Window.md#snapshotignoreprivacy18)接口实现。

- 当业务场景明确需要对隐私窗口进行屏幕录制时，需要先调用[setWindowPrivacyMode(false)](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9-1)接口取消该窗口的隐私模式，以避免无法获取到对应的窗口画面。

### 设置隐私模式

可以使用[setWindowPrivacyMode()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9-1)接口设置窗口是否隐私模式。

对于需要防截屏/录屏/投屏的页面，通常是在进入到该页面时就设置为隐私模式（[setWindowPrivacyMode(true)](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9-1)），当页面隐藏、销毁，或切换到其他非隐私页面时，应该在对应生命周期中取消隐私模式（[setWindowPrivacyMode(false)](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9-1)）。

## 窗口截图

窗口截图主要提供单窗口截图、多窗口截图。通过对应监听能力可以在窗口截图时，接收到截图监听回调。

- 单窗口截图：可通过调用[snapshot()](../reference/apis-arkui/arkts-apis-window-Window.md#snapshot9-1)/[SnapshotSync()](../reference/apis-arkui/arkts-apis-window-Window.md#snapshotsync20)接口对当前窗口进行截图。  

  ```ts
  import { display, window } from '@kit.ArkUI';
  import { common } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { image } from '@kit.ImageKit';
  
  
  const DOMAIN = 0x0000;
  const COMPONENT_ID = 'snapshotTarget';
  
  @Entry
  @Component
  struct Index {
    @State statusText: string = 'Tap a button to run the snapshot sample.';
    @State logText: string = 'ready\n';
    @State imageWidth: number = 0;
    @State imageHeight: number = 0;
    @State previewPixelMap?: image.PixelMap = undefined;
    @State displayIdText: string = '0';
    @State displayInfoText: string = '-';
    @State pickRectText: string = '-';
  
    private currentWindow?: window.Window = undefined;
  
    aboutToAppear(): void {
      void this.initContextInfo();
    }
    // 在页面内保留日志，方便直接观察每个截图接口的调用结果。
    private appendLog(message: string): void {
      const line = `${Date.now()}: ${message}`;
      this.logText += `${line}\n`;
      hilog.info(DOMAIN, 'snapshotSample', line);
    }
  
    // 初始化宿主窗口，并收集可用于 screenshot.capture 的 displayId。
    private async initContextInfo(): Promise<void> {
      try {
        const hostContext = this.getUIContext().getHostContext();
        if (!hostContext) {
          throw new Error('Host context is unavailable.');
        }
        const context = hostContext as common.UIAbilityContext;
        this.currentWindow = await window.getLastWindow(context);
  
        const defaultDisplay = display.getDefaultDisplaySync();
        this.displayIdText = `${defaultDisplay.id}`;
  
        const displays = await display.getAllDisplays();
        this.displayInfoText = displays.map((item) => `${item.id}`).join(', ');
  
        const windowId = this.currentWindow.getWindowProperties().id;
        this.statusText = `windowId=${windowId}, displays=${this.displayInfoText}`;
        this.appendLog(`window initialized, windowId=${windowId}, displayIds=${this.displayInfoText}`);
      } catch (err) {
        this.statusText = `Initialization failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
  
    // 所有截图结果都复用同一个预览区域，便于对比不同接口的输出。
    private async updatePreview(pixelMap: image.PixelMap, source: string): Promise<void> {
      this.previewPixelMap = pixelMap;
      try {
        const imageInfo = pixelMap.getImageInfoSync();
        this.imageWidth = imageInfo.size.width;
        this.imageHeight = imageInfo.size.height;
        this.statusText = `${source} success, size=${this.imageWidth}x${this.imageHeight}`;
      } catch (err) {
        this.imageWidth = 0;
        this.imageHeight = 0;
        this.statusText = `${source} success, but getImageInfoSync failed: ${JSON.stringify(err)}`;
      }
      this.appendLog(this.statusText);
    }
  
    // window.snapshot 系列接口都依赖当前窗口对象，这里统一兜底初始化。
    private async ensureWindow(): Promise<boolean> {
      if (!this.currentWindow) {
        await this.initContextInfo();
      }
      if (!this.currentWindow) {
        this.statusText = 'Current window is unavailable.';
        this.appendLog(this.statusText);
        return false;
      }
      return true;
    }
  
    // 单窗口异步截图
    private async takeWindowSnapshot(): Promise<void> {
      if (!await this.ensureWindow()) {
        return;
      }
      try {
        const pixelMap = await this.currentWindow!.snapshot();
        await this.updatePreview(pixelMap, 'window.snapshot');
      } catch (err) {
        this.statusText = `window.snapshot failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
  
    // 单窗口同步截图
    private takeWindowSnapshotSync(): void {
      if (!this.currentWindow) {
        this.statusText = 'window.snapshotSync failed: current window is unavailable.';
        this.appendLog(this.statusText);
        return;
      }
      try {
        const pixelMap = this.currentWindow.snapshotSync();
        void this.updatePreview(pixelMap, 'window.snapshotSync');
      } catch (err) {
        this.statusText = `window.snapshotSync failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
  
    // 在设备支持的前提下，忽略隐私模式截取当前窗口。
    private async takeWindowSnapshotIgnorePrivacy(): Promise<void> {
      if (!await this.ensureWindow()) {
        return;
      }
      try {
        const pixelMap = await this.currentWindow!.snapshotIgnorePrivacy();
        await this.updatePreview(pixelMap, 'window.snapshotIgnorePrivacy');
      } catch (err) {
        this.statusText = `window.snapshotIgnorePrivacy failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
    build() {
      Scroll() {
        Column({ space: 16 }) {
          Column({ space: 8 }) {
            Text('Snapshot Sample Center')
              .fontSize(26)
              .fontWeight(FontWeight.Bold)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text('Includes window.snapshot, screenshot.pick, screenshot.capture(displayId), and componentSnapshot.')
              .fontSize(14)
              .fontColor('#666666')
              .width('100%')
              .textAlign(TextAlign.Start)
          }
          .width('100%')
  
          Column({ space: 10 }) {
            Text('Window Snapshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Button('window.snapshot')
              .width('100%')
              .onClick(() => {
                void this.takeWindowSnapshot();
              })
  
            Button('window.snapshotSync')
              .width('100%')
              .backgroundColor('#0A7A5A')
              .onClick(() => {
                this.takeWindowSnapshotSync();
              })
  
            Button('window.snapshotIgnorePrivacy')
              .width('100%')
              .backgroundColor('#AD5C00')
              .onClick(() => {
                void this.takeWindowSnapshotIgnorePrivacy();
              })
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#F8F4ED')
          .borderRadius(20)
  
          Column({ space: 10 }) {
            Text('Screen Screenshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(`Available displayIds: ${this.displayInfoText}`)
              .width('100%')
              .fontSize(12)
              .fontColor('#666666')
              .textAlign(TextAlign.Start)
  
            TextInput({ text: this.displayIdText, placeholder: 'Input displayId' })
              .width('100%')
              .onChange((value: string) => {
                this.displayIdText = value;
              })
  
  
            Text(`Last pickRect: ${this.pickRectText}`)
              .width('100%')
              .fontSize(12)
              .fontColor('#666666')
              .textAlign(TextAlign.Start)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#EDF3FB')
          .borderRadius(20)
  
          Column({ space: 10 }) {
            Text('Component Snapshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
  
            Column({ space: 6 }) {
              Text('This card is the component snapshot target.')
                .fontSize(16)
                .fontWeight(FontWeight.Medium)
                .fontColor('#1E3A2F')
  
              Text('ID: snapshotTarget')
                .fontSize(12)
                .fontColor('#4C6A5A')
  
              Text('Use componentSnapshot to capture only this component.')
                .fontSize(13)
                .fontColor('#2E5143')
            }
            .id(COMPONENT_ID)
            .width('100%')
            .padding(16)
            .backgroundColor('#DFF3E7')
            .borderRadius(16)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#FFF2E8')
          .borderRadius(20)
  
          Column({ space: 8 }) {
            Text('Status')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(this.statusText)
              .width('100%')
              .fontSize(14)
              .textAlign(TextAlign.Start)
  
            if (this.previewPixelMap) {
              Text(`Preview size: ${this.imageWidth} x ${this.imageHeight}`)
                .width('100%')
                .fontSize(12)
                .fontColor('#666666')
                .textAlign(TextAlign.Start)
  
              Image(this.previewPixelMap)
                .width('100%')
                .height(360)
                .objectFit(ImageFit.Contain)
                .borderRadius(12)
                .backgroundColor('#F3F3F3')
            }
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#F6F4EE')
          .borderRadius(20)
  
          Column({ space: 8 }) {
            Text('Log')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(this.logText)
              .width('100%')
              .fontSize(12)
              .textAlign(TextAlign.Start)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#EEF3F8')
          .borderRadius(20)
        }
        .width('100%')
        .padding(20)
        .alignItems(HorizontalAlign.Start)
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

- 多窗口截图：可通过调用[getMainWindowSnapshot()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetmainwindowsnapshot21)接口，针对一个或多个主窗（通过windowId指定）进行截图。  

  ```ts
  import { display, window, screenshot } from '@kit.ArkUI';
  import { common } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
  import { image } from '@kit.ImageKit';
  
  const DOMAIN = 0x0000;
  const COMPONENT_ID = 'snapshotTarget';
  
  @Entry
  @Component
  struct Index {
    @State statusText: string = 'Tap a button to run the snapshot sample.';
    @State logText: string = 'ready\n';
    @State imageWidth: number = 0;
    @State imageHeight: number = 0;
    @State previewPixelMap?: image.PixelMap = undefined;
    @State displayIdText: string = '0';
    @State displayInfoText: string = '-';
    @State pickRectText: string = '-';
  
    private currentWindow?: window.Window = undefined;
  
    aboutToAppear(): void {
      void this.initContextInfo();
    }
    // 在页面内保留日志，方便直接观察每个截图接口的调用结果。
    private appendLog(message: string): void {
      const line = `${Date.now()}: ${message}`;
      this.logText += `${line}\n`;
      hilog.info(DOMAIN, 'snapshotSample', line);
    }
  
    // 初始化宿主窗口，并收集可用于 screenshot.capture 的 displayId。
    private async initContextInfo(): Promise<void> {
      try {
        const hostContext = this.getUIContext().getHostContext();
        if (!hostContext) {
          throw new Error('Host context is unavailable.');
        }
        const context = hostContext as common.UIAbilityContext;
        this.currentWindow = await window.getLastWindow(context);
  
        const defaultDisplay = display.getDefaultDisplaySync();
        this.displayIdText = `${defaultDisplay.id}`;
  
        const displays = await display.getAllDisplays();
        this.displayInfoText = displays.map((item) => `${item.id}`).join(', ');
  
        const windowId = this.currentWindow.getWindowProperties().id;
        this.statusText = `windowId=${windowId}, displays=${this.displayInfoText}`;
        this.appendLog(`window initialized, windowId=${windowId}, displayIds=${this.displayInfoText}`);
      } catch (err) {
        this.statusText = `Initialization failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
  
    // 解析页面输入的 displayId
    private parseDisplayId(): number {
      const displayId = Number.parseInt(this.displayIdText, 10);
      if (Number.isNaN(displayId) || displayId < 0) {
        throw new Error(`Invalid displayId: ${this.displayIdText}`);
      }
      return displayId;
    }
  
    // 所有截图结果都复用同一个预览区域，便于对比不同接口的输出。
    private async updatePreview(pixelMap: image.PixelMap, source: string): Promise<void> {
      this.previewPixelMap = pixelMap;
      try {
        const imageInfo = pixelMap.getImageInfoSync();
        this.imageWidth = imageInfo.size.width;
        this.imageHeight = imageInfo.size.height;
        this.statusText = `${source} success, size=${this.imageWidth}x${this.imageHeight}`;
      } catch (err) {
        this.imageWidth = 0;
        this.imageHeight = 0;
        this.statusText = `${source} success, but getImageInfoSync failed: ${JSON.stringify(err)}`;
      }
      this.appendLog(this.statusText);
    }
  
    // window.snapshot 系列接口都依赖当前窗口对象，这里统一兜底初始化。
    private async ensureWindow(): Promise<boolean> {
      if (!this.currentWindow) {
        await this.initContextInfo();
      }
      if (!this.currentWindow) {
        this.statusText = 'Current window is unavailable.';
        this.appendLog(this.statusText);
        return false;
      }
      return true;
    }
  
    // 在运行时申请截图权限。
    private async requestCapturePermission(): Promise<boolean> {
      try {
        const hostContext = this.getUIContext().getHostContext();
        if (!hostContext) {
          this.appendLog('permission request failed: hostContext is unavailable');
          return false;
        }
  
        const context = hostContext as common.UIAbilityContext;
        const atManager = abilityAccessCtrl.createAtManager();
        const result = await atManager.requestPermissionsFromUser(context, [
          'ohos.permission.CUSTOM_SCREEN_CAPTURE' as Permissions
        ]);
  
        this.appendLog(`permission request result=${JSON.stringify(result.authResults)}`);
        return result.authResults.length > 0 && result.authResults[0] === 0;
      } catch (err) {
        this.appendLog(`permission request failed: ${JSON.stringify(err)}`);
        return false;
      }
    }
  
    // 指定displayId截取对应屏幕
    private async captureByDisplayId(): Promise<void> {
      try {
        const granted = await this.requestCapturePermission();
        if (!granted) {
          this.statusText = 'CUSTOM_SCREEN_CAPTURE permission denied or unavailable.';
          this.appendLog(this.statusText);
          return;
        }
  
        const displayId = this.parseDisplayId();
        const pixelMap = await screenshot.capture({ displayId });
        await this.updatePreview(pixelMap, `screenshot.capture(displayId=${displayId})`);
      } catch (err) {
        this.statusText = `screenshot.capture failed: ${JSON.stringify(err)}`;
        this.appendLog(`${this.statusText}. Hint: declare/grant ohos.permission.CUSTOM_SCREEN_CAPTURE first.`);
      }
    }
  
    // 多窗口截图（通过主窗口id调用getMainWindowSnapshot获取主窗口截图）
    private async takeMainWindowSnapshot(): Promise<void> {
      if (!await this.ensureWindow()) {
        return;
      }
  
      const granted = await this.requestCapturePermission();
      if (!granted) {
        this.statusText = 'CUSTOM_SCREEN_CAPTURE permission denied or unavailable.';
        this.appendLog(this.statusText);
        return;
      }
  
      try {
        const windowId = this.currentWindow!.getWindowProperties().id;
        const pixelMap = (await window.getMainWindowSnapshot([windowId], {
          useCache: false
        }))[0];
  
        if (!pixelMap) {
          this.statusText = `getMainWindowSnapshot(${windowId}) returned undefined.`;
          this.appendLog(this.statusText);
          return;
        }
  
        await this.updatePreview(pixelMap, 'window.getMainWindowSnapshot');
      } catch (err) {
        this.statusText = `getMainWindowSnapshot failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
    build() {
      Scroll() {
        Column({ space: 16 }) {
          Column({ space: 8 }) {
            Text('Snapshot Sample Center')
              .fontSize(26)
              .fontWeight(FontWeight.Bold)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text('Includes window.snapshot, window.getMainWindowSnapshot, screenshot.pick, screenshot.capture(displayId), and componentSnapshot.')
              .fontSize(14)
              .fontColor('#666666')
              .width('100%')
              .textAlign(TextAlign.Start)
          }
          .width('100%')
  
          Column({ space: 10 }) {
            Text('Window Snapshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Button('window.getMainWindowSnapshot')
              .width('100%')
              .backgroundColor('#6D4CC2')
              .onClick(() => {
                void this.takeMainWindowSnapshot();
              })
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#F8F4ED')
          .borderRadius(20)
  
          Column({ space: 10 }) {
            Text('Screen Screenshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(`Available displayIds: ${this.displayInfoText}`)
              .width('100%')
              .fontSize(12)
              .fontColor('#666666')
              .textAlign(TextAlign.Start)
  
            TextInput({ text: this.displayIdText, placeholder: 'Input displayId' })
              .width('100%')
              .onChange((value: string) => {
                this.displayIdText = value;
              })
            
            Button('screenshot.capture({ displayId })')
              .width('100%')
              .backgroundColor('#6D4CC2')
              .onClick(() => {
                void this.captureByDisplayId();
              })
  
            Text(`Last pickRect: ${this.pickRectText}`)
              .width('100%')
              .fontSize(12)
              .fontColor('#666666')
              .textAlign(TextAlign.Start)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#EDF3FB')
          .borderRadius(20)
  
          Column({ space: 10 }) {
            Text('Component Snapshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Column({ space: 6 }) {
              Text('This card is the component snapshot target.')
                .fontSize(16)
                .fontWeight(FontWeight.Medium)
                .fontColor('#1E3A2F')
  
              Text('ID: snapshotTarget')
                .fontSize(12)
                .fontColor('#4C6A5A')
  
              Text('Use componentSnapshot to capture only this component.')
                .fontSize(13)
                .fontColor('#2E5143')
            }
            .id(COMPONENT_ID)
            .width('100%')
            .padding(16)
            .backgroundColor('#DFF3E7')
            .borderRadius(16)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#FFF2E8')
          .borderRadius(20)
  
          Column({ space: 8 }) {
            Text('Status')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(this.statusText)
              .width('100%')
              .fontSize(14)
              .textAlign(TextAlign.Start)
  
            if (this.previewPixelMap) {
              Text(`Preview size: ${this.imageWidth} x ${this.imageHeight}`)
                .width('100%')
                .fontSize(12)
                .fontColor('#666666')
                .textAlign(TextAlign.Start)
  
              Image(this.previewPixelMap)
                .width('100%')
                .height(360)
                .objectFit(ImageFit.Contain)
                .borderRadius(12)
                .backgroundColor('#F3F3F3')
            }
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#F6F4EE')
          .borderRadius(20)
  
          Column({ space: 8 }) {
            Text('Log')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(this.logText)
              .width('100%')
              .fontSize(12)
              .textAlign(TextAlign.Start)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#EEF3F8')
          .borderRadius(20)
        }
        .width('100%')
        .padding(20)
        .alignItems(HorizontalAlign.Start)
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

## 屏幕截图

屏幕截图是指对当前屏幕进行截屏。

屏幕截图相关接口的使用及示例如下所示：

- [screenshot.pick()](../reference/apis-arkui/js-apis-screenshot.md#screenshotpick)接口仅支持获取主屏的屏幕截图，允许区域截屏，用户通过手势交互选择屏幕任意区域。

- [screenshot.capture()](../reference/apis-arkui/js-apis-screenshot.md#screenshotcapture14)接口可以通过设置不同的displayId针对不同屏幕进行截图，且只能截取全屏。

- 监听屏幕截图：注册屏幕截图监听后，每当有截屏发生时，都会触发注册的回调函数。

  - [on('screenshot')](../reference/apis-arkui/arkts-apis-window-Window.md#onscreenshot9)接口只能监听截屏动作，无法区分具体的截屏事件类型。对控制中心截屏、hdc命令截屏、整屏截屏接口等生效。

  - [on('screenshotAppEvent')](../reference/apis-arkui/arkts-apis-window-Window.md#onscreenshotappevent20)接口可以监听截屏动作，并能返回触发的截屏事件类型[ScreenshotEventType](../reference/apis-arkui/arkts-apis-window-e.md#screenshoteventtype20)。比如系统截屏成功或中止、滚动截屏开始或结束等。

  - 当不需要再对进行屏幕截图进行监听时，可通过对应off接口（[off('screenshot')](../reference/apis-arkui/arkts-apis-window-Window.md#offscreenshot9)/[off('screenshotAppEvent')](../reference/apis-arkui/arkts-apis-window-Window.md#onscreenshotappevent20)）关闭监听。

- 长截屏/滚动截屏：用于获取超出单屏范围的连续内容，适用于长页面、长列表等完整截取场景。  

  ```ts
  import { display, window, screenshot } from '@kit.ArkUI';
  import { common } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
  import { image } from '@kit.ImageKit';
  
  const DOMAIN = 0x0000;
  const COMPONENT_ID = 'snapshotTarget';
  
  @Entry
  @Component
  struct Index {
    @State statusText: string = 'Tap a button to run the snapshot sample.';
    @State logText: string = 'ready\n';
    @State imageWidth: number = 0;
    @State imageHeight: number = 0;
    @State previewPixelMap?: image.PixelMap = undefined;
    @State displayIdText: string = '0';
    @State displayInfoText: string = '-';
    @State pickRectText: string = '-';
  
    private currentWindow?: window.Window = undefined;
  
    aboutToAppear(): void {
      void this.initContextInfo();
    }
    // 在页面内保留日志，方便直接观察每个截图接口的调用结果。
    private appendLog(message: string): void {
      const line = `${Date.now()}: ${message}`;
      this.logText += `${line}\n`;
      hilog.info(DOMAIN, 'snapshotSample', line);
    }
  
    // 初始化宿主窗口，并收集可用于 screenshot.capture 的 displayId。
    private async initContextInfo(): Promise<void> {
      try {
        const hostContext = this.getUIContext().getHostContext();
        if (!hostContext) {
          throw new Error('Host context is unavailable.');
        }
        const context = hostContext as common.UIAbilityContext;
        this.currentWindow = await window.getLastWindow(context);
  
        const defaultDisplay = display.getDefaultDisplaySync();
        this.displayIdText = `${defaultDisplay.id}`;
  
        const displays = await display.getAllDisplays();
        this.displayInfoText = displays.map((item) => `${item.id}`).join(', ');
  
        const windowId = this.currentWindow.getWindowProperties().id;
        this.statusText = `windowId=${windowId}, displays=${this.displayInfoText}`;
        this.appendLog(`window initialized, windowId=${windowId}, displayIds=${this.displayInfoText}`);
      } catch (err) {
        this.statusText = `Initialization failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
  
    // 解析页面输入的 displayId
    private parseDisplayId(): number {
      const displayId = Number.parseInt(this.displayIdText, 10);
      if (Number.isNaN(displayId) || displayId < 0) {
        throw new Error(`Invalid displayId: ${this.displayIdText}`);
      }
      return displayId;
    }
  
    // 所有截图结果都复用同一个预览区域，便于对比不同接口的输出。
    private async updatePreview(pixelMap: image.PixelMap, source: string): Promise<void> {
      this.previewPixelMap = pixelMap;
      try {
        const imageInfo = pixelMap.getImageInfoSync();
        this.imageWidth = imageInfo.size.width;
        this.imageHeight = imageInfo.size.height;
        this.statusText = `${source} success, size=${this.imageWidth}x${this.imageHeight}`;
      } catch (err) {
        this.imageWidth = 0;
        this.imageHeight = 0;
        this.statusText = `${source} success, but getImageInfoSync failed: ${JSON.stringify(err)}`;
      }
      this.appendLog(this.statusText);
    }
  
  
    // 通过手势交互选择屏幕任意区域
    private async pickScreenArea(): Promise<void> {
      try {
        const result = await screenshot.pick();
        this.pickRectText = `left=${result.pickRect.left}, top=${result.pickRect.top}, width=${result.pickRect.width}, height=${result.pickRect.height}`;
        this.appendLog(`screenshot.pick rect=${this.pickRectText}`);
        await this.updatePreview(result.pixelMap, 'screenshot.pick');
      } catch (err) {
        this.statusText = `screenshot.pick failed: ${JSON.stringify(err)}`;
        this.appendLog(this.statusText);
      }
    }
  
    // 在运行时申请截图权限。
    private async requestCapturePermission(): Promise<boolean> {
      try {
        const hostContext = this.getUIContext().getHostContext();
        if (!hostContext) {
          this.appendLog('permission request failed: hostContext is unavailable');
          return false;
        }
  
        const context = hostContext as common.UIAbilityContext;
        const atManager = abilityAccessCtrl.createAtManager();
        const result = await atManager.requestPermissionsFromUser(context, [
          'ohos.permission.CUSTOM_SCREEN_CAPTURE' as Permissions
        ]);
  
        this.appendLog(`permission request result=${JSON.stringify(result.authResults)}`);
        return result.authResults.length > 0 && result.authResults[0] === 0;
      } catch (err) {
        this.appendLog(`permission request failed: ${JSON.stringify(err)}`);
        return false;
      }
    }
  
    // 指定displayId截取对应屏幕
    private async captureByDisplayId(): Promise<void> {
      try {
        const granted = await this.requestCapturePermission();
        if (!granted) {
          this.statusText = 'CUSTOM_SCREEN_CAPTURE permission denied or unavailable.';
          this.appendLog(this.statusText);
          return;
        }
  
        const displayId = this.parseDisplayId();
        const pixelMap = await screenshot.capture({ displayId });
        await this.updatePreview(pixelMap, `screenshot.capture(displayId=${displayId})`);
      } catch (err) {
        this.statusText = `screenshot.capture failed: ${JSON.stringify(err)}`;
        this.appendLog(`${this.statusText}. Hint: declare/grant ohos.permission.CUSTOM_SCREEN_CAPTURE first.`);
      }
    }
    build() {
      Scroll() {
        Column({ space: 16 }) {
          Column({ space: 8 }) {
            Text('Snapshot Sample Center')
              .fontSize(26)
              .fontWeight(FontWeight.Bold)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text('Includes window.snapshot, window.getMainWindowSnapshot, screenshot.pick, screenshot.capture(displayId), and componentSnapshot.')
              .fontSize(14)
              .fontColor('#666666')
              .width('100%')
              .textAlign(TextAlign.Start)
          }
          .width('100%')
  
          Column({ space: 10 }) {
            Text('Window Snapshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
          .width('100%')
          .padding(16)
          .backgroundColor('#F8F4ED')
          .borderRadius(20)
  
          Column({ space: 10 }) {
            Text('Screen Screenshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(`Available displayIds: ${this.displayInfoText}`)
              .width('100%')
              .fontSize(12)
              .fontColor('#666666')
              .textAlign(TextAlign.Start)
  
            TextInput({ text: this.displayIdText, placeholder: 'Input displayId' })
              .width('100%')
              .onChange((value: string) => {
                this.displayIdText = value;
              })
  
            Button('screenshot.pick()')
              .width('100%')
              .backgroundColor('#3F6FB6')
              .onClick(() => {
                void this.pickScreenArea();
              })
  
            Button('screenshot.capture({ displayId })')
              .width('100%')
              .backgroundColor('#6D4CC2')
              .onClick(() => {
                void this.captureByDisplayId();
              })
  
            Text(`Last pickRect: ${this.pickRectText}`)
              .width('100%')
              .fontSize(12)
              .fontColor('#666666')
              .textAlign(TextAlign.Start)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#EDF3FB')
          .borderRadius(20)
  
          Column({ space: 10 }) {
            Text('Component Snapshot')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Column({ space: 6 }) {
              Text('This card is the component snapshot target.')
                .fontSize(16)
                .fontWeight(FontWeight.Medium)
                .fontColor('#1E3A2F')
  
              Text('ID: snapshotTarget')
                .fontSize(12)
                .fontColor('#4C6A5A')
  
              Text('Use componentSnapshot to capture only this component.')
                .fontSize(13)
                .fontColor('#2E5143')
            }
            .id(COMPONENT_ID)
            .width('100%')
            .padding(16)
            .backgroundColor('#DFF3E7')
            .borderRadius(16)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#FFF2E8')
          .borderRadius(20)
  
          Column({ space: 8 }) {
            Text('Status')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(this.statusText)
              .width('100%')
              .fontSize(14)
              .textAlign(TextAlign.Start)
  
            if (this.previewPixelMap) {
              Text(`Preview size: ${this.imageWidth} x ${this.imageHeight}`)
                .width('100%')
                .fontSize(12)
                .fontColor('#666666')
                .textAlign(TextAlign.Start)
  
              Image(this.previewPixelMap)
                .width('100%')
                .height(360)
                .objectFit(ImageFit.Contain)
                .borderRadius(12)
                .backgroundColor('#F3F3F3')
            }
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#F6F4EE')
          .borderRadius(20)
  
          Column({ space: 8 }) {
            Text('Log')
              .fontSize(18)
              .fontWeight(FontWeight.Medium)
              .width('100%')
              .textAlign(TextAlign.Start)
  
            Text(this.logText)
              .width('100%')
              .fontSize(12)
              .textAlign(TextAlign.Start)
          }
          .width('100%')
          .padding(16)
          .backgroundColor('#EEF3F8')
          .borderRadius(20)
        }
        .width('100%')
        .padding(20)
        .alignItems(HorizontalAlign.Start)
      }
      .width('100%')
      .height('100%')
    }
  }
  }
  ```

## 组件截图

组件截图只能够截取组件大小的区域，如果组件的绘制超出了它的区域，或子组件的绘制超出了父组件的区域，这些在组件区域外绘制的内容不会在截图中呈现，具体可见[使用组件截图（ComponentSnapshot）](../ui/arkts-uicontext-component-snapshot.md)。
