# 证书管理概述

证书管理主要提供系统级的证书管理能力，实现证书全生命周期（安装、存储、使用和销毁）的管理和安全使用。

## 证书管理基本概念

- 证书：经证书授权中心（CA）数字签名的、包含公钥拥有者信息以及公钥的文件。常见的证书文件格式为X509证书。
- 凭据：指的是证书文件中公钥所对应的私钥信息。
- 密钥库：包含证书和凭据的文件。常见的密钥库文件格式为P12文件（PKCS#12）。
- 签名：使用私钥对需要传输的文件摘要进行加密得到的密文。
- 验签：用公钥对签名密文进行解密，得到文本的摘要，然后使用与发送方同样的方法对文本计算摘要值，再与解密得到的摘要做对比，二者一致则说明文本没有被篡改过。

### 证书生命周期管理概述

实现业务证书和CA证书的安装、存储、使用和销毁管理，保证证书安全使用。

- 证书安装：使用者可以通过安装接口，传入证书文件或密钥库文件，实现证书的安装。
- 证书存储：证书管理模块将安装后的证书存储在证书管理服务私有目录下，对应的证书对应的私钥凭据存储在HUKS模块中。
- 证书使用：通过查询对应的证书，使用者可获取到证书文件进行业务相关操作；并可以使用证书管理服务提供接口使用证书和私钥进行签名和验签。
- 证书销毁：删除接口允许使用者，批量或单张销毁存储在证书管理中的证书和凭据。

## 约束与限制

证书管理目前仅支持业务证书的使用，并仅支持RSA、ECC及SM2算法类型的私有凭据安装及使用。
