---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface Rect
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface Rect
breadcrumbText: Interface Rect
description: Dynamsoft Document Viewer Documentation API Reference Interface Rect Page
permalink: /api/interface/rect.html
---

# Rect

## Syntax

```typescript
interface Rect {
    left: number;
    top: number;
    width: number;
    height: number;
}
```

## Attributes

### left

The x-coordinate of the upper-left corner of the area.

### top

The y-coordinate of the upper-left corner of the area.

### width 

The width of the rectangle area. The unit is point.

### height

The height of the rectangle area. The unit is point.

![Rect](/assets/imgs/rect.png)

## Related

- [`crop()`]({{ site.api }}class/editviewer.html#crop)
- [`getCropRect()`]({{ site.api }}class/editviewer.html#getcroprect)
- [`setCropRect()`]({{ site.api }}class/editviewer.html#setcroprect)