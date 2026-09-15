# interop-config.json5配置文件
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @jiangkaiwen678217-->
<!--Designer: @luchenxu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

模块级配置文件，包含模块中参与ArkTS动静态类型互操作的入口配置信息，包括本模块下的ArkTS-Sta源码入口文件、ArkTS-Dyn源码入口文件，以及参与互操作的外部依赖。参与互操作的模块须在模块根目录下创建该文件，文件所在目录为`工程名称/模块名称（例如entry）/interop-config.json5`，文件名固定为`interop-config.json5`。所有参与互操作的入口文件都必须显式配置在该文件中，互操作声明文件生成工具[Declgen](arkts-sta-declgen-spec.md)根据配置的入口生成互操作声明文件。

ArkTS动静态类型互操作的详细规格，请参见[ArkTS动静态类型易用互操作规格指南](arkts-sta-interop-spec.md)。

## 配置文件示例

通过一个示例，整体了解`interop-config.json5`配置文件。

``` JSON5
{
  "interopEntries": {
    "static": [
      "src/main/ets/StaEntry.ets",
      // ...
    ],
    "dynamic": [
      "src/main/ets/DynEntry.ets",
      // ...
    ],
    "dependency": {
      "package": [
        "some.package.for.interop",
        // ...
      ],
      "source": {
        "some.package.for.interop": {
          "static": [
            "src/main/ets/StaEntry.ets",
            // ...
          ],
          "dynamic": [
            "src/main/ets/DynEntry.ets",
            // ...
          ]
        }
      }
    }
  }
}
```

## 配置文件标签

`interop-config.json5`配置文件包含以下标签。

  **表1** interop-config.json5配置文件标签说明

<!--Table: 15%; 60%; 10%; 15%-->
| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| [interopEntries](#interopentries标签) | 标识模块中参与互操作的入口配置信息，包括本模块下的ArkTS-Sta源码入口文件、ArkTS-Dyn源码入口文件，以及参与互操作的外部依赖。 | 对象 | 该标签不可缺省。 |

## interopEntries标签

该标签标识模块中参与互操作的所有入口，标签值为对象类型，包含static、dynamic、dependency三个子标签。

  **表2** interopEntries标签说明

<!--Table: 15%; 60%; 10%; 15%-->
| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| static | 标识本模块下参与互操作的ArkTS-Sta源码入口文件，取值为相对于本模块根目录的文件路径。 | 字符串数组 | 该标签可缺省，缺省值为空。 |
| dynamic | 标识本模块下参与互操作的ArkTS-Dyn源码入口文件，取值为相对于本模块根目录的文件路径。 | 字符串数组 | 该标签可缺省，缺省值为空。 |
| [dependency](#dependency标签) | 标识参与互操作的外部依赖，支持配置依赖包的包名和依赖包中被指定为互操作入口的具体文件两种方式。 | 对象 | 该标签可缺省，缺省值为空。 |

interopEntries示例：

``` JSON5
{
  "interopEntries": {
    "static": [
      "src/main/ets/StaEntry.ets"
    ],
    "dynamic": [
      "src/main/ets/DynEntry.ets"
    ],
    // ...
  }
}
```

## dependency标签

该标签标识参与互操作的外部依赖，标签值为对象类型，包含package、source两个子标签。

  **表3** dependency标签说明

<!--Table: 15%; 60%; 10%; 15%-->
| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| package | 标识参与互操作的依赖包的包名。配置在该标签下的依赖包，其包内所有文件均作为互操作入口。 | 字符串数组 | 该标签可缺省，缺省值为空。 |
| source | 标识依赖包中被指定为互操作入口的具体文件。该标签以依赖包的包名为键，键值为该依赖包内的入口配置，包含static和dynamic两个子标签，分别标识该依赖包下参与互操作的ArkTS-Sta源码入口文件和ArkTS-Dyn源码入口文件，取值为相对于该依赖包根目录的文件路径。 | 对象 | 该标签可缺省，缺省值为空；其static和dynamic子标签均可缺省，缺省值为空。 |

当同一依赖包同时配置于package和source时，两处配置合并生效，该依赖包的互操作范围取两处配置的并集。

dependency示例：

``` JSON5
{
  "interopEntries": {
    // ...
    "dependency": {
      "package": [
        "some.package.for.interop"
      ],
      "source": {
        "some.package.for.interop": {
          "static": [
            "src/main/ets/StaEntry.ets"
          ],
          "dynamic": [
            "src/main/ets/DynEntry.ets"
          ]
        }
      }
    }
  }
}
```
