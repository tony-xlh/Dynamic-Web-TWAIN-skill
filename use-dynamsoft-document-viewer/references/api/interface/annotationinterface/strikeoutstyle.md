---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface StrikeoutStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface StrikeoutStyle
breadcrumbText: Interface StrikeoutStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface StrikeoutStyle Page
---

# StrikeoutStyle

## Syntax

```typescript
interface StrikeoutStyle {
    opacity?: number;
    borderColor?: string;
}
```

## Attributes

### borderColor

The borderColor style of annotation.

Default value: `#F01314`.

**Example**

```typescript
borderColor: "rgb(255,255,255)", 
```

**Remark**

Supported string value of `borderColor`:

- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1.

Default value: 1
