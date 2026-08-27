# 开发准备

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

应用在开发用户身份认证功能时，需要先了解以下流程，并根据实际需求参考对应指导开发。

- 查询设备支持的用户身份认证能力。

- 发起身份认证请求，获取身份认证结果。

- 校验和使用认证结果：请参考通用密钥库二次认证密钥访问控制。

- （可选）认证过程中取消认证。

- （可选）切换自定义认证。

## 申请权限

在开发具备用户身份认证的应用前，需要先申请权限ohos.permission.ACCESS_BIOMETRIC，应用才能使用生物特征识别能力（如人脸、指纹）进行身份认证。

该权限授权方式为system_grant（系统授权），开发者只需要在module.json5配置文件的requestPermissions标签中声明权限，即可获取系统授权。具体声明指导请参考申请应用权限-声明权限。
