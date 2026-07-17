# SM2CipherTextSpec

SM2密文参数，使用SM2密文格式转换函数进行格式转换时，需要用到此对象。可以通过指定此参数，生成符合国密标准的ASN.1格式的SM2密文，反之，也可以从ASN.1格式的SM2密文中获取具体参数。

> **说明：**  
>  
> - hashData为使用SM3算法对明文数据运算得到的杂凑值，其长度固定为256位。  
>  
> - cipherTextData是与明文等长的密文。  
>  
> - 在拼接生成C1C3C2格式的密文时，如果x分量（C1_X）或y分量（C1_Y）的长度不足32字节，需要在高位补0，使得x分量和y分量的长度均为32字节。

**起始版本：** 12

<!--Device-cryptoFramework-interface SM2CipherTextSpec--><!--Device-cryptoFramework-interface SM2CipherTextSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## cipherTextData

```TypeScript
cipherTextData: Uint8Array
```

密文数据，也称为C2。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SM2CipherTextSpec-cipherTextData: Uint8Array--><!--Device-SM2CipherTextSpec-cipherTextData: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## hashData

```TypeScript
hashData: Uint8Array
```

哈希值，也称为C3。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SM2CipherTextSpec-hashData: Uint8Array--><!--Device-SM2CipherTextSpec-hashData: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## xCoordinate

```TypeScript
xCoordinate: bigint
```

x分量。

**类型：** bigint

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SM2CipherTextSpec-xCoordinate: bigint--><!--Device-SM2CipherTextSpec-xCoordinate: bigint-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## yCoordinate

```TypeScript
yCoordinate: bigint
```

y分量，也称为C1y。

**类型：** bigint

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SM2CipherTextSpec-yCoordinate: bigint--><!--Device-SM2CipherTextSpec-yCoordinate: bigint-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

