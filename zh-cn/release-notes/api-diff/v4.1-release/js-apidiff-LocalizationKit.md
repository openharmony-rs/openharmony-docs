| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace i18n<br>差异内容：declare namespace i18n|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;<br>差异内容：export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;<br>差异内容：export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getSystemLanguage(): string;<br>差异内容：export function getSystemLanguage(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getSystemRegion(): string;<br>差异内容：export function getSystemRegion(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getSystemLocale(): string;<br>差异内容：export function getSystemLocale(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class System<br>差异内容：export class System|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;<br>差异内容：static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;<br>差异内容：static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getSystemLanguages(): Array\<string>;<br>差异内容：static getSystemLanguages(): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getSystemCountries(language: string): Array\<string>;<br>差异内容：static getSystemCountries(language: string): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static isSuggested(language: string, region?: string): boolean;<br>差异内容：static isSuggested(language: string, region?: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getSystemLanguage(): string;<br>差异内容：static getSystemLanguage(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getSystemRegion(): string;<br>差异内容：static getSystemRegion(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getSystemLocale(): string;<br>差异内容：static getSystemLocale(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static is24HourClock(): boolean;<br>差异内容：static is24HourClock(): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getPreferredLanguageList(): Array\<string>;<br>差异内容：static getPreferredLanguageList(): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getFirstPreferredLanguage(): string;<br>差异内容：static getFirstPreferredLanguage(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static setAppPreferredLanguage(language: string): void;<br>差异内容：static setAppPreferredLanguage(language: string): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getAppPreferredLanguage(): string;<br>差异内容：static getAppPreferredLanguage(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：System；<br>API声明：static getUsingLocalDigit(): boolean;<br>差异内容：static getUsingLocalDigit(): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export interface Util<br>差异内容：export interface Util|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Util；<br>API声明：unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;<br>差异内容：unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class I18NUtil<br>差异内容：export class I18NUtil|api/@ohos.i18n.d.ts|
|新增API|NA|类名：I18NUtil；<br>API声明：static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;<br>差异内容：static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：I18NUtil；<br>API声明：static getDateOrder(locale: string): string;<br>差异内容：static getDateOrder(locale: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：I18NUtil；<br>API声明：static getTimePeriodName(hour: number, locale?: string): string;<br>差异内容：static getTimePeriodName(hour: number, locale?: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export interface UnitInfo<br>差异内容：export interface UnitInfo|api/@ohos.i18n.d.ts|
|新增API|NA|类名：UnitInfo；<br>API声明：unit: string;<br>差异内容：unit: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：UnitInfo；<br>API声明：measureSystem: string;<br>差异内容：measureSystem: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export interface PhoneNumberFormatOptions<br>差异内容：export interface PhoneNumberFormatOptions|api/@ohos.i18n.d.ts|
|新增API|NA|类名：PhoneNumberFormatOptions；<br>API声明：type?: string;<br>差异内容：type?: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class PhoneNumberFormat<br>差异内容：export class PhoneNumberFormat|api/@ohos.i18n.d.ts|
|新增API|NA|类名：PhoneNumberFormat；<br>API声明：isValidNumber(number: string): boolean;<br>差异内容：isValidNumber(number: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：PhoneNumberFormat；<br>API声明：format(number: string): string;<br>差异内容：format(number: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：PhoneNumberFormat；<br>API声明：getLocationName(number: string, locale: string): string;<br>差异内容：getLocationName(number: string, locale: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getCalendar(locale: string, type?: string): Calendar;<br>差异内容：export function getCalendar(locale: string, type?: string): Calendar;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class Calendar<br>差异内容：export class Calendar|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setTime(date: Date): void;<br>差异内容：setTime(date: Date): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setTime(time: number): void;<br>差异内容：setTime(time: number): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：set(year: number, month: number, date: number, hour?: number, minute?: number, second?: number): void;<br>差异内容：set(year: number, month: number, date: number, hour?: number, minute?: number, second?: number): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setTimeZone(timezone: string): void;<br>差异内容：setTimeZone(timezone: string): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getTimeZone(): string;<br>差异内容：getTimeZone(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getFirstDayOfWeek(): number;<br>差异内容：getFirstDayOfWeek(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setFirstDayOfWeek(value: number): void;<br>差异内容：setFirstDayOfWeek(value: number): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getMinimalDaysInFirstWeek(): number;<br>差异内容：getMinimalDaysInFirstWeek(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setMinimalDaysInFirstWeek(value: number): void;<br>差异内容：setMinimalDaysInFirstWeek(value: number): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：get(field: string): number;<br>差异内容：get(field: string): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getDisplayName(locale: string): string;<br>差异内容：getDisplayName(locale: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：isWeekend(date?: Date): boolean;<br>差异内容：isWeekend(date?: Date): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：add(field: string, amount: number): void;<br>差异内容：add(field: string, amount: number): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getTimeInMillis(): number;<br>差异内容：getTimeInMillis(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：compareDays(date: Date): number;<br>差异内容：compareDays(date: Date): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function isRTL(locale: string): boolean;<br>差异内容：export function isRTL(locale: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getLineInstance(locale: string): BreakIterator;<br>差异内容：export function getLineInstance(locale: string): BreakIterator;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class BreakIterator<br>差异内容：export class BreakIterator|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：current(): number;<br>差异内容：current(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：first(): number;<br>差异内容：first(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：last(): number;<br>差异内容：last(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：next(index?: number): number;<br>差异内容：next(index?: number): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：previous(): number;<br>差异内容：previous(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：setLineBreakText(text: string): void;<br>差异内容：setLineBreakText(text: string): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：following(offset: number): number;<br>差异内容：following(offset: number): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：getLineBreakText(): string;<br>差异内容：getLineBreakText(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：BreakIterator；<br>API声明：isBoundary(offset: number): boolean;<br>差异内容：isBoundary(offset: number): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getInstance(locale?: string): IndexUtil;<br>差异内容：export function getInstance(locale?: string): IndexUtil;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class IndexUtil<br>差异内容：export class IndexUtil|api/@ohos.i18n.d.ts|
|新增API|NA|类名：IndexUtil；<br>API声明：getIndexList(): Array\<string>;<br>差异内容：getIndexList(): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：IndexUtil；<br>API声明：addLocale(locale: string): void;<br>差异内容：addLocale(locale: string): void;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：IndexUtil；<br>API声明：getIndex(text: string): string;<br>差异内容：getIndex(text: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class Character<br>差异内容：export class Character|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isDigit(char: string): boolean;<br>差异内容：isDigit(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isSpaceChar(char: string): boolean;<br>差异内容：isSpaceChar(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isWhitespace(char: string): boolean;<br>差异内容：isWhitespace(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isRTL(char: string): boolean;<br>差异内容：isRTL(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isIdeograph(char: string): boolean;<br>差异内容：isIdeograph(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isLetter(char: string): boolean;<br>差异内容：isLetter(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isLowerCase(char: string): boolean;<br>差异内容：isLowerCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：isUpperCase(char: string): boolean;<br>差异内容：isUpperCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Character；<br>API声明：getType(char: string): string;<br>差异内容：getType(char: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class Unicode<br>差异内容：export class Unicode|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isDigit(char: string): boolean;<br>差异内容：static isDigit(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isSpaceChar(char: string): boolean;<br>差异内容：static isSpaceChar(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isWhitespace(char: string): boolean;<br>差异内容：static isWhitespace(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isRTL(char: string): boolean;<br>差异内容：static isRTL(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isIdeograph(char: string): boolean;<br>差异内容：static isIdeograph(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isLetter(char: string): boolean;<br>差异内容：static isLetter(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isLowerCase(char: string): boolean;<br>差异内容：static isLowerCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static isUpperCase(char: string): boolean;<br>差异内容：static isUpperCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Unicode；<br>API声明：static getType(char: string): string;<br>差异内容：static getType(char: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function is24HourClock(): boolean;<br>差异内容：export function is24HourClock(): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function set24HourClock(option: boolean): boolean;<br>差异内容：export function set24HourClock(option: boolean): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function addPreferredLanguage(language: string, index?: number): boolean;<br>差异内容：export function addPreferredLanguage(language: string, index?: number): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function removePreferredLanguage(index: number): boolean;<br>差异内容：export function removePreferredLanguage(index: number): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getPreferredLanguageList(): Array\<string>;<br>差异内容：export function getPreferredLanguageList(): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getFirstPreferredLanguage(): string;<br>差异内容：export function getFirstPreferredLanguage(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export function getTimeZone(zoneID?: string): TimeZone;<br>差异内容：export function getTimeZone(zoneID?: string): TimeZone;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class TimeZone<br>差异内容：export class TimeZone|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：getID(): string;<br>差异内容：getID(): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：getDisplayName(locale?: string, isDST?: boolean): string;<br>差异内容：getDisplayName(locale?: string, isDST?: boolean): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：getRawOffset(): number;<br>差异内容：getRawOffset(): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：getOffset(date?: number): number;<br>差异内容：getOffset(date?: number): number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：static getAvailableIDs(): Array\<string>;<br>差异内容：static getAvailableIDs(): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：static getAvailableZoneCityIDs(): Array\<string>;<br>差异内容：static getAvailableZoneCityIDs(): Array\<string>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：static getCityDisplayName(cityID: string, locale: string): string;<br>差异内容：static getCityDisplayName(cityID: string, locale: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：static getTimezoneFromCity(cityID: string): TimeZone;<br>差异内容：static getTimezoneFromCity(cityID: string): TimeZone;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：TimeZone；<br>API声明：static getTimezonesByLocation(longitude: number, latitude: number): Array\<TimeZone>;<br>差异内容：static getTimezonesByLocation(longitude: number, latitude: number): Array\<TimeZone>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class Transliterator<br>差异内容：export class Transliterator|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Transliterator；<br>API声明：static getAvailableIDs(): string[];<br>差异内容：static getAvailableIDs(): string[];|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Transliterator；<br>API声明：static getInstance(id: string): Transliterator;<br>差异内容：static getInstance(id: string): Transliterator;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Transliterator；<br>API声明：transform(text: string): string;<br>差异内容：transform(text: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export enum NormalizerMode<br>差异内容：export enum NormalizerMode|api/@ohos.i18n.d.ts|
|新增API|NA|类名：NormalizerMode；<br>API声明：NFC = 1<br>差异内容：NFC = 1|api/@ohos.i18n.d.ts|
|新增API|NA|类名：NormalizerMode；<br>API声明：NFD = 2<br>差异内容：NFD = 2|api/@ohos.i18n.d.ts|
|新增API|NA|类名：NormalizerMode；<br>API声明：NFKC = 3<br>差异内容：NFKC = 3|api/@ohos.i18n.d.ts|
|新增API|NA|类名：NormalizerMode；<br>API声明：NFKD = 4<br>差异内容：NFKD = 4|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class Normalizer<br>差异内容：export class Normalizer|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Normalizer；<br>API声明：static getInstance(mode: NormalizerMode): Normalizer;<br>差异内容：static getInstance(mode: NormalizerMode): Normalizer;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：Normalizer；<br>API声明：normalize(text: string): string;<br>差异内容：normalize(text: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export interface HolidayInfoItem<br>差异内容：export interface HolidayInfoItem|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayInfoItem；<br>API声明：baseName: string;<br>差异内容：baseName: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayInfoItem；<br>API声明：year: number;<br>差异内容：year: number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayInfoItem；<br>API声明：month: number;<br>差异内容：month: number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayInfoItem；<br>API声明：day: number;<br>差异内容：day: number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayInfoItem；<br>API声明：localNames?: Array\<HolidayLocalName>;<br>差异内容：localNames?: Array\<HolidayLocalName>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export interface HolidayLocalName<br>差异内容：export interface HolidayLocalName|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayLocalName；<br>API声明：language: string;<br>差异内容：language: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayLocalName；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class HolidayManager<br>差异内容：export class HolidayManager|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayManager；<br>API声明：isHoliday(date?: Date): boolean;<br>差异内容：isHoliday(date?: Date): boolean;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：HolidayManager；<br>API声明：getHolidayInfoItemArray(year?: number): Array\<HolidayInfoItem>;<br>差异内容：getHolidayInfoItemArray(year?: number): Array\<HolidayInfoItem>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export interface EntityInfoItem<br>差异内容：export interface EntityInfoItem|api/@ohos.i18n.d.ts|
|新增API|NA|类名：EntityInfoItem；<br>API声明：begin: number;<br>差异内容：begin: number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：EntityInfoItem；<br>API声明：end: number;<br>差异内容：end: number;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：EntityInfoItem；<br>API声明：type: string;<br>差异内容：type: string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：i18n；<br>API声明：export class EntityRecognizer<br>差异内容：export class EntityRecognizer|api/@ohos.i18n.d.ts|
|新增API|NA|类名：EntityRecognizer；<br>API声明：findEntityInfo(text: string): Array\<EntityInfoItem>;<br>差异内容：findEntityInfo(text: string): Array\<EntityInfoItem>;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace intl<br>差异内容：declare namespace intl|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface LocaleOptions<br>差异内容：export interface LocaleOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：LocaleOptions；<br>API声明：calendar?: string;<br>差异内容：calendar?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：LocaleOptions；<br>API声明：collation?: string;<br>差异内容：collation?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：LocaleOptions；<br>API声明：hourCycle?: string;<br>差异内容：hourCycle?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：LocaleOptions；<br>API声明：numberingSystem?: string;<br>差异内容：numberingSystem?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：LocaleOptions；<br>API声明：numeric?: boolean;<br>差异内容：numeric?: boolean;|api/@ohos.intl.d.ts|
|新增API|NA|类名：LocaleOptions；<br>API声明：caseFirst?: string;<br>差异内容：caseFirst?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export class Locale<br>差异内容：export class Locale|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：language: string;<br>差异内容：language: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：script: string;<br>差异内容：script: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：region: string;<br>差异内容：region: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：baseName: string;<br>差异内容：baseName: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：caseFirst: string;<br>差异内容：caseFirst: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：calendar: string;<br>差异内容：calendar: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：collation: string;<br>差异内容：collation: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：hourCycle: string;<br>差异内容：hourCycle: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：numberingSystem: string;<br>差异内容：numberingSystem: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：numeric: boolean;<br>差异内容：numeric: boolean;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：maximize(): Locale;<br>差异内容：maximize(): Locale;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Locale；<br>API声明：minimize(): Locale;<br>差异内容：minimize(): Locale;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface DateTimeOptions<br>差异内容：export interface DateTimeOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：dateStyle?: string;<br>差异内容：dateStyle?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：timeStyle?: string;<br>差异内容：timeStyle?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：hourCycle?: string;<br>差异内容：hourCycle?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：timeZone?: string;<br>差异内容：timeZone?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：numberingSystem?: string;<br>差异内容：numberingSystem?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：hour12?: boolean;<br>差异内容：hour12?: boolean;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：weekday?: string;<br>差异内容：weekday?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：era?: string;<br>差异内容：era?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：year?: string;<br>差异内容：year?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：month?: string;<br>差异内容：month?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：day?: string;<br>差异内容：day?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：hour?: string;<br>差异内容：hour?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：minute?: string;<br>差异内容：minute?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：second?: string;<br>差异内容：second?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：timeZoneName?: string;<br>差异内容：timeZoneName?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：dayPeriod?: string;<br>差异内容：dayPeriod?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：localeMatcher?: string;<br>差异内容：localeMatcher?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeOptions；<br>API声明：formatMatcher?: string;<br>差异内容：formatMatcher?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export class DateTimeFormat<br>差异内容：export class DateTimeFormat|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeFormat；<br>API声明：format(date: Date): string;<br>差异内容：format(date: Date): string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeFormat；<br>API声明：formatRange(startDate: Date, endDate: Date): string;<br>差异内容：formatRange(startDate: Date, endDate: Date): string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：DateTimeFormat；<br>API声明：resolvedOptions(): DateTimeOptions;<br>差异内容：resolvedOptions(): DateTimeOptions;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface NumberOptions<br>差异内容：export interface NumberOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：currency?: string;<br>差异内容：currency?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：currencySign?: string;<br>差异内容：currencySign?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：currencyDisplay?: string;<br>差异内容：currencyDisplay?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：unit?: string;<br>差异内容：unit?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：unitDisplay?: string;<br>差异内容：unitDisplay?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：unitUsage?: string;<br>差异内容：unitUsage?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：signDisplay?: string;<br>差异内容：signDisplay?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：compactDisplay?: string;<br>差异内容：compactDisplay?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：notation?: string;<br>差异内容：notation?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：localeMatcher?: string;<br>差异内容：localeMatcher?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：style?: string;<br>差异内容：style?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：numberingSystem?: string;<br>差异内容：numberingSystem?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：useGrouping?: boolean;<br>差异内容：useGrouping?: boolean;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：minimumIntegerDigits?: number;<br>差异内容：minimumIntegerDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：minimumFractionDigits?: number;<br>差异内容：minimumFractionDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：maximumFractionDigits?: number;<br>差异内容：maximumFractionDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：minimumSignificantDigits?: number;<br>差异内容：minimumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberOptions；<br>API声明：maximumSignificantDigits?: number;<br>差异内容：maximumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export class NumberFormat<br>差异内容：export class NumberFormat|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberFormat；<br>API声明：format(number: number): string;<br>差异内容：format(number: number): string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：NumberFormat；<br>API声明：resolvedOptions(): NumberOptions;<br>差异内容：resolvedOptions(): NumberOptions;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface CollatorOptions<br>差异内容：export interface CollatorOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：localeMatcher?: string;<br>差异内容：localeMatcher?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：usage?: string;<br>差异内容：usage?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：sensitivity?: string;<br>差异内容：sensitivity?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：ignorePunctuation?: boolean;<br>差异内容：ignorePunctuation?: boolean;|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：collation?: string;<br>差异内容：collation?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：numeric?: boolean;<br>差异内容：numeric?: boolean;|api/@ohos.intl.d.ts|
|新增API|NA|类名：CollatorOptions；<br>API声明：caseFirst?: string;<br>差异内容：caseFirst?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export class Collator<br>差异内容：export class Collator|api/@ohos.intl.d.ts|
|新增API|NA|类名：Collator；<br>API声明：compare(first: string, second: string): number;<br>差异内容：compare(first: string, second: string): number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：Collator；<br>API声明：resolvedOptions(): CollatorOptions;<br>差异内容：resolvedOptions(): CollatorOptions;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface PluralRulesOptions<br>差异内容：export interface PluralRulesOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：localeMatcher?: string;<br>差异内容：localeMatcher?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：type?: string;<br>差异内容：type?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：minimumIntegerDigits?: number;<br>差异内容：minimumIntegerDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：minimumFractionDigits?: number;<br>差异内容：minimumFractionDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：maximumFractionDigits?: number;<br>差异内容：maximumFractionDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：minimumSignificantDigits?: number;<br>差异内容：minimumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRulesOptions；<br>API声明：maximumSignificantDigits?: number;<br>差异内容：maximumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export class PluralRules<br>差异内容：export class PluralRules|api/@ohos.intl.d.ts|
|新增API|NA|类名：PluralRules；<br>API声明：select(n: number): string;<br>差异内容：select(n: number): string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface RelativeTimeFormatInputOptions<br>差异内容：export interface RelativeTimeFormatInputOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatInputOptions；<br>API声明：localeMatcher?: string;<br>差异内容：localeMatcher?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatInputOptions；<br>API声明：numeric?: string;<br>差异内容：numeric?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatInputOptions；<br>API声明：style?: string;<br>差异内容：style?: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export interface RelativeTimeFormatResolvedOptions<br>差异内容：export interface RelativeTimeFormatResolvedOptions|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：locale: string;<br>差异内容：locale: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：style: string;<br>差异内容：style: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：numeric: string;<br>差异内容：numeric: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：numberingSystem: string;<br>差异内容：numberingSystem: string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：intl；<br>API声明：export class RelativeTimeFormat<br>差异内容：export class RelativeTimeFormat|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormat；<br>API声明：format(value: number, unit: string): string;<br>差异内容：format(value: number, unit: string): string;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormat；<br>API声明：formatToParts(value: number, unit: string): Array\<object>;<br>差异内容：formatToParts(value: number, unit: string): Array\<object>;|api/@ohos.intl.d.ts|
|新增API|NA|类名：RelativeTimeFormat；<br>API声明：resolvedOptions(): RelativeTimeFormatResolvedOptions;<br>差异内容：resolvedOptions(): RelativeTimeFormatResolvedOptions;|api/@ohos.intl.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace resourceManager<br>差异内容：declare namespace resourceManager|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export enum Direction<br>差异内容：export enum Direction|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Direction；<br>API声明：DIRECTION_VERTICAL = 0<br>差异内容：DIRECTION_VERTICAL = 0|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Direction；<br>API声明：DIRECTION_HORIZONTAL = 1<br>差异内容：DIRECTION_HORIZONTAL = 1|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export enum DeviceType<br>差异内容：export enum DeviceType|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_PHONE = 0x00<br>差异内容：DEVICE_TYPE_PHONE = 0x00|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_TABLET = 0x01<br>差异内容：DEVICE_TYPE_TABLET = 0x01|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_CAR = 0x02<br>差异内容：DEVICE_TYPE_CAR = 0x02|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_PC = 0x03<br>差异内容：DEVICE_TYPE_PC = 0x03|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_TV = 0x04<br>差异内容：DEVICE_TYPE_TV = 0x04|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_WEARABLE = 0x06<br>差异内容：DEVICE_TYPE_WEARABLE = 0x06|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceType；<br>API声明：DEVICE_TYPE_2IN1 = 0x07<br>差异内容：DEVICE_TYPE_2IN1 = 0x07|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export enum ScreenDensity<br>差异内容：export enum ScreenDensity|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_SDPI = 120<br>差异内容：SCREEN_SDPI = 120|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_MDPI = 160<br>差异内容：SCREEN_MDPI = 160|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_LDPI = 240<br>差异内容：SCREEN_LDPI = 240|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_XLDPI = 320<br>差异内容：SCREEN_XLDPI = 320|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_XXLDPI = 480<br>差异内容：SCREEN_XXLDPI = 480|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ScreenDensity；<br>API声明：SCREEN_XXXLDPI = 640<br>差异内容：SCREEN_XXXLDPI = 640|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export class Configuration<br>差异内容：export class Configuration|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：direction: Direction;<br>差异内容：direction: Direction;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：locale: string;<br>差异内容：locale: string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export class DeviceCapability<br>差异内容：export class DeviceCapability|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceCapability；<br>API声明：screenDensity: ScreenDensity;<br>差异内容：screenDensity: ScreenDensity;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：DeviceCapability；<br>API声明：deviceType: DeviceType;<br>差异内容：deviceType: DeviceType;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export interface AsyncCallback<br>差异内容：export interface AsyncCallback|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export function getResourceManager(callback: AsyncCallback\<ResourceManager>): void;<br>差异内容：export function getResourceManager(callback: AsyncCallback\<ResourceManager>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export function getResourceManager(bundleName: string, callback: AsyncCallback\<ResourceManager>): void;<br>差异内容：export function getResourceManager(bundleName: string, callback: AsyncCallback\<ResourceManager>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export function getResourceManager(): Promise\<ResourceManager>;<br>差异内容：export function getResourceManager(): Promise\<ResourceManager>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export function getResourceManager(bundleName: string): Promise\<ResourceManager>;<br>差异内容：export function getResourceManager(bundleName: string): Promise\<ResourceManager>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export function getSystemResourceManager(): ResourceManager;<br>差异内容：export function getSystemResourceManager(): ResourceManager;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export interface ResourceManager<br>差异内容：export interface ResourceManager|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getString(resId: number, callback: AsyncCallback\<string>): void;<br>差异内容：getString(resId: number, callback: AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getString(resId: number): Promise\<string>;<br>差异内容：getString(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringValue(resource: Resource, callback: _AsyncCallback\<string>): void;<br>差异内容：getStringValue(resource: Resource, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringValue(resource: Resource): Promise\<string>;<br>差异内容：getStringValue(resource: Resource): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringValue(resId: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getStringValue(resId: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringValue(resId: number): Promise\<string>;<br>差异内容：getStringValue(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArray(resId: number, callback: AsyncCallback\<Array\<string>>): void;<br>差异内容：getStringArray(resId: number, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArray(resId: number): Promise\<Array\<string>>;<br>差异内容：getStringArray(resId: number): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayValue(resource: Resource, callback: _AsyncCallback\<Array\<string>>): void;<br>差异内容：getStringArrayValue(resource: Resource, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayValue(resource: Resource): Promise\<Array\<string>>;<br>差异内容：getStringArrayValue(resource: Resource): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayValue(resId: number, callback: _AsyncCallback\<Array\<string>>): void;<br>差异内容：getStringArrayValue(resId: number, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayValue(resId: number): Promise\<Array\<string>>;<br>差异内容：getStringArrayValue(resId: number): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMedia(resId: number, callback: AsyncCallback\<Uint8Array>): void;<br>差异内容：getMedia(resId: number, callback: AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMedia(resId: number): Promise\<Uint8Array>;<br>差异内容：getMedia(resId: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resource: Resource, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getMediaContent(resource: Resource, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resource: Resource, density: number, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getMediaContent(resource: Resource, density: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resource: Resource): Promise\<Uint8Array>;<br>差异内容：getMediaContent(resource: Resource): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resource: Resource, density: number): Promise\<Uint8Array>;<br>差异内容：getMediaContent(resource: Resource, density: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resId: number, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getMediaContent(resId: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resId: number, density: number, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getMediaContent(resId: number, density: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resId: number): Promise\<Uint8Array>;<br>差异内容：getMediaContent(resId: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContent(resId: number, density: number): Promise\<Uint8Array>;<br>差异内容：getMediaContent(resId: number, density: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64(resId: number, callback: AsyncCallback\<string>): void;<br>差异内容：getMediaBase64(resId: number, callback: AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64(resId: number): Promise\<string>;<br>差异内容：getMediaBase64(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resource: Resource, callback: _AsyncCallback\<string>): void;<br>差异内容：getMediaContentBase64(resource: Resource, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resource: Resource, density: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getMediaContentBase64(resource: Resource, density: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resource: Resource): Promise\<string>;<br>差异内容：getMediaContentBase64(resource: Resource): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resource: Resource, density: number): Promise\<string>;<br>差异内容：getMediaContentBase64(resource: Resource, density: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resId: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getMediaContentBase64(resId: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resId: number, density: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getMediaContentBase64(resId: number, density: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resId: number): Promise\<string>;<br>差异内容：getMediaContentBase64(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64(resId: number, density: number): Promise\<string>;<br>差异内容：getMediaContentBase64(resId: number, density: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getDeviceCapability(callback: _AsyncCallback\<DeviceCapability>): void;<br>差异内容：getDeviceCapability(callback: _AsyncCallback\<DeviceCapability>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getDeviceCapability(): Promise\<DeviceCapability>;<br>差异内容：getDeviceCapability(): Promise\<DeviceCapability>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getConfiguration(callback: _AsyncCallback\<Configuration>): void;<br>差异内容：getConfiguration(callback: _AsyncCallback\<Configuration>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getConfiguration(): Promise\<Configuration>;<br>差异内容：getConfiguration(): Promise\<Configuration>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralString(resId: number, num: number, callback: AsyncCallback\<string>): void;<br>差异内容：getPluralString(resId: number, num: number, callback: AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralString(resId: number, num: number): Promise\<string>;<br>差异内容：getPluralString(resId: number, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringValue(resource: Resource, num: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getPluralStringValue(resource: Resource, num: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringValue(resource: Resource, num: number): Promise\<string>;<br>差异内容：getPluralStringValue(resource: Resource, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringValue(resId: number, num: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getPluralStringValue(resId: number, num: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringValue(resId: number, num: number): Promise\<string>;<br>差异内容：getPluralStringValue(resId: number, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFile(path: string, callback: AsyncCallback\<Uint8Array>): void;<br>差异内容：getRawFile(path: string, callback: AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFile(path: string): Promise\<Uint8Array>;<br>差异内容：getRawFile(path: string): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileDescriptor(path: string, callback: AsyncCallback\<RawFileDescriptor>): void;<br>差异内容：getRawFileDescriptor(path: string, callback: AsyncCallback\<RawFileDescriptor>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileDescriptor(path: string): Promise\<RawFileDescriptor>;<br>差异内容：getRawFileDescriptor(path: string): Promise\<RawFileDescriptor>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：closeRawFileDescriptor(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：closeRawFileDescriptor(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：closeRawFileDescriptor(path: string): Promise\<void>;<br>差异内容：closeRawFileDescriptor(path: string): Promise\<void>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringByName(resName: string, callback: _AsyncCallback\<string>): void;<br>差异内容：getStringByName(resName: string, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringByName(resName: string): Promise\<string>;<br>差异内容：getStringByName(resName: string): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayByName(resName: string, callback: _AsyncCallback\<Array\<string>>): void;<br>差异内容：getStringArrayByName(resName: string, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayByName(resName: string): Promise\<Array\<string>>;<br>差异内容：getStringArrayByName(resName: string): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaByName(resName: string, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getMediaByName(resName: string, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaByName(resName: string, density: number, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getMediaByName(resName: string, density: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaByName(resName: string): Promise\<Uint8Array>;<br>差异内容：getMediaByName(resName: string): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaByName(resName: string, density: number): Promise\<Uint8Array>;<br>差异内容：getMediaByName(resName: string, density: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64ByName(resName: string, callback: _AsyncCallback\<string>): void;<br>差异内容：getMediaBase64ByName(resName: string, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64ByName(resName: string, density: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getMediaBase64ByName(resName: string, density: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64ByName(resName: string): Promise\<string>;<br>差异内容：getMediaBase64ByName(resName: string): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64ByName(resName: string, density: number): Promise\<string>;<br>差异内容：getMediaBase64ByName(resName: string, density: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringByName(resName: string, num: number, callback: _AsyncCallback\<string>): void;<br>差异内容：getPluralStringByName(resName: string, num: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringByName(resName: string, num: number): Promise\<string>;<br>差异内容：getPluralStringByName(resName: string, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringSync(resId: number): string;<br>差异内容：getStringSync(resId: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringSync(resId: number, ...args: Array\<string \| number>): string;<br>差异内容：getStringSync(resId: number, ...args: Array\<string \| number>): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringSync(resource: Resource): string;<br>差异内容：getStringSync(resource: Resource): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringSync(resource: Resource, ...args: Array\<string \| number>): string;<br>差异内容：getStringSync(resource: Resource, ...args: Array\<string \| number>): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringByNameSync(resName: string): string;<br>差异内容：getStringByNameSync(resName: string): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringByNameSync(resName: string, ...args: Array\<string \| number>): string;<br>差异内容：getStringByNameSync(resName: string, ...args: Array\<string \| number>): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getBoolean(resId: number): boolean;<br>差异内容：getBoolean(resId: number): boolean;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getBoolean(resource: Resource): boolean;<br>差异内容：getBoolean(resource: Resource): boolean;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getBooleanByName(resName: string): boolean;<br>差异内容：getBooleanByName(resName: string): boolean;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getNumber(resId: number): number;<br>差异内容：getNumber(resId: number): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getNumber(resource: Resource): number;<br>差异内容：getNumber(resource: Resource): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getNumberByName(resName: string): number;<br>差异内容：getNumberByName(resName: string): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：release();<br>差异内容：release();|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileContent(path: string, callback: _AsyncCallback\<Uint8Array>): void;<br>差异内容：getRawFileContent(path: string, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileContent(path: string): Promise\<Uint8Array>;<br>差异内容：getRawFileContent(path: string): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFd(path: string, callback: _AsyncCallback\<RawFileDescriptor>): void;<br>差异内容：getRawFd(path: string, callback: _AsyncCallback\<RawFileDescriptor>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFd(path: string): Promise\<RawFileDescriptor>;<br>差异内容：getRawFd(path: string): Promise\<RawFileDescriptor>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：closeRawFd(path: string, callback: _AsyncCallback\<void>): void;<br>差异内容：closeRawFd(path: string, callback: _AsyncCallback\<void>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：closeRawFd(path: string): Promise\<void>;<br>差异内容：closeRawFd(path: string): Promise\<void>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor;<br>差异内容：getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor;<br>差异内容：getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor;<br>差异内容：getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileList(path: string, callback: _AsyncCallback\<Array\<string>>): void;<br>差异内容：getRawFileList(path: string, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileList(path: string): Promise\<Array\<string>>;<br>差异内容：getRawFileList(path: string): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColor(resId: number, callback: _AsyncCallback\<number>): void;<br>差异内容：getColor(resId: number, callback: _AsyncCallback\<number>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColor(resId: number): Promise\<number>;<br>差异内容：getColor(resId: number): Promise\<number>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColor(resource: Resource, callback: _AsyncCallback\<number>): void;<br>差异内容：getColor(resource: Resource, callback: _AsyncCallback\<number>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColor(resource: Resource): Promise\<number>;<br>差异内容：getColor(resource: Resource): Promise\<number>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColorByName(resName: string, callback: _AsyncCallback\<number>): void;<br>差异内容：getColorByName(resName: string, callback: _AsyncCallback\<number>): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColorByName(resName: string): Promise\<number>;<br>差异内容：getColorByName(resName: string): Promise\<number>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColorSync(resId: number): number;<br>差异内容：getColorSync(resId: number): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColorSync(resource: Resource): number;<br>差异内容：getColorSync(resource: Resource): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getColorByNameSync(resName: string): number;<br>差异内容：getColorByNameSync(resName: string): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：addResource(path: string): void;<br>差异内容：addResource(path: string): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：removeResource(path: string): void;<br>差异内容：removeResource(path: string): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFdSync(path: string): RawFileDescriptor;<br>差异内容：getRawFdSync(path: string): RawFileDescriptor;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：closeRawFdSync(path: string): void;<br>差异内容：closeRawFdSync(path: string): void;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileListSync(path: string): Array\<string>;<br>差异内容：getRawFileListSync(path: string): Array\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getRawFileContentSync(path: string): Uint8Array;<br>差异内容：getRawFileContentSync(path: string): Uint8Array;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentSync(resId: number, density?: number): Uint8Array;<br>差异内容：getMediaContentSync(resId: number, density?: number): Uint8Array;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentSync(resource: Resource, density?: number): Uint8Array;<br>差异内容：getMediaContentSync(resource: Resource, density?: number): Uint8Array;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64Sync(resId: number, density?: number): string;<br>差异内容：getMediaContentBase64Sync(resId: number, density?: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaContentBase64Sync(resource: Resource, density?: number): string;<br>差异内容：getMediaContentBase64Sync(resource: Resource, density?: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringValueSync(resId: number, num: number): string;<br>差异内容：getPluralStringValueSync(resId: number, num: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringValueSync(resource: Resource, num: number): string;<br>差异内容：getPluralStringValueSync(resource: Resource, num: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayValueSync(resId: number): Array\<string>;<br>差异内容：getStringArrayValueSync(resId: number): Array\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayValueSync(resource: Resource): Array\<string>;<br>差异内容：getStringArrayValueSync(resource: Resource): Array\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getPluralStringByNameSync(resName: string, num: number): string;<br>差异内容：getPluralStringByNameSync(resName: string, num: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaByNameSync(resName: string, density?: number): Uint8Array;<br>差异内容：getMediaByNameSync(resName: string, density?: number): Uint8Array;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getMediaBase64ByNameSync(resName: string, density?: number): string;<br>差异内容：getMediaBase64ByNameSync(resName: string, density?: number): string;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getStringArrayByNameSync(resName: string): Array\<string>;<br>差异内容：getStringArrayByNameSync(resName: string): Array\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getConfigurationSync(): Configuration;<br>差异内容：getConfigurationSync(): Configuration;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getDeviceCapabilitySync(): DeviceCapability;<br>差异内容：getDeviceCapabilitySync(): DeviceCapability;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getLocales(includeSystem?: boolean): Array\<string>;<br>差异内容：getLocales(includeSystem?: boolean): Array\<string>;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getSymbol(resId: number): number;<br>差异内容：getSymbol(resId: number): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getSymbol(resource: Resource): number;<br>差异内容：getSymbol(resource: Resource): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getSymbolByName(resName: string): number;<br>差异内容：getSymbolByName(resName: string): number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export type RawFileDescriptor = _RawFileDescriptor;<br>差异内容：export type RawFileDescriptor = _RawFileDescriptor;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export type Resource = _Resource;<br>差异内容：export type Resource = _Resource;|api/@ohos.resourceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.i18n.d.ts<br>差异内容：LocalizationKit|api/@ohos.i18n.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.intl.d.ts<br>差异内容：LocalizationKit|api/@ohos.intl.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.resourceManager.d.ts<br>差异内容：LocalizationKit|api/@ohos.resourceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.LocalizationKit.d.ts<br>差异内容：LocalizationKit|kits/@kit.LocalizationKit.d.ts|
