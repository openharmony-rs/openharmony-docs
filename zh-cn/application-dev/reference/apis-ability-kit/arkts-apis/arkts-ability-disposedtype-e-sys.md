# DisposedType（系统接口）

标识拦截应用程序的方式，例如禁用应用的全部能力、禁用应用的指定能力、或者不禁用。

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## BLOCK_APPLICATION

```TypeScript
BLOCK_APPLICATION = 1
```

应用所有能力都将被禁用。

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## BLOCK_ABILITY

```TypeScript
BLOCK_ABILITY = 2
```

应用指定的能力才会被禁用。

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## NON_BLOCK

```TypeScript
NON_BLOCK = 3
```

应用所有能力不会被禁用。

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

