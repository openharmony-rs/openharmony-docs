# @ohos.ability.screenLockFileManager(锁屏敏感数据管理)

/*
 Copyright (C) 2024-2026 Huawei Device Co., Ltd.
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

<!--Device-unnamed-declare namespace screenLockFileManager--><!--Device-unnamed-declare namespace screenLockFileManager-End-->

**系统能力：** SystemCapability.Security.ScreenLockFileManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md#acquireAccess) | 以同步方法申请调用方应用锁屏下敏感数据访问权限。申请成功后，敏感数据密钥的引用计数增加，防止密钥在屏幕被锁定达到系统配置的时长阈值后被销毁。该方法需与[releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md#releaseAccess)配对使用。 调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并通过[queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f.md#queryAppKeyState)接口查询密钥状态为KEY_EXIST。 |
| [queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f.md#queryAppKeyState) | 以同步方法查询调用方应用锁屏下敏感数据密钥的状态。 |
| [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md#releaseAccess) | 以同步方法释放调用方应用锁屏下敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当计数归零时，密钥可以在屏幕被锁定达到系统配置的时长阈值后被销毁。 调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md#acquireAccess)接口成功申请权限后才能使用。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f-sys.md#acquireAccess（系统接口）) | 以同步方法申请锁屏下指定类型的敏感数据访问权限。申请成功后，敏感数据密钥的引用计数增加，防止密钥在锁屏达到系统配置的时长阈值后被销毁。该方法需与[releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f.md#releaseAccess)配对使用。 调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并通过[queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f.md#queryAppKeyState)接口查询密钥状态为KEY_EXIST。 |
| [queryAppKeyState](arkts-ability-screenlockfilemanager-queryappkeystate-f-sys.md#queryAppKeyState（系统接口）) | 以同步方法查询锁屏下指定类型敏感数据密钥的状态。 |
| [releaseAccess](arkts-ability-screenlockfilemanager-releaseaccess-f-sys.md#releaseAccess（系统接口）) | 以同步方法释放锁屏下指定类型敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当引用计数归零时，密钥可以在锁屏达到系统配置的时长阈值后被销毁。 调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md#acquireAccess)接口成功申请权限后才能使用。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessStatus](arkts-ability-screenlockfilemanager-accessstatus-e.md) | 表示锁屏下敏感数据访问权限申请状态的枚举。 |
| [DataType](arkts-ability-screenlockfilemanager-datatype-e.md) | 表示锁屏下访问敏感数据类型的枚举。 |
| [KeyStatus](arkts-ability-screenlockfilemanager-keystatus-e.md) | 表示锁屏下敏感数据密钥状态的枚举。 |
| [ReleaseStatus](arkts-ability-screenlockfilemanager-releasestatus-e.md) | 表示锁屏下敏感数据访问权限释放状态的枚举。 |

