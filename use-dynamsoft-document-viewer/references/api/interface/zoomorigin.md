---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface ZoomOrigin
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface ZoomOrigin
breadcrumbText: Interface ZoomOrigin
description: Dynamsoft Document Viewer Documentation API Reference Interface ZoomOrigin Page
permalink: /api/interface/zoomorigin.html
---

# ZoomOrigin

## Syntax

```typescript
interface ZoomOrigin {
    x: string; 
    y: string; 
}
```

## Attributes

### x

Specify the origin of x-coordinate.

Supported value: `center`, `start`, `end`

Default value: `center`

### y

Specify the origin of y-coordinate.

Supported value: `center`, `start`, `end`

Default value: `center`


![Zoom Origin](/assets/imgs/zoomorigin.png)    

## Related APIs

- [`zoom`]({{ site.api }}class/editviewer.html#zoom)