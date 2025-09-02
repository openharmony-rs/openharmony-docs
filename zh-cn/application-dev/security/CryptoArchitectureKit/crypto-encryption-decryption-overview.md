# 加解密介绍

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

在数据存储或传输场景中，可以使用加解密操作用于保证数据的机密性，防止敏感数据泄露。

使用加解密操作中，典型的场景有：

1. 使用对称密钥的加解密操作。

2. 使用非对称密钥的加解密操作。

3. 使用RSA（PKCS1_OAEP填充模式）时，获取、设置CipherSpecItem参数。
