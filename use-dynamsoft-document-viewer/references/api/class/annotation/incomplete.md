---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Incomplete Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Incomplete Class
breadcrumbText: Incomplete Class
description: Dynamsoft Document Viewer Documentation API Reference Incomplete Class Page
permalink: /api/class/annotation/incomplete.html
---

# Incomplete Class

This type of annotation may not be supported by Dynamsoft Document Viewer so far.

## API Index

| API Name                        | Description                                                 |
| ------------------------------- | ----------------------------------------------------------- |
| [`uid`](#uid)                   | Return the uid of the annotation.                           |
| [`pageUid`](#pageuid)           | Return the uid of the page where the annotation is located. |
| [`source`](#source)                   | Return the source of the annotation.                               |
| [`type`](#type)                   | Return the type of the annotation                               |
| [`creationDate`](#creationdate) | Return the creation date of the annotation.                 |
| [`raw`](#raw)                   | Return the raw data of the annotation.                      |


## uid

Return the uid of the annotation.

**Syntax**

```typescript
readonly uid: string;
```

{% comment %}
**Remark**

- It will return `''`, if the annotation is deleted. 
{% endcomment %}

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

Return the type of the annotation: `incomplete`.

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

{% comment %}
- It will return `''`, if the annotation is deleted. 
{% endcomment %}

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

## raw

Return the raw data of the annotation.

**Syntax**

```typescript
readonly raw: any;
```
