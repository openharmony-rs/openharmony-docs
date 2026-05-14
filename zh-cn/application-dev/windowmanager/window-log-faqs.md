# 窗口开发常见日志问题与定位
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 使用窗口hidumper命令查看窗口信息定位问题

**hidumper**是OpenHarmony系统提供的诊断工具，可以实时查看系统中所有窗口的详细信息，帮助开发者快速定位窗口相关问题。

### hidumper参数说明

基本命令格式：
```bash
hdc shell hidumper -s WindowManagerService -a '<参数>'
```

**参数列表**：

| 参数 | 含义 | 命令示例 | 使用场景 |
|------|------|----------|----------|
| `-h` | 查看帮助信息 | `hidumper -s WindowManagerService -a '-h'` | 首次使用时查看完整参数说明 |
| `-a` | dump所有窗口信息 | `hidumper -s WindowManagerService -a '-a'` | 需要查看所有窗口时使用（最常用） |
| `-w {WinId}` | dump指定窗口详细信息 | `hidumper -s WindowManagerService -a '-w 13'` | 已知窗口ID，需要查看特定窗口详细信息 |
| `-w {WinId} {ArkUI option}` | dump指定窗口的ArkUI信息 | `hidumper -s WindowManagerService -a '-w 13 -arkui'` | 需要查看窗口UI渲染细节时 |
| `-p` | dump窗口树结构 | `hidumper -s WindowManagerService -a '-p'` | 排查窗口父子关系、层级树结构时 |
| `-v` | dump窗口可见性信息 | `hidumper -s WindowManagerService -a '-v'` | 排查窗口显示/隐藏问题时 |
| `-c` | dump窗口截图信息 | `hidumper -s WindowManagerService -a '-c'` | 高级调试场景（截图相关信息） |
| `-b` | dump窗口绑定的信息 | `hidumper -s WindowManagerService -a '-b'` | 高级调试场景（surface、buffer绑定等） |


### 查看所有窗口列表

```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```

该命令输出窗口管理服务的完整状态信息，包括所有窗口的详细信息、焦点状态、层级关系等。`-a '-a'`参数表示dump所有窗口信息。

输出示例：
```
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

**前台窗口与后台窗口说明**：

输出中通过分隔线区分前台窗口和后台窗口：分隔线以上为前台窗口（正在显示或可交互），分隔线以下为后台窗口（隐藏或不在前台显示）。

**字段含义详细说明**：

| 字段 | 含义 | 示例值说明 |
|------|------|----------|
| `WindowName` | 窗口名称 | `note0`（备忘录应用窗口），`SystemUi_StatusBar`（系统状态栏） |
| `DisplayId` | 显示设备ID | `0`表示主屏幕，多屏场景下会有多个DisplayId |
| `Pid` | 进程ID | `18299`表示创建该窗口的应用进程ID |
| `WinId` | 窗口唯一标识符 | `13`表示窗口ID，用于唯一标识一个窗口实例 |
| `Type` | 窗口类型 | 见下表详细说明 |
| `Mode` | 窗口模式 | `1`表示全屏模式，`102`表示特定模式 |
| `Flag` | 状态标志位 | `0`表示正常显示，`1`表示隐藏状态 |
| `ZOrd` | 窗口层级（Z序） | 数值越大越靠前，`4`比`2`层级高 |
| `Orientation` | 窗口方向 | `0`=未指定，`8`=竖屏等方向设置 |
| `[ x y w h ]` | 窗口矩形区域 | `[0 0 720 1280]`表示位置(0,0)，大小720x1280 |

### 查看获焦窗口

**直接查看Focus window字段**：

在输出的末尾可以直接看到获焦窗口信息：

```
Focus window: 13
```

**含义解读**：
- `Focus window: 13`：当前获焦窗口的WinId是13
- 根据WinId=13，在窗口列表中找到对应窗口：`note0`
- 结论：当前获焦窗口是`note0`（备忘录应用）

**详细定位获焦窗口**：

```bash
hdc shell hidumper -s WindowManagerService -a '-a' | grep "Focus window"
```

输出示例：
```
Focus window: 13
```

根据Focus window的WinId值，结合窗口列表找到具体窗口：
1. Focus window: 13 → 焦点窗口WinId=13
2. 在窗口列表中查找WinId=13的窗口：
   ```
   note0  0  18299  13  1  1  0  1  0  [ 0  0  720  1280 ]
   ```
3. 确认获焦窗口：`note0`（备忘录应用主窗口）

**前台窗口和后台窗口的焦点说明**：

**前台窗口焦点**：

焦点窗口通常在前台窗口中：

```
Focus window: 13
```

含义：
- WinId=13（`note0`）是当前获焦窗口
- `note0`位于前台窗口区域（分隔线以上）
- 前台窗口才有机会获焦，后台窗口不会获焦

**后台窗口焦点规则**：

- 后台窗口（分隔线以下）通常`ZOrd=-1`或`Flag=1`，不参与焦点竞争
- 只有前台窗口（分隔线以上）才能获焦
- 窗口从前台切换到后台时，会自动失焦

**焦点窗口切换示例**：

当应用从前台切换到后台时：
1. 前台状态：`note0` WinId=13, Flag=0, ZOrd=1, Focus window: 13
2. 切换到后台：`note0` WinId=13, Flag=1, ZOrd=-1（移到分隔线以下）
3. 焦点转移：Focus window变为其他前台窗口（如桌面EntryView）

开发者可以通过分隔线快速判断：
- 焦点窗口必然在前台窗口区域
- 后台窗口区域不会有焦点窗口

### 查看指定窗口详细信息

**基本命令格式**：

使用 `-w WinId` 参数查看特定窗口的详细信息：

```bash
hdc shell hidumper -s WindowManagerService -a '-w 13'
```

`-w 13` 参数表示查看WinId为13的窗口详细信息。

输出示例：
```
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

