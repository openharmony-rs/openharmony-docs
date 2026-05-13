# 窗口开发常见日志问题与定位
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 使用窗口hidumper命令查看窗口信息定位问题

**hidumper**是OpenHarmony系统提供的诊断工具，可以实时查看系统中所有窗口的详细信息，帮助开发者快速定位窗口相关问题。窗口信息的dump分为两个层面：

#### hidumper参数说明

基本命令格式：
```bash
hdc shell hidumper -s WindowManagerService -a '<参数>'
```

**参数列表**：

| 参数 | 含义 | 命令示例 | 输出说明 |
|------|------|----------|----------|
| `-h` | 查看帮助信息 | `hidumper -s WindowManagerService -a '-h'` | 显示所有可用参数及说明 |
| `-a` | dump所有窗口信息 | `hidumper -s WindowManagerService -a '-a'` | 输出系统中所有窗口的列表、属性、焦点状态等完整信息 |
| `-w {WinId}` | dump指定窗口详细信息 | `hidumper -s WindowManagerService -a '-w 13'` | 输出WinId为13的窗口详细属性（可见性、焦点、隐私模式等） |
| `-w {WinId} {ArkUI option}` | dump指定窗口的ArkUI信息 | `hidumper -s WindowManagerService -a '-w 13 -arkui'` | 输出WinId为13窗口的ArkUI渲染详细信息 |
| `-c` | dump窗口截图信息 | `hidumper -s WindowManagerService -a '-c'` | 输出窗口截图相关信息 |
| `-p` | dump窗口树结构 | `hidumper -s WindowManagerService -a '-p'` | 输出窗口树结构，显示父子窗口关系 |
| `-b` | dump窗口绑定的信息 | `hidumper -s WindowManagerService -a '-b'` | 输出窗口绑定信息（如绑定的surface、buffer等） |
| `-v` | dump窗口可见性信息 | `hidumper -s WindowManagerService -a '-v'` | 输出窗口可见性详细信息 |

**参数使用场景**：

- **`-h`**：首次使用时查看完整参数说明
- **`-a`**：需要查看所有窗口时使用（最常用）
- **`-w {WinId}`**：已知窗口ID，需要查看特定窗口详细信息
- **`-w {WinId} {ArkUI option}`**：需要查看窗口UI渲染细节时
- **`-p`**：排查窗口父子关系、层级树结构时
- **`-v`**：排查窗口显示/隐藏问题时
- **`-c`、`-b`**：高级调试场景（截图、surface绑定等）

**常用参数组合示例**：

```bash
# 查看帮助
hdc shell hidumper -s WindowManagerService -a '-h'

# 查看所有窗口列表
hdc shell hidumper -s WindowManagerService -a '-a'

# 查看WinId=13的窗口详情
hdc shell hidumper -s WindowManagerService -a '-w 13'

# 查看窗口树结构
hdc shell hidumper -s WindowManagerService -a '-p'

# 查看窗口可见性
hdc shell hidumper -s WindowManagerService -a '-v'
```

#### 查看所有窗口列表

**查看所有窗口信息**：

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

输出中通过分隔线`---------------------------------------------------------------------------------------`区分前台窗口和后台窗口：

- **分隔线以上**：前台窗口（正在显示或可交互的窗口）
  - `SystemUi_NavigationB`、`SystemUi_PrivacyIndi`、`SystemUi_StatusBar`、`note0`、`EntryView`
  - 特征：`Flag=0`（显示状态），`ZOrd≥0`（参与层级竞争）
  - 这些窗口当前可见，用户可以看到或交互

- **分隔线以下**：后台窗口（隐藏或不在前台显示的窗口）
  - `SystemUi_VolumePanel`、`ScreenLockWindow`、`RecentView`、`SystemUi_DropdownPan`、`SystemUi_BannerNotic`、`mms0`、`camera0`
  - 特征：`Flag=1`（隐藏状态）或`ZOrd=-1`（隐藏层级）
  - 这些窗口当前不可见或不在前台显示，处于后台状态

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

**窗口类型（Type）详细说明**：

| Type值 | 含义 | 典型窗口 |
|--------|------|----------|
| `1` | 应用主窗口 | `note0`、`EntryView`等应用窗口 |
| `102` | 系统特定类型 | 系统UI窗口如状态栏、导航栏 |
| `2001` | 应用窗口基础类型 | `EntryView`桌面入口窗口 |
| `2108` | 系统主窗口 | `SystemUi_StatusBar`状态栏 |
| `2109` | 系统子窗口 | `SystemUi_DropdownPan`下拉面板 |
| `2110` | 模态窗口类型 | `ScreenLockWindow`锁屏窗口 |
| `2111` | 系统UI窗口类型 | `SystemUi_PrivacyIndi`隐私指示器、`SystemUi_VolumePanel`音量面板 |
| `2112` | 导航栏类型 | `SystemUi_NavigationB`导航栏 |
| `2115` | 屏幕管理窗口 | `RecentView`最近任务视图 |

