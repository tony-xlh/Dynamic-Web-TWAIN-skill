---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Document Detection
keywords: Documentation, Dynamsoft Document Viewer, Features, Document Detection
breadcrumbText: Document Detection
description: Dynamsoft Document Viewer Documentation Features, Document Detection
permalink: /features/advanced/documentdetect.html
---

# How to configure boundaries detection

DDV provides [`setProcessingHandler()`]({{ site.api }}namespace/ddv.html#static-setprocessinghandler) method for developers to access the corresponding document boundaries detection and image filter algorithms. This article mainly introduces how to configure boundaries detection in the process of capturing documents.

As you may know, Dynamsoft has an SDK which is named [Dynamsoft Document Normalizer](https://www.dynamsoft.com/document-normalizer/docs/web/programming/javascript/user-guide/index.html#check-the-code) and it contains two main features, "Detect the document boundaries" and "Normalize the document based on the detected boundaries". Let us take its "Detect the document boundaries" feature as the example document boundaries detection algorithm.

## Step one: Include and Initialize DDN

### Include DDN

To include document boundaries detection feature, we need to include three packages.

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN.

- jsDelivr

    ```html
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.30/dist/core.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-license@3.0.20/dist/license.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@2.0.20/dist/ddn.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.30/dist/cvr.js"></script>
    ```

- UNPKG

    ```html
    <script src="https://unpkg.com/npm/dynamsoft-core@3.0.30/dist/core.js"></script>
    <script src="https://unpkg.com/npm/dynamsoft-license@3.0.20/dist/license.js"></script>
    <script src="https://unpkg.com/npm/dynamsoft-document-normalizer@2.0.20/dist/ddn.js"></script>
    <script src="https://unpkg.com/npm/dynamsoft-capture-vision-router@2.0.30/dist/cvr.js"></script>
    ```

You can also download the SDK and host its files on your own website/server before including it in your application. Please refer to [Host the SDK yourself](https://www.dynamsoft.com/document-normalizer/docs/web/programming/javascript/user-guide/index.html#host-the-sdk-yourself).

### Initialize DDN

```typescript
// Initializes the DDN license using a license key string.
Dynamsoft.License.LicenseManager.initLicense("**********"); 
// Preloads the DocumentNormalizer module, saving time in preparing for document border detection.
Dynamsoft.Core.CoreModule.loadWasm(["DDN"]); 
// Initializes the router variable by creating an instance of the CaptureVisionRouter class.
const router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance(); 
```

## Step two: Create document boundaries detection module

```typescript
// Inherit DocumentDetect class
class MyDocumentDetect extends Dynamsoft.DDV.DocumentDetect {
    // Rewrite the detect method
    async detect(image, detectConfig) {
        if (!router) {
            return Promise.resolve({
                success: false,
            });
        }

        // Use DDN document boundaries detection algorithm
        const DSImageData = {
            bytes: new Uint8Array(image.data.slice(0)),
            width: image.width,
            height: image.height,
            stride: image.width * 4,
            format: 10,
        };

        const results = await router.capture(DSImageData, "detect-document-boundaries");

        // Filter DDN detection results
        if (results.items.length <= 0) {
            return Promise.resolve({
                success: false,
            });
        }

        // Use processDetectResult to obtain the comprehensive detection result DocumentDetectResult 
        //by passing in the detected points and other parameters (including confidence, status, etc.).
        const quad= [];
        results.items[0].location.points.forEach(p => {
            quad.push([p.x, p.y]);
        });

        const ret = this.processDetectResult({
                location: quad,
                width: image.width,
                height: image.height,
                config: detectConfig,
        });

        // Return detection result
        return Promise.resolve(ret);
    }
}

const detectHandler = new MyDocumentDetect();
```

## Step three: Set document boundaries detection handler

```typescript
Dynamsoft.DDV.setProcessingHandler("documentBoundariesDetect", detectHandler);
```

## Review the complete code

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Detect</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.css">
</head>
<style>
    html,body {
        width:100%;
        height:100%;
        margin:0;
        padding:0;
    }
    #viewer{
        width: 1280px;
        height: 860px;
        margin: 10px;
    }
</style>
<body>
    <div id="viewer"></div>
</body>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.30/dist/core.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-license@3.0.20/dist/license.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@2.0.20/dist/ddn.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.30/dist/cvr.js"></script>
<script type="module">
    (async () => {
        // Initializes DDV
        Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"; // Public trial license which is valid for 24 hours
        Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine";
        await Dynamsoft.DDV.Core.init(); 

        // Initializes the DDN license using a license key string.
        Dynamsoft.License.LicenseManager.initLicense("**********"); 

        Dynamsoft.Core.CoreModule.loadWasm(["DDN"]); 
        // Initializes the router variable by creating an instance of the CaptureVisionRouter class.
        const router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance(); 

        // Inherit DocumentDetect class
        class MyDocumentDetect extends Dynamsoft.DDV.DocumentDetect {
            // Rewrite the detect method
            async detect(image, detectConfig) {
                if (!router) {
                    return Promise.resolve({
                        success: false,
                    });
                }

                // Use DDN document boundaries detection algorithm
                const DSImageData = {
                    bytes: new Uint8Array(image.data.slice(0)),
                    width: image.width,
                    height: image.height,
                    stride: image.width * 4,
                    format: 10,
                };

                const results = await router.capture(DSImageData, "detect-document-boundaries");

                // Filter DDN detection results
                if (results.items.length <= 0) {
                    return Promise.resolve({
                        success: false,
                    });
                }

                // Use processDetectResult to obtain the comprehensive detection result DocumentDetectResult 
                //by passing in the detected points and other parameters (including confidence, status, etc.).
                const quad = [];
                results.items[0].location.points.forEach(p => {
                    quad.push([p.x, p.y]);
                });

                const ret = this.processDetectResult({
                        location: quad,
                        width: image.width,
                        height: image.height,
                        config: detectConfig,
                });

                // Return detection result
                return Promise.resolve(ret);
            }
        }

        const detectHandler = new MyDocumentDetect();
        
        Dynamsoft.DDV.setProcessingHandler("documentBoundariesDetect", detectHandler);

        // Enable auto detect and auto capture when initializing capture viewer
        const captureViewerConfig = {
            enableAutoCapture: true,
            enableAutoDetect: true,
            maxFrameNumber: 10,
        };
        // Create the capture viewer
        const captureViewer = new Dynamsoft.DDV.CaptureViewer({
            container: "viewer",
            viewerConfig: captureViewerConfig,
        });
        captureViewer.play();

    })();
</script>
</html>
```

## Reference

- [`DocumentDetect class`]({{ site.api }}class/advanced/documentdetect.html)