---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface HighlightStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface HighlightStyle
breadcrumbText: Interface HighlightStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface HighlightStyle Page
---

# HighlightStyle

## Syntax

```typescript
interface HighlightStyle {
    opacity?: number;
    background?: string;
}
```

## Attributes

### background

The backgroud style of annotation.

Default value: `#FD7C10`.

**Example**

```typescript
background: "rgb(255,255,255)", 
```

**Remark**

Supported string value of `background`:

- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1.

Default value: 1
