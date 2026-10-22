# GPU graphic接口快速接入指导文档

## 概述

### 背景

L1图形栈对应用提供BaseGfxEngine引擎接口，全部接口由SoftEngine **软件实现兜底**（不接入GPU功能也完整，仅性能损失）；芯片厂商通过**适配**的硬件加速实现获得性能收益。



### 接入后效果

| 接口状态       | 绘制路径                         | 效果                   |
| -------------- | -------------------------------- | ---------------------- |
| 未适配（默认） | CPU软绘（SoftEngine）           | 功能正常，性能一般     |
| 已适配         | GPU硬件加速 → 失败自动回落软绘 | 性能提升，功能始终完整 |

> **容错原则**：未实现对应接口仅降低绘制性能，不阻断设备接入；已实现的接口绘制失败时自动回落软件路径。

## 接入总览

```text
第一步【必选】HDI 层：实现 GfxFuncs 函数表
        → Fill/Blit 两条系统既有通路立即获得硬件加速
第二步【可选】引擎层：继承 SoftEngine override 扩展加速接口
        → DrawLine/DrawLetter/DrawArc/DrawRect 等高频接口按需加速
第三步【必选】产品集成：编译配置与启用
        → 宏开关与 buffer 物理地址（phyAddr）前提确认
```

> **HDI层** = drivers/peripheral/display驱动接口层；**引擎层** = foundation/arkui/ui_lite图形引擎层。

## 第一步：HDI层适配

### 要实现什么

实现drivers/peripheral/display/interfaces/include/display_gfx.h定义的GfxFuncs函数表，并通过GfxInitialize导出。

### 函数表实现（L1场景）

| 接口                                    | 是否必须 | 说明                                                                                                          |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------- |
| InitGfx / DeinitGfx                 | **必须** | 函数表"入场券"：系统GfxEngines::InitDriver() 对InitGfx做空检查与调用检查，缺失则整张函数表被拒收          |
| FillRect                              | **必须** | 矩形填充加速；系统侧经GfxEngines::GfxFillArea转调（引擎层Fill通路）                                    |
| DrawRectangle                         | 暂不实现 | L1系统侧当前无转调通路，实现后暂无法被调用                                     |
| DrawLine                              | 暂不实现 | L1系统侧当前无转调通路，实现后暂无法被调用                                     |
| DrawCircle                            | 暂不实现 | L1系统侧当前无转调通路，实现后暂无法被调用                                     |
| Blit                                  | **必须** | 位块搬运加速（含缩放/格式转换）；系统侧经GfxEngines::GfxBlit转调 |
| Sync                                  | 暂不实现 | L1系统侧当前无调用方                                                                                         |

### 交付形态

1. 在自家display HAL中实现上述函数 + GfxInitialize(GfxFuncs**) 出口；
2. 编译为display接口库，**替换系统默认空桩实现**（drivers/peripheral/display/hal/default/display_gfx.c，其GfxInitialize将 *funcs置为NULL）；
3. 系统启动时自动完成注册：设备引擎注册 → GfxEngines::InitDriver() → GfxInitialize() 取表 → InitGfx() 初始化GPU。

### 前提条件

| 前提                           | 说明                                                                                                                                                  |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| buffer物理地址（phyAddr）有效 | 硬件路径要求目标/源buffer具备有效物理地址；phyAddr == nullptr时系统判空自动回落软绘。由display层既有分配机制保障，接入方需确认自家分配路径满足 |
| 失败语义                       | 硬件实现返回失败时**必须保证未写入任何像素**（系统据此安全回落软绘）；不得部分写入后返回失败                                                        |

## 第二步：引擎层扩展加速（可选）

### SoftEngine接口功能总表

> 来源：foundation/arkui/ui_lite/interfaces/innerkits/engines/gfx/soft_engine.h
> 角色：SoftEngine : BaseGfxEngine，L1图形栈软件绘制实现（CPU光栅化），全部引擎接口的兜底方。