**窗口模式（Mode）说明**：

- `1`：全屏模式（应用窗口常见）
- `102`：特定系统模式（系统UI窗口）

**状态标志位（Flag）说明**：

- `0`：窗口处于显示状态
- `1`：窗口处于隐藏状态

**层级关系（ZOrd）判断**：

根据ZOrd值判断窗口前后关系：
- `ZOrd=4`（SystemUi_NavigationB）：导航栏层级较高
- `ZOrd=3`（SystemUi_PrivacyIndi）：隐私指示器中间层
- `ZOrd=2`（SystemUi_StatusBar）：状态栏较低层
- `ZOrd=1`（note0）：应用窗口基础层
- `ZOrd=0`（EntryView）：桌面入口底层
- `ZOrd=-1`：特殊隐藏层级（不显示的窗口）

层级规则：数值越大越靠前显示，会覆盖数值较小的窗口。

#### 查看获焦窗口

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

#### 查看指定窗口详细信息

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

**关键字段详解**：

**VisibilityState（可见性状态）**

取值说明：
- `0`：窗口可见（前台显示）
- `1`：窗口不可见（隐藏或后台）

应用场景：
- 检查窗口是否正确显示
- 判断窗口是否被隐藏

**Focusable（可获焦状态）**

取值说明：
- `true`：窗口可以获焦，能接收键盘输入
- `false`：窗口不可获焦，不参与焦点竞争

典型场景：
- 幅通知窗口设置为`Focusable: false`，不打断用户输入
- 主窗口设置为`Focusable: true`，可以接收键盘输入

**IsPrivacyMode（隐私模式）**

取值说明：
- `false`：普通窗口，可以被截屏录屏
- `true`：隐私窗口，禁止截屏录屏（如银行应用、密码输入界面）

安全用途：
- 防止敏感信息被截屏泄露
- 金融类应用常用隐私模式

**isSnapshotSkip（截屏跳过标志）**

取值说明：
- `0`：允许截屏
- `1`：禁止截屏

与IsPrivacyMode类似，用于控制窗口是否可被截屏捕获。

**FirstFrameCallbackCalled（首帧回调）**

取值说明：
- `0`：首帧回调未调用，窗口未完成首帧绘制
- `1`：首帧回调已调用，窗口已完成首帧绘制

用途：
- 判断窗口是否已完成渲染启动
- 检测窗口启动性能问题（长时间未回调）

**DecoStatus（装饰状态）**

取值说明：
- `true`：窗口有装饰（标题栏、边框等）
- `false`：窗口无装饰（无边框窗口）

**TouchHotAreas（触摸热区）**

格式：`[ x, y, w, h ]`

说明：
- 定义窗口可响应触摸的区域
- 通常与WindowRect相同（整个窗口可触摸）
- 可以设置特定的触摸区域（如仅部分区域可交互）

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

**实用技巧**：

**技巧1：快速定位焦点窗口详情**

当Focus window: 13时，直接查看WinId=13的详细信息：

```bash
hdc shell hidumper -s WindowManagerService -a '-w 13'
```

确认Focusable=true，确保窗口可获焦。

**技巧2：排查隐私模式设置**

检查敏感窗口的隐私模式：

```bash
hdc shell hidumper -s WindowManagerService -a '-w <敏感窗口WinId>'
```

确认IsPrivacyMode=true，防止截屏泄露。

**技巧3：验证窗口显示状态**

检查窗口是否正确显示：

```bash
hdc shell hidumper -s WindowManagerService -a '-w <目标WinId>'
```

确认：
- VisibilityState=0（可见）
- Flag=0（显示状态）
- WindowRect尺寸正常

**技巧4：对比前后台窗口状态差异**

前台窗口（分隔线以上）的特征：
- VisibilityState: 0
- Flag: 0
- Focusable: true

后台窗口（分隔线以下）的特征：
- VisibilityState: 1
- Flag: 1
- Focusable可能为false

对比前后台窗口的详细信息，理解窗口状态切换。

#### 查看窗口ArkUI渲染信息

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

**关键字段详解**：

##### UINodeCount（UI节点数量）

含义：
- 表示窗口当前UI树中的节点总数
- 包括所有组件、容器、布局等UI元素
- 反映页面UI复杂度

应用场景：
- 性能优化：节点数过多会影响渲染性能
- UI复杂度分析：判断页面是否过于复杂
- 排查性能问题：节点数异常多可能导致卡顿

典型范围：
- 简单页面：50-100个节点
- 中等复杂度：100-300个节点
- 复杂页面：300+个节点（需要优化）

##### LastRequestVsyncTime（最后请求VSync时间）

含义：
- 表示窗口上次请求垂直同步的时间戳
- VSync用于同步渲染帧与显示器刷新
- 用于判断窗口渲染活跃度

应用场景：
- 判断窗口是否正在渲染更新
- 检测长时间未更新（时间戳过于陈旧）
- 性能分析：对比VSync请求频率

