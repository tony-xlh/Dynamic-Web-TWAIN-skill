---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - DocumentDetect Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, DocumentDetect Class
breadcrumbText: DocumentDetect Class
description: Dynamsoft Document Viewer Documentation API Reference DocumentDetect Class Page
permalink: /api/class/advanced/documentdetect.html
---

# DocumentDetect Class

`DocumentDetect` implements [`IDocumentDetect`]({{ site.api }}interface/idocumentdetect.html). 

This class is used to configure document boundaries detection feature in capture viewer. Please refer to [How to configure boundaries detection]({{ site.features }}advanced/documentdetect.html).

The APIs for this class include:

 API Name                   | Description                                 
----------------------------|---------------------------------------------
 [`detect()`](#detect)                   | Detect the boundaries quadrangle.                   
 [`processDetectResult()`](#processdetectresult)      | Process the detected result.                
 [`getStatusMsg()`](#getstatusmsg)             | Get the message of status during detection.             

## detect()

Detect the boundaries quadrangle.

**Syntax**

```typescript
detect(image: VImageData, config?: DocumentDetectConfig): Promise<DocumentDetectResult>;
```

**Parameters**

`image`: The image to detect boundaries. Please refer to [`VImageData`]({{ site.api }}interface/vimagedata.html).

`config`: The configuration of document detect. Please refer to [`DocumentDetectConfig`]({{ site.api }}interface/documentdetectconfig.html).

**Return Value**

A promise resolving to an [`DocumentDetectResult`]({{ site.api }}interface/documentdetectresult.html) object that contains the detected result.

**Remark**

The border detection process will periodically call the custom detect method to obtain the detected result.

## processDetectResult()

Process the detected result.

**Syntax**

```typescript
processDetectResult(detectResult: DetectResult): DocumentDetectResult;
```

**Parameters**

`detectResult`: The detected result. Please refer to [`DetectResult`]({{ site.api }}interface/detectresult.html).

**Return Value**

A promise resolving to an [`DocumentDetectResult`]({{ site.api }}interface/documentdetectresult.html) object that contains the detected result.

## getStatusMsg()

Get the message of status during detection. 

**Syntax**

```typescript
getStatusMsg(status: EnumDocumentDetectionStatus): string;
```

**Parameters**

`status`: The status during detection. Please refer to [`EnumDocumentDetectionStatus`]({{ site.api }}enumeration-type/enumdocumentdetectionstatus.html).

**Return Value**

The status message string.



