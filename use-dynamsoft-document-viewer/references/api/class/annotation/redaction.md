---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Redaction Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Redaction Class
breadcrumbText: Redaction Class
description: Dynamsoft Document Viewer Documentation API Reference Redaction Class Page
---

# Redaction Class

## API Index

| API Name                                | Description                                                                                 |
| --------------------------------------- | ------------------------------------------------------------------------------------------- |
| [`uid`](#uid)                           | Return the uid of the annotation.                                                           |
| [`pageUid`](#pageuid)                   | Return the uid of the page where the annotation is located.                                 |
| [`source`](#source)                   | Return the source of the annotation.                               |
| [`type`](#type)                   | Return the type of the annotation                               |
| [`creationDate`](#creationdate)         | Return the creation date of the annotation.                                                 |
| [`flattened`](#flattened)               | Flattens the annotation onto the image layer, or inspect if the annotation is flattened. |
| [`modificationDate`](#modificationdate) | Return the modification date of the annotation.                                             |
| [`getOptions()`](#getoptions)           | Get the annotation options.                                                                 |
| [`updateOptions()`](#updateoptions)     | Update the annotation options.                                                              |

## uid

Return the uid of the annotation.

**Syntax**

```typescript
readonly uid: string;
```

## pageUid

Return the uid of the page where the annotation is located.

**Syntax**

```typescript
readonly pageUid: string;
```

**Remark**

- It will return `''`, if the annotation is deleted.

## source

Return the source of the annotation. Possible values:

* user: the annotation is created by the user's action
* file: the annotation is created from a PDF file
* api: the annotation is created with code

**Remark**

It will return `''`, if the annotation is deleted.

## type

Return the type of the annotation: `redaction`.

All annotation types:

```ts
"rectangle" | "redaction" | "ellipse" | "line" | "polygon" | "polyline" | "ink" | "textBox" | "textTypewriter" | "stamp" | "highlight" | "underline" | "strikeout" | "incomplete" | "unknown"
```

## creationDate

Return the creation date of the annotation.

**Syntax**

```typescript
readonly creationDate: string;
```

**Remark**

- The string would be `D:YYYYMMDDHHmmSSOHH'mm'`, like `D:20230101085959-08'00'`.

## flattened

Flattens the annotation onto the image layer, or inspect if the annotation is flattened.

**Syntax**

```typescript
flattened: boolean;   //Default value is `false`.
```

**Remark**

Flattened annotations move below all unflattened annotations on the page, and are stacked amongst themselves accordingly.

Flattened annotations become part of the page layer upon file export and cease to be annotations.

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80326 | The annotation has already been deleted.  

## modificationDate

Return the modification date of the annotation.

**Syntax**

```typescript
readonly modificationDate: string;
```

**Remark**

- The string would be `D:YYYYMMDDHHmmSSOHH'mm'`, like `D:20230101085959-08'00'`.
- It will return `''`, if the annotation is deleted.
- If the annotation is created but not be modified after adding, it equals to [`creationDate`](#creationdate).

## getOptions()

Get the annotation options.

**Syntax**

```typescript
getOptions(): RedactionAnnotationOptions;
```

**Return value**

The object of redaction annotation options. Please refer to [`RedactionAnnotationOptions`](/api/interface/annotationinterface/redactionannotationoptions.md).

**Code Snippet**

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);
const redaction = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "redaction"); // Create a default Redaction annotation instance.
const options = redaction.getOptions();
```

## updateOptions()

Update the annotation options.

**Syntax**

```typescript
updateOptions(redactionAnnotationOptions: RedactionAnnotationOptions): boolean;
```

**Parameters**

`redactionAnnotationOptions`: The new redaction annotation options. Please refer to [`RedactionAnnotationOptions`](/api/interface/annotationinterface/redactionannotationoptions.md).

**Return value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);
const redaction = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "redaction"); // Create a default Redaction annotation instance.
const options = {
    background: "red",
};
redaction.updateOptions(options); // Update the background of the redaction to red.
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`
 -80323 | The redaction annotation has already been applied.  | `false`

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80326 | The annotation has already been deleted.  
 -80328 | Rectangle-type redaction requires exactly one rect.