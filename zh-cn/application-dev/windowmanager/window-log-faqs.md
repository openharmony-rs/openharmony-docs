# 窗口开发常见日志问题与定位
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @liangryan-->
<!--Designer: @liangryan-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 使用窗口hidumper命令查看窗口信息定位问题

**hidumper**是OpenHarmony系统提供的诊断工具，可以实时查看系统中所有窗口的详细信息，帮助开发者快速定位窗口的相关问题。

### hidumper参数说明

基本命令格式：
```bash
hdc shell hidumper -s WindowManagerService -a '<参数>'
```

参数列表：

| 参数 | 含义 | 命令示例 | 使用场景 |
|------|------|----------|----------|
| `-h` | 查看帮助信息 | `hidumper -s WindowManagerService -a '-h'` | 首次使用时查看完整参数说明。 |
| `-a` | 查看所有窗口信息 | `hidumper -s WindowManagerService -a '-a'` | 需要查看所有窗口时使用（最常用）。 |
| `-w {WinId}` | 查看指定窗口详细信息 | `hidumper -s WindowManagerService -a '-w 13'` | 已知窗口ID，需要查看特定窗口详细信息。 |
| `-w {WinId} {ArkUI option}` | 查看指定窗口的ArkUI渲染信息 | `hidumper -s WindowManagerService -a '-w 13 -arkui'` | 需要查看窗口UI节点数量、渲染状态等信息。 |
| `-p` | 查看窗口父子树结构 | `hidumper -s WindowManagerService -a '-p'` | 排查窗口父子关系、层级树结构等问题。 |
| `-c` | 查看窗口截图信息 | `hidumper -s WindowManagerService -a '-c'` | 高级调试场景（截图相关信息）。 |


### 查看所有窗口列表

```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```

该命令输出窗口管理服务的完整状态信息，包括所有窗口的详细信息、焦点状态、层级关系等。

输出示例：
```bash
----------------------------------WindowManagerService----------------------------------
-------------------------------------ScreenGroup 1-------------------------------------
WindowName           DisplayId Pid     WinId Type Mode Flag ZOrd Orientation [ x    y    w    h    ]
SystemUi_NavigationB 0         1572    2     2112 102  0    4    0           [ 0    1208 720  72   ]
SystemUi_PrivacyIndi 0         1572    3     2111 102  0    3    0           [ 0    0    720  32   ]
SystemUi_StatusBar   0         1572    9     2108 102  0    2    0           [ 0    0    720  72   ]
note0                0         18299   13    1    1    0    1    0           [ 0    0    720  1280 ]
EntryView            0         1584    5     2001 1    0    0    8           [ 0    0    720  1280 ]
---------------------------------------------------------------------------------------  (前台窗口与后台窗口分隔线)
SystemUi_VolumePanel 0         1572    1     2111 1    0    -1   0           [ 0    0    0    0    ]
ScreenLockWindow     0         1572    4     2110 1    0    -1   0           [ 0    0    720  1280 ]
RecentView           0         1584    6     2115 1    0    -1   8           [ 0    0    720  1280 ]
SystemUi_DropdownPan 0         1572    7     2109 1    0    -1   0           [ 0    0    0    0    ]
SystemUi_BannerNotic 0         1572    8     2111 1    0    -1   0           [ 0    0    0    0    ]
mms0                 0         18119   11    1    1    1    -1   0           [ 0    0    720  1208 ]
camera0              0         18234   12    1    1    0    -1   0           [ 0    0    720  1280 ]
Focus window: 13
total window num: 12
```

前台窗口与后台窗口说明：

输出中通过分隔线区分前台窗口和后台窗口：分隔线以上为前台窗口（正在显示或可交互），分隔线以下为后台窗口（隐藏或不在前台显示）。

字段含义详细说明：

