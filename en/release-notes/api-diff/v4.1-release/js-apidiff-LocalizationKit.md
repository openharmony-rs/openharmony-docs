| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace i18n<br>Differences: declare namespace i18n|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;<br>Differences: export function getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;<br>Differences: export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getSystemLanguage(): string;<br>Differences: export function getSystemLanguage(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getSystemRegion(): string;<br>Differences: export function getSystemRegion(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getSystemLocale(): string;<br>Differences: export function getSystemLocale(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class System<br>Differences: export class System|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;<br>Differences: static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;<br>Differences: static getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getSystemLanguages(): Array\<string>;<br>Differences: static getSystemLanguages(): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getSystemCountries(language: string): Array\<string>;<br>Differences: static getSystemCountries(language: string): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static isSuggested(language: string, region?: string): boolean;<br>Differences: static isSuggested(language: string, region?: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getSystemLanguage(): string;<br>Differences: static getSystemLanguage(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getSystemRegion(): string;<br>Differences: static getSystemRegion(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getSystemLocale(): string;<br>Differences: static getSystemLocale(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static is24HourClock(): boolean;<br>Differences: static is24HourClock(): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getPreferredLanguageList(): Array\<string>;<br>Differences: static getPreferredLanguageList(): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getFirstPreferredLanguage(): string;<br>Differences: static getFirstPreferredLanguage(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static setAppPreferredLanguage(language: string): void;<br>Differences: static setAppPreferredLanguage(language: string): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getAppPreferredLanguage(): string;<br>Differences: static getAppPreferredLanguage(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: System;<br>API declaration: static getUsingLocalDigit(): boolean;<br>Differences: static getUsingLocalDigit(): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export interface Util<br>Differences: export interface Util|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Util;<br>API declaration: unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;<br>Differences: unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class I18NUtil<br>Differences: export class I18NUtil|api/@ohos.i18n.d.ts|
|New API|NA|Class name: I18NUtil;<br>API declaration: static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;<br>Differences: static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: I18NUtil;<br>API declaration: static getDateOrder(locale: string): string;<br>Differences: static getDateOrder(locale: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: I18NUtil;<br>API declaration: static getTimePeriodName(hour: number, locale?: string): string;<br>Differences: static getTimePeriodName(hour: number, locale?: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export interface UnitInfo<br>Differences: export interface UnitInfo|api/@ohos.i18n.d.ts|
|New API|NA|Class name: UnitInfo;<br>API declaration: unit: string;<br>Differences: unit: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: UnitInfo;<br>API declaration: measureSystem: string;<br>Differences: measureSystem: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export interface PhoneNumberFormatOptions<br>Differences: export interface PhoneNumberFormatOptions|api/@ohos.i18n.d.ts|
|New API|NA|Class name: PhoneNumberFormatOptions;<br>API declaration: type?: string;<br>Differences: type?: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class PhoneNumberFormat<br>Differences: export class PhoneNumberFormat|api/@ohos.i18n.d.ts|
|New API|NA|Class name: PhoneNumberFormat;<br>API declaration: isValidNumber(number: string): boolean;<br>Differences: isValidNumber(number: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: PhoneNumberFormat;<br>API declaration: format(number: string): string;<br>Differences: format(number: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: PhoneNumberFormat;<br>API declaration: getLocationName(number: string, locale: string): string;<br>Differences: getLocationName(number: string, locale: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getCalendar(locale: string, type?: string): Calendar;<br>Differences: export function getCalendar(locale: string, type?: string): Calendar;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class Calendar<br>Differences: export class Calendar|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setTime(date: Date): void;<br>Differences: setTime(date: Date): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setTime(time: number): void;<br>Differences: setTime(time: number): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: set(year: number, month: number, date: number, hour?: number, minute?: number, second?: number): void;<br>Differences: set(year: number, month: number, date: number, hour?: number, minute?: number, second?: number): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setTimeZone(timezone: string): void;<br>Differences: setTimeZone(timezone: string): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getTimeZone(): string;<br>Differences: getTimeZone(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getFirstDayOfWeek(): number;<br>Differences: getFirstDayOfWeek(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setFirstDayOfWeek(value: number): void;<br>Differences: setFirstDayOfWeek(value: number): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getMinimalDaysInFirstWeek(): number;<br>Differences: getMinimalDaysInFirstWeek(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setMinimalDaysInFirstWeek(value: number): void;<br>Differences: setMinimalDaysInFirstWeek(value: number): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: get(field: string): number;<br>Differences: get(field: string): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getDisplayName(locale: string): string;<br>Differences: getDisplayName(locale: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: isWeekend(date?: Date): boolean;<br>Differences: isWeekend(date?: Date): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: add(field: string, amount: number): void;<br>Differences: add(field: string, amount: number): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getTimeInMillis(): number;<br>Differences: getTimeInMillis(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: compareDays(date: Date): number;<br>Differences: compareDays(date: Date): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function isRTL(locale: string): boolean;<br>Differences: export function isRTL(locale: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getLineInstance(locale: string): BreakIterator;<br>Differences: export function getLineInstance(locale: string): BreakIterator;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class BreakIterator<br>Differences: export class BreakIterator|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: current(): number;<br>Differences: current(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: first(): number;<br>Differences: first(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: last(): number;<br>Differences: last(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: next(index?: number): number;<br>Differences: next(index?: number): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: previous(): number;<br>Differences: previous(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: setLineBreakText(text: string): void;<br>Differences: setLineBreakText(text: string): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: following(offset: number): number;<br>Differences: following(offset: number): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: getLineBreakText(): string;<br>Differences: getLineBreakText(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: BreakIterator;<br>API declaration: isBoundary(offset: number): boolean;<br>Differences: isBoundary(offset: number): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getInstance(locale?: string): IndexUtil;<br>Differences: export function getInstance(locale?: string): IndexUtil;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class IndexUtil<br>Differences: export class IndexUtil|api/@ohos.i18n.d.ts|
|New API|NA|Class name: IndexUtil;<br>API declaration: getIndexList(): Array\<string>;<br>Differences: getIndexList(): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: IndexUtil;<br>API declaration: addLocale(locale: string): void;<br>Differences: addLocale(locale: string): void;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: IndexUtil;<br>API declaration: getIndex(text: string): string;<br>Differences: getIndex(text: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class Character<br>Differences: export class Character|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isDigit(char: string): boolean;<br>Differences: isDigit(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isSpaceChar(char: string): boolean;<br>Differences: isSpaceChar(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isWhitespace(char: string): boolean;<br>Differences: isWhitespace(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isRTL(char: string): boolean;<br>Differences: isRTL(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isIdeograph(char: string): boolean;<br>Differences: isIdeograph(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isLetter(char: string): boolean;<br>Differences: isLetter(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isLowerCase(char: string): boolean;<br>Differences: isLowerCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: isUpperCase(char: string): boolean;<br>Differences: isUpperCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Character;<br>API declaration: getType(char: string): string;<br>Differences: getType(char: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class Unicode<br>Differences: export class Unicode|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isDigit(char: string): boolean;<br>Differences: static isDigit(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isSpaceChar(char: string): boolean;<br>Differences: static isSpaceChar(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isWhitespace(char: string): boolean;<br>Differences: static isWhitespace(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isRTL(char: string): boolean;<br>Differences: static isRTL(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isIdeograph(char: string): boolean;<br>Differences: static isIdeograph(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isLetter(char: string): boolean;<br>Differences: static isLetter(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isLowerCase(char: string): boolean;<br>Differences: static isLowerCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static isUpperCase(char: string): boolean;<br>Differences: static isUpperCase(char: string): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Unicode;<br>API declaration: static getType(char: string): string;<br>Differences: static getType(char: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function is24HourClock(): boolean;<br>Differences: export function is24HourClock(): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function set24HourClock(option: boolean): boolean;<br>Differences: export function set24HourClock(option: boolean): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function addPreferredLanguage(language: string, index?: number): boolean;<br>Differences: export function addPreferredLanguage(language: string, index?: number): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function removePreferredLanguage(index: number): boolean;<br>Differences: export function removePreferredLanguage(index: number): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getPreferredLanguageList(): Array\<string>;<br>Differences: export function getPreferredLanguageList(): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getFirstPreferredLanguage(): string;<br>Differences: export function getFirstPreferredLanguage(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export function getTimeZone(zoneID?: string): TimeZone;<br>Differences: export function getTimeZone(zoneID?: string): TimeZone;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class TimeZone<br>Differences: export class TimeZone|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: getID(): string;<br>Differences: getID(): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: getDisplayName(locale?: string, isDST?: boolean): string;<br>Differences: getDisplayName(locale?: string, isDST?: boolean): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: getRawOffset(): number;<br>Differences: getRawOffset(): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: getOffset(date?: number): number;<br>Differences: getOffset(date?: number): number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: static getAvailableIDs(): Array\<string>;<br>Differences: static getAvailableIDs(): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: static getAvailableZoneCityIDs(): Array\<string>;<br>Differences: static getAvailableZoneCityIDs(): Array\<string>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: static getCityDisplayName(cityID: string, locale: string): string;<br>Differences: static getCityDisplayName(cityID: string, locale: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: static getTimezoneFromCity(cityID: string): TimeZone;<br>Differences: static getTimezoneFromCity(cityID: string): TimeZone;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: TimeZone;<br>API declaration: static getTimezonesByLocation(longitude: number, latitude: number): Array\<TimeZone>;<br>Differences: static getTimezonesByLocation(longitude: number, latitude: number): Array\<TimeZone>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class Transliterator<br>Differences: export class Transliterator|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Transliterator;<br>API declaration: static getAvailableIDs(): string[];<br>Differences: static getAvailableIDs(): string[];|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Transliterator;<br>API declaration: static getInstance(id: string): Transliterator;<br>Differences: static getInstance(id: string): Transliterator;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Transliterator;<br>API declaration: transform(text: string): string;<br>Differences: transform(text: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export enum NormalizerMode<br>Differences: export enum NormalizerMode|api/@ohos.i18n.d.ts|
|New API|NA|Class name: NormalizerMode;<br>API declaration: NFC = 1<br>Differences: NFC = 1|api/@ohos.i18n.d.ts|
|New API|NA|Class name: NormalizerMode;<br>API declaration: NFD = 2<br>Differences: NFD = 2|api/@ohos.i18n.d.ts|
|New API|NA|Class name: NormalizerMode;<br>API declaration: NFKC = 3<br>Differences: NFKC = 3|api/@ohos.i18n.d.ts|
|New API|NA|Class name: NormalizerMode;<br>API declaration: NFKD = 4<br>Differences: NFKD = 4|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class Normalizer<br>Differences: export class Normalizer|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Normalizer;<br>API declaration: static getInstance(mode: NormalizerMode): Normalizer;<br>Differences: static getInstance(mode: NormalizerMode): Normalizer;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: Normalizer;<br>API declaration: normalize(text: string): string;<br>Differences: normalize(text: string): string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export interface HolidayInfoItem<br>Differences: export interface HolidayInfoItem|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayInfoItem;<br>API declaration: baseName: string;<br>Differences: baseName: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayInfoItem;<br>API declaration: year: number;<br>Differences: year: number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayInfoItem;<br>API declaration: month: number;<br>Differences: month: number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayInfoItem;<br>API declaration: day: number;<br>Differences: day: number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayInfoItem;<br>API declaration: localNames?: Array\<HolidayLocalName>;<br>Differences: localNames?: Array\<HolidayLocalName>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export interface HolidayLocalName<br>Differences: export interface HolidayLocalName|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayLocalName;<br>API declaration: language: string;<br>Differences: language: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayLocalName;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class HolidayManager<br>Differences: export class HolidayManager|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayManager;<br>API declaration: isHoliday(date?: Date): boolean;<br>Differences: isHoliday(date?: Date): boolean;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: HolidayManager;<br>API declaration: getHolidayInfoItemArray(year?: number): Array\<HolidayInfoItem>;<br>Differences: getHolidayInfoItemArray(year?: number): Array\<HolidayInfoItem>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export interface EntityInfoItem<br>Differences: export interface EntityInfoItem|api/@ohos.i18n.d.ts|
|New API|NA|Class name: EntityInfoItem;<br>API declaration: begin: number;<br>Differences: begin: number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: EntityInfoItem;<br>API declaration: end: number;<br>Differences: end: number;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: EntityInfoItem;<br>API declaration: type: string;<br>Differences: type: string;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: i18n;<br>API declaration: export class EntityRecognizer<br>Differences: export class EntityRecognizer|api/@ohos.i18n.d.ts|
|New API|NA|Class name: EntityRecognizer;<br>API declaration: findEntityInfo(text: string): Array\<EntityInfoItem>;<br>Differences: findEntityInfo(text: string): Array\<EntityInfoItem>;|api/@ohos.i18n.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace intl<br>Differences: declare namespace intl|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface LocaleOptions<br>Differences: export interface LocaleOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: LocaleOptions;<br>API declaration: calendar?: string;<br>Differences: calendar?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: LocaleOptions;<br>API declaration: collation?: string;<br>Differences: collation?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: LocaleOptions;<br>API declaration: hourCycle?: string;<br>Differences: hourCycle?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: LocaleOptions;<br>API declaration: numberingSystem?: string;<br>Differences: numberingSystem?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: LocaleOptions;<br>API declaration: numeric?: boolean;<br>Differences: numeric?: boolean;|api/@ohos.intl.d.ts|
|New API|NA|Class name: LocaleOptions;<br>API declaration: caseFirst?: string;<br>Differences: caseFirst?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export class Locale<br>Differences: export class Locale|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: language: string;<br>Differences: language: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: script: string;<br>Differences: script: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: region: string;<br>Differences: region: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: baseName: string;<br>Differences: baseName: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: caseFirst: string;<br>Differences: caseFirst: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: calendar: string;<br>Differences: calendar: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: collation: string;<br>Differences: collation: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: hourCycle: string;<br>Differences: hourCycle: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: numberingSystem: string;<br>Differences: numberingSystem: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: numeric: boolean;<br>Differences: numeric: boolean;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: toString(): string;<br>Differences: toString(): string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: maximize(): Locale;<br>Differences: maximize(): Locale;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Locale;<br>API declaration: minimize(): Locale;<br>Differences: minimize(): Locale;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface DateTimeOptions<br>Differences: export interface DateTimeOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: dateStyle?: string;<br>Differences: dateStyle?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: timeStyle?: string;<br>Differences: timeStyle?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: hourCycle?: string;<br>Differences: hourCycle?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: timeZone?: string;<br>Differences: timeZone?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: numberingSystem?: string;<br>Differences: numberingSystem?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: hour12?: boolean;<br>Differences: hour12?: boolean;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: weekday?: string;<br>Differences: weekday?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: era?: string;<br>Differences: era?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: year?: string;<br>Differences: year?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: month?: string;<br>Differences: month?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: day?: string;<br>Differences: day?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: hour?: string;<br>Differences: hour?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: minute?: string;<br>Differences: minute?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: second?: string;<br>Differences: second?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: timeZoneName?: string;<br>Differences: timeZoneName?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: dayPeriod?: string;<br>Differences: dayPeriod?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: localeMatcher?: string;<br>Differences: localeMatcher?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeOptions;<br>API declaration: formatMatcher?: string;<br>Differences: formatMatcher?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export class DateTimeFormat<br>Differences: export class DateTimeFormat|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeFormat;<br>API declaration: format(date: Date): string;<br>Differences: format(date: Date): string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeFormat;<br>API declaration: formatRange(startDate: Date, endDate: Date): string;<br>Differences: formatRange(startDate: Date, endDate: Date): string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: DateTimeFormat;<br>API declaration: resolvedOptions(): DateTimeOptions;<br>Differences: resolvedOptions(): DateTimeOptions;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface NumberOptions<br>Differences: export interface NumberOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: currency?: string;<br>Differences: currency?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: currencySign?: string;<br>Differences: currencySign?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: currencyDisplay?: string;<br>Differences: currencyDisplay?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: unit?: string;<br>Differences: unit?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: unitDisplay?: string;<br>Differences: unitDisplay?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: unitUsage?: string;<br>Differences: unitUsage?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: signDisplay?: string;<br>Differences: signDisplay?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: compactDisplay?: string;<br>Differences: compactDisplay?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: notation?: string;<br>Differences: notation?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: localeMatcher?: string;<br>Differences: localeMatcher?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: style?: string;<br>Differences: style?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: numberingSystem?: string;<br>Differences: numberingSystem?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: useGrouping?: boolean;<br>Differences: useGrouping?: boolean;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: minimumIntegerDigits?: number;<br>Differences: minimumIntegerDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: minimumFractionDigits?: number;<br>Differences: minimumFractionDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: maximumFractionDigits?: number;<br>Differences: maximumFractionDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: minimumSignificantDigits?: number;<br>Differences: minimumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberOptions;<br>API declaration: maximumSignificantDigits?: number;<br>Differences: maximumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export class NumberFormat<br>Differences: export class NumberFormat|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberFormat;<br>API declaration: format(number: number): string;<br>Differences: format(number: number): string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: NumberFormat;<br>API declaration: resolvedOptions(): NumberOptions;<br>Differences: resolvedOptions(): NumberOptions;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface CollatorOptions<br>Differences: export interface CollatorOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: localeMatcher?: string;<br>Differences: localeMatcher?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: usage?: string;<br>Differences: usage?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: sensitivity?: string;<br>Differences: sensitivity?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: ignorePunctuation?: boolean;<br>Differences: ignorePunctuation?: boolean;|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: collation?: string;<br>Differences: collation?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: numeric?: boolean;<br>Differences: numeric?: boolean;|api/@ohos.intl.d.ts|
|New API|NA|Class name: CollatorOptions;<br>API declaration: caseFirst?: string;<br>Differences: caseFirst?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export class Collator<br>Differences: export class Collator|api/@ohos.intl.d.ts|
|New API|NA|Class name: Collator;<br>API declaration: compare(first: string, second: string): number;<br>Differences: compare(first: string, second: string): number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: Collator;<br>API declaration: resolvedOptions(): CollatorOptions;<br>Differences: resolvedOptions(): CollatorOptions;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface PluralRulesOptions<br>Differences: export interface PluralRulesOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: localeMatcher?: string;<br>Differences: localeMatcher?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: type?: string;<br>Differences: type?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: minimumIntegerDigits?: number;<br>Differences: minimumIntegerDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: minimumFractionDigits?: number;<br>Differences: minimumFractionDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: maximumFractionDigits?: number;<br>Differences: maximumFractionDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: minimumSignificantDigits?: number;<br>Differences: minimumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRulesOptions;<br>API declaration: maximumSignificantDigits?: number;<br>Differences: maximumSignificantDigits?: number;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export class PluralRules<br>Differences: export class PluralRules|api/@ohos.intl.d.ts|
|New API|NA|Class name: PluralRules;<br>API declaration: select(n: number): string;<br>Differences: select(n: number): string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface RelativeTimeFormatInputOptions<br>Differences: export interface RelativeTimeFormatInputOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatInputOptions;<br>API declaration: localeMatcher?: string;<br>Differences: localeMatcher?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatInputOptions;<br>API declaration: numeric?: string;<br>Differences: numeric?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatInputOptions;<br>API declaration: style?: string;<br>Differences: style?: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export interface RelativeTimeFormatResolvedOptions<br>Differences: export interface RelativeTimeFormatResolvedOptions|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatResolvedOptions;<br>API declaration: locale: string;<br>Differences: locale: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatResolvedOptions;<br>API declaration: style: string;<br>Differences: style: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatResolvedOptions;<br>API declaration: numeric: string;<br>Differences: numeric: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormatResolvedOptions;<br>API declaration: numberingSystem: string;<br>Differences: numberingSystem: string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: intl;<br>API declaration: export class RelativeTimeFormat<br>Differences: export class RelativeTimeFormat|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormat;<br>API declaration: format(value: number, unit: string): string;<br>Differences: format(value: number, unit: string): string;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormat;<br>API declaration: formatToParts(value: number, unit: string): Array\<object>;<br>Differences: formatToParts(value: number, unit: string): Array\<object>;|api/@ohos.intl.d.ts|
|New API|NA|Class name: RelativeTimeFormat;<br>API declaration: resolvedOptions(): RelativeTimeFormatResolvedOptions;<br>Differences: resolvedOptions(): RelativeTimeFormatResolvedOptions;|api/@ohos.intl.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace resourceManager<br>Differences: declare namespace resourceManager|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export enum Direction<br>Differences: export enum Direction|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: DIRECTION_VERTICAL = 0<br>Differences: DIRECTION_VERTICAL = 0|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: Direction;<br>API declaration: DIRECTION_HORIZONTAL = 1<br>Differences: DIRECTION_HORIZONTAL = 1|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export enum DeviceType<br>Differences: export enum DeviceType|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_PHONE = 0x00<br>Differences: DEVICE_TYPE_PHONE = 0x00|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_TABLET = 0x01<br>Differences: DEVICE_TYPE_TABLET = 0x01|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_CAR = 0x02<br>Differences: DEVICE_TYPE_CAR = 0x02|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_PC = 0x03<br>Differences: DEVICE_TYPE_PC = 0x03|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_TV = 0x04<br>Differences: DEVICE_TYPE_TV = 0x04|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_WEARABLE = 0x06<br>Differences: DEVICE_TYPE_WEARABLE = 0x06|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceType;<br>API declaration: DEVICE_TYPE_2IN1 = 0x07<br>Differences: DEVICE_TYPE_2IN1 = 0x07|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export enum ScreenDensity<br>Differences: export enum ScreenDensity|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ScreenDensity;<br>API declaration: SCREEN_SDPI = 120<br>Differences: SCREEN_SDPI = 120|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ScreenDensity;<br>API declaration: SCREEN_MDPI = 160<br>Differences: SCREEN_MDPI = 160|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ScreenDensity;<br>API declaration: SCREEN_LDPI = 240<br>Differences: SCREEN_LDPI = 240|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ScreenDensity;<br>API declaration: SCREEN_XLDPI = 320<br>Differences: SCREEN_XLDPI = 320|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ScreenDensity;<br>API declaration: SCREEN_XXLDPI = 480<br>Differences: SCREEN_XXLDPI = 480|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ScreenDensity;<br>API declaration: SCREEN_XXXLDPI = 640<br>Differences: SCREEN_XXXLDPI = 640|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export class Configuration<br>Differences: export class Configuration|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: Configuration;<br>API declaration: direction: Direction;<br>Differences: direction: Direction;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: Configuration;<br>API declaration: locale: string;<br>Differences: locale: string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export class DeviceCapability<br>Differences: export class DeviceCapability|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceCapability;<br>API declaration: screenDensity: ScreenDensity;<br>Differences: screenDensity: ScreenDensity;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: DeviceCapability;<br>API declaration: deviceType: DeviceType;<br>Differences: deviceType: DeviceType;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export interface AsyncCallback<br>Differences: export interface AsyncCallback|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export function getResourceManager(callback: AsyncCallback\<ResourceManager>): void;<br>Differences: export function getResourceManager(callback: AsyncCallback\<ResourceManager>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export function getResourceManager(bundleName: string, callback: AsyncCallback\<ResourceManager>): void;<br>Differences: export function getResourceManager(bundleName: string, callback: AsyncCallback\<ResourceManager>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export function getResourceManager(): Promise\<ResourceManager>;<br>Differences: export function getResourceManager(): Promise\<ResourceManager>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export function getResourceManager(bundleName: string): Promise\<ResourceManager>;<br>Differences: export function getResourceManager(bundleName: string): Promise\<ResourceManager>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export function getSystemResourceManager(): ResourceManager;<br>Differences: export function getSystemResourceManager(): ResourceManager;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export interface ResourceManager<br>Differences: export interface ResourceManager|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getString(resId: number, callback: AsyncCallback\<string>): void;<br>Differences: getString(resId: number, callback: AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getString(resId: number): Promise\<string>;<br>Differences: getString(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringValue(resource: Resource, callback: _AsyncCallback\<string>): void;<br>Differences: getStringValue(resource: Resource, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringValue(resource: Resource): Promise\<string>;<br>Differences: getStringValue(resource: Resource): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringValue(resId: number, callback: _AsyncCallback\<string>): void;<br>Differences: getStringValue(resId: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringValue(resId: number): Promise\<string>;<br>Differences: getStringValue(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArray(resId: number, callback: AsyncCallback\<Array\<string>>): void;<br>Differences: getStringArray(resId: number, callback: AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArray(resId: number): Promise\<Array\<string>>;<br>Differences: getStringArray(resId: number): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayValue(resource: Resource, callback: _AsyncCallback\<Array\<string>>): void;<br>Differences: getStringArrayValue(resource: Resource, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayValue(resource: Resource): Promise\<Array\<string>>;<br>Differences: getStringArrayValue(resource: Resource): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayValue(resId: number, callback: _AsyncCallback\<Array\<string>>): void;<br>Differences: getStringArrayValue(resId: number, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayValue(resId: number): Promise\<Array\<string>>;<br>Differences: getStringArrayValue(resId: number): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMedia(resId: number, callback: AsyncCallback\<Uint8Array>): void;<br>Differences: getMedia(resId: number, callback: AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMedia(resId: number): Promise\<Uint8Array>;<br>Differences: getMedia(resId: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resource: Resource, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getMediaContent(resource: Resource, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resource: Resource, density: number, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getMediaContent(resource: Resource, density: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resource: Resource): Promise\<Uint8Array>;<br>Differences: getMediaContent(resource: Resource): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resource: Resource, density: number): Promise\<Uint8Array>;<br>Differences: getMediaContent(resource: Resource, density: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resId: number, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getMediaContent(resId: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resId: number, density: number, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getMediaContent(resId: number, density: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resId: number): Promise\<Uint8Array>;<br>Differences: getMediaContent(resId: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContent(resId: number, density: number): Promise\<Uint8Array>;<br>Differences: getMediaContent(resId: number, density: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64(resId: number, callback: AsyncCallback\<string>): void;<br>Differences: getMediaBase64(resId: number, callback: AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64(resId: number): Promise\<string>;<br>Differences: getMediaBase64(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resource: Resource, callback: _AsyncCallback\<string>): void;<br>Differences: getMediaContentBase64(resource: Resource, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resource: Resource, density: number, callback: _AsyncCallback\<string>): void;<br>Differences: getMediaContentBase64(resource: Resource, density: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resource: Resource): Promise\<string>;<br>Differences: getMediaContentBase64(resource: Resource): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resource: Resource, density: number): Promise\<string>;<br>Differences: getMediaContentBase64(resource: Resource, density: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resId: number, callback: _AsyncCallback\<string>): void;<br>Differences: getMediaContentBase64(resId: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resId: number, density: number, callback: _AsyncCallback\<string>): void;<br>Differences: getMediaContentBase64(resId: number, density: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resId: number): Promise\<string>;<br>Differences: getMediaContentBase64(resId: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64(resId: number, density: number): Promise\<string>;<br>Differences: getMediaContentBase64(resId: number, density: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getDeviceCapability(callback: _AsyncCallback\<DeviceCapability>): void;<br>Differences: getDeviceCapability(callback: _AsyncCallback\<DeviceCapability>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getDeviceCapability(): Promise\<DeviceCapability>;<br>Differences: getDeviceCapability(): Promise\<DeviceCapability>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getConfiguration(callback: _AsyncCallback\<Configuration>): void;<br>Differences: getConfiguration(callback: _AsyncCallback\<Configuration>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getConfiguration(): Promise\<Configuration>;<br>Differences: getConfiguration(): Promise\<Configuration>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralString(resId: number, num: number, callback: AsyncCallback\<string>): void;<br>Differences: getPluralString(resId: number, num: number, callback: AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralString(resId: number, num: number): Promise\<string>;<br>Differences: getPluralString(resId: number, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringValue(resource: Resource, num: number, callback: _AsyncCallback\<string>): void;<br>Differences: getPluralStringValue(resource: Resource, num: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringValue(resource: Resource, num: number): Promise\<string>;<br>Differences: getPluralStringValue(resource: Resource, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringValue(resId: number, num: number, callback: _AsyncCallback\<string>): void;<br>Differences: getPluralStringValue(resId: number, num: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringValue(resId: number, num: number): Promise\<string>;<br>Differences: getPluralStringValue(resId: number, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFile(path: string, callback: AsyncCallback\<Uint8Array>): void;<br>Differences: getRawFile(path: string, callback: AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFile(path: string): Promise\<Uint8Array>;<br>Differences: getRawFile(path: string): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileDescriptor(path: string, callback: AsyncCallback\<RawFileDescriptor>): void;<br>Differences: getRawFileDescriptor(path: string, callback: AsyncCallback\<RawFileDescriptor>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileDescriptor(path: string): Promise\<RawFileDescriptor>;<br>Differences: getRawFileDescriptor(path: string): Promise\<RawFileDescriptor>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: closeRawFileDescriptor(path: string, callback: AsyncCallback\<void>): void;<br>Differences: closeRawFileDescriptor(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: closeRawFileDescriptor(path: string): Promise\<void>;<br>Differences: closeRawFileDescriptor(path: string): Promise\<void>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringByName(resName: string, callback: _AsyncCallback\<string>): void;<br>Differences: getStringByName(resName: string, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringByName(resName: string): Promise\<string>;<br>Differences: getStringByName(resName: string): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayByName(resName: string, callback: _AsyncCallback\<Array\<string>>): void;<br>Differences: getStringArrayByName(resName: string, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayByName(resName: string): Promise\<Array\<string>>;<br>Differences: getStringArrayByName(resName: string): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaByName(resName: string, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getMediaByName(resName: string, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaByName(resName: string, density: number, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getMediaByName(resName: string, density: number, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaByName(resName: string): Promise\<Uint8Array>;<br>Differences: getMediaByName(resName: string): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaByName(resName: string, density: number): Promise\<Uint8Array>;<br>Differences: getMediaByName(resName: string, density: number): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64ByName(resName: string, callback: _AsyncCallback\<string>): void;<br>Differences: getMediaBase64ByName(resName: string, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64ByName(resName: string, density: number, callback: _AsyncCallback\<string>): void;<br>Differences: getMediaBase64ByName(resName: string, density: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64ByName(resName: string): Promise\<string>;<br>Differences: getMediaBase64ByName(resName: string): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64ByName(resName: string, density: number): Promise\<string>;<br>Differences: getMediaBase64ByName(resName: string, density: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringByName(resName: string, num: number, callback: _AsyncCallback\<string>): void;<br>Differences: getPluralStringByName(resName: string, num: number, callback: _AsyncCallback\<string>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringByName(resName: string, num: number): Promise\<string>;<br>Differences: getPluralStringByName(resName: string, num: number): Promise\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringSync(resId: number): string;<br>Differences: getStringSync(resId: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringSync(resId: number, ...args: Array\<string \| number>): string;<br>Differences: getStringSync(resId: number, ...args: Array\<string \| number>): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringSync(resource: Resource): string;<br>Differences: getStringSync(resource: Resource): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringSync(resource: Resource, ...args: Array\<string \| number>): string;<br>Differences: getStringSync(resource: Resource, ...args: Array\<string \| number>): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringByNameSync(resName: string): string;<br>Differences: getStringByNameSync(resName: string): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringByNameSync(resName: string, ...args: Array\<string \| number>): string;<br>Differences: getStringByNameSync(resName: string, ...args: Array\<string \| number>): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getBoolean(resId: number): boolean;<br>Differences: getBoolean(resId: number): boolean;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getBoolean(resource: Resource): boolean;<br>Differences: getBoolean(resource: Resource): boolean;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getBooleanByName(resName: string): boolean;<br>Differences: getBooleanByName(resName: string): boolean;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getNumber(resId: number): number;<br>Differences: getNumber(resId: number): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getNumber(resource: Resource): number;<br>Differences: getNumber(resource: Resource): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getNumberByName(resName: string): number;<br>Differences: getNumberByName(resName: string): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: release();<br>Differences: release();|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileContent(path: string, callback: _AsyncCallback\<Uint8Array>): void;<br>Differences: getRawFileContent(path: string, callback: _AsyncCallback\<Uint8Array>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileContent(path: string): Promise\<Uint8Array>;<br>Differences: getRawFileContent(path: string): Promise\<Uint8Array>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFd(path: string, callback: _AsyncCallback\<RawFileDescriptor>): void;<br>Differences: getRawFd(path: string, callback: _AsyncCallback\<RawFileDescriptor>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFd(path: string): Promise\<RawFileDescriptor>;<br>Differences: getRawFd(path: string): Promise\<RawFileDescriptor>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: closeRawFd(path: string, callback: _AsyncCallback\<void>): void;<br>Differences: closeRawFd(path: string, callback: _AsyncCallback\<void>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: closeRawFd(path: string): Promise\<void>;<br>Differences: closeRawFd(path: string): Promise\<void>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor;<br>Differences: getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor;<br>Differences: getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor;<br>Differences: getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileList(path: string, callback: _AsyncCallback\<Array\<string>>): void;<br>Differences: getRawFileList(path: string, callback: _AsyncCallback\<Array\<string>>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileList(path: string): Promise\<Array\<string>>;<br>Differences: getRawFileList(path: string): Promise\<Array\<string>>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColor(resId: number, callback: _AsyncCallback\<number>): void;<br>Differences: getColor(resId: number, callback: _AsyncCallback\<number>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColor(resId: number): Promise\<number>;<br>Differences: getColor(resId: number): Promise\<number>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColor(resource: Resource, callback: _AsyncCallback\<number>): void;<br>Differences: getColor(resource: Resource, callback: _AsyncCallback\<number>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColor(resource: Resource): Promise\<number>;<br>Differences: getColor(resource: Resource): Promise\<number>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColorByName(resName: string, callback: _AsyncCallback\<number>): void;<br>Differences: getColorByName(resName: string, callback: _AsyncCallback\<number>): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColorByName(resName: string): Promise\<number>;<br>Differences: getColorByName(resName: string): Promise\<number>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColorSync(resId: number): number;<br>Differences: getColorSync(resId: number): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColorSync(resource: Resource): number;<br>Differences: getColorSync(resource: Resource): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getColorByNameSync(resName: string): number;<br>Differences: getColorByNameSync(resName: string): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: addResource(path: string): void;<br>Differences: addResource(path: string): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: removeResource(path: string): void;<br>Differences: removeResource(path: string): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFdSync(path: string): RawFileDescriptor;<br>Differences: getRawFdSync(path: string): RawFileDescriptor;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: closeRawFdSync(path: string): void;<br>Differences: closeRawFdSync(path: string): void;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileListSync(path: string): Array\<string>;<br>Differences: getRawFileListSync(path: string): Array\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getRawFileContentSync(path: string): Uint8Array;<br>Differences: getRawFileContentSync(path: string): Uint8Array;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentSync(resId: number, density?: number): Uint8Array;<br>Differences: getMediaContentSync(resId: number, density?: number): Uint8Array;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentSync(resource: Resource, density?: number): Uint8Array;<br>Differences: getMediaContentSync(resource: Resource, density?: number): Uint8Array;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64Sync(resId: number, density?: number): string;<br>Differences: getMediaContentBase64Sync(resId: number, density?: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaContentBase64Sync(resource: Resource, density?: number): string;<br>Differences: getMediaContentBase64Sync(resource: Resource, density?: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringValueSync(resId: number, num: number): string;<br>Differences: getPluralStringValueSync(resId: number, num: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringValueSync(resource: Resource, num: number): string;<br>Differences: getPluralStringValueSync(resource: Resource, num: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayValueSync(resId: number): Array\<string>;<br>Differences: getStringArrayValueSync(resId: number): Array\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayValueSync(resource: Resource): Array\<string>;<br>Differences: getStringArrayValueSync(resource: Resource): Array\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getPluralStringByNameSync(resName: string, num: number): string;<br>Differences: getPluralStringByNameSync(resName: string, num: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaByNameSync(resName: string, density?: number): Uint8Array;<br>Differences: getMediaByNameSync(resName: string, density?: number): Uint8Array;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getMediaBase64ByNameSync(resName: string, density?: number): string;<br>Differences: getMediaBase64ByNameSync(resName: string, density?: number): string;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getStringArrayByNameSync(resName: string): Array\<string>;<br>Differences: getStringArrayByNameSync(resName: string): Array\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getConfigurationSync(): Configuration;<br>Differences: getConfigurationSync(): Configuration;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getDeviceCapabilitySync(): DeviceCapability;<br>Differences: getDeviceCapabilitySync(): DeviceCapability;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getLocales(includeSystem?: boolean): Array\<string>;<br>Differences: getLocales(includeSystem?: boolean): Array\<string>;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getSymbol(resId: number): number;<br>Differences: getSymbol(resId: number): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getSymbol(resource: Resource): number;<br>Differences: getSymbol(resource: Resource): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: ResourceManager;<br>API declaration: getSymbolByName(resName: string): number;<br>Differences: getSymbolByName(resName: string): number;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export type RawFileDescriptor = _RawFileDescriptor;<br>Differences: export type RawFileDescriptor = _RawFileDescriptor;|api/@ohos.resourceManager.d.ts|
|New API|NA|Class name: resourceManager;<br>API declaration: export type Resource = _Resource;<br>Differences: export type Resource = _Resource;|api/@ohos.resourceManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.i18n.d.ts<br>Differences: LocalizationKit|api/@ohos.i18n.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.intl.d.ts<br>Differences: LocalizationKit|api/@ohos.intl.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.resourceManager.d.ts<br>Differences: LocalizationKit|api/@ohos.resourceManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.LocalizationKit.d.ts<br>Differences: LocalizationKit|kits/@kit.LocalizationKit.d.ts|
