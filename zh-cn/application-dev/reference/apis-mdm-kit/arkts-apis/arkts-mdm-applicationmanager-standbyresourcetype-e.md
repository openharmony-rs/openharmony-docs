# StandbyResourceType

```TypeScript
enum StandbyResourceType
```

枚举备用资源类型。这些类型表示可以从设备待机中豁免的资源限制。当设备进入待机模式时，系统会限制后台应用程序。通过申请备用资源豁免，指定的应用可以继续使用这些资源即使在设备处于待机模式时也是如此。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## NETWORK

```TypeScript
NETWORK = 1
```

网络访问资源。启用后，指定的应用程序可在设备待机期间继续访问网络。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
