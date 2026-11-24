# "js" Tag
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-18T03:04:35.419Z pushedAt=2026-11-19T08:37:52.528Z nl=1 -->

The "js" tag contains the instance name and page route information.


| Tag   | Type    | Default Value    | Mandatory  | Description                           |
| ----- | ------ | ------- | ---- | ----------------------------- |
| name  | string | default | Yes   | Name of the JavaScript instance.                   |
| pages | Array  | -       | Yes   | Route information. For details, see ["pages"](#pages).|


>  **NOTE**
>
>  The "name" and "pages" tags are configured in the "js" tag of the configuration file.


## "pages"

Defines the route information of each page. Each page consists of the page path and page name. The page file name is the page name. For example:


```json5
{
  // ...
  "pages": [
    "pages/index/index",
    "pages/detail/detail"
  ]
  // ...
}
```


>  **NOTE**
>
>
>  - The application home page is fixed to **pages/index/index**.
>
>  - The page name should not be a component name, for example, **text.hml** or **button.hml**.


## Example


```json5
{
  "app": {
    "bundleName": "com.example.player",
    "version": {
        "code": 1,
        "name": "1.0"
    },
    "vendor": "example"
  },
  "module": {
    // ...
    "js": [
      {
        "name": "default",
        "pages": [
          "pages/index/index",
          "pages/detail/detail"
        ]
      }
    ],
    "abilities": [
      {
        // ...
      }
    ]
  }
}
```