**字段含义详细说明**：

| 字段 | 含义 | 示例值解读 |
|------|------|----------|
| `WindowName` | 窗口名称 | `note0`表示备忘录应用窗口 |
| `DisplayId` | 显示设备ID | `0`表示主屏幕显示 |
| `WinId` | 窗口唯一标识符 | `13`表示窗口ID，用于唯一标识该窗口实例 |
| `Pid` | 进程ID | `18299`表示创建该窗口的应用进程ID |
| `Type` | 窗口类型 | `1`=应用主窗口 |
| `Mode` | 窗口模式 | `1`=全屏模式 |
| `Flag` | 状态标志位 | `0`=正常显示状态 |
| `Orientation` | 窗口方向 | `0`=未指定方向 |
| `IsStartingWindow` | 是否是启动窗口 | `false`=不是启动过渡窗口 |
| `FirstFrameCallbackCalled` | 首帧回调状态 | `1`=首帧绘制回调已调用 |
| `VisibilityState` | 可见性状态 | `0`=窗口可见 |
| `Focusable` | 是否可获焦 | `true`=窗口可以获焦 |
| `DecoStatus` | 装饰状态 | `true`=窗口装饰已启用（有标题栏等） |
| `IsPrivacyMode` | 是否隐私模式 | `false`=不是隐私窗口 |
| `isSnapshotSkip` | 是否跳过截屏 | `0`=可以被截屏 |
| `WindowRect` | 窗口矩形区域 | `[ 0, 0, 720, 1280 ]`表示位置(0,0)，尺寸720x1280 |
| `TouchHotAreas` | 触摸热区 | `[ 0, 0, 720, 1280 ]`表示整个窗口区域可触摸 |

**常见问题定位**：

**问题1：窗口不显示**

检查字段：
- `VisibilityState: 1` → 窗口被隐藏，调用showWindow()显示
- `Flag: 1` → 状态标志为隐藏，检查窗口是否调用hideWindow()

**问题2：窗口无法接收键盘输入**

检查字段：
- `Focusable: false` → 窗口不可获焦，调用setWindowFocusable(true)设置可获焦
- 确认窗口在前台区域（分隔线以上）

**问题3：窗口被截屏泄露**

检查字段：
- `IsPrivacyMode: false` → 未启用隐私模式
- `isSnapshotSkip: 0` → 允许截屏

解决方案：调用setPrivacyMode(true)启用隐私模式。

**问题4：窗口启动性能慢**

检查字段：
- `FirstFrameCallbackCalled: 0` → 首帧未完成，可能页面加载慢
- 结合日志分析启动耗时

**问题5：窗口触摸区域异常**

检查字段：
- `TouchHotAreas` 尺寸异常 → 触摸热区设置错误
- 与WindowRect对比，确认是否正确

### 查看窗口ArkUI渲染信息

**基本命令格式**：

使用 `-w WinId ArkUI option` 参数查看窗口的ArkUI渲染详细信息：