| 接口 | 功能分类 | 作用 | 关键参数/数据 | 备注 |
|---|---|---|---|---|
| DrawLine | 基础绘制 | 绘制直线段 | 起点/终点、裁剪掩码、线宽、颜色、透明度 | 基础图元 |
| DrawArc | 基础绘制 | 绘制圆弧/椭圆弧（含扇形边线） | 圆心/半径/角度、样式、线帽 | 圆角矩形圆角实现的核心依赖；draw_rect.cpp高频复用 |
| DrawRect | 基础绘制 | 绘制矩形/圆角矩形（填充或描边） | 矩形、脏区、样式（含圆角半径/描边）、透明度 | 样式驱动填充或描边 |
| DrawCubicBezier | 基础绘制 | 绘制三次贝塞尔曲线 | 起点/终点、两个控制点、线宽、颜色、透明度 | 用于曲线动画/路径 |
| DrawPath | 路径绘制 | 路径描边（沿矢量路径轮廓绘制） | 路径数据、Paint、失效区 | 矢量图元 |
| FillPath | 路径绘制 | 路径填充（填充矢量路径内部区域） | 同上 | 矢量图元 |
| DrawLetter | 文字绘制 | 绘制单个字符（位图字库方式） | 字形位图、字形矩形、字重、颜色、透明度 | 双重重载：另一版使用LetterDataInfo |
| DrawLetterPath | 文字绘制 | 绘制矢量字形轮廓（支持几何变换） | LetterPathDataInfo、变换矩阵 | 用于旋转/缩放文字 |
| DrawLetterPathWithClip | 文字绘制 | 绘制带裁剪区域的矢量字形 | 同上 + 裁剪矩形 | 用于单行省略号等截断场景 |
| DrawTransform | 图像变换 | 图像变换绘制（旋转/缩放/镜像/模糊） | 目标位置、变换矩阵、变换数据（含算法/模糊级别） | 图标/图片动画核心接口 |
| ClipCircle | 裁剪 | 设置圆形裁剪区 | 圆心、半径 | 后续绘制仅在圆内可见 |
| ClipScreenShape | 裁剪 | 设置屏幕形状裁剪 | 位置与宽高 | 适配圆角矩形屏/圆形手表屏 |
| Blit | 像素搬运/填充 | 位块搬运（源buffer复制到目标，支持混合） | 目标点、源buffer、子区域、BlendOption | 窗口合成上屏的核心操作；对应GfxFuncs::Blit硬件通路 |
| Fill | 像素搬运/填充 | 区域填充（纯色 + 透明度） | 填充区、颜色、透明度 | 大面积填充GPU收益最高；Hi3516唯一硬件加速实证接口；对应GfxFuncs::FillRect硬件通路 |
| AllocBuffer | 缓冲管理 | 分配图形缓冲 | 大小、用途标识 | 软件实现为内存分配；硬件引擎可override为显存/物理连续内存 |
| FreeBuffer | 缓冲管理 | 释放图形缓冲 | 缓冲指针、用途标识 | 须与AllocBuffer同一后端配对释放 |

### 实现模式（参考Hi3516GfxEngine）

```cpp
// 1. 继承 SoftEngine（获得全部引擎接口的软件兜底实现）
class HiXXGfxEngine : public SoftEngine {
public:
    void DrawLine(BufferInfo& dst, ...) override;   // 只 override 要加速的接口
};

// 2. override 实现：硬件优先，失败回落
void HiXXGfxEngine::DrawLine(BufferInfo& dst, ...) {
    if (/* 自家 GPU 可处理的条件 */) {
        if (/* 调自家 GPU 库绘制成功 */) {
            return;
        }
    }
    SoftEngine::DrawLine(dst, ...);   // 必须保留：兜底回落
}

// 3. 注册（库加载时自动生效）
__attribute__((constructor)) void RegisterHiXXGfxEngine() {
    BaseGfxEngine::InitGfxEngine(new HiXXGfxEngine());
}
```

### 规则与约束

| 规则                     | 说明                                                                                                                                                                                                                                                                                                         |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 只override要加速的接口 | 未override的接口自动继承SoftEngine软实现，无需重复开发                                                                                                                                                                                                                                                   |
| **失败必须回落（强制）** | SoftEngine::Xxx(...) 调用是每个override的必备尾巴；硬件实现返回失败时不得部分写入像素。**结构性要求**：若绘制调用链为全void设计，失败将无法传回引擎层——驱动/渲染入口必须以**错误码**向上暴露失败，引擎层才可检测并触发回落；**仅记录日志不算兜底**（样本实证：存在底层记日志后直接丢弃绘制的实现） |
| 注意注册互斥             | 若产品同时编译了其他设备引擎（如系统仓hi3516_engine.cpp），多个constructor注册时**后注册生效**，集成时须确保仅保留本厂引擎（裁剪或构建排除）                                                                                                                                                              |
| 引擎代码归属             | 建议放置于vendor/&lt;厂商&gt;/ 自家目录                                                                                                                                                                                                                                        |
| 硬件尺寸/粒度约束        | 厂商2D引擎普遍存在单次操作尺寸/粒度上限，override实现需将大区域切片分次提交（各产品阈值不同）；切片失败同样必须回落软实现                                                                                                                                                                                 |
| 通路选择自由             | Fill/Blit为**双通路接口**：既可经系统标准通路（GfxEngines → GfxFuncs），也可在引擎层override中直驱自家加速接口；规范只统一语义层，不约束内部通路选择                                                                                                                                         |

## 适配指导：新设备接入流程

### 适配目录结构

新设备接入时，需要在以下目录创建适配代码：

```text
vendor/<厂商>/<产品>/
├── config.json                    # 产品配置文件
├── hdf_config/                    # HDF 配置
│   └── lcd/
│       └── lcd_config.hcs         # LCD 面板配置
└── graphic/
    ├── BUILD.gn                   # 编译配置
    ├── <产品>_engine.h            # 引擎头文件
    └── <产品>_engine.cpp          # 引擎实现
```

### 参考实现：Hi3516GfxEngine

