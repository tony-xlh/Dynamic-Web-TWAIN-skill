---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: IPointerEvent Interface – Dynamsoft Document Viewer
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IPointerEvent
breadcrumbText: Interface IPointerEvent
description: Dynamsoft Document Viewer Documentation API Reference Interface IPointerEvent Page
---

# IPointerEvent

## Syntax

```typescript
export interface IPointerEvent {
    index: number;
    pageUid: string;
    imageX: number;
    imageY: number;
    canvasX: number;
    canvasY: number;
    nativeEvent: PointerEvent;
}
```

