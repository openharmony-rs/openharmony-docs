# Glossary

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=e82880fc1b3fb82c03ab5c9c350aff1a7e98d202 translatedAt=2026-07-13T07:23:50.683Z pushedAt=2026-07-13T09:28:38.138Z -->

## A

### Application Preferred Language

The language preference configured for an application. If an application preferred language is set, the application loads resources for that language. Otherwise, it loads resources for the system preferred language.

## L

### Local Digit

The numeral system used in a specific locale. For example, in Arabic, both the common Arabic numerals (`0123456789`) and Arabic-Indic digits (`٠١٢٣٤٥٦٧٨٩`) can be used.

## S

### System Preferred Language

The language preference configured for the system. The system preferred language is represented as a prioritized language list, where the first language is the system language. When loading resources, the system attempts to load resources in the order of the list, giving priority to the first language. If no matching resources are available, it falls back to the next language in the list. Currently, only the first language in the list is supported for resource loading.