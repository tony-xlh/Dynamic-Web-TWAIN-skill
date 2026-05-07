---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface TextContent
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface TextContent
breadcrumbText: Interface TextContent
description: Dynamsoft Document Viewer Documentation API Reference Interface TextContent Page
permalink: /api/interface/annotationinterface/textcontent.html
---

# TextContent

## Syntax

```typescript
interface TextContent {
    content?: string;
    color?: string;
    underline?: boolean; 
    lineThrough?: boolean;
    fontFamily?: string; 
    fontSize?: number; 
    fontStyle?: string; 
    fontWeight?: string; 
}
```

## Attributes

### content

The text content string. 

Default value: `''`

**Example**

```typescript
content: "Dynamsoft Document Viewer",
```

### color

The color of text content string.

Default value: `rgb(0,0,0)`

**Example**

```typescript
color: "#000000",
```

**Remark**

Supported string value of `color`: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### underline

A line will be displayed under the text

Default value: `false`

### lineThrough

A line will be displayed through the text.

Default value: `false`

### fontFamily

The font family of text content string.

Default value: `Helvetica`

**Example**

```typescript
fontFamily: "Times",
```

### fontSize

The font size of text content string.

Default value: 16

**Example**

```typescript
fontSize: 20,
```

### fontStyle

The font style of text content string.

Supported values: `normal`, `italic`

Default value: `normal`

**Example**

```typescript
fontStyle: "italic",
```

### fontWeight

The font weight of text content string.

Supported values: `normal`, `bold`

Default value: `normal`

**Example**

```typescript
fontWeight: "bold",
```

## Related

- [`TextBoxAnnotationOptions`]({{ site.api }}interface/annotationinterface/textboxannotationoptions.html)
- [`TextTypewriterAnnotationOptions`]({{ site.api }}interface/annotationinterface/texttypewriterannotationoptions.html)
- [`TextBoxStyle`]({{ site.api }}interface/annotationinterface/textboxstyle.html)
- [`TextTypewriterStyle`]({{ site.api }}interface/annotationinterface/texttypewriterstyle.html)