##### last vsyncId（最后VSync ID）

含义：
- 表示上次VSync的序列号ID
- 用于跟踪渲染帧序号
- 每次VSync都会生成新的ID

应用场景：
- 确认渲染帧是否持续更新
- 判断是否停止渲染（ID长时间不变）
- 调试帧同步问题

##### finishCount（完成计数）

含义：
- 表示当前未完成的渲染任务数量
- `[ ]`表示空，即没有未完成的渲染任务
- 数值表示待处理的渲染事务

应用场景：
- 判断是否有渲染任务堆积
- 检查渲染是否完成（空值表示完成）
- 性能排查：计数过多表示渲染压力

##### transactionFlags（事务标志）

含义：
- 表示渲染事务的标识信息
- `[进程ID, 标志位]`格式
- 用于标识渲染事务归属

应用场景：
- 确认渲染事务的来源进程
- 调试渲染事务同步问题

##### bundleName和moduleName

含义：
- `bundleName`：应用包名，标识窗口所属应用
- `moduleName`：模块名称，标识窗口所属模块

应用场景：
- 确认窗口归属的应用和模块
- 多应用多模块场景下的窗口识别
- 日志分析时关联应用信息

**常见问题定位**：

##### 问题1：UI渲染性能差（卡顿）

检查字段：
- `UINodeCount` 值过大（如500+）→ UI过于复杂，需要优化组件结构
- `finishCount` 有未完成任务 → 渲染任务堆积，可能UI更新过于频繁
- `LastRequestVsyncTime` 时间戳陈旧 → 窗口长时间未渲染更新

解决方案：
- 减少UI节点数量，简化组件结构
- 优化布局，避免嵌套过深
- 减少不必要的UI更新

##### 问题2：窗口停止渲染

检查字段：
- `last vsyncId` 长时间不变 → 渲染停止，可能窗口被隐藏或冻结
- `LastRequestVsyncTime` 时间戳过旧 → 未请求VSync，可能停止渲染

解决方案：
- 检查VisibilityState，确认窗口可见性
- 调用showWindow()或触发UI更新

##### 问题3：UI节点异常多

检查字段：
- `UINodeCount` 远超预期 → UI复杂度过高

典型对比：
- 正常页面：100个节点左右
- 异常页面：500+个节点，需要优化

解决方案：
- 简化UI结构，减少嵌套
- 使用懒加载、虚拟列表等优化技术
- 移除不必要的隐藏节点

##### 问题4：渲染任务堆积

检查字段：
- `finishCount` 有数值或非空 → 存在未完成的渲染任务

可能原因：
- UI更新过于频繁
- 渲染阻塞（如耗时计算）
- 性能瓶颈

解决方案：
- 减少UI更新频率
- 优化渲染逻辑
- 避免在渲染线程执行耗时操作

**实用技巧**：

##### 技巧1：快速判断UI复杂度

查看UINodeCount：
```bash
hdc shell hidumper -s WindowManagerService -a '-w 13 ArkUI option' | grep "UINodeCount"
```

根据节点数判断：
- `< 100`：简单页面
- `100-300`：中等复杂度
- `> 300`：需要优化

##### 技巧2：排查渲染停止问题

检查VSync相关字段：
```bash
hdc shell hidumper -s WindowManagerService -a '-w 13 ArkUI option' | grep -E "vsyncId|VsyncTime"
```

对比多次输出的vsyncId：
- ID持续增加 → 正常渲染
- ID不变 → 渲染停止，需要排查

##### 技巧3：对比前后台窗口渲染状态

前台窗口：
- UINodeCount正常，VSync持续更新

后台窗口：
- UINodeCount可能为0或很少
- VSync停止更新

对比前后台窗口的ArkUI信息，理解窗口渲染状态差异。

##### 技巧4：分析性能瓶颈

综合分析：
- UINodeCount + finishCount：UI复杂度和渲染压力
- LastRequestVsyncTime + vsyncId：渲染活跃度
- 多次dump对比，观察渲染状态变化

根据综合信息定位性能瓶颈点。

#### 分析窗口显示异常

**场景1：窗口不显示**

如果窗口不显示，检查以下字段：

```
mms0  0  18119  11  1  1  1  -1  0  [ 0  0  720  1208 ]
```

异常判断：
- `Flag=1`：窗口处于隐藏状态
- `ZOrd=-1`：层级为负，不参与显示
- 解决方案：调用showWindow()显示窗口，Flag应变为0，ZOrd变为正数

**场景2：窗口尺寸异常**

```
SystemUi_VolumePanel  0  1572  1  2111  1  0  -1  0  [ 0  0  0  0 ]
```

异常判断：
- `[ 0  0  0  0 ]`：窗口尺寸为0，不显示
- 可能是窗口创建但未设置大小，或窗口隐藏时尺寸清零

**场景3：窗口层级错误导致遮挡**