```bash
hdc shell hidumper -s WindowManagerService -a '-w 13 ArkUI option'
```

该命令在窗口基础信息的基础上，额外输出ArkUI渲染相关的字段，用于分析UI渲染性能、节点数量等。

输出示例：
```
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
VisibilityState: 2
Focusable: true
DecoStatus: true
IsPrivacyMode: false
isSnapshotSkip: 0
WindowRect: [ 0, 0, 720, 1280 ]
TouchHotAreas: [ 0, 0, 720, 1280 ]
bundleName: com.ohos.note
moduleName: default
LastRequestVsyncTime: 17816965532004
transactionFlags: [18299,0]
last vsyncId: 1948
finishCount: [ ]
UINodeCount: 159
```

**ArkUI相关新增字段说明**：

| 字段 | 含义 | 示例值解读 |
|------|------|----------|
| `bundleName` | 应用包名 | `com.ohos.note`表示备忘录应用的包名 |
| `moduleName` | 模块名称 | `default`表示默认模块 |
| `LastRequestVsyncTime` | 最后请求VSync时间 | `17816965532004`表示上次请求垂直同步的时间戳（纳秒） |
| `transactionFlags` | 事务标志 | `[18299,0]`表示渲染事务的进程ID和标志位 |
| `last vsyncId` | 最后VSync ID | `1948`表示上次垂直同步的ID |
| `finishCount` | 完成计数 | `[ ]`表示当前未完成的渲染任务计数 |
| `UINodeCount` | UI节点数量 | `159`表示当前窗口的UI节点总数 |

**常见问题定位**：

| 问题 | 检查字段 | 判断标准 | 解决方案 |
|------|----------|----------|----------|
| UI渲染性能差（卡顿） | `UINodeCount`、`finishCount`、`LastRequestVsyncTime` | `UINodeCount`≥500 或 `finishCount`有任务堆积 | 简化UI结构，减少节点嵌套，优化渲染逻辑 |
| 窗口停止渲染 | `last vsyncId`、`LastRequestVsyncTime` | VSync长时间未更新或时间戳过旧 | 检查VisibilityState，调用showWindow() |
| UI节点异常多 | `UINodeCount` | 正常页面约100节点，异常页面≥500节点 | 使用懒加载、虚拟列表，移除隐藏节点 |
| 渲染任务堆积 | `finishCount` | `finishCount`非空，存在未完成任务 | 减少UI更新频率，避免渲染线程耗时操作 |

### 最佳实践

1. **问题定位流程**：
   ```
   发现问题 → 使用hidumper查看窗口状态 → 分析异常属性 → 定位代码位置 → 修复验证
   ```

2. **结合日志使用**：
   - hidumper提供实时窗口状态
   - 系统日志（WINDOW_EXCEPTION_DETECTION）提供异常警告
   - 两者结合可以更快速定位问题

3. **对比验证**：
   - 执行操作前后对比窗口状态
   - 确认操作是否生效

4. **关注关键属性**：
   - VisibilityState：确认窗口是否显示
   - ZOrder：确认层级关系
   - WindowRect：确认窗口大小和位置

> **说明：**
>
> hidumper命令需要在设备或模拟器上执行，开发者可以通过hdc shell连接设备后执行。hidumper输出的是实时窗口状态，可能随窗口操作而变化，建议在问题发生时立即执行查询以获取准确信息。

## 1300002错误码的定位指导

错误码1300002表示窗口状态异常或窗口对象无效。

### 可能原因

- 窗口对象已被销毁，但代码仍在尝试使用该窗口
- 窗口处于不可操作状态（如已销毁、正在销毁）
- 窗口生命周期管理错误，如在销毁流程中调用getLastWindow()
- 异步任务在销毁后执行，访问已销毁的窗口对象

### 窗口销毁时调用getLastWindow崩溃

开发者在窗口销毁过程中（如onWindowStageDestroy、页面销毁等）调用[getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1)接口，导致应用崩溃。

**日志信息**

通过DevEco Studio或hdc查看崩溃日志：

```bash
hdc shell hilog | grep "1300002"
```

典型日志示例：

```
Error Name: Error
Error Message: This window state is abnormal
Error code: 1300002
Stack trace:
  at window.getLastWindow (WindowManagerService)
  at MyComponent.onWindowStageDestroy (MyAbility.ts:50)
```

关键信息：
- 错误码：1300002
- 堆栈：getLastWindow()调用位置
- 文件名和行号：定位具体代码位置（如MyAbility.ts第50行）

