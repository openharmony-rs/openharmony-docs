# @ohos.ability.screenLockFileManager

本模块提供锁屏下应用敏感数据保护的能力，支持申请和释放锁屏下应用敏感数据访问权限，以及查询敏感数据密钥的状态。当敏感数据密钥的引用计数归零，且屏幕被锁定达到系统配置的时长阈值后，密钥会被销毁，此时无法对该数据进行操作。这些密钥只有在屏幕解锁后才能恢复。通过调用本模块的[acquireAccess](arkts-ability-acquireaccess-f.md#acquireaccess-1)接口，可以防止密钥在屏幕被锁定达到系统配置的时长阈值后被销毁。

> **说明：**
>
> - 应用开启锁屏下敏感数据保护功能，需在[requestPermissions](../../../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)中配置权限ohos.permission.PROTECT_SCREEN_LOCK_DATA。

**起始版本：** 12

**系统能力：** SystemCapability.Security.ScreenLockFileManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [acquireAccess](arkts-ability-acquireaccess-f.md#acquireaccess-1) | 以同步方法申请调用方应用锁屏下敏感数据访问权限。申请成功后，敏感数据密钥的引用计数增加，防止密钥在屏幕被锁定达到系统配置的时长阈值后被销毁。该方法需与[releaseAccess](arkts-ability-releaseaccess-f.md#releaseaccess-1)配对使用。调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并通过[queryAppKeyState](arkts-ability-queryappkeystate-f.md#queryappkeystate-1)接口查询密钥状态为KEY_EXIST。 |
| [queryAppKeyState](arkts-ability-queryappkeystate-f.md#queryappkeystate-1) | 以同步方法查询调用方应用锁屏下敏感数据密钥的状态。 |
| [releaseAccess](arkts-ability-releaseaccess-f.md#releaseaccess-1) | 以同步方法释放调用方应用锁屏下敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当计数归零时，密钥可以在屏幕被锁定达到系统配置的时长阈值后被销毁。调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](arkts-ability-acquireaccess-f.md#acquireaccess-1)接口成功申请权限后才能使用。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [acquireAccess](arkts-ability-acquireaccess-f-sys.md#acquireaccess-2) | 以同步方法申请锁屏下指定类型的敏感数据访问权限。申请成功后，敏感数据密钥的引用计数增加，防止密钥在锁屏达到系统配置的时长阈值后被销毁。该方法需与[releaseAccess](arkts-ability-releaseaccess-f.md#releaseaccess-1)配对使用。调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并通过[queryAppKeyState](arkts-ability-queryappkeystate-f.md#queryappkeystate-1)接口查询密钥状态为KEY_EXIST。 |
| [queryAppKeyState](arkts-ability-queryappkeystate-f-sys.md#queryappkeystate-2) | 以同步方法查询锁屏下指定类型敏感数据密钥的状态。 |
| [releaseAccess](arkts-ability-releaseaccess-f-sys.md#releaseaccess-2) | 以同步方法释放锁屏下指定类型敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当引用计数归零时，密钥可以在锁屏达到系统配置的时长阈值后被销毁。调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](arkts-ability-acquireaccess-f.md#acquireaccess-1)接口成功申请权限后才能使用。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessStatus](arkts-ability-accessstatus-e.md) | 表示锁屏下敏感数据访问权限申请状态的枚举。 |
| [DataType](arkts-ability-datatype-e.md) | 表示锁屏下访问敏感数据类型的枚举。 |
| [KeyStatus](arkts-ability-keystatus-e.md) | 表示锁屏下敏感数据密钥状态的枚举。 |
| [ReleaseStatus](arkts-ability-releasestatus-e.md) | 表示锁屏下敏感数据访问权限释放状态的枚举。 |

