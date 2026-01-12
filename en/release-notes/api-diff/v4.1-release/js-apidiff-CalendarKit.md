| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace calendarManager<br>Differences: declare namespace calendarManager|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: function getCalendarManager(context: Context): CalendarManager;<br>Differences: function getCalendarManager(context: Context): CalendarManager;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export interface CalendarManager<br>Differences: export interface CalendarManager|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>Differences: createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>Differences: createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: deleteCalendar(calendar: Calendar): Promise\<void>;<br>Differences: deleteCalendar(calendar: Calendar): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>Differences: deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>Differences: getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>Differences: getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: getCalendar(callback: AsyncCallback\<Calendar>): void;<br>Differences: getCalendar(callback: AsyncCallback\<Calendar>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: getAllCalendars(): Promise\<Calendar[]>;<br>Differences: getAllCalendars(): Promise\<Calendar[]>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarManager;<br>API declaration: getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>Differences: getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export interface Calendar<br>Differences: export interface Calendar|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: readonly id: number;<br>Differences: readonly id: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: addEvent(event: Event): Promise\<number>;<br>Differences: addEvent(event: Event): Promise\<number>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: addEvent(event: Event, callback: AsyncCallback\<number>): void;<br>Differences: addEvent(event: Event, callback: AsyncCallback\<number>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: addEvents(events: Event[]): Promise\<void>;<br>Differences: addEvents(events: Event[]): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: addEvents(events: Event[], callback: AsyncCallback\<void>): void;<br>Differences: addEvents(events: Event[], callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: deleteEvent(id: number): Promise\<void>;<br>Differences: deleteEvent(id: number): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: deleteEvent(id: number, callback: AsyncCallback\<void>): void;<br>Differences: deleteEvent(id: number, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: deleteEvents(ids: number[]): Promise\<void>;<br>Differences: deleteEvents(ids: number[]): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: deleteEvents(ids: number[], callback: AsyncCallback\<void>): void;<br>Differences: deleteEvents(ids: number[], callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: updateEvent(event: Event): Promise\<void>;<br>Differences: updateEvent(event: Event): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: updateEvent(event: Event, callback: AsyncCallback\<void>): void;<br>Differences: updateEvent(event: Event, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getEvents(eventFilter?: EventFilter, eventKey?: (keyof Event)[]): Promise\<Event[]>;<br>Differences: getEvents(eventFilter?: EventFilter, eventKey?: (keyof Event)[]): Promise\<Event[]>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getEvents(eventFilter: EventFilter, eventKey: (keyof Event)[], callback: AsyncCallback\<Event[]>): void;<br>Differences: getEvents(eventFilter: EventFilter, eventKey: (keyof Event)[], callback: AsyncCallback\<Event[]>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getEvents(callback: AsyncCallback\<Event[]>): void;<br>Differences: getEvents(callback: AsyncCallback\<Event[]>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getConfig(): CalendarConfig;<br>Differences: getConfig(): CalendarConfig;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setConfig(config: CalendarConfig): Promise\<void>;<br>Differences: setConfig(config: CalendarConfig): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: setConfig(config: CalendarConfig, callback: AsyncCallback\<void>): void;<br>Differences: setConfig(config: CalendarConfig, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Calendar;<br>API declaration: getAccount(): CalendarAccount;<br>Differences: getAccount(): CalendarAccount;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: interface CalendarAccount<br>Differences: interface CalendarAccount|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarAccount;<br>API declaration: readonly name: string;<br>Differences: readonly name: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarAccount;<br>API declaration: type: CalendarType;<br>Differences: type: CalendarType;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarAccount;<br>API declaration: displayName?: string;<br>Differences: displayName?: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: interface CalendarConfig<br>Differences: interface CalendarConfig|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarConfig;<br>API declaration: enableReminder?: boolean;<br>Differences: enableReminder?: boolean;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarConfig;<br>API declaration: color?: number \| string;<br>Differences: color?: number \| string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: interface Event<br>Differences: interface Event|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: id?: number;<br>Differences: id?: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: type: EventType;<br>Differences: type: EventType;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: location?: Location;<br>Differences: location?: Location;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: startTime: number;<br>Differences: startTime: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: endTime: number;<br>Differences: endTime: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: isAllDay?: boolean;<br>Differences: isAllDay?: boolean;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: attendee?: Attendee[];<br>Differences: attendee?: Attendee[];|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: timeZone?: string;<br>Differences: timeZone?: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: reminderTime?: number[];<br>Differences: reminderTime?: number[];|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: recurrenceRule?: RecurrenceRule;<br>Differences: recurrenceRule?: RecurrenceRule;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: description?: string;<br>Differences: description?: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Event;<br>API declaration: service?: EventService;<br>Differences: service?: EventService;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: enum CalendarType<br>Differences: enum CalendarType|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarType;<br>API declaration: LOCAL = 'local'<br>Differences: LOCAL = 'local'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarType;<br>API declaration: EMAIL = 'email'<br>Differences: EMAIL = 'email'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarType;<br>API declaration: BIRTHDAY = 'birthday'<br>Differences: BIRTHDAY = 'birthday'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarType;<br>API declaration: CALDAV = 'caldav'<br>Differences: CALDAV = 'caldav'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: CalendarType;<br>API declaration: SUBSCRIBED = 'subscribed'<br>Differences: SUBSCRIBED = 'subscribed'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: interface Location<br>Differences: interface Location|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: location?: string;<br>Differences: location?: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: longitude?: number;<br>Differences: longitude?: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Location;<br>API declaration: latitude?: number;<br>Differences: latitude?: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: class EventFilter<br>Differences: class EventFilter|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventFilter;<br>API declaration: static filterById(ids: number[]): EventFilter;<br>Differences: static filterById(ids: number[]): EventFilter;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventFilter;<br>API declaration: static filterByTime(start: number, end: number): EventFilter;<br>Differences: static filterByTime(start: number, end: number): EventFilter;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventFilter;<br>API declaration: static filterByTitle(title: string): EventFilter;<br>Differences: static filterByTitle(title: string): EventFilter;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: enum EventType<br>Differences: enum EventType|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: NORMAL = 0<br>Differences: NORMAL = 0|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventType;<br>API declaration: IMPORTANT = 1<br>Differences: IMPORTANT = 1|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export interface RecurrenceRule<br>Differences: export interface RecurrenceRule|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: RecurrenceRule;<br>API declaration: recurrenceFrequency: RecurrenceFrequency;<br>Differences: recurrenceFrequency: RecurrenceFrequency;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: RecurrenceRule;<br>API declaration: expire?: number;<br>Differences: expire?: number;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export enum RecurrenceFrequency<br>Differences: export enum RecurrenceFrequency|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: RecurrenceFrequency;<br>API declaration: YEARLY = 0<br>Differences: YEARLY = 0|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: RecurrenceFrequency;<br>API declaration: MONTHLY = 1<br>Differences: MONTHLY = 1|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: RecurrenceFrequency;<br>API declaration: WEEKLY = 2<br>Differences: WEEKLY = 2|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: RecurrenceFrequency;<br>API declaration: DAILY = 3<br>Differences: DAILY = 3|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export interface Attendee<br>Differences: export interface Attendee|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Attendee;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: Attendee;<br>API declaration: email: string;<br>Differences: email: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export interface EventService<br>Differences: export interface EventService|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventService;<br>API declaration: type: ServiceType;<br>Differences: type: ServiceType;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventService;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: EventService;<br>API declaration: description?: string;<br>Differences: description?: string;|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: calendarManager;<br>API declaration: export enum ServiceType<br>Differences: export enum ServiceType|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: MEETING = 'Meeting'<br>Differences: MEETING = 'Meeting'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: WATCHING = 'Watching'<br>Differences: WATCHING = 'Watching'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: REPAYMENT = 'Repayment'<br>Differences: REPAYMENT = 'Repayment'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: LIVE = 'Live'<br>Differences: LIVE = 'Live'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: SHOPPING = 'Shopping'<br>Differences: SHOPPING = 'Shopping'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: TRIP = 'Trip'<br>Differences: TRIP = 'Trip'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: CLASS = 'Class'<br>Differences: CLASS = 'Class'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: SPORTS_EVENTS = 'SportsEvents'<br>Differences: SPORTS_EVENTS = 'SportsEvents'|api/@ohos.calendarManager.d.ts|
|New API|NA|Class name: ServiceType;<br>API declaration: SPORTS_EXERCISE = 'SportsExercise'<br>Differences: SPORTS_EXERCISE = 'SportsExercise'|api/@ohos.calendarManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.calendarManager.d.ts<br>Differences: CalendarKit|api/@ohos.calendarManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.CalendarKit.d.ts<br>Differences: CalendarKit|kits/@kit.CalendarKit.d.ts|