```
WindowName      ZOrd
note0           1    (应该显示但被遮挡)
SystemUi_StatusBar 2  (遮挡note0)
```

异常判断：
- 应用窗口ZOrd=1，系统UI窗口ZOrd=2
- 系统UI层级更高，可能遮挡应用窗口内容
- 正常情况：应用窗口应该有足够层级显示

可以快速找到应用的所有窗口及其ID。

**查看特定窗口ID的详细信息**：

```bash
hdc shell hidumper -s windowmanagerservice -a 'a' | grep -A 20 "window\[341\]"
```

输出示例：
```
window[341](0x5d2e43c0): type=MAIN_WINDOW, bundleName=com.example.app1
  rect=[0,0][1080,1920]
  visibility=true, drawn=true
  focusState=ACTIVE
  zOrder=100
  windowMode=WINDOW_MODE_FULLSCREEN
  orientation=UNSPECIFIED
  alpha=1.0
  turnScreenOn=false
  keepScreenOn=false
```

**详细属性说明**：

| 属性 | 含义 | 异常判断 |
|------|------|---------|
| `rect` | 窗口位置和大小 | 尺寸为0可能导致不显示 |
| `visibility` | 窗口可见性 | false表示窗口未显示或被隐藏 |
| `drawn` | 窗口绘制状态 | false表示窗口未绘制内容 |
| `focusState` | 焦点状态 | ACTIVE=获焦，INACTIVE=失焦 |
| `zOrder` | 层级 | 数值越大越靠前 |
| `windowMode` | 窗口模式 | FULLSCREEN/SPLIT/FLOATING |
| `orientation` | 旋转方向 | 确认窗口旋转策略 |
| `alpha` | 透明度 | 值越小越透明 |
| `turnScreenOn` | 是否点亮屏幕 | 对特定窗口有用 |
| `keepScreenOn` | 是否保持屏幕常亮 | 对特定窗口有用 |

### 定位问题的典型方法

#### 方法1：验证窗口创建和显示完整流程

**问题场景**：窗口创建后显示异常。

**定位步骤**：

1. Native侧确认窗口创建：
```bash
hidumper -s WindowManagerService | grep "com.example.myapp"
```

2. Native侧确认窗口属性：
```bash
hidumper -s WindowManagerService | grep -A 20 "WindowId: <目标ID>"
```
检查VisibilityState、WindowRect是否正常。

3. UI侧确认内容加载：
```bash
hidumper -s SceneBoard | grep -A 10 "WindowId: <目标ID>"
```
检查UIContentLoaded、RenderStatus。

#### 方法2：排查窗口层级遮挡问题

**问题场景**：窗口被遮挡或不显示。

**定位步骤**：

1. Native侧查看窗口树：
```bash
hidumper -s WindowManagerService
```
检查窗口的ZOrder和父子关系。

2. 确认遮挡原因：
   - ZOrder较小 → 被其他窗口遮挡
   - VisibilityState=INVISIBLE → 窗口被隐藏

#### 方法3：排查渲染性能问题

**问题场景**：窗口显示卡顿或帧率低。

**定位步骤**：

1. UI侧查看渲染状态：
```bash
hidumper -s SceneBoard | grep "WindowId: <目标ID>"
```

2. 分析性能指标：
   - FrameRate过低 → 页面性能问题，需要优化UI
   - UITreeDepth过深 → UI树复杂，考虑简化页面结构

### 实用技巧

#### 技巧1：对比窗口状态变化

```bash
# 操作前dump
hidumper -s WindowManagerService > native_before.txt
hidumper -s SceneBoard > ui_before.txt

# 执行操作（如显示窗口）

# 操作后dump
hidumper -s WindowManagerService > native_after.txt
hidumper -s SceneBoard > ui_after.txt

# 对比差异
diff native_before.txt native_after.txt
diff ui_before.txt ui_after.txt
```

#### 技巧2：快速定位特定应用

```bash
# Native侧按包名过滤
hidumper -s WindowManagerService | grep "com.example.myapp"

# UI侧需要先找到WindowId再查看
hidumper -s WindowManagerService | grep "com.example.myapp" | grep WindowId
# 然后用WindowId查询UI侧
hidumper -s SceneBoard | grep -A 10 "WindowId: <找到的ID>"
```

#### 技巧3：导出完整信息供分析

```bash
# 导出Native侧完整信息
hidumper -s WindowManagerService > window_native_dump.txt

# 导出UI侧完整信息
hidumper -s SceneBoard > window_ui_dump.txt
```

### 最佳实践

1. **分层面定位**：
   - 窗口属性问题 → 查看Native侧
   - 内容渲染问题 → 查看UI侧（SceneBoard）

2. **综合排查**：
   - 复杂问题同时查看两个层面
   - 对比两层面的信息一致性

3. **对比验证**：
   - 操作前后对比状态变化
   - 确认问题是否修复

4. **关注关键指标**：
   - Native侧：VisibilityState、ZOrder、WindowRect
   - UI侧：UIContentLoaded、RenderStatus、FrameRate