**分析定位**

**步骤1：查找getLastWindow调用位置**

```bash
grep -n "getLastWindow" src/**/*.ts
```

检查调用位置的上下文：
- 是否在onWindowStageDestroy中？
- 是否在aboutToDisappear中？
- 是否在setTimeout、Promise等异步回调中？

**步骤2：分析窗口生命周期**

窗口销毁流程：
```
窗口创建 → 窗口显示 → 窗口激活 → 窗口销毁开始 → 窗口资源释放 → 窗口对象无效
                                    ↑                    ↑
                               getLastWindow失效点     禁止访问点
```

关键结论：
- 窗口销毁开始后，getLastWindow()可能返回无效对象
- 窗口资源释放后，任何窗口操作都会触发1300002崩溃

**步骤3：使用hidumper验证窗口状态**

销毁前：
```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```
检查窗口是否存在、状态是否正常。

销毁后：
```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```
确认窗口已从列表中移除。

对比前后状态，确认销毁时机。

**错误示例**：

```ts
// 错误：在onWindowStageDestroy中调用getLastWindow
onWindowStageDestroy() {
    let lastWindow = window.getLastWindow(this.context);
    lastWindow.getWindowId(); // 1300002崩溃！
}

// 错误：销毁后异步调用getLastWindow
onWindowStageDestroy() {
    setTimeout(() => {
        let lastWindow = window.getLastWindow(this.context); // 崩溃
    }, 1000);
}
```

**解决步骤**

避免在销毁流程中调用getLastWindow()，不在以下位置调用：
- onWindowStageDestroy()
- aboutToDisappear()
- onDestroy()
- 窗口销毁回调中

正确示例：

```ts
// 正确：在窗口活跃时调用getLastWindow
onWindowStageCreate(windowStage: window.WindowStage) {
    let mainWindow = window.getLastWindow(this.context);
    mainWindow.loadContent('pages/MainPage');
}

onWindowStageDestroy() {
    // 销毁流程中不要调用getLastWindow，只做资源清理
    this.cleanupResources();
}
```

**检查清单**：

1. 找到所有getLastWindow()调用位置
2. 检查是否在销毁流程中调用（onWindowStageDestroy等）
3. 检查是否有异步任务在销毁后执行
4. 检查窗口对象引用是否在销毁时清空
5. 使用hidumper验证销毁前后窗口状态

> **说明：**
>
> 错误码1300002是窗口生命周期管理不当的典型错误。开发者应遵循"创建时缓存、活跃时使用、销毁时清理"的原则，避免在销毁流程中访问窗口。

## 超时警告WINDOW_EXCEPTION_DETECTION的定位指导

窗口异常检测日志用于监控窗口生命周期异常，常见异常类型包括伪冻屏/透明窗检测、窗口生命周期异常等。

**可能原因**

- 窗口创建后未在5秒内调用loadContent()或setUIContent()加载页面内容
- 异步操作耗时过长，超过超时阈值
- 先调用showWindow()显示窗口，再调用loadContent()加载内容
- 页面路径错误，导致加载失败

### setUIContent timeout（伪冻屏/透明窗检测）

窗口创建后未在规定时间内（5秒）加载页面内容，导致窗口显示为透明或冻结状态。

**日志信息**

```
MSG = SetUIContent timeout uid: [uid], windowName: [windowName], bundleName: [bundleName], abilityName: [abilityName]
```

关键信息：
- `uid`：用户ID
- `windowName`：窗口名
- `bundleName`：包名
- `abilityName`：实例名

**分析定位**

检查代码流程：
1. 是否在窗口创建后立即调用了loadContent()或setUIContent()
2. 是否在页面加载和窗口显示之间有耗时操作
3. 是否先调用showWindow()再调用loadContent()
4. 页面路径是否正确

错误示例：

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

**解决步骤**

确保窗口创建后立即加载页面内容，遵循正确调用顺序：先加载内容，后显示窗口。

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

**检查清单**：

1. 找到窗口创建代码，确认是否调用loadContent()或setUIContent()
2. 检查页面加载和窗口显示之间是否有耗时操作
3. 确认调用顺序：先loadContent()后showWindow()
4. 验证页面路径是否正确

> **说明：**
>
> 系统的超时检测机制是为了保障用户体验，避免用户长时间看到空白窗口。开发者应重视此警告并及时修复。
