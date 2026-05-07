---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Type Quad
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Type Quad
breadcrumbText: Type Quad
description: Dynamsoft Document Viewer Documentation API Reference Type Quad Page
permalink: /api/enumeration-type/quad.html
---

# Quad

## Syntax

```typescript
type Quad = [
    [ number,number ], // Point one. The unit is pixel.
    [ number,number ], // Point two. The unit is pixel.
    [ number,number ], // Point three. The unit is pixel.
    [ number,number ], // Point four. The unit is pixel.
];
```

**Remark**

The four points should be arranged in a clockwise or counterclockwise  order.

![Quad](/assets/imgs/quad.png)