> **说明：**
>
> hidumper命令需要在设备或模拟器上执行，开发者可以通过hdc shell连接设备后执行。Native侧和UI侧的信息从不同维度反映窗口状态，建议开发者结合两个层面的信息综合分析问题。dump输出的是实时窗口状态，可能随窗口操作而变化，建议在问题发生时立即执行查询以获取准确信息。
```bash
hidumper -s WindowManagerService | grep -A 20 "WindowId: <目标窗口ID>"
```

2. 检查关键属性：
   - `VisibilityState`：
     - INVISIBLE → 窗口未调用showWindow()或被隐藏
     - VISIBLE → 窗口应该可见，检查内容是否加载
   - `WindowRect`：
     - 尺寸为0 → 窗口大小设置错误
     - 位置超出屏幕 → 窗口位置设置错误

3. 根据属性判断问题原因并修复

#### 方法3：排查焦点相关问题

**问题场景**：窗口无法获焦，或焦点切换不符合预期。

**定位步骤**：

1. 查看当前焦点窗口：
```bash
hidumper -s WindowManagerService | grep "FocusState: ACTIVE"
```

2. 检查目标窗口的焦点状态：
```bash
hidumper -s WindowManagerService | grep -A 10 "WindowId: <目标窗口ID>" | grep FocusState
```

3. 分析焦点状态：
   - 目标窗口FocusState为INACTIVE → 可能窗口不可获焦（setWindowFocusable(false)），或有其他窗口持有焦点
   - 多个窗口同时ACTIVE → 焦点管理异常，检查是否有多个屏幕组

#### 方法4：排查窗口遮挡问题

**问题场景**：窗口被其他窗口遮挡，或层级关系不符合预期。

**定位步骤**：

1. 查看所有窗口的ZOrder：
```bash
hidumper -s WindowManagerService | grep "ZOrder"
```

2. 分析层级关系：
   - 目标窗口ZOrder较小 → 被其他窗口遮挡，需要提升层级（调用raiseToAppTop()）
   - ZOrder异常 → 可能窗口类型层级设置错误

3. 检查父子窗口关系：
```bash
hidumper -s WindowManagerService | grep -A 30 "ParentWindowId"
```

### 实用技巧

#### 技巧1：实时监控窗口状态变化

在调试过程中，可以多次执行hidumper命令，对比窗口状态变化：

```bash
# 第一次查询
hidumper -s WindowManagerService > window_state1.txt

# 执行某个操作后再次查询
hidumper -s WindowManagerService > window_state2.txt

# 对比差异
diff window_state1.txt window_state2.txt
```

通过对比可以发现窗口状态的变化，定位操作是否生效。

#### 技巧2：结合应用包名快速定位

当系统中窗口较多时，直接搜索应用包名：

```bash
hidumper -s WindowManagerService | grep -A 50 "BundleName: com.example.myapp"
```

可以快速找到应用相关的所有窗口信息。

#### 技巧3：导出完整信息供分析

对于复杂问题，可以导出完整的窗口信息供离线分析：

```bash
hidumper -s WindowManagerService > window_dump.txt
```

然后在文本编辑器中详细分析窗口状态、属性、关系等。

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
   - FocusState：确认焦点状态
   - ZOrder：确认层级关系
   - WindowRect：确认窗口大小和位置

> **说明：**
>
> hidumper命令需要在设备或模拟器上执行，开发者可以通过hdc shell连接设备后执行。hidumper输出的是实时窗口状态，可能随窗口操作而变化，建议在问题发生时立即执行查询以获取准确信息。

## 1300002错误码的定位指导

**错误码1300002**表示窗口操作相关错误，常见于窗口生命周期管理不当、窗口已销毁但仍在使用等场景。

### 错误码含义

错误码1300002：窗口状态异常或窗口对象无效。

典型含义：
- 窗口对象已被销毁，但代码仍在尝试使用该窗口
- 窗口处于不可操作状态（如已销毁、正在销毁）
- 窗口生命周期管理错误

### 典型崩溃场景：destroy时调用getLastWindow崩溃

**问题描述**：

开发者在窗口销毁过程中（如onWindowStageDestroy、页面销毁等）调用[getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1)接口，导致应用崩溃，报错1300002。

**崩溃现象**：
- 应用突然退出或闪退
- 日志中出现错误码1300002
- 堆栈信息指向getLastWindow()调用位置

### 问题原因分析

#### 原因1：窗口已销毁，getLastWindow返回无效对象

**原理**：

getLastWindow()接口用于获取当前应用内层级最高的窗口。当窗口正在销毁或已销毁时，接口可能返回：
- null或undefined（无效对象）
- 已销毁的窗口对象（代理对象，实际资源已释放）

此时如果开发者直接使用返回值，会导致空指针或访问已释放资源，触发1300002错误。

**错误示例**：