Hi3516GfxEngine是系统提供的参考实现，以内嵌方式编译在ui_lite中，源码位于：
- foundation/arkui/ui_lite/frameworks/engines/gfx/hi3516/hi3516_engine.h
- foundation/arkui/ui_lite/frameworks/engines/gfx/hi3516/hi3516_engine.cpp

> 参考实现直接编进 //foundation/arkui/ui_lite:ui，并非独立组件。厂商若按独立组件集成，需自行维护BUILD.gn与config.json。

### 实现步骤

#### 步骤1：创建引擎类

在vendor/&lt;厂商&gt;/&lt;产品&gt;/graphic/ 目录下创建引擎类：

```cpp
// vendor/<厂商>/<产品>/graphic/<产品>_engine.h
#ifndef VENDOR_<厂商>_<产品>_ENGINE_H
#define VENDOR_<厂商>_<产品>_ENGINE_H

#include "engines/gfx/soft_engine.h"

namespace OHOS {

class <产品>GfxEngine : public SoftEngine {
public:
    <产品>GfxEngine() = default;
    ~<产品>GfxEngine() override = default;

    // 只 override 要加速的接口
    void Fill(BufferInfo& dst, const Rect& fillArea, const ColorType color, const OpacityType opacity) override;
    void DrawLine(BufferInfo& dst, const Point& start, const Point& end, const Rect& mask,
                  int16_t width, ColorType color, OpacityType opacity) override;
    // ... 其他需要加速的接口
};

} // namespace OHOS
#endif // VENDOR_<厂商>_<产品>_ENGINE_H
```

#### 步骤2：实现引擎类

```cpp
// vendor/<厂商>/<产品>/graphic/<产品>_engine.cpp
#include "<产品>_engine.h"

namespace OHOS {

void <产品>GfxEngine::Fill(BufferInfo& dst, const Rect& fillArea, const ColorType color, const OpacityType opacity)
{
    if (/* 自家 GPU 可处理的条件 */) {
        if (/* 调自家 GPU 库填充成功 */) {
            return;
        }
    }
    SoftEngine::Fill(dst, fillArea, color, opacity);  // 必须保留：兜底回落
}

void <产品>GfxEngine::DrawLine(BufferInfo& dst, const Point& start, const Point& end, const Rect& mask,
                              int16_t width, ColorType color, OpacityType opacity)
{
    if (/* 自家 GPU 可处理的条件 */) {
        if (/* 调自家 GPU 库绘制成功 */) {
            return;
        }
    }
    SoftEngine::DrawLine(dst, start, end, mask, width, color, opacity);  // 必须保留：兜底回落
}

} // namespace OHOS
```

#### 步骤3：注册引擎

```cpp
// vendor/<厂商>/<产品>/graphic/<产品>_engine.cpp
__attribute__((constructor)) void Register<产品>GfxEngine()
{
    BaseGfxEngine::InitGfxEngine(new <产品>GfxEngine());
}
```

#### 步骤4：配置编译

在vendor/&lt;厂商&gt;/&lt;产品&gt;/graphic/BUILD.gn中添加编译配置：

```gn
# vendor/<厂商>/<产品>/graphic/BUILD.gn
import("//build/lite/config/component/lite_component.gni")

lite_component("<产品>_gfx_engine") {
  sources = [
    "<产品>_engine.cpp",
  ]

  include_dirs = [
    "//foundation/arkui/ui_lite/interfaces/innerkits",
    "//foundation/arkui/ui_lite/interfaces/kits",
    "//foundation/graphic/graphic_utils_lite/interfaces/innerkits",
  ]

  deps = [
    "//foundation/arkui/ui_lite:ui_lite",
    "//foundation/graphic/graphic_utils_lite:utils_lite",
  ]
}
```

#### 步骤5：集成到产品

在vendor/&lt;厂商&gt;/&lt;产品&gt;/config.json中添加编译配置：

```json
{
  "subsystems": [
    {
      "subsystem": "arkui",
      "components": [
        {
          "component": "ui_lite",
          "features": []
        },
        {
          "component": "<产品>_gfx_engine",
          "features": []
        }
      ]
    }
  ]
}
```

> 若使用自定义subsystem，需先在build/lite/config/subsystem中注册该subsystem。

### 编译命令

```bash
python3 build.py -p <产品>@<厂商> --gn-flags "linux_kernel_version=linux-5.10"
```

### 验证结果

编译成功后，引擎实现会链接到ui_lite产物中（参考实现Hi3516GfxEngine即以内嵌方式编译进ui_lite）。若按独立组件集成，产物路径取决于具体构建配置，建议以实际out目录为准。

### 注意事项

1. **注册互斥**：若产品同时编译了其他设备引擎（如系统仓hi3516_engine.cpp），多个constructor注册时**后注册生效**，集成时须确保仅保留本厂引擎（裁剪或构建排除）。
2. **失败必须回落**：SoftEngine::Xxx(...) 调用是每个override的必备尾巴；硬件实现返回失败时不得部分写入像素。
3. **硬件尺寸/粒度约束**：厂商2D引擎普遍存在单次操作尺寸/粒度上限，override实现需将大区域切片分次提交（各产品阈值不同）；切片失败同样必须回落软实现。