| 字段 | 含义 | 说明 |
|------|------|------|
| WindowName | 窗口名称 | 应用窗口名称（如note0表示备忘录应用），系统窗口名称（如SystemUi_StatusBar表示系统状态栏）。 |
| DisplayId | 显示设备ID | 屏幕设备的唯一标识，0表示主屏幕，多屏场景下可通过[getAllDisplays()](../reference/apis-arkui/js-apis-display.md#displaygetalldisplays9)查询所有屏幕的DisplayId。 |
| Pid | 进程ID | 创建该窗口的应用进程ID，如18299。 |
| WinId | 窗口唯一标识符 | 窗口ID，用于唯一标识一个窗口实例，如13。 |
| Type | 窗口类型 | 应用窗口：1表示应用主窗口，2表示应用子窗口；系统窗口：值为2000+。该值是系统内部标识，不直接对应[WindowType](../reference/apis-arkui/arkts-apis-window-e.md#windowtype7)枚举值。 |
| Mode | 窗口模式 | 1表示全屏模式。该值是系统内部标识，不完全对应[WindowMode](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#windowmode12)枚举值。 |
| Flag | 状态标志位 | 状态标识值。当前该字段为预留字段，无实际意义。 |
| ZOrd | 窗口层级（Z序） | 数值越大层级越高，如4比2层级高，-1表示隐藏层级。 |
| Orientation | 窗口方向 | 窗口方向标识值。当前该字段为预留字段，无实际意义。 |
| [ x y w h ] | 窗口矩形区域 | 窗口位置和大小，坐标以屏幕左顶点为原点。如[0 0 720 1280]表示位置(0,0)，大小720x1280。 |

### 查看获焦窗口

使用`-a`参数查看所有窗口信息时，输出中会显示获取焦点的窗口：

```bash
hdc shell hidumper -s WindowManagerService -a '-a' | grep "Focus window"
```

输出示例：
```text
Focus window: 13
```

根据WinId在窗口列表中找到对应窗口：`note0`（备忘录应用主窗口）。

前台窗口和后台窗口的焦点说明：

- 前台窗口才有机会获焦，后台窗口不会获焦。
- 后台窗口通常`ZOrd为-1`，不参与焦点竞争。
- 窗口从前台切换到后台时，会自动失焦。
- 开发者可以通过分隔线快速判断：焦点窗口必然在前台窗口区域，后台窗口区域不会有焦点窗口。

### 查看指定窗口详细信息

基本命令格式：

使用 `-w WinId` 参数查看特定窗口的详细信息：

```bash
hdc shell hidumper -s WindowManagerService -a '-w 13'
```

输出示例：

<!--RP1-->
```bash
----------------------------------WindowManagerService----------------------------------
WindowName: note0
DisplayId: 0
WinId: 13
Pid: 18299
Type: 1
Mode: 1
Flag: 0
Orientation: 0
IsStartingWindow: false
FirstFrameCallbackCalled: 1
VisibilityState: 0
Focusable: true
DecoStatus: true
IsPrivacyMode: false
isSnapshotSkip: 0
WindowRect: [ 0, 0, 720, 1280 ]
TouchHotAreas: [ 0, 0, 720, 1280 ]
```

字段含义详细说明：

| 字段 | 含义         | 取值说明                                                                                                                                |
|------|------------|-------------------------------------------------------------------------------------------------------------------------------------|
| WindowName | 窗口名称       | 应用自定义的窗口名称。如note0：表示为备忘录应用窗口；SystemUi_StatusBar：表示为系统状态栏窗口。                                                                         |
| DisplayId | 显示设备ID     | 显示设备标识。0：表示为主屏幕；其他值：表示为其他屏幕。多屏场景可通过[getAllDisplays()](../reference/apis-arkui/js-apis-display.md#displaygetalldisplays9)查询所有屏幕信息。   |
| WinId | 窗口唯一标识符    | 窗口ID，用于唯一标识该窗口实例，如13：表示为窗口ID。                                                                                                       |
| Pid | 进程ID       | 创建该窗口的应用进程ID，如18299：表示为应用进程ID。                                                                                                      |
| Type | 窗口类型       | 窗口类型标识。1：表示为应用主窗口；2：表示为应用子窗口；2000+：表示为系统窗口。                                                                                         |
| Mode | 窗口模式       | 窗口模式标识。1：表示为全屏模式。该值是系统内部标识，不完全对应[WindowMode](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#windowmode12)枚举值。 |
| Flag | 状态标志位      | 状态标识值。当前该字段为预留字段，无实际意义。                                                                                                             |
| Orientation | 窗口方向       | 窗口方向标识值。当前该字段为预留字段，无实际意义。                                                                                                           |
| IsStartingWindow | 是否显示启动页    | 执行命令时当前窗口显示的内容。true：表示当前窗口显示的是[应用启动页](launch-page-overview.md)；false：表示当前窗口显示的是正常应用窗口内容。 |
| FirstFrameCallbackCalled | 首帧回调状态     | 0：表示首帧回调未返回；1：表示首帧回调已返回。                                                                                                            |
| VisibilityState | 可见性状态      | 窗口可见性。0：表示为窗口可见；1：表示为窗口隐藏；2：表示为窗口部分可见。                                                                                              |
| Focusable | 是否可获焦      | true：表示窗口可以获焦；false：表示窗口不可获焦。                                                                                                       |
| DecoStatus | 装饰状态       | true：表示窗口装饰已启用（有标题栏等）；false：表示窗口无装饰。                                                                                                |
| IsPrivacyMode | 是否隐私模式     | 窗口隐私模式。true：表示为隐私窗口；false：表示为正常窗口。隐私窗口在不同设备上的截屏表现不同，详见[隐私模式](./screenshot-and-privacy-mode.md#规格表现)。                                |
| isSnapshotSkip | 截屏时是否显示该窗口 | 截屏显示标识。0：表示为截屏时显示该窗口内容；1：表示为截屏时不显示该窗口内容。                                                                                            |
| WindowRect | 窗口矩形区域     | 窗口位置和尺寸，格式为[x, y, width, height]，坐标以屏幕左顶点为原点。如[0, 0, 720, 1280]：表示为位置(0,0)，尺寸720x1280。                                              |
| TouchHotAreas | 触摸热区       | 窗口可触摸的区域，格式为[x, y, width, height]，坐标以窗口左顶点为原点。                                                                                      |
<!--RP1End-->

常见问题定位：

窗口无法接收键盘输入

- 确认窗口的`Focusable`是否为false，若为false，调用[setWindowFocusable()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9)传入true设置可获焦。
- 确认窗口是否在前台区域（分隔线以上）。

<!--Del-->
截屏时窗口内容未隐藏

- 确认窗口是否为非隐私窗口且设置了截图时显示窗口内容，即`IsPrivacyMode`为false且`isSnapshotSkip`为0，截图时不会隐藏。
- 若需要截屏时隐藏窗口内容，调用[setWindowPrivacyMode()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9)传入true启用隐私模式。
<!--DelEnd-->

窗口启动性能慢

- 确认窗口是否首帧未显示完成，若FirstFrameCallbackCalled为0：首帧未完成，可能页面加载慢。需要结合日志分析启动耗时原因。

<!--Del-->
窗口触摸区域异常
- `TouchHotAreas`尺寸异常：触摸热区设置错误。
- 与`WindowRect`对比，确认是否正确设置
<!--DelEnd-->

### 定位思路

1. 问题定位流程：
   1. 发现问题
   2. 使用hidumper查看窗口状态
   3. 分析异常属性
   4. 定位代码位置
   5. 修复验证

2. 结合日志使用：
   - hidumper提供实时窗口状态
   - 系统日志（WINDOW_FROZEN_DETECTION）提供异常警告
   - 两者结合可以更快速定位问题

3. 对比验证：
   - 执行操作前后对比窗口状态
   - 确认操作是否生效

4. 关注关键属性：
   <!--Del-->
   - VisibilityState：确认窗口是否显示
   <!--DelEnd-->
   - ZOrder：确认层级关系
   - WindowRect：确认窗口大小和位置

> **说明：**
>
> hidumper命令需要在设备或模拟器上执行，开发者可以通过hdc shell连接设备后执行。hidumper输出的是实时窗口状态，可能随窗口操作而变化，建议在问题发生时立即执行查询以获取准确信息。

## WINDOW_FROZEN_DETECTION异常检测

**可能原因**

WINDOW_FROZEN_DETECTION是一个窗口伪冻屏检测事件。搭载OpenHarmony 7.0.0及以上版本的设备支持此检测事件。

当未成功设置UIContent、布局异常等情形时会触发此事件，可为排查伪冻屏问题提供线索，但事件触发并不等同于伪冻屏已实际发生。常见的异常类型包括：SetUIContent timeout（窗口内容加载超时）、RectCheck err（窗口尺寸异常）等。

### 定位窗口内容加载超时问题

窗口创建后未在规定时间内（5秒）加载页面内容，导致窗口显示为透明或冻结状态。

**典型日志信息**

故障日志格式：

```text
MSG = SetUIContent timeout uid: [uid], windowName: [windowName], bundleName: [bundleName], abilityName: [abilityName]
```

关键信息：
- `uid`：用户ID
- `windowName`：窗口名
- `bundleName`：包名
- `abilityName`：实例名

**检测逻辑**

系统在窗口创建时启动定时器监控页面加载过程。如果窗口创建后5秒内未调用[loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)或[setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9)加载页面内容，系统判定为异常并生成故障日志。

> **说明：**
>
> 系统的超时检测机制是为了保障用户体验，避免用户长时间看到空白窗口。开发者应重视此警告并及时修复。

**分析定位及解决**

排查步骤：
1. 是否在窗口创建后立即调用了[loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)或[setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9)。
2. 是否在页面加载和窗口显示之间有耗时操作。
3. 是否先调用[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9)再调用[loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)。
4. 页面路径是否正确。

**正反案例**

错误示例

```ts
// 错误：创建窗口后未加载内容
windowStage.createSubWindow('subWindow', (err, windowClass) => {
    if (err.code) {
        console.error('Failed to create sub window.');
        return;
    }
    // 未调用loadContent加载页面
    windowClass.showWindow(); // 直接显示窗口，导致透明窗
});
```

正确示例

```ts
// 正确：创建窗口后立即加载内容
windowStage.createSubWindow('subWindow', (err, windowClass) => {
    if (err.code) {
        console.error('Failed to create sub window.');
        return;
    }
    // 立即加载页面内容
    windowClass.loadContent('pages/SubWindowPage', (err) => {
        if (err.code) {
            console.error('Failed to load content.');
            return;
        }
        // 内容加载成功后再显示窗口
        windowClass.showWindow();
    });
});
```

### 定位窗口尺寸异常问题

窗口尺寸异常检测用于发现窗口尺寸超出合理范围的问题。当窗口设置的尺寸超过最大尺寸限制，或小于最小尺寸限制且小于屏幕尺寸时，系统会生成故障日志。

**典型日志信息**

故障日志格式：

```text
RectCheck err size cur persistentId: [persistentId], windowType: [windowType], windowName: [windowName], windowState: [windowState], curWidth: [curWidth], curHeight: [curHeight], minWidth: [minWidth], minHeight: [minHeight], screenWidth: [screenWidth], screenHeight: [screenHeight], maxFloatingWindowSize: [maxFloatingWindowSize], sessionRect: [sessionRect];
```

字段含义：

| 字段 | 含义 | 说明                                                                                                                                                                                                                                     |
|------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `persistentId` | 窗口持久化ID | 窗口的唯一标识，用于定位具体窗口                                                                                                                                                                                                                       |
| `windowName` | 窗口名称 | 应用设置的窗口名称                                                                                                                                                                                                                              |
| `windowType` | 窗口类型 | 窗口类型值（如应用主窗口、子窗口等）                                                                                                                                                                                                                     |
| `windowState` | 窗口状态 | 窗口当前状态（显示、隐藏等）                                                                                                                                                                                                                         |
| `curWidth` | 当前宽度（vp） | 窗口当前实际宽度，单位为vp                                                                                                                                                                                                                         |
| `curHeight` | 当前高度（vp） | 窗口当前实际高度，单位为vp                                                                                                                                                                                                                         |
| `minWidth` | 最小宽度限制（vp） | 系统规定的最小宽度。该值等于未调用[setWindowLimits()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11)配置过WindowLimits时，[getWindowLimitsVP()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22)返回的最小宽度。     |
| `minHeight` | 最小高度限制（vp） | 系统规定的最小高度。该值等于未调用[setWindowLimits()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11)配置过WindowLimits时，[getWindowLimitsVP()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22)返回的最小高度。     |
| `maxFloatingWindowSize` | 最大尺寸限制（vp） | 系统规定的最大尺寸阈值。该值等于未调用[setWindowLimits()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11)配置过WindowLimits时，[getWindowLimitsVP()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22)返回的最大尺寸阈值。 |
| `sessionRect` | 窗口矩形区域（px） | 窗口的位置和尺寸，单位为px，坐标以屏幕左顶点为原点                                                                                                                                                                                                             |

**检测逻辑**

当窗口尺寸满足以下任一条件时触发异常：

1. 尺寸超过最大限制：`curWidth > maxFloatingWindowSize` 或 `curHeight > maxFloatingWindowSize`。
2. 尺寸小于最小限制且小于屏幕尺寸（非系统窗口类型）：`curWidth < minWidth` 且 `curWidth < screenWidthVp`，或 `curHeight < minHeight` 且 `curHeight < screenHeightVp`。

> **说明：**
>
> `screenWidthVp`、`screenHeightVp`为屏幕尺寸的vp值，由系统内部根据故障日志中的`screenWidth`、`screenHeight`（px值）除以屏幕密度计算得到。故障日志中不直接输出这两个值，开发者可通过`screenWidthVp = screenWidth / density`自行计算。
>
> WINDOW_RECT_CHECK异常表示窗口尺寸不在系统规定的范围内。开发者应根据故障日志中的curWidth、curHeight值与系统限制对比，调整[resize()](../reference/apis-arkui/arkts-apis-window-Window.md#resize9)调用时的尺寸参数。`maxFloatingWindowSize`为系统规定的最大尺寸阈值，窗口宽度和高度的最大限制均为此值，即窗口宽度应在[minWidth, maxFloatingWindowSize]范围内，窗口高度应在[minHeight, maxFloatingWindowSize]范围内。
>
> 条件2需要同时满足"小于最小限制"和"小于屏幕尺寸"两个条件，原因如下：当窗口尺寸小于最小限制但已达到屏幕尺寸时（如`curWidth < minWidth`但`curWidth >= screenWidthVp`），说明屏幕尺寸本身较小，窗口已占满屏幕无法再增大，属于设备限制而非开发者设置问题，系统不会上报RectCheck err；只有当窗口尺寸同时小于最小限制和屏幕尺寸时，才说明开发者设置的窗口尺寸过小，可以设置更大的窗口，需要调整。

**分析定位及解决**

1. 获取故障日志。通过DevEco Studio的FaultLog或hdc查看故障日志：

   ```bash
   hdc shell hilog | grep "RectCheck err"
   ```

2. 解析故障日志字段。从故障日志中提取关键信息：
   - `windowName`：确认异常窗口名称
   - `curWidth`、`curHeight`：查看当前异常尺寸值（vp）
   - `minWidth`、`minHeight`、`maxFloatingWindowSize`：对比限制阈值（vp）
   - `screenWidth`、`screenHeight`：对比屏幕尺寸（px，需转换为vp）

3. 判断异常类型。根据curWidth、curHeight与限制值、屏幕尺寸的对比：
   - 如果 `curWidth > maxFloatingWindowSize` 或 `curHeight > maxFloatingWindowSize`：窗口尺寸超过最大限制
   - 如果 `curWidth < minWidth` 且 `curWidth < screenWidthVp`：窗口宽度过小且小于屏幕宽度
   - 如果 `curHeight < minHeight` 且 `curHeight < screenHeightVp`：窗口高度过小且小于屏幕高度

4. 检查代码中[resize()](../reference/apis-arkui/arkts-apis-window-Window.md#resize9)调用位置的尺寸参数。

5. 确认窗口模式切换时的尺寸计算逻辑。

6. 使用hidumper验证修复后的窗口状态。

**正反案例**

错误示例

```ts
// 错误：窗口尺寸过小
let windowClass = await windowStage.createSubWindow('subWindow');
windowClass.resize(50, 50); // 尺寸小于最小限制，触发WINDOW_RECT_CHECK异常
windowClass.showWindow();
```

正确示例

```ts
// 正确：先查询系统限制，再设置在规定范围内的尺寸
let windowClass = await windowStage.createSubWindow('subWindow');
// 通过getWindowLimits查询窗口尺寸限制范围
let windowLimits = windowClass.getWindowLimits();
// 确保设置的尺寸在[windowLimits.minWidth, windowLimits.maxWidth]和[windowLimits.minHeight, windowLimits.maxHeight]范围内
windowClass.resize(720, 640);
windowClass.showWindow();
```

## 1300002错误码的定位指导

错误码1300002表示窗口状态异常或窗口对象无效。

### 窗口销毁时调用getLastWindow崩溃

开发者在窗口销毁过程中（如onWindowStageDestroy、页面销毁等）调用[getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1)接口，导致应用崩溃。

**典型日志信息**

故障日志格式：

```text
Error Name: Error
Error Message: [window][getLastWindow]msg: xxx
Error code: 1300002
Stack trace:
  at window.getLastWindow (WindowManagerService)
  at MyComponent.onWindowStageDestroy (MyAbility.ts:50)
```

关键信息：
- 错误码：1300002
- 堆栈：getLastWindow()调用位置
- 文件名和行号：定位具体代码位置

**分析定位及解决**

根据日志堆栈定位getLastWindow()调用位置，检查是否在销毁流程中（onWindowStageDestroy、aboutToDisappear等）。常见场景：窗口创建时未调用[loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)加载页面，销毁流程中错误调用getLastWindow导致崩溃。

解决要点：
- getLastWindow()调用位置不在onWindowStageDestroy、aboutToDisappear、onDestroy等销毁回调中
- 异步任务不会在销毁后执行getLastWindow()

**正反案例**

错误示例

```ts
// 错误：窗口创建时未加载页面，销毁流程中调用getLastWindow
onWindowStageCreate(windowStage: window.WindowStage) {
    // 缺失：未调用loadContent加载页面
    windowStage.getMainWindow((err, win) => {
        win.showWindow(); // 直接显示空窗口
    });
}

onWindowStageDestroy() {
    let lastWindow = window.getLastWindow(this.context); // 崩溃！
}
```

正确示例

```ts
// 正确：窗口创建时立即加载页面，销毁流程只做资源清理
onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.getMainWindow((err, win) => {
        win.loadContent('pages/MainPage'); // 创建时加载页面
    });
}

onWindowStageDestroy() {
    this.cleanupResources(); // 只做资源清理，不调用getLastWindow
}
```

### 子窗口调用setResizeByDragEnabled接口失败

开发者在子窗口上调用[setResizeByDragEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setresizebydragenabled14)接口设置窗口可拖拽缩放时，返回错误码1300002，无法实现拖拽缩放功能。

**典型日志信息**

通过DevEco Studio或hdc查看错误日志：

```bash
hdc shell hilog | grep -i -E "1300002|setResizeByDragEnabled"
```

典型日志示例：

``` text
SetResizeByDragEnabled: This is not main window or decor enabled sub window
```

关键信息：
- 错误码：1300002（窗口状态异常）
- 错误信息：This is not main window or decor enabled sub window
- 原因：子窗口未启用装饰栏，不支持拖拽缩放

**分析定位及解决**

检查创建子窗口时是否在SubWindowOptions中将`decorEnabled`设置为`true`。

对于调用该接口的子窗口，要保证子窗口已开启窗口装饰栏。

**正反案例**

错误示例

```ts
windowStage.createSubWindowWithOptions('mySubWindow', {
  title: "",
  decorEnabled: false,    // 错误：未开启装饰栏
  isModal: false,
  maximizeSupported: true
})
```

正确示例

```ts
let options: window.SubWindowOptions = {
  title: "",
  decorEnabled: true,   // 开启窗口装饰栏
  isModal: false,
  maximizeSupported: true
};
windowStage.createSubWindowWithOptions('mySubWindow', options).then((windowClass) => {
  // decorEnabled=true时可正常调用
  windowClass.setResizeByDragEnabled(true, (err: BusinessError) => {
    console.error("setResizeByDragEnabled failed.", ` code: ${err.code}, message: ${err.message}`)
  })
})
```

### 窗口名不存在，调用findWindow查找崩溃

开发者在调用[findWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowfindwindow9)查找不存在的窗口时，导致应用崩溃。

**典型日志信息**

故障日志格式：

```text
Error Name: Error
Error Message: [window][findWindow]msg: The window is not created or destroyed
Error code: 1300002
Stack trace:
  at window.findWindow (WindowManagerService)
  at MyComponent.onCreate (MyAbility.ts:50)
```

关键信息：
- 错误码：1300002
- 堆栈：findWindow()调用位置
- 文件名和行号：定位具体代码位置

**分析定位及解决**

根据日志堆栈定位findWindow()调用位置，检查窗口名称是否正确。使用以下命令查找findWindow参数信息：

```bash
grep -n "findWindow" src/**/*.ts
```

使用hidumper验证窗口状态：

```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```

解决要点：
- 查找非主窗时使用Configuration中的窗口名称
- findWindow之后对获取到的对象进行空校验

**正反案例**

错误示例

```ts
// 错误：查找窗口时传入错误窗口名称
const currWindow = window.findWindow("test_Window");
// 错误：对为空的对象进行函数调用
currWindow.showWindow();
```

正确示例

```ts
// 正确：findWindow之后对获取到的对象进行空校验
const currWindow = window.findWindow("test_Window");
if (currWindow) {
    currWindow.showWindow();
} else {
    console.error('Window not found');
}
```

### 销毁未完成导致createSubWindow创建同名子窗失败

开发者在[createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9)创建窗口对象后，使用[destroyWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#destroywindow9)，在窗口还未销毁的情况下，再次调用[createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9)，且使用相同名称，导致窗口创建失败，报错1300002。

**典型日志信息**

故障日志格式：

```text
WindowSessionCreateCheck: WindowName(TestSubWindow) already exists.
Error code: 1300002
```

关键信息：
- 重复窗口名：TestSubWindow
- 错误码：1300002

**分析定位及解决**

destroyWindow()接口用于销毁对应窗口实例，该接口为异步接口，若createSubWindow接口调用时，需要销毁的窗口实例还未销毁完成，则有可能创建同名，触发1300002错误。

根据日志堆栈定位createSubWindow()调用位置，查找所有createSubWindow调用位置，检查是否有使用相同窗口名称的情况：

```bash
grep -n "createSubWindow" src/**/*.ts
```

在创建窗口失败后，使用hidumper查看当前窗口状态：

```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```

解决要点：
- 确保destroyWindow()调用后等待异步回调完成，使用await等待销毁完成
- 或使用不同的窗口名称避免重名

**正反案例**

错误示例

```ts
let windowClass: window.Window | undefined = undefined;

let windowClass = await windowStage.createSubWindow('mySubWindow');

// 错误，destroyWindow为异步接口，却当做同步接口使用
windowClass.destroyWindow();
let newWindow = await windowStage.createSubWindow('mySubWindow'); // 此处可能会返回1300002错误
```

正确示例

```ts
// 正确：等待销毁完成后再创建
let windowClass = await windowStage.createSubWindow('mySubWindow');

// 调用销毁并等待完成
await windowClass.destroyWindow();
// 确保销毁完成后，再创建同名窗口
let newWindow = await windowStage.createSubWindow('mySubWindow');
```

或使用不同的窗口名称避免重名：

```ts
// 使用时间戳作为窗口名称的一部分，避免重名
let windowName = 'mySubWindow_' + Date.now();
let windowClass = await windowStage.createSubWindow(windowName);
```

### 窗口销毁时调用off('avoidAreaChange')崩溃

开发者在窗口销毁过程中（如onWindowStageDestroy或页面销毁等）调用[off('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offavoidareachange9)接口，导致应用崩溃。

**典型日志信息**

```text
Error Name: Error
Error Message: [window][off]msg: Unregister listener failed.
Error code: 1300002
Stack trace:
  at windowClass.off('avoidAreaChange') (WindowManagerService)
  at MyComponent.onWindowStageDestroy (MyAbility.ts:50)
```

关键信息：
- 错误码：1300002
- 堆栈：off('avoidAreaChange')调用位置
- 文件名和行号：定位具体代码位置（如MyAbility.ts第50行）

**分析定位及解决**

根据日志堆栈定位off('avoidAreaChange')调用位置，检查是否在销毁流程中（onWindowStageDestroy或aboutToDisappear等）。

常见场景：销毁流程中错误调用off('avoidAreaChange')导致崩溃。

解决要点：

- off('avoidAreaChange')调用位置不在onWindowStageDestroy、aboutToDisappear或onDestroy等销毁回调中
- 异步任务不会在销毁后执行off('avoidAreaChange')

**正反案例**

错误示例

```ts
// 错误：在onWindowStageDestroy中调用off
onWindowStageDestroy() {
    this.windowClass.off('avoidAreaChange'); // 窗口可能已经销毁，1300002崩溃！
}
```

正确示例

```ts
// 取消监听时机：页面隐藏或卸载前（非销毁流程）
onPageHide() {
  try {
    this.windowClass?.off('avoidAreaChange');
  } catch (exception) {
    console.error(`Failed to disable the listener. Cause code: ${exception.code}, message: ${exception.message}`);
  }
}
```

## 1300004错误码的定位指导

错误码1300004表示无权限操作，常见于窗口类型与接口不匹配场景。


### 子窗调用restore失败

开发者对子窗口调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口，导致操作失败，报错1300004。

**典型日志信息**

故障日志：

```text
BusinessError 1300004: Unauthorized operation. Possible cause: Invalid window Type.Only main windows are supported.
```

**分析定位及解决**

`restore()`接口只能对主窗口进行恢复操作，否则会报1300004错误。

 1.使用hidumper查看窗口类型，确认窗口是否为主窗口：

```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```

 2.在输出中查找目标窗口，根据Type字段判断：
- 若Type为1，则对应为主窗口（MainWindow），可以调用restore()。
- Type不为1的窗口，均不能调用restore()。例如，通过[createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9)接口创建的窗口为子窗口，可在创建时指定子窗口名称。

### 子窗口调用getWindowSystemBarProperties()崩溃

开发者在应用子窗口、全局悬浮窗等非应用主窗口上调用[getWindowSystemBarProperties()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowsystembarproperties12)接口，报错1300004。

**典型日志信息**

```text
Error Name: Error
Error Message: [window][getWindowSystemBarProperties]msg: Invalid window type. Only main windows are supported.
Error code: 1300004
Stack trace:
  at windowClass.getWindowSystemBarProperties() (WindowManagerService)
  at MyComponent.onWindowStageCreate (MyAbility.ts:50)
```

关键信息：
- 错误码：1300004
- 堆栈：getWindowSystemBarProperties()调用位置
- 文件名和行号：定位具体代码位置（如MyAbility.ts第50行）

**分析定位及解决**

getWindowSystemBarProperties()接口只适用于应用主窗口调用，否则会报1300004错误。

1. 使用hidumper查看窗口类型，确认当前窗口是否为应用主窗口：

    ```bash
    hdc shell hidumper -s WindowManagerService -a '-a'
    ```
2. 在输出中查找目标窗口，根据Type字段判断。若Type为1，则对应为主窗口，可以调用getWindowSystemBarProperties()；否则不可以调用getWindowSystemBarProperties()。

**正反案例**

错误示例

```ts
windowStage.createSubWindow('mySubWindow', (err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to create the subwindow. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  windowClass = data;
  console.info(`Succeeded in creating the subwindow. Data: ${JSON.stringify(data)}`);
  if (!windowClass) {
    console.info('Failed to load the content. Cause: windowClass is null');
  }
  let systemBarProperty = windowClass.getWindowSystemBarProperties()
});
```

正确示例

```ts
onWindowStageCreate(windowStage: window.WindowStage) {
  let windowClass = windowStage.getMainWindowSync();
  try {
    let systemBarProperty = windowClass.getWindowSystemBarProperties();
    console.info('Success in obtaining system bar properties. Property: ' + JSON.stringify(systemBarProperty));
  } catch (err) {
    console.error(`Failed to get system bar properties. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## 1300012 画中画窗口状态异常

错误码1300012表示画中画窗口状态异常。

### 可能原因

- 画中画窗口已被销毁，但代码仍在尝试访问该窗口。

- 画中画窗口处于无效状态（如尚未创建、已关闭、正在销毁）。

- 在画中画窗口销毁后，异步任务或回调中访问了窗口对象。

- 画中画窗口已经启动或正在启动中，但代码仍在尝试重复启动画中画窗口。

### 画中画窗口销毁后访问导致崩溃

开发者在画中画窗口销毁后（如用户退出画中画、窗口生命周期结束等）调用画中画窗口[stopPiP()](../reference/apis-arkui/js-apis-pipWindow.md#stoppip)接口，触发错误码1300012。

**典型日志信息**

```text
Error Name: Error
Error Message: [PiPWindow][stopPiP]msg: The window is not created or destroyed.
Error code: 1300012
```

**分析定位及解决**

- 是否在画中画生命周期状态为`ABOUT_TO_STOP`或`STOPPED`时调用stopPiP()接口。

  在以上状态时，代表画中画窗口即将停止或已经停止，此时不可调用stopPiP()接口。

- 是否在`setTimeout`、`Promise`等异步回调中调用stopPiP()，且回调执行时窗口可能已销毁。

  在异步回调中，画中画窗口可能已被销毁，代码中没有对画中画窗口状态进行校验，此时调用stopPiP()接口会导致错误。

**正反案例**

错误示例

```ts
// 错误：异步任务在窗口销毁后调用stopPiP()接口
stopPiPTimer() {
    setTimeout(() => {
        this.pipController?.stopPiP();
    }, 1000);
}
```

正确示例
```ts
async stopPiPSafely(pipController: PiPController) {
  let state: string = 'undefined';
  
  pipController.on('stateChange', (newState: string, reason: string) => {
    state = newState;
    if (state === 'STARTED') {
      pipController?.stopPiP();
    }
  });
}
```

### 画中画窗口重复启动导致崩溃

开发者在画中画窗口处于已经启动或正在启动中的状态时，调用画中画窗口[startPiP()](../reference/apis-arkui/js-apis-pipWindow.md#startpip)接口，触发错误码1300012。

**典型日志信息**

```text
Error Name: Error
Error Message: [PiPWindow][startPiP]msg: The window is already started or is about to start.
Error code: 1300012
```

**分析定位及解决**

- 是否在画中画生命周期状态为`ABOUT_TO_START`或`STARTED`时调用startPiP()接口。

  在该状态时，代表画中画窗口即将启动或已经启动，此时不可调用startPiP()接口。

- 是否在`setTimeout`、`Promise`等异步回调中调用startPiP()，且回调执行时窗口可能已启动。

  在异步回调中，画中画窗口可能已经启动或正在启动中，代码中没有对画中画窗口状态进行校验，此时调用startPiP()接口会导致错误。

**正反案例**

错误示例

```ts
// 错误：异步任务在窗口已创建后调用startPiP()接口
startPiPTimer() {
    setTimeout(() => {
        this.pipController?.startPiP();
    }, 1000);
}
```

正确示例
```ts
async startPiPSafely(pipController: PiPController) {
  let state: string = 'undefined';
  
  pipController.on('stateChange', (newState: string, reason: string) => {
    state = newState;
    if (state === 'STOPPED') {
      pipController?.startPiP();
    }
  });
}
```