```ts
// 错误：在onWindowStageDestroy中调用getLastWindow
onWindowStageDestroy() {
    // 窗口正在销毁，getLastWindow可能返回无效对象
    let lastWindow = window.getLastWindow(this.context);
    // 直接使用lastWindow，可能崩溃
    lastWindow.getWindowId(); // 1300002崩溃！
}
```

#### 原因2：时序问题——销毁时机早于getLastWindow调用

**原理**：

窗口销毁流程：
1. 触发销毁事件（如onWindowStageDestroy）
2. 系统开始销毁窗口资源
3. 窗口对象变为无效状态

如果在第2步或第3步调用getLastWindow()：
- 系统认为窗口已不可用
- 返回无效对象或抛出1300002错误

**错误示例**：

```ts
// 错误：销毁后异步调用getLastWindow
onWindowStageDestroy() {
    // 异步操作
    setTimeout(() => {
        // 此时窗口已销毁，getLastWindow崩溃
        let lastWindow = window.getLastWindow(this.context);
    }, 1000);
}
```

### 定位方法

#### 步骤1：查看崩溃日志和堆栈

**方法**：

通过DevEco Studio或hdc查看崩溃日志：

```bash
# 查看应用崩溃日志
hdc shell hilog | grep "1300002"
```

或查看DevEco Studio的FaultLog。

**关键信息**：
- 错误码：1300002
- 堆栈：getLastWindow()调用位置
- 文件名和行号：定位具体代码位置

**典型日志示例**：
```
Error Name: Error
Error Message: This window state is abnormal
Error code: 1300002
Stack trace:
  at window.getLastWindow (WindowManagerService)
  at MyComponent.onWindowStageDestroy (MyAbility.ts:50)
```

根据堆栈信息，定位到MyAbility.ts第50行。

#### 步骤2：检查代码调用时机

**检查点**：

在崩溃位置检查：
- 是否在销毁流程中调用getLastWindow()
- 调用时机是否在窗口销毁之后
- 是否有异步任务在销毁后执行

**具体检查**：

1. 查找getLastWindow()调用位置：
```bash
grep -n "getLastWindow" src/**/*.ts
```

2. 检查调用位置的上下文：
   - 是否在onWindowStageDestroy中？
   - 是否在aboutToDisappear中？
   - 是否在setTimeout、Promise等异步回调中？

#### 步骤3：分析窗口生命周期

**方法**：

绘制窗口生命周期流程图，明确各个阶段的窗口状态：

```
窗口创建 → 窗口显示 → 窗口激活 → 窗口销毁开始 → 窗口资源释放 → 窗口对象无效
                                    ↑                    ↑
                               getLastWindow失效点     禁止访问点
```

关键结论：
- 窗口销毁开始后，getLastWindow()可能返回无效对象
- 窗口资源释放后，任何窗口操作都会1300002崩溃

#### 步骤4：使用hidumper验证窗口状态

**方法**：

在销毁流程前后，使用hidumper查看窗口列表：

**销毁前**：
```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```
检查窗口是否存在、状态是否正常。

**销毁后**：
```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```
确认窗口已从列表中移除。

对比前后状态，确认销毁时机。

### 解决方案

#### 方案1：避免在销毁流程中调用getLastWindow

**正确做法**：

不要在以下位置调用getLastWindow()：
- onWindowStageDestroy()
- aboutToDisappear()
- onDestroy()
- 窗口销毁回调中

**正确示例**：

```ts
// 正确：在窗口活跃时调用getLastWindow
onWindowStageCreate(windowStage: window.WindowStage) {
    // 窗口创建后，可以安全调用
    let mainWindow = window.getLastWindow(this.context);
    console.log('Main window created:', mainWindow.getWindowId());
}

onWindowStageDestroy() {
    // 销毁流程中不要调用getLastWindow
    // 只做资源清理工作
    this.cleanupResources();
}
```

#### 方案2：使用窗口对象缓存而非getLastWindow

**原理**：

在窗口创建时缓存窗口对象，销毁时清空引用，避免销毁时重新获取。

**正确示例**：

```ts
// 正确：缓存窗口对象，销毁时清空
let mainWindow: window.Window | null = null;

onWindowStageCreate(windowStage: window.WindowStage) {
    // 创建时缓存窗口对象
    windowStage.getMainWindow((err, win) => {
        if (!err.code) {
            mainWindow = win; // 缓存引用
        }
    });
}

aboutToAppear() {
    // 使用缓存的窗口对象
    if (mainWindow) {
        mainWindow.showWindow();
    }
}

aboutToDisappear() {
    // 销毁时清空引用
    mainWindow = null;
}

onWindowStageDestroy() {
    // 销毁时清空引用
    mainWindow = null;
}
```

**优点**：
- 避免销毁时调用getLastWindow
- 通过null判断确保安全
- 生命周期管理清晰

#### 方案3：添加有效性检查

**原理**：

调用getLastWindow()后，检查返回值是否有效，避免直接使用。

**正确示例**：

