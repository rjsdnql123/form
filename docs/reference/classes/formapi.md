---
id: FormApi
title: FormApi
---

# Class: FormApi\<TFormData, TFormValidator\>

A class representing the Form API. It handles the logic and interactions with the form state.

Normally, you will not need to create a new `FormApi` instance directly. Instead, you will use a framework
hook/function like `useForm` or `createForm` to create a new instance for you that uses your framework's reactivity model.
However, if you need to create a new instance manually, you can do so by calling the `new FormApi` constructor.

## Type Parameters

• **TFormData**

• **TFormValidator** *extends* `Validator`\<`TFormData`, `unknown`\> \| `undefined` = `undefined`

## Constructors

### new FormApi()

```ts
new FormApi<TFormData, TFormValidator>(opts?): FormApi<TFormData, TFormValidator>
```

Constructs a new `FormApi` instance with the given form options.

#### Parameters

• **opts?**: [`FormOptions`](../interfaces/formoptions.md)\<`TFormData`, `TFormValidator`\>

#### Returns

[`FormApi`](formapi.md)\<`TFormData`, `TFormValidator`\>

#### Defined in

[packages/form-core/src/FormApi.ts:364](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L364)

## Properties

### fieldInfo

```ts
fieldInfo: Record<unknown extends TFormData ? string : TFormData extends readonly any[] & IsTuple<TFormData> ? PrefixTupleAccessor<TFormData<TFormData>, AllowedIndexes<TFormData<TFormData>, never>, []> : TFormData extends any[] ? PrefixArrayAccessor<TFormData<TFormData>, [any]> : TFormData extends Date ? never : TFormData extends object ? PrefixObjectAccessor<TFormData<TFormData>, []> : TFormData extends string | number | bigint | boolean ? "" : never, FieldInfo<TFormData, TFormValidator>>;
```

A record of field information for each field in the form.

#### Defined in

[packages/form-core/src/FormApi.ts:353](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L353)

***

### options

```ts
options: FormOptions<TFormData, TFormValidator> = {};
```

The options for the form.

#### Defined in

[packages/form-core/src/FormApi.ts:337](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L337)

***

### state

```ts
state: FormState<TFormData>;
```

The current state of the form.

**Note:**
Do not use `state` directly, as it is not reactive.
Please use form.useStore() utility to subscribe to state

#### Defined in

[packages/form-core/src/FormApi.ts:349](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L349)

***

### store

```ts
store: Store<FormState<TFormData>, (cb) => FormState<TFormData>>;
```

A [TanStack Store instance](https://tanstack.com/store/latest/docs/reference/Store) that keeps track of the form's state.

#### Defined in

[packages/form-core/src/FormApi.ts:341](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L341)

## Methods

### deleteField()

```ts
deleteField<TField>(field): void
```

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:1025](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1025)

***

### getFieldInfo()

```ts
getFieldInfo<TField>(field): FieldInfo<TFormData, TFormValidator>
```

Gets the field info of the specified field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

#### Returns

[`FieldInfo`](../type-aliases/fieldinfo.md)\<`TFormData`, `TFormValidator`\>

#### Defined in

[packages/form-core/src/FormApi.ts:943](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L943)

***

### getFieldMeta()

```ts
getFieldMeta<TField>(field): undefined | FieldMeta
```

Gets the metadata of the specified field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

#### Returns

`undefined` \| [`FieldMeta`](../type-aliases/fieldmeta.md)

#### Defined in

[packages/form-core/src/FormApi.ts:934](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L934)

***

### getFieldValue()

```ts
getFieldValue<TField>(field): DeepValue<TFormData, TField, IsNullable<TFormData>>
```

Gets the value of the specified field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

#### Returns

