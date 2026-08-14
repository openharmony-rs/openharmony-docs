# @ohos.graphics.colorSpaceManager(色彩管理)

/*
 Copyright (C) 2022-2023 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace colorSpaceManager--><!--Device-unnamed-declare namespace colorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkgraphics2d-colorspacemanager-create-f.md#create) | 创建标准色域对象。 |
| [create](arkts-arkgraphics2d-colorspacemanager-create-f.md#create) | 创建用户自定义色域对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | 当前色域对象实例。 下列API示例中都需先使用[create()](arkts-arkgraphics2d-colorspacemanager-create-f.md#create)获取到ColorSpaceManager实例，再通过此实例调用对应方法。 |
| [ColorSpacePrimaries](arkts-arkgraphics2d-colorspacemanager-colorspaceprimaries-i.md) | 色域标准三原色（红、绿、蓝）和白色，基于现实世界的色度，使用(x, y)表示其在色彩空间中的位置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | 色域类型枚举。 |

