---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface DocumentDetectResult
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface DocumentDetectResult
breadcrumbText: Interface DocumentDetectResult
description: Dynamsoft Document Viewer Documentation API Reference Interface DocumentDetectResult Page
permalink: /api/interface/documentdetectresult.html
---

# DocumentDetectResult

## Syntax

```typescript
interface DocumentDetectResult {
    success: boolean;
    location?: Quad;
    confidence?: number;
    status?: EnumDocumentDetectionStatus;
    statusMsg?: string;
}
```

## Attributes

### success

Whether to detect the quadrangle successfully.

`true`: Successful.

`false`: Failed.

### location

The result of boundaries quadrangle. Please refer to [`Quad`]({{ site.api }}enumeration-type/quad.html).

### confidence

The confidence of detection result. Value range: [0, 100] in percentage.

### status

The status during detection. Please refer to [`EnumDocumentDetectionStatus`]({{ site.api }}enumeration-type/enumdocumentdetectionstatus.html).

### statusMsg

The status message string.
