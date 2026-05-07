---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface IDocumentDetect
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IDocumentDetect
breadcrumbText: Interface IDocumentDetect
description: Dynamsoft Document Viewer Documentation API Reference Interface IDocumentDetect Page
permalink: /api/interface/idocumentdetect.html
---

# IDocumentDetect

It is implemented by [`DocuemntDetect`]({{ site.api }}class/advanced/documentdetect.html) Class.

## Members

### detect()

**Syntax**

```typescript
detect(image: VImageData, config?: DocumentDetectConfig): Promise<DocumentDetectResult>;
```

**Parameters**

`image`: The image which is used to detect boundaries. Please refer to [`VImageData`]({{ site.api }}interface/vimagedata.html).

`config`: The configuration of document detect. Please refer to [`DocumentDetectConfig`]({{ site.api }}interface/documentdetectconfig.html).

**Return Value**

A promise resolving to an [`DocumentDetectResult`]({{ site.api }}interface/documentdetectresult.html) object that contains the detected result.

### destory()

**Syntax**

```typescript
destory(): void;
```
