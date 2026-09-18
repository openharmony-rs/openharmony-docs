# Constants

## ListFormat

```TypeScript
const ListFormat: {
        prototype: ListFormat;

        /**
         * Creates [Intl.ListFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat) objects that
         * enable language-sensitive list formatting.
         *
         * @param locales - A string with a [BCP 47 language tag](http://tools.ietf.org/html/rfc5646), or an array of such strings.
         *  For the general form and interpretation of the `locales` argument,
         *  see the [`Intl` page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#Locale_identification_and_negotiation).
         *
         * @param options - An [object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/ListFormat#parameters)
         *  with some or all options of `ListFormatOptions`.
         *
         * @returns [Intl.ListFormatOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat) object.
         *
         * [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat).
         */
        new(locales?: BCP47LanguageTag | BCP47LanguageTag[], options?: ListFormatOptions): ListFormat;

        /**
         * Returns an array containing those of the provided locales that are
         * supported in list formatting without having to fall back to the runtime's default locale.
         *
         * @param locales - A string with a [BCP 47 language tag](http://tools.ietf.org/html/rfc5646), or an array of such strings.
         *  For the general form and interpretation of the `locales` argument,
         *  see the [`Intl` page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#Locale_identification_and_negotiation).
         *
         * @param options - An [object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/supportedLocalesOf#parameters).
         *  with some or all possible options.
         *
         * @returns An array of strings representing a subset of the given locale tags that are supported in list
         *  formatting without having to fall back to the runtime's default locale.
         *
         * [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/supportedLocalesOf).
         */
        supportedLocalesOf(locales: BCP47LanguageTag | BCP47LanguageTag[], options?: Pick<ListFormatOptions, "localeMatcher">): BCP47LanguageTag[];
    }
```

**Type:** {         prototype: ListFormat;          /**          * Creates [Intl.ListFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat) objects that          * enable language-sensitive list formatting.          *          * @param locales - A string with a [BCP 47 language tag](http://tools.ietf.org/html/rfc5646), or an array of such strings.          *  For the general form and interpretation of the `locales` argument,          *  see the [`Intl` page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#Locale_identification_and_negotiation).          *          * @param options - An [object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/ListFormat#parameters)          *  with some or all options of `ListFormatOptions`.          *          * @returns [Intl.ListFormatOptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat) object.          *          * [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat).          */         new(locales?: BCP47LanguageTag &#124; BCP47LanguageTag[], options?: ListFormatOptions): ListFormat;          /**          * Returns an array containing those of the provided locales that are          * supported in list formatting without having to fall back to the runtime's default locale.          *          * @param locales - A string with a [BCP 47 language tag](http://tools.ietf.org/html/rfc5646), or an array of such strings.          *  For the general form and interpretation of the `locales` argument,          *  see the [`Intl` page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#Locale_identification_and_negotiation).          *          * @param options - An [object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/supportedLocalesOf#parameters).          *  with some or all possible options.          *          * @returns An array of strings representing a subset of the given locale tags that are supported in list          *  formatting without having to fall back to the runtime's default locale.          *          * [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/ListFormat/supportedLocalesOf).          */         supportedLocalesOf(locales: BCP47LanguageTag &#124; BCP47LanguageTag[], options?: Pick&lt;[ListFormatOptions](arkts-intl-listformatoptions-i.md), "localeMatcher"&gt;): BCP47LanguageTag[];     }
