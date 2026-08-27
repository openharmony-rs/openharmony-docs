# FusionFenceType（系统接口）

融合围栏类型采用二进制标记，该类型在使用时是将支持的围栏类型所在bit位置为1。例如支持GNSS和CELLULAR围栏，则值为0011（二进制），转换为十进制为3；全部四种围栏都支持，则值为1111（二进制），转换为十进制为15。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## GNSS

```TypeScript
GNSS = 1
```

四位二进制数的最低位，表示GNSS围栏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## CELLULAR

```TypeScript
CELLULAR = 2
```

四位二进制数由低到高的第二位，表示CELLULAR围栏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## WIFI

```TypeScript
WIFI = 4
```

四位二进制数由低到高的第三位，表示Wi-Fi围栏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## BLUETOOTH

```TypeScript
BLUETOOTH = 8
```

四位二进制数的最高位，表示蓝牙围栏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。
