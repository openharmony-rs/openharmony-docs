# AES解密失败返回17630001

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

开发者使用加解密算法库经常遇到对称算法解密报错17630001，下文将对其失败原因进行详细分析。

## AES-GCM算法

**问题现象**

AES解密时调用doFinal失败，返回错误码17630001，无法得到正确明文。

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

解密时调用doFinal失败，返回错误码17630001，无法得到正确明文。

> **说明：**
>
> AES-CBC属于块加密算法，因此需要使用到填充算法PKCS7 padding，将明文填充至块大小整倍数。
>
> 解密时，doFinal接口会对padding进行校验。

**可能原因**

doFinal失败，表示校验padding失败，doFinal对最后一块密文数据解密，并校验padding是否合法。解密输入的key、iv和ciphertext，任意一个不正确，都可能会导致该报错。

1. key不正确，update得到的明文不正确，doFinal失败，即校验padding失败。

2. iv不正确，完整的密文长度为16字节，update无输出，doFinal失败，即校验padding失败；完整的密文长度不是16字节（16的倍数），update得到的明文部分正确，doFinal成功。

3. ciphertext不正确，倒数第一个或第二个密文块错误，update得到的明文部分正确（或无输出），doFinal失败，即校验padding失败；其他密文块错误，update得到的明文部分正确，doFinal成功。

**解决措施**

确认加密和解密的key和iv参数一致，确保解密时输入的ciphertext是正确的。