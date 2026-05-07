---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface DetectResult
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface DetectResult
breadcrumbText: Interface DetectResult
description: Dynamsoft Document Viewer Documentation API Reference Interface DetectResult Page
permalink: /api/interface/detectresult.html
---

# DetectResult

## Syntax

```typescript
interface DetectResult {
    location: Quad;
    width: number;
    height: number;
    config: DocumentDetectConfig;
    confidence?: number;
}
```

## Attributes

### location

The result of boundaries quadrangle. Please refer to [`Quad`]({{ site.api }}enumeration-type/quad.html).

### width

The width of image.

### height

The height of image.

### config

The configuration of document detect. Please refer to [`DocumentDetectConfig`]({{ site.api }}interface/documentdetectconfig.html).

### confidence

The confidence of the result quadrangle.