```ts
// 正确：检查窗口有效性
let lastWindow = window.getLastWindow(this.context);

// 添加有效性检查
if (lastWindow && lastWindow.isWindowValid()) {
    // 确认窗口有效后才使用
    lastWindow.showWindow();
} else {
    // 窗口无效，跳过操作
    console.warn('Window is invalid, skip operation');
}
```

**注意**：
- isWindowValid()为伪代码，实际使用窗口属性检查
- 结合VisibilityState、WinId等字段判断有效性

#### 方案4：取消销毁时的异步任务

**原理**：

确保销毁时所有异步任务都被取消，避免异步回调访问已销毁窗口。

**正确示例**：

```ts
// 正确：销毁时取消异步任务
let fetchDataPromise = null;

aboutToAppear() {
    // 记录异步任务
    fetchDataPromise = fetchData();
    
    fetchDataPromise.then(() => {
        // 检查窗口是否还有效
        if (this.isWindowActive()) {
            this.updateUI();
        }
    });
}

aboutToDisappear() {
    // 销毁时取消异步任务（如果支持）
    if (fetchDataPromise && fetchDataPromise.cancel) {
        fetchDataPromise.cancel();
    }
    
    // 或使用标志位控制
    this.isDestroyed = true;
}

updateUI() {
    // 异步回调中检查销毁标志
    if (this.isDestroyed) {
        return; // 已销毁，不执行操作
    }
    
    // 正常执行UI更新
}
```

#### 方案5：正确理解getLastWindow的使用时机

**使用时机**：

getLastWindow()适合在以下场景使用：
- 窗口创建后，获取主窗口对象
- 窗口活跃期间，查询当前最前窗口
- 需要操作应用窗口时（非销毁流程）

**不适合的场景**：
- 窗口销毁流程中
- 窗口已隐藏或后台时
- 异步回调中（销毁可能已完成）

**最佳实践**：

```ts
// 最佳实践：在合适的时机使用getLastWindow
onWindowStageCreate(windowStage: window.WindowStage) {
    // ✅ 正确：创建后获取窗口
    let mainWindow = window.getLastWindow(this.context);
    mainWindow.loadContent('pages/MainPage');
}

onActive() {
    // ✅ 正确：窗口活跃时操作
    let lastWindow = window.getLastWindow(this.context);
    if (lastWindow) {
        lastWindow.showWindow();
    }
}

onWindowStageDestroy() {
    // ❌ 错误：销毁时不要调用getLastWindow
    // let lastWindow = window.getLastWindow(this.context); // 不要这样做！
    
    // ✅ 正确：只做清理工作
    this.cleanup();
}
```

### 检查清单

开发者排查1300002崩溃时，按以下清单检查：

**代码检查**：
1. ✅ 找到所有getLastWindow()调用位置
2. ✅ 检查是否在销毁流程中调用（onWindowStageDestroy等）
3. ✅ 检查是否有异步任务在销毁后执行
4. ✅ 检查窗口对象引用是否在销毁时清空
5. ✅ 检查是否有多个销毁事件重叠

**生命周期检查**：
1. ✅ 确认getLastWindow调用时机在窗口活跃期间
2. ✅ 确认销毁流程不包含窗口操作
3. ✅ 确认异步任务有销毁时取消机制
4. ✅ 确认窗口对象缓存和清理正确

**日志检查**：
1. ✅ 查看崩溃堆栈，定位getLastWindow调用位置
2. ✅ 查看错误码1300002的完整错误信息
3. ✅ 对比销毁前后窗口列表变化
4. ✅ 确认窗口销毁时机与getLastWindow调用时机的关系

### 最佳实践总结

**避免1300002崩溃的核心原则**：

1. **时机原则**：不要在销毁流程中调用getLastWindow()

2. **缓存原则**：窗口创建时缓存对象，销毁时清空引用

3. **异步原则**：销毁时取消异步任务，或检查销毁标志

4. **有效性原则**：使用窗口前检查有效性

5. **生命周期原则**：明确窗口生命周期边界，合理规划调用时机

**推荐的窗口管理流程**：

```ts
// 推荐流程示例
class MyAbility extends UIAbility {
    private mainWindow: window.Window | null = null;
    private isDestroyed: boolean = false;
    
    // 创建阶段：缓存窗口对象
    onWindowStageCreate(windowStage: window.WindowStage) {
        this.isDestroyed = false;
        
        windowStage.getMainWindow((err, win) => {
            if (!err.code) {
                this.mainWindow = win;
                this.mainWindow.loadContent('pages/MainPage');
            }
        });
    }
    
    // 活跃阶段：使用缓存的窗口对象
    onForeground() {
        if (this.mainWindow && !this.isDestroyed) {
            this.mainWindow.showWindow();
        }
    }
    
    // 销毁阶段：只做清理，不调用getLastWindow
    onWindowStageDestroy() {
        this.isDestroyed = true;
        this.mainWindow = null;
        this.cleanupResources();
    }
    
    // 异步任务：检查销毁标志
    async fetchData() {
        const data = await api.fetch();
        
        // 检查是否已销毁
        if (this.isDestroyed) {
            return; // 已销毁，不继续操作
        }
        
        // 使用窗口对象前再次检查
        if (this.mainWindow) {
            this.updateUI(data);
        }
    }
}
```

