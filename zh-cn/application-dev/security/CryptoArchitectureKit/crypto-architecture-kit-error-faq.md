# 算法库加解密失败返回错误码17630001

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

开发者使用加解密算法库经常遇到报错17630001，下文将对其失败原因进行详细分析。

## AES-GCM算法

**问题现象**

AES-GCM解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> 建议开发者使用update接口加密数据，最后调用doFinal接口完成本次加密，获取tag。
>
> 建议开发者使用update接口解密数据，最后调用doFinal接口完成本次解密，doFinal接口内将会对tag进行验证，若失败，接口会抛出异常。

**可能原因**

doFinal失败，表示校验tag失败，解密输入的tag和解密过程中计算的tag不一致。解密输入的key、iv、aad、tag和ciphertext，任意一个不正确，都会导致该报错。

1. key不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

2. iv不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

3. aad不正确，update得到的明文正确，doFinal失败，即校验tag失败。

4. ciphertext不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

5. tag不正确，update得到的明文正确，doFinal失败，即校验tag失败。

**解决措施**

确认加密和解密的key、iv和aad参数一致，确保解密时输入的ciphertext和tag是正确的。

## AES-CBC算法

**问题现象**

解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> AES-CBC属于块加密算法，因此需要使用到填充算法PKCS7，将明文填充至块大小整数倍。
>
> 解密时，doFinal接口会对padding进行校验。

**可能原因**

doFinal失败，表示校验padding失败，doFinal对最后一块密文数据解密，并校验padding是否合法。解密输入的key、iv和ciphertext，任意一个不正确，都可能会导致该报错。

1. key不正确，update得到的明文不正确，doFinal失败，即校验padding失败。

2. iv不正确，完整的密文长度为16字节，update无输出，doFinal失败，即校验padding失败；完整的密文长度是16字节的整数倍（不包含16字节），update得到的明文部分正确，doFinal成功。

3. ciphertext不正确，倒数第一个或第二个密文块错误，update得到的明文部分正确（或无输出），doFinal失败，即校验padding失败；其他密文块错误，update得到的明文部分正确，doFinal成功。

**解决措施**

确认加密和解密的key和iv参数一致，确保解密时输入的ciphertext是正确的。

## AES-CCM算法

**问题现象**

AES-CCM解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> AES-CCM为认证加密模式，加解密时需要指定附加验证数据aad（长度需大于等于1字节且小于等于2048字节）和认证标签tag。
>
> 建议开发者使用update接口加密数据，最后调用doFinal接口完成本次加密，获取tag。
>
> 建议开发者使用update接口解密数据，最后调用doFinal接口完成本次解密，doFinal接口内将会对tag进行验证，若失败，接口会抛出异常。

**可能原因**

doFinal失败，表示校验tag失败，解密输入的tag和解密过程中计算的tag不一致。解密输入的key、iv、aad、tag和ciphertext，任意一个不正确，都会导致该报错。

1. key不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

2. iv不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

3. aad不正确，update得到的明文正确，doFinal失败，即校验tag失败。

4. ciphertext不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

5. tag不正确，update得到的明文正确，doFinal失败，即校验tag失败。

**解决措施**

确认加密和解密的key、iv和aad参数一致，确保解密时输入的ciphertext和tag是正确的。

## AES-ECB算法

**问题现象**

AES-ECB解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> AES-ECB属于块加密算法，分组长度为128位（16字节），因此需要使用到填充算法PKCS7，将明文填充至分组大小的整数倍。
>
> 解密时，doFinal接口会对padding进行校验。

**可能原因**

doFinal失败，表示校验padding失败，doFinal对最后一块密文数据解密，并校验padding是否合法。解密输入的key和ciphertext，任意一个不正确，都可能会导致该报错。

1. key不正确，update得到的明文不正确，doFinal失败，即校验padding失败。

2. ciphertext不正确，最后一个密文块错误，update得到的明文部分正确，doFinal失败，即校验padding失败；其他密文块错误，update得到的明文部分正确，doFinal成功。

3. ciphertext长度不是16字节（分组大小）的整数倍（使用PKCS7填充时），doFinal失败。

**解决措施**

确认加密和解密的key参数一致，确保解密时输入的ciphertext是正确的，且密文长度为分组大小（16字节）的整数倍。

## DES/3DES算法

**问题现象**

DES或3DES解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> DES/3DES为分组加密算法，分组长度为64位（8字节）。ECB、CBC模式下，明文长度不是64位整数倍时，必须使用填充方法补足。
>
> 解密时，doFinal接口会对padding进行校验。
>
> 若使用NoPadding模式，key、iv或密文不正确（长度均符合要求）时，解密仍能成功，但得到的明文是错误的。

