# 地址数据捐赠错误码
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @weixin_40768329-->
<!--Designer: @CynthiaYeh-->
<!--Tester: @logic42; @zhaofangyuan-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 36900001 接口内部错误

**错误信息**

Internal error in the API.

**错误描述**

系统服务内部发生错误。

**可能原因**

系统服务内部状态异常或系统错误（如空指针、内存不足、系统服务异常重启、IPC异常等）。

**处理步骤**

尝试重新调用接口；如问题持续存在，可提示用户重启应用、升级应用或升级设备版本。

## 36900002 订阅失败

**错误信息**

Subscription failed.

**错误描述**

调用[onDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress)接口订阅地址数据更新事件失败时，系统会产生此错误码。

**可能原因**

已订阅成功后，未取消订阅，再次调用订阅接口。

**处理步骤**

如业务需要重新订阅，请先调用[offDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress)取消订阅，再调用[onDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress)订阅；否则可直接忽略该错误，已订阅成功的业务不受影响。

## 36900003 取消订阅失败

**错误信息**

Unsubscription failed.

**错误描述**

调用[offDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress)接口取消订阅地址数据更新事件失败时，系统会产生此错误码。

**可能原因**

在未成功订阅的情况下，直接调用取消订阅接口。

**处理步骤**

调用[onDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressondatafabricaddress)订阅成功后，再调用[offDataFabricAddress](js-apis-data-dataFabricAddress-sys.md#datafabricaddressoffdatafabricaddress)取消订阅。

## 36900004 操作不支持

**错误信息**

Operation not supported.

**错误描述**

调用接口时，若传入的参数格式正确但条件不满足，系统会产生此错误码。

**可能原因**

1. 目前仅支持通勤导航场景，当传入的场景类型不是通勤导航场景时，会产生此错误码。

2. 订阅或更新操作时，若场景类型为通勤导航场景且传入的家与公司的距离小于配置支持的最小距离，会产生此错误码。

3. 更新操作时，若当前尚未订阅，会产生此错误码。

**处理步骤**

1. 将场景类型配置为通勤导航场景（目前仅支持该场景）。

2. 确保传入的家与公司的距离不小于配置支持的最小距离。该距离默认值为1000米，可通过云推配置调整为其他值。

3. 若执行更新操作，请先调用订阅接口成功订阅后，再执行更新。

## 36900005 参数错误

**错误信息**

Invalid parameter.

**错误描述**

调用接口时，传入的参数无效，系统会产生此错误码。

**可能原因**

1. 枚举类型的参数超出枚举范围。

2. 坐标的经纬度值超出范围。

3. 参考点的数量超出限制或不符合业务场景要求。

**处理步骤**

1. 检查枚举类型参数是否超出枚举范围。

2. 检查坐标经纬度是否有效：经度在-180°~180°范围内、纬度在-90°~90°范围内。

3. 检查参考点数量是否在[0, 128]范围内，且符合业务场景要求：通勤导航场景必须为2个参考点。