[`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\>

#### Defined in

[packages/form-core/src/FormApi.ts:927](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L927)

***

### handleSubmit()

```ts
handleSubmit(): Promise<void>
```

Handles the form submission, performs validation, and calls the appropriate onSubmit or onInvalidSubmit callbacks.

#### Returns

`Promise`\<`void`\>

#### Defined in

[packages/form-core/src/FormApi.ts:867](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L867)

***

### insertFieldValue()

```ts
insertFieldValue<TField>(
   field, 
   index, 
   value, 
opts?): Promise<void>
```

Inserts a value into an array field at the specified index, shifting the subsequent values to the right.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **index**: `number`

• **value**: [`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\> *extends* `any`[] ? `any`[] & [`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\>\[`number`\] : `never`

• **opts?**: `UpdateMetaOptions`

#### Returns

`Promise`\<`void`\>

#### Defined in

[packages/form-core/src/FormApi.ts:1057](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1057)

***

### mount()

```ts
mount(): void
```

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:462](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L462)

***

### moveFieldValues()

```ts
moveFieldValues<TField>(
   field, 
   index1, 
   index2, 
   opts?): void
```

Moves the value at the first specified index to the second specified index within an array field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **index1**: `number`

• **index2**: `number`

• **opts?**: `UpdateMetaOptions`

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:1175](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1175)

***

### pushFieldValue()

```ts
pushFieldValue<TField>(
   field, 
   value, 
   opts?): void
```

Pushes a value into an array field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **value**: [`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\> *extends* `any`[] ? `any`[] & [`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\>\[`number`\] : `never`

• **opts?**: `UpdateMetaOptions`

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:1039](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1039)

***

### removeFieldValue()

```ts
removeFieldValue<TField>(
   field, 
   index, 
opts?): Promise<void>
```

Removes a value from an array field at the specified index.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **index**: `number`

• **opts?**: `UpdateMetaOptions`

#### Returns

`Promise`\<`void`\>

#### Defined in

[packages/form-core/src/FormApi.ts:1110](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1110)

***

### replaceFieldValue()

```ts
replaceFieldValue<TField>(
   field, 
   index, 
   value, 
opts?): Promise<void>
```

Replaces a value into an array field at the specified index.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **index**: `number`

• **value**: [`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\> *extends* `any`[] ? `any`[] & [`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\>\[`number`\] : `never`

• **opts?**: `UpdateMetaOptions`

#### Returns

`Promise`\<`void`\>

#### Defined in

[packages/form-core/src/FormApi.ts:1084](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1084)

***

### reset()

```ts
reset(): void
```

Resets the form state to the default values.

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:524](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L524)

***

### resetFieldMeta()

```ts
resetFieldMeta<TField>(fieldMeta): Record<TField, FieldMeta>
```

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **fieldMeta**: `Record`\<`TField`, [`FieldMeta`](../type-aliases/fieldmeta.md)\>

#### Returns

`Record`\<`TField`, [`FieldMeta`](../type-aliases/fieldmeta.md)\>

#### Defined in

[packages/form-core/src/FormApi.ts:977](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L977)

***

### setErrorMap()

```ts
setErrorMap(errorMap): void
```

Updates the form's errorMap

#### Parameters

• **errorMap**: `ValidationErrorMap`

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:1199](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1199)

***

### setFieldMeta()

```ts
setFieldMeta<TField>(field, updater): void
```

Updates the metadata of the specified field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **updater**: [`Updater`](../type-aliases/updater.md)\<[`FieldMeta`](../type-aliases/fieldmeta.md)\>

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:962](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L962)

***

### setFieldValue()

```ts
setFieldValue<TField>(
   field, 
   updater, 
   opts?): void
```

Sets the value of the specified field and optionally updates the touched state.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **updater**: [`Updater`](../type-aliases/updater.md)\<[`DeepValue`](../type-aliases/deepvalue.md)\<`TFormData`, `TField`, `IsNullable`\<`TFormData`\>\>\>

• **opts?**: `UpdateMetaOptions`

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:1000](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1000)

***

### swapFieldValues()

```ts
swapFieldValues<TField>(
   field, 
   index1, 
   index2, 
   opts?): void
```

Swaps the values at the specified indices within an array field.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **index1**: `number`

• **index2**: `number`

• **opts?**: `UpdateMetaOptions`

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:1149](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L1149)

***

### update()

```ts
update(options?): void
```

Updates the form options and form state.

#### Parameters

• **options?**: [`FormOptions`](../interfaces/formoptions.md)\<`TFormData`, `TFormValidator`\>

#### Returns

`void`

#### Defined in

[packages/form-core/src/FormApi.ts:484](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L484)

***

### validateAllFields()

```ts
validateAllFields(cause): Promise<ValidationError[]>
```

Validates all fields in the form using the correct handlers for a given validation type.

#### Parameters

• **cause**: `ValidationCause`

#### Returns

`Promise`\<[`ValidationError`](../type-aliases/validationerror.md)[]\>

#### Defined in

[packages/form-core/src/FormApi.ts:539](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L539)

***

### validateArrayFieldsStartingFrom()

```ts
validateArrayFieldsStartingFrom<TField>(
   field, 
   index, 
cause): Promise<ValidationError[]>
```

Validates the children of a specified array in the form starting from a given index until the end using the correct handlers for a given validation type.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **index**: `number`

• **cause**: `ValidationCause`

#### Returns

`Promise`\<[`ValidationError`](../type-aliases/validationerror.md)[]\>

#### Defined in

[packages/form-core/src/FormApi.ts:566](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L566)

***

### validateField()

```ts
validateField<TField>(field, cause): ValidationError[] | Promise<ValidationError[]>
```

Validates a specified field in the form using the correct handlers for a given validation type.

#### Type Parameters

• **TField** *extends* `string` \| `number`

#### Parameters

• **field**: `TField`

• **cause**: `ValidationCause`

#### Returns

[`ValidationError`](../type-aliases/validationerror.md)[] \| `Promise`\<[`ValidationError`](../type-aliases/validationerror.md)[]\>

#### Defined in

[packages/form-core/src/FormApi.ts:605](https://github.com/TanStack/form/blob/main/packages/form-core/src/FormApi.ts#L605)