# @ohos.security.cryptoFramework

提供统一的密码算法库加解密接口，以屏蔽底层硬件和算法库。

**起始版本：** 9

<!--Device-unnamed-declare namespace cryptoFramework--><!--Device-unnamed-declare namespace cryptoFramework-End-->

**系统能力：** SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createasykeygenerator-f.md#createasykeygenerator) | 通过指定算法名称的字符串，获取相应的非对称密钥生成器实例。  支持的规格详见[非对称密钥生成和转换规格](docroot://security/CryptoArchitectureKit/crypto-asym-key-generation-conversion-spec.md)。 |
| [createAsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec) | 指定密钥参数，获取AsyKeyGeneratorBySpec非对称密钥生成器实例。 |
| [createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md#createcipher) | 通过指定算法名称，获取相应的[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例。 |
| [createKdf](arkts-cryptoarchitecture-cryptoframework-createkdf-f.md#createkdf) | 密钥派生函数（key derivation function）实例生成。 |
| [createKem](arkts-cryptoarchitecture-cryptoframework-createkem-f.md#createkem) | 创建一个用于密钥封装和解封装操作的KEM实例。 |
| [createKeyAgreement](arkts-cryptoarchitecture-cryptoframework-createkeyagreement-f.md#createkeyagreement) | 生成KeyAgreement实例。 |
| [createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md#createmac) | 生成Mac实例，用于消息认证码的计算与操作。  支持的规格详见[HMAC消息认证码算法规格](docroot://security/CryptoArchitectureKit/crypto-compute-mac-overview.md)。 |
| [createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md#createmac-1) | 生成Mac实例，用于进行消息认证码的计算与操作。  支持的规格详见[MAC消息认证码算法规格](docroot://security/CryptoArchitectureKit/crypto-compute-mac-overview.md)。 |
| [createMd](arkts-cryptoarchitecture-cryptoframework-createmd-f.md#createmd) | 生成Md实例，用于进行消息摘要的计算与操作。  支持的规格详见[MD消息摘要算法规格](docroot://security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#支持的算法与规格)。 |
| [createRandom](arkts-cryptoarchitecture-cryptoframework-createrandom-f.md#createrandom) | 生成Random实例，用于进行随机数的计算与设置种子。 |
| [createSign](arkts-cryptoarchitecture-cryptoframework-createsign-f.md#createsign) | 生成Sign实例。 |
| [createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator) | 通过指定算法名称获取相应的对称密钥生成器实例。  支持的规格详见[对称密钥生成和转换规格](docroot://security/CryptoArchitectureKit/crypto-sym-key-generation-conversion-spec.md)。 |
| [createVerify](arkts-cryptoarchitecture-cryptoframework-createverify-f.md#createverify) | 生成Verify实例。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [DHKeyUtil](arkts-cryptoarchitecture-cryptoframework-dhkeyutil-c.md) | 根据素数P的长度和私钥长度（bit位数）生成DH公共密钥参数。 |
| [ECCKeyUtil](arkts-cryptoarchitecture-cryptoframework-ecckeyutil-c.md) | 提供ECC密钥参数生成和基于指定椭圆曲线的点转换工具。 |
| [SM2CryptoUtil](arkts-cryptoarchitecture-cryptoframework-sm2cryptoutil-c.md) | 用于SM2密码学运算的工具类。 |
| [SignatureUtils](arkts-cryptoarchitecture-cryptoframework-signatureutils-c.md) | 用于ECC/SM2签名数据转换的工具类。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AeadParamsSpec](arkts-cryptoarchitecture-cryptoframework-aeadparamsspec-i.md) | 用于AEAD（带附加数据的认证加密）对称加解密的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法参数，继承自[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)。  适用于[AES算法](docroot://security/CryptoArchitectureKit/crypto-sym-encrypt-decrypt-spec.md#aes)的CCM和GCM分组模式。适用于[SM4算法](docroot://security/CryptoArchitectureKit/crypto-sym-encrypt-decrypt-spec.md#sm4)的GCM分组模式。适用于[ChaCha20-Poly1305算法](docroot://security/CryptoArchitectureKit/crypto-sym-encrypt-decrypt-spec.md#chacha20)分组模式。 |
| [AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md) | 非对称密钥生成器。在使用该类的方法前，需要先使用[createAsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createasykeygenerator-f.md#createasykeygenerator-1)方法构建一个AsyKeyGenerator实例。 |
| [AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md) | AsyKeyGeneratorBySpec非对称密钥生成器。在使用该类的方法前，需要先使用[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法构建一个AsyKeyGeneratorBySpec实例。 |
| [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) | 指定非对称密钥参数的基本接口，用于创建密钥生成器。在指定非对称密钥参数时需要构造其子类对象，并将子类对象传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。构造子类对象时，除了RSA密钥采用小端写法外，其他bigint类型的密钥参数均采用大端写法，并使用正数。 |
| [CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md) | 加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，封装使用CCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证标签。它是[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法的参数。  适用于CCM模式。 |
| [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) | 提供加解密的算法操作功能，按序调用本类中的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)、[update()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#update-1)、[doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal-1)方法，可以实现对称加密/对称解密/非对称加密/非对称解密。  完整的加解密流程示例可参考[开发指南](docroot://security/CryptoArchitectureKit/crypto-encryption-decryption-overview.md)。  一次完整的加/解密流程在对称加密和非对称加密中略有不同：  - 对称加解密：init为必选，update为可选（且允许多次update加/解密大数据），doFinal为必选；doFinal结束后可以重新init开始新一轮加/解密流程。  - RSA、SM2非对称加解密：init为必选，不支持update操作，doFinal为必选（允许连续多次doFinal加/解密大数据）；RSA不支持重复init，切换加解密模式或填充方式时，需要重新创建Cipher对象。 |
| [CmacSpec](arkts-cryptoarchitecture-cryptoframework-cmacspec-i.md) | 消息认证码参数[MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)的子类，作为CMAC计算的输入。 |
| [DHCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dhcommonparamsspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DH算法中公私钥包含的公共参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DHKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-dhkeypairspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DH算法中公私钥包含的全量参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DHPriKeySpec](arkts-cryptoarchitecture-cryptoframework-dhprikeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DH算法中私钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DHPubKeySpec](arkts-cryptoarchitecture-cryptoframework-dhpubkeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DH算法中公钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DSACommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dsacommonparamsspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DSA算法中公私钥包含的公共参数，随机生成公/私钥。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DSAKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-dsakeypairspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DSA算法中公私钥包含的全量参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DSAPubKeySpec](arkts-cryptoarchitecture-cryptoframework-dsapubkeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定DSA算法中公钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 二进制数据的封装接口，核心字段data为Uint8Array类型。 |
| [ECCCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-ecccommonparamsspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定ECC算法中公私钥包含的公共参数，随机生成公/私钥。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [ECCKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-ecckeypairspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定ECC算法中公私钥包含的全量参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [ECCPriKeySpec](arkts-cryptoarchitecture-cryptoframework-eccprikeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定ECC算法中私钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [ECCPubKeySpec](arkts-cryptoarchitecture-cryptoframework-eccpubkeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定ECC算法中公钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md) | 指定椭圆曲线的域类型。当前只支持Fp域。 |
| [ECFieldFp](arkts-cryptoarchitecture-cryptoframework-ecfieldfp-i.md) | 指定椭圆曲线的素数域。是[ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md)的子类。 |
| [ED25519KeyPairSpec](arkts-cryptoarchitecture-cryptoframework-ed25519keypairspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定Ed25519算法中公私钥包含的全量参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [ED25519PriKeySpec](arkts-cryptoarchitecture-cryptoframework-ed25519prikeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定Ed25519算法中私钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [ED25519PubKeySpec](arkts-cryptoarchitecture-cryptoframework-ed25519pubkeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定Ed25519算法中公钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [EccSignatureSpec](arkts-cryptoarchitecture-cryptoframework-eccsignaturespec-i.md) | 包含（r、s）的ECC/SM2签名数据的对象。 |
| [GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md) | 加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，封装使用GCM AEAD模式进行加密或解密的参数，需要IV、AAD和认证标签。它是[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法的参数。  适用于GCM模式。 |
| [HKDFSpec](arkts-cryptoarchitecture-cryptoframework-hkdfspec-i.md) | 密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为HKDF密钥派生函数进行密钥派生时的输入。 |
| [HmacSpec](arkts-cryptoarchitecture-cryptoframework-hmacspec-i.md) | 消息认证码参数[MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md)的子类，作为HMAC计算的输入。 |
| [IvParamsSpec](arkts-cryptoarchitecture-cryptoframework-ivparamsspec-i.md) | 加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法的参数。  适用于CBC、CTR、OFB、CFB这些需要iv作为参数的加解密模式。 |
| [Kdf](arkts-cryptoarchitecture-cryptoframework-kdf-i.md) | 密钥派生函数（key derivation function）类，使用密钥派生方法之前需要创建该类的实例进行操作，通过createKdf(algName: string): Kdf方法构造此实例。 |
| [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | 密钥派生函数参数，使用密钥派生函数进行密钥派生时，需要构建其子类对象并作为输入。 |
| [Kem](arkts-cryptoarchitecture-cryptoframework-kem-i.md) | 提供KEM密钥封装和解封装操作的API。 |
| [KemEncapResult](arkts-cryptoarchitecture-cryptoframework-kemencapresult-i.md) | KEM封装结果。 |
| [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | 密钥（父类），在运行密码算法（如加解密）时需要提前生成其子类对象，并传入[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法。  密钥通过子类密钥生成器来生成，详见子类描述。具体子类有：[SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md)、[PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md)、[PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md)。 |
| [KeyAgreement](arkts-cryptoarchitecture-cryptoframework-keyagreement-i.md) | KeyAgreement类，使用密钥协商方法之前需要创建该类的实例进行操作，通过[createKeyAgreement(algName: string): KeyAgreement](arkts-cryptoarchitecture-cryptoframework-createkeyagreement-f.md#createkeyagreement-1)方法构造此实例。 |
| [KeyEncodingConfig](arkts-cryptoarchitecture-cryptoframework-keyencodingconfig-i.md) | RSA私钥编码参数，使用获取私钥字符串时，可以添加此参数，生成指定算法、密码的编码后的私钥字符串。 |
| [KeyPair](arkts-cryptoarchitecture-cryptoframework-keypair-i.md) | 非对称密钥对包含公钥和私钥。  可以通过非对称密钥生成器[AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md)、[AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md)来生成。 |
| [Mac](arkts-cryptoarchitecture-cryptoframework-mac-i.md) | Mac类，调用Mac方法进行消息认证码（Message Authentication Code）计算。调用前，需要通过[createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md#createmac-1)构造Mac实例。 |
| [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md) | 消息认证码参数，计算HMAC或CMAC时，需要构建子类对象并作为输入参数。 |
| [Md](arkts-cryptoarchitecture-cryptoframework-md-i.md) | Md类，调用Md方法进行消息摘要（Message Digest）计算。调用前，需要通过[createMd](arkts-cryptoarchitecture-cryptoframework-createmd-f.md#createmd-1)构造Md实例。 |
| [PBKDF2Spec](arkts-cryptoarchitecture-cryptoframework-pbkdf2spec-i.md) | 密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为PBKDF2密钥派生函数进行密钥派生时的输入。 |
| [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) | 加解密参数，在进行对称加解密时需要构造其子类对象，并将子类对象传入[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法。  适用于需要iv等参数的对称加解密模式（对于无iv等参数的模式如ECB模式，无需构造，在[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)中传入null即可）。 |
| [Point](arkts-cryptoarchitecture-cryptoframework-point-i.md) | 指定椭圆曲线上的一个点。 |
| [Poly1305ParamsSpec](arkts-cryptoarchitecture-cryptoframework-poly1305paramsspec-i.md) | 加解密参数[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，封装使用ChaCha20-Poly1305 AEAD模式进行加密或解密的参数，需要nonce、AAD和认证标签。它是[ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md)的子类，用于在对称加解密时作为[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法的参数。  适用于[ChaCha20-Poly1305](docroot://security/CryptoArchitectureKit/crypto-sym-encrypt-decrypt-spec.md#chacha20)。 |
| [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 私钥，是[Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)的子类，在非对称解密、签名、密钥协商时需要将其作为输入使用。  私钥可以通过非对称密钥生成器[AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md)、[AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md)来生成。 |
| [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | 公钥，是[Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)的子类，在非对称加密、签名验证、密钥协商时需要将其对象作为输入使用。  公钥可以通过非对称密钥生成器[AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md)、[AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md)来生成。 |
| [RSACommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-rsacommonparamsspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定RSA算法中公私钥包含的公共参数，随机生成公/私钥。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [RSAKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-rsakeypairspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定RSA算法中公私钥包含的全量参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [RSAPubKeySpec](arkts-cryptoarchitecture-cryptoframework-rsapubkeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定RSA算法中公钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [Random](arkts-cryptoarchitecture-cryptoframework-random-i.md) | Random类，调用Random方法生成随机数。调用前，需要通过[createRandom](arkts-cryptoarchitecture-cryptoframework-createrandom-f.md#createrandom-1)构造Random实例。 |
| [SM2CipherTextSpec](arkts-cryptoarchitecture-cryptoframework-sm2ciphertextspec-i.md) | SM2密文参数，使用SM2密文格式转换函数进行格式转换时，需要用到此对象。可以通过指定此参数，生成符合国密标准的ASN.1格式的SM2密文，反之，也可以从ASN.1格式的SM2密文中获取具体参数。 |
| [ScryptSpec](arkts-cryptoarchitecture-cryptoframework-scryptspec-i.md) | 密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为SCRYPT密钥派生函数进行密钥派生时的输入。 |
| [Sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md) | Sign类，使用Sign方法之前需要创建该类的实例进行操作，通过[createSign(algName: string): Sign](arkts-cryptoarchitecture-cryptoframework-createsign-f.md#createsign-1)方法构造此实例。按序调用本类中的init、update、sign方法完成签名操作。签名操作的示例代码详见[签名验签开发指导](docroot://security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1.md)。  Sign类不支持重复初始化，当业务方需要使用新密钥签名时，需要重新创建新Sign对象并调用init初始化。  业务方使用时，调用createSign接口确定签名的模式，调用init接口设置密钥。  当待签名数据长度较短时，可在初始化后直接调用sign接口传入数据进行签名，无需调用update。  当待签名数据较长时，可通过update接口分段传入切分后的原文数据，最后调用sign接口对整体原文数据进行签名。  当使用update分段传入原文时，sign接口API 10之前只支持传入DataBlob， API 10之后增加支持null。业务方可在循环中调用update接口，循环结束后调用sign进行签名。  使用DSA算法签名时，如果摘要算法设置为NoHash，则不支持update操作，调用update接口将返回错误码ERR_CRYPTO_OPERATION。 |
| [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | 对称密钥，是[Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)的子类，在对称加解密时需要将其对象传入[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法使用。  对称密钥通过对称密钥生成器[SymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md)来生成。 |
| [SymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md) | 对称密钥生成器。  在使用该类的方法前，先使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)构建SymKeyGenerator实例。 |
| [Verify](arkts-cryptoarchitecture-cryptoframework-verify-i.md) | Verify类，使用Verify方法之前需要创建该类的实例进行操作，通过[createVerify(algName: string): Verify](arkts-cryptoarchitecture-cryptoframework-createverify-f.md#createverify-1)方法构造此实例。按序调用本类中的init、update、verify方法完成签名操作。验签操作的示例代码详见[签名验签开发指导](docroot://security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1.md)。  Verify类不支持重复初始化，当业务方需要使用新密钥验签时，需要重新创建新Verify对象并调用init初始化。  业务方使用时，在createVerify时确定验签的模式，调用init接口设置密钥。  当被签名的消息较短时，可在init初始化后，（无需update）直接调用verify接口传入被签名的消息和签名（signatureData）进行验签。  当被签名的消息较长时，可通过update接口分段传入被签名的消息，最后调用verify接口对消息全文进行验签。verify接口的data入参在API 10之前只支持DataBlob， API 10之后增加支持null。业务方可在循环中调用update接口，循环结束后调用verify传入签名（signatureData）进行验签。  当使用DSA算法进行验签，并设置了摘要算法为NoHash时，则不支持update操作，update接口会返回错误码ERR_CRYPTO_OPERATION。 |
| [X25519KeyPairSpec](arkts-cryptoarchitecture-cryptoframework-x25519keypairspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定X25519算法中公私钥包含的全量参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [X25519PriKeySpec](arkts-cryptoarchitecture-cryptoframework-x25519prikeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定X25519算法中私钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [X25519PubKeySpec](arkts-cryptoarchitecture-cryptoframework-x25519pubkeyspec-i.md) | 密钥参数[AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md)的子类，用于指定X25519算法中公钥包含的参数。  在使用密钥参数生成密钥时，将其传入[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法创建密钥生成器。 |
| [X963KdfSpec](arkts-cryptoarchitecture-cryptoframework-x963kdfspec-i.md) | 密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)的子类，作为X963KDF密钥派生函数进行密钥派生时的输入。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AsyKeyDataItem](arkts-cryptoarchitecture-cryptoframework-asykeydataitem-e.md) | 表示非对称密钥数据项类型的枚举。 |
| [AsyKeySpecItem](arkts-cryptoarchitecture-cryptoframework-asykeyspecitem-e.md) | 表示密钥参数的枚举。 |
| [AsyKeySpecType](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md) | 表示密钥参数类型的枚举。 |
| [CipherSpecItem](arkts-cryptoarchitecture-cryptoframework-cipherspecitem-e.md) | 表示加解密参数的枚举。这些参数支持通过[setCipherSpec](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#setcipherspec-1)接口设置，通过[getCipherSpec](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#getcipherspec-1)接口获取。  当前只支持RSA算法和SM2算法，从API version 11开始，增加对SM2_MD_NAME_STR参数的支持，详细规格请参考[加解密规格](docroot://security/CryptoArchitectureKit/crypto-asym-encrypt-decrypt-spec.md)。  API version 10-11 系统能力为 SystemCapability.Security.CryptoFramework；从 API version 12 开始为SystemCapability.Security.CryptoFramework.Cipher |
| [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | 枚举加密和解密的密码操作模式。 |
| [KemAlgNameId](arkts-cryptoarchitecture-cryptoframework-kemalgnameid-e.md) | 枚举KEM算法名称ID。 |
| [Result](arkts-cryptoarchitecture-cryptoframework-result-e.md) | 表示执行结果的枚举。 |
| [SignSpecItem](arkts-cryptoarchitecture-cryptoframework-signspecitem-e.md) | 表示签名验签参数的枚举。这些参数支持通过[setSignSpec](arkts-cryptoarchitecture-cryptoframework-sign-i.md#setsignspec-1)、[setVerifySpec](arkts-cryptoarchitecture-cryptoframework-verify-i.md#setverifyspec-1)接口设置，通过[getSignSpec](arkts-cryptoarchitecture-cryptoframework-sign-i.md#getsignspec-1)、[getVerifySpec](arkts-cryptoarchitecture-cryptoframework-verify-i.md#getverifyspec-1)接口获取。  当前只支持RSA算法和SM2算法，从API version 11开始，增加对SM2_USER_ID_UINT8ARR参数的支持，详细规格请参考[签名验签规格](docroot://security/CryptoArchitectureKit/crypto-sign-sig-verify-overview.md)。 |