**可能原因**

doFinal失败，表示校验padding失败。解密输入的key内容错误（长度正确但密钥值不正确）或ciphertext不正确，都可能会导致该报错。

1. key内容不正确（DES密钥应为8字节，3DES密钥应为24字节），update得到的明文不正确，doFinal失败。

2. iv不正确（CBC/OFB/CFB模式下iv为8字节）：CBC和CFB模式下仅影响第一个密文块的解密，update得到的明文部分不正确，doFinal成功；OFB为流密码，iv不正确将导致所有明文不正确，但doFinal仍成功。

3. ciphertext不正确，ECB模式下最后一个密文块错误，或CBC模式下倒数第一或第二个密文块错误时，doFinal失败，即padding校验失败；其他密文块错误，doFinal成功，但得到的明文不正确。

4. ciphertext长度不是8字节（分组大小）的整数倍（使用PKCS7填充时），doFinal失败。

**解决措施**

确认加密和解密的key和iv参数一致，确保解密时输入的ciphertext是正确的。DES密钥长度为8字节，3DES密钥长度为24字节。

## SM4-GCM算法

**问题现象**

SM4-GCM解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> SM4-GCM为认证加密模式，加解密时需要指定附加验证数据aad和认证标签tag。
>
> 建议开发者使用update接口加密数据，最后调用doFinal接口完成本次加密，获取tag。
>
> 建议开发者使用update接口解密数据，最后调用doFinal接口完成本次解密，doFinal接口内将会对tag进行验证，若失败，接口会抛出异常。

**可能原因**

doFinal失败，表示校验tag失败，解密输入的tag和解密过程中计算的tag不一致。解密输入的key、iv、aad、tag和ciphertext，任意一个不正确，都会导致该报错。

1. key不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

2. iv不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

3. aad不正确，update得到的明文正确，doFinal失败，即校验tag失败。

4. ciphertext不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

5. tag不正确，update得到的明文正确，doFinal失败，即校验tag失败。

**解决措施**

确认加密和解密的key、iv和aad参数一致，确保解密时输入的ciphertext和tag是正确的。

## SM4-ECB/CBC算法

**问题现象**

SM4-ECB或SM4-CBC解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> SM4为分组加密算法，分组长度为128位。ECB、CBC模式下，明文长度不是128位整数倍时，必须使用填充方法补足。
>
> 解密时，doFinal接口会对padding进行校验。

**可能原因**

doFinal失败，表示校验padding失败。解密输入的key和ciphertext，任意一个不正确，都可能会导致该报错。

1. key不正确（SM4密钥应为16字节），update得到的明文不正确，doFinal失败，即校验padding失败。

2. iv不正确（CBC模式下iv为16字节），仅影响第一个密文块的解密，update得到的明文部分不正确，doFinal成功。

3. ciphertext不正确，ECB模式下最后一个密文块错误，或CBC模式下倒数第一或第二个密文块错误时，doFinal失败，即padding校验失败；其他密文块错误，doFinal成功，但得到的明文不正确。

4. ciphertext长度不是16字节（分组大小）的整数倍（使用PKCS7填充时），doFinal失败。

**解决措施**

确认加密和解密的key和iv参数一致，确保解密时输入的ciphertext是正确的。SM4密钥长度为16字节（128位）。

## ChaCha20-Poly1305算法

**问题现象**

ChaCha20-Poly1305解密时调用doFinal失败，返回错误码17630001。

> **说明：**
>
> ChaCha20-Poly1305为认证加密模式，加解密时需要指定附加验证数据aad和认证标签tag。
>
> 建议开发者使用update接口加密数据，最后调用doFinal接口完成本次加密，获取tag。
>
> 建议开发者使用update接口解密数据，最后调用doFinal接口完成本次解密，doFinal接口内将会对tag进行验证，若失败，接口会抛出异常。

**可能原因**

doFinal失败，表示校验tag失败，解密输入的tag和解密过程中计算的tag不一致。解密输入的key、nonce（IV）、aad、tag和ciphertext，任意一个不正确，都会导致该报错。

1. key值不正确（key长度正确，但key内容不正确），update得到的明文不正确，doFinal失败，即校验tag失败。

2. nonce不正确（nonce为12字节），update得到的明文不正确，doFinal失败，即校验tag失败。

3. aad不正确，update得到的明文正确，doFinal失败，即校验tag失败。

4. ciphertext不正确，update得到的明文不正确，doFinal失败，即校验tag失败。

5. tag不正确，update得到的明文正确，doFinal失败，即校验tag失败。

**解决措施**

确认加密和解密的key、nonce和aad参数一致，确保解密时输入的ciphertext和tag是正确的。
