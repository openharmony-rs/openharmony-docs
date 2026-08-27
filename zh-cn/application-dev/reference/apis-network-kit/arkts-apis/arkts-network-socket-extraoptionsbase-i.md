# ExtraOptionsBase

Socket套接字的基础属性。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## receiveBufferSize

```TypeScript
receiveBufferSize?: number
```

接收缓冲区大小（单位：Byte），取值范围0~262144，不设置或设置的值超过取值范围则会默认为8192。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack

## reuseAddress

```TypeScript
reuseAddress?: boolean
```

是否重用地址。true：重用地址；false：不重用地址。默认值为false。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack

## sendBufferSize

```TypeScript
sendBufferSize?: number
```

发送缓冲区大小（单位：Byte），取值范围0~262144，不设置或设置的值超过取值范围则会默认为8192。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack

## socketTimeout

```TypeScript
socketTimeout?: number
```

套接字超时时间，单位毫秒（ms）。默认值为0，表示不设置超时时间。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack
