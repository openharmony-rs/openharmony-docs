# Device Certificate Kit（设备证书服务）

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3; @chaceli-->
<!--Designer: @lanming; @chande-->
<!--Tester: @PAFT; @zhangzhi1995-->
<!--Adviser: @zengyawen-->

- Device Certificate Kit简介
- 证书算法库框架<!--certificate-framework-->
  - 证书算法库框架概述
  - 证书对象的创建、解析和校验
  - 证书扩展信息对象的创建、解析和校验
  - 证书吊销列表对象的创建、解析和校验
  - 证书链校验时从PKCS #12文件构造TrustAnchor对象数组
  - 证书链校验器对象的创建和校验
  - 证书集合及证书吊销列表集合对象的创建和获取
  - 证书链对象的创建和校验
  - 使用系统预置CA证书校验证书链
  - 证书CMS签名
  - 证书CMS封装
  - 证书CMS验签
  - 证书CMS解封装
  - 证书PKCS #12的创建和解析
  - 证书链在线校验证书吊销状态
  - 证书链校验时下载缺失的中间CA证书
  - 构建并校验证书链
- 证书管理服务<!--certmanager-->
  - 证书管理服务概述
  - CA证书开发指导
  - 应用证书凭据开发指导
  - 用户证书凭据开发指导
  - 系统证书凭据开发指导
- Device Certificate Kit术语