> **说明：**
>
> 错误码1300002是窗口生命周期管理不当的典型错误。开发者应遵循"创建时缓存、活跃时使用、销毁时清理"的原则，避免在销毁流程中访问窗口。合理管理窗口引用和异步任务，可有效防止此类崩溃。

## 1300004错误码的定位指导
### xxxx

## 超时警告WINDOW_EXCEPTION_DETECTION的定位指导

窗口异常检测日志是系统用于监控窗口生命周期异常的工具，帮助开发者及时发现和定位窗口相关问题。常见的异常类型包括：伪冻屏/透明窗检测、窗口生命周期异常等。

### 伪冻屏/透明窗检测（setUIContent timeout）

#### 什么是setUIContent timeout

**setUIContent timeout**（设置UI内容超时）是指在窗口创建后，开发者未在规定时间内（通常为5秒）调用[loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)或[setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9)接口加载页面内容，导致窗口显示为透明或冻结状态。

该问题通常表现为：
- 窗口创建后显示为透明或空白
- 窗口无法响应用户交互
- 用户视觉上看到"卡住"或"冻结"的现象
- 系统日志中出现`WINDOW_EXCEPTION_DETECTION`警告

#### 检测原理

系统在窗口创建时会启动一个定时器，监控窗口的页面加载过程：

1. **窗口创建阶段**：系统创建窗口实例，初始化窗口属性
2. **内容加载监控**：启动定时器，等待开发者调用loadContent()或setUIContent()接口
3. **超时判断**：如果在5秒内未完成页面内容加载，系统判定为异常
4. **日志上报**：记录`WINDOW_EXCEPTION_DETECTION`警告日志，帮助开发者定位问题

检测机制的目的是避免用户长时间看到空白或透明的窗口，影响用户体验。

#### 常见原因

开发者遇到setUIContent timeout问题时，通常由以下原因导致：

- **忘记调用loadContent/setUIContent接口**：创建窗口后遗漏了页面加载步骤
- **异步操作耗时过长**：在窗口创建和页面加载之间执行耗时操作（如网络请求、大量计算），超过5秒超时阈值
- **错误的加载顺序**：先调用showWindow()显示窗口，再调用loadContent()加载内容
- **页面路径错误**：提供的页面路径不存在，导致加载失败

**错误示例**：

```ts
// 错误：创建窗口后未加载内容
windowStage.createSubWindow('subWindow', (err, windowClass) => {
    if (err.code) {
        console.error('Failed to create sub window.');
        return;
    }
    // 缺失：未调用loadContent或setUIContent加载页面
    windowClass.showWindow(); // 直接显示窗口，导致透明窗
});
```

**正确示例**：

```ts
// 正确：创建窗口后立即加载内容
windowStage.createSubWindow('subWindow', (err, windowClass) => {
    if (err.code) {
        console.error('Failed to create sub window.');
        return;
    }
    // 先加载页面内容
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

#### 定位方法

当开发者发现`setUIContent`日志警告时，可按以下步骤定位问题：

##### 步骤1：查看日志内容

日志中会包含详细的异常信息，例如：

```
MSG = SetUIContent timeout uid: [uid], windowName: [windowName], bundleName: [bundleName], abilityName: [abilityName]
```

关键信息：
- `uid`：用户id
- `windowName`：窗口名
- `bundleName`：包名
- `abilityName`：实例名

##### 步骤2：检查代码流程

对照异常窗口的创建流程，检查：
1. 是否在窗口创建后立即调用了loadContent()或setUIContent()
2. 是否在页面加载和窗口显示之间有耗时操作
3. 是否先调用showWindow()再调用loadContent()
4. 页面路径是否正确

#### 解决方案

确保窗口创建后立即加载页面内容，并遵循正确的调用顺序：先加载内容，后显示窗口。

```ts
// 正确做法：窗口创建后立即加载内容
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

#### 最佳实践

为避免setUIContent timeout问题，建议开发者遵循以下最佳实践：

1. **立即加载原则**：窗口创建后立即调用loadContent()或setUIContent()，确保在5秒内完成页面加载

2. **正确调用顺序**：先加载页面内容，再显示窗口，避免用户看到透明窗口

3. **异步操作时机**：将耗时异步操作放在页面加载完成后执行，不在窗口创建和页面加载之间阻塞

4. **日志跟踪**：在关键节点添加日志，便于问题定位和排查

> **说明：**
>
> 系统的超时检测机制是为了保障用户体验，避免用户长时间看到空白窗口。开发者应重视此警告并及时修复，确保应用窗口能够快速、正确地显示内容。

## 1300012错误码的定位指导
