---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface HighlightAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface HighlightAnnotationOptions
breadcrumbText: Interface HighlightAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface HighlightAnnotationOptions Page
---

# HighlightAnnotationOptions

## Syntax

```typescript
interface HighlightAnnotationOptions {
    background?: string;
    rects: RectXY[];
    opacity?: number;
    flags?: Flags;
}
```

## Attributes

### background

The backgroud style of annotation.

Default value: `#FD7C10`.

**Example**

```typescript
background: "#FF0000", 
```

**Remark**

Supported string value of `background`: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### rects

An array of rectangles marking where to put the annotations.

Please refer to [`RectXY`](/api/interface/rectxy.md).

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

### flags

The flags of annotation. 

Please refer to [`Flags`]({{ site.api }}interface/annotationinterface/flags.html).

## Related

- [`getOptions()`](/api/class/annotation/highlight.md#getoptions) under `Highlight` class
- [`updateOptions()`](/api/class/annotation/highlight.md#updateoptions) under `Highlight` class
