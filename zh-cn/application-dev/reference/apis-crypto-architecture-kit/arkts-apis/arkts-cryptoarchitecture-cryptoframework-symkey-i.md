# SymKey

对称密钥，是[Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)的子类，在对称加解密时需要将其对象传入[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-4)方法使用。

对称密钥通过对称密钥生成器[SymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md)来生成。

**继承/实现关系：** SymKey extends [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)

**起始版本：** 9

<!--Device-cryptoFramework-interface SymKey extends Key--><!--Device-cryptoFramework-interface SymKey extends Key-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## clearMem

```TypeScript
clearMem(): void
```

同步方法，将系统底层内存中的密钥数据清零。建议在不再使用对称密钥实例时调用此函数，避免密钥数据在内存中存留过久。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKey-clearMem(): void--><!--Device-SymKey-clearMem(): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGenerateAesKeyFun() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
  let key = await symKeyGenerator.generateSymKey();
  let encodedKey = key.getEncoded();
  console.info('key blob: '+ encodedKey.data);
  key.clearMem();
  encodedKey = key.getEncoded();
  console.info('key blob：' + encodedKey.data);
}

```

