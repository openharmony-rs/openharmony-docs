# InstallParam（系统接口）

安装、恢复或卸载时需要指定的参数。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [InstallParam](arkts-ability-installparam-i-sys.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## installFlag

```TypeScript
installFlag: number
```

指示安装标志, 默认值：1。 </br>取值范围：</br>1: 覆盖安装。</br>16: 免安装。

**类型：** number

**默认值：** Indicates the install flag

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [installFlag](arkts-ability-installparam-i-sys.md#installflag)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## isKeepData

```TypeScript
isKeepData: boolean
```

指示应用卸载时是否保留包数据，默认值：false，true表示保留，false表示不保留。

**类型：** boolean

**默认值：** Indicates whether the param has data

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isKeepData](arkts-ability-installparam-i-sys.md#iskeepdata)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId: number
```

指示用户id, 默认值：调用方的userId。

**类型：** number

**默认值：** Indicates the user id

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [userId](arkts-ability-installparam-i-sys.md#userid)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

