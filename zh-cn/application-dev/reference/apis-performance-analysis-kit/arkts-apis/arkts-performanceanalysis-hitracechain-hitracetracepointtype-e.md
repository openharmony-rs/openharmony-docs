# HiTraceTracepointType

跟踪埋点类型枚举。用于标识业务流程中的关键节点，例如CS和CR用于标记客户端请求的发送和接收，SS和SR用于标记服务端请求的接收和发送，GENERAL用 于标记无法归入上述四种场景的其他关键节点。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hiTraceChain-enum HiTraceTracepointType--><!--Device-hiTraceChain-enum HiTraceTracepointType-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## CS

```TypeScript
CS = 0
```

客户端发送(Client Send)。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceTracepointType-CS = 0--><!--Device-HiTraceTracepointType-CS = 0-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## CR

```TypeScript
CR = 1
```

客户端接收(Client Receive)。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceTracepointType-CR = 1--><!--Device-HiTraceTracepointType-CR = 1-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## SS

```TypeScript
SS = 2
```

服务端发送(Server Send)。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceTracepointType-SS = 2--><!--Device-HiTraceTracepointType-SS = 2-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## SR

```TypeScript
SR = 3
```

服务端接收(Server Receive)。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceTracepointType-SR = 3--><!--Device-HiTraceTracepointType-SR = 3-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## GENERAL

```TypeScript
GENERAL = 4
```

通用类型，标识CS、CR、SS、SR四种场景之外的埋点。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceTracepointType-GENERAL = 4--><!--Device-HiTraceTracepointType-GENERAL = 4-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

