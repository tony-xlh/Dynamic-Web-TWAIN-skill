---
name: use-dynamsoft-document-viewer
description: Integrate Dynamic Web TWAIN document scanning into web apps. Scan, upload, and process images from scanners/cameras in vanilla JS or React.
version: 1.0.0
license: MIT
---

## What is Dynamsoft Document Viewer?

Dynamsoft Document Viewer (DDV) is a browser-based JavaScript SDK designed for viewing and editing images and PDFs. It provides a wide range of functionalities, including PDF annotation, page manipulation, image quality enhancement, and document saving.

> **Official documentation:** [Dynamsoft Document Viewer Docs](https://www.dynamsoft.com/document-viewer/docs/)

## When to Use Dynamsoft Document Viewer

Use DDV when you need:

- View and annotate PDFs directly in the browser
- View and manage scanned images
- Edit scanned images (rotate, crop, enhance)
- Save documents in various formats (PDF, TIFF, JPEG)

Dynamsoft Document Viewer can be used with Dynamic Web TWAIN and Dynamsoft Mobile Document Scanner for a complete scanning and viewing solution.

## Basic Usage

### Vanilla JavaScript

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DDV - HelloWorld</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.css">
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.js"></script>
</head>
<style>
    html,body {
        width: 100%;
        height: 100%;
        margin:0;
        padding:0;
        overscroll-behavior-y: none;
        overflow: hidden;
    }

    #container {
        width: 100%;
        height: 100%;
    }
</style>
<body>
    <div id="container"></div>
</body>
<script type="module">
    (async () => {
        // Public trial license which is valid for 24 hours
        // You can request a 30-day trial key from https://www.dynamsoft.com/customer/license/trialLicense/?product=ddv
        Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";
        Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine";
        // Preload DDV Resource
        Dynamsoft.DDV.Core.loadWasm();
        await Dynamsoft.DDV.Core.init();
        const editViewer = new Dynamsoft.DDV.EditViewer({
            container: "container",
            uiConfig: Dynamsoft.DDV.getDefaultUiConfig("editViewer"),
        });
    })();
</script>
</html>
```

### NPM

1. Install the package:

   ```bash
   npm install use-dynamsoft-document-viewer
   ```

2. Copy the resources (CSS and JS) from `node_modules/dynamsoft-document-viewer/dist/` to your public directory, like `public/dynamsoft-document-viewer`. You can use ncp or a similar tool to copy the files.

3. Use the library in your code (Vue example):

   ```javascript
   <script setup lang="ts">
   import { onMounted } from 'vue'
   import { DDV } from 'dynamsoft-document-viewer'
   import 'dynamsoft-document-viewer/dist/ddv.css'

   onMounted(async () => {
     DDV.on('error', (e) => {
       alert(e.message)
     })

     // Public trial license which is valid for 24 hours
     DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";
     DDV.Core.engineResourcePath = "/dynamsoft-document-viewer/dist/engine";
     // Preload DDV Resource
     DDV.Core.loadWasm();
     await DDV.Core.init();
        
     const viewer = new DDV.EditViewer({
       container: 'container'
     });
   })
   </script>

   <template>
     <div id="container"></div>
   </template>

   <style scoped>
   #container {
     width: 100%;
     height: 100%;
   }
   </style>
   ```


## Coordinate System

Dynamsoft Document Viewer uses the upper-left corner of the viewer as the origin (0,0) of the coordinate system. The x-axis extends to the right, and the y-axis extends downward. All coordinates and dimensions are in points.

When working with annotations, selections, or any elements that require positioning, you will use this coordinate system to specify locations and sizes.

## Reference Documentation

The `references/` directory contains the full API reference, organized by topic:

### API Overview

| File | Content |
| --- | --- |
| [index.md](references/index.md) | Full reference index and navigation |
| [api/index.md](references/api/index.md) | API reference index |

### Namespaces

| File | Content |
| --- | --- |
| [Dynamsoft.DDV](references/api/namespace/ddv.md) | Main namespace for Dynamsoft Document Viewer |
| [Dynamsoft.DDV.Core](references/api/namespace/ddv_core.md) | Core functionalities like initialization and configuration |
| [Dynamsoft.DDV.Elements](references/api/namespace/ddv_elements.md) | Built-in UI elements and related methods |

### Core Classes

| File | Content |
| --- | --- |
| [EditViewer](references/api/class/editviewer.md) | EditViewer class — the main viewer for viewing and editing documents |
| [BrowseViewer](references/api/class/browseviewer.md) | BrowseViewer class — multi-page display, multi-select |
| [PerspectiveViewer](references/api/class/perspectiveviewer.md) | PerspectiveViewer class — view and adjust document perspective |
| [CaptureViewer](references/api/class/captureviewer.md) | CaptureViewer class — camera control, video stream, image capture (not recommended to use. Use Dynamsoft Mobile Document Scanner) |
| [DocumentManager](references/api/class/documentmanager.md) | DocumentManager class — create, delete, merge documents and manage pages |
| [AnnotationManager](references/api/class/annotationmanager.md) | AnnotationManager class — manage annotations on documents |

### Document Interfaces

| File | Content |
| --- | --- |
| [IDocument](references/api/interface/idocument/index.md) | Document interface for creating documents, managing page data and saving |
| [IBrowseViewer](references/api/interface/ibrowseviewer.md) | Browse viewer object interface |
| [IDocumentDetect](references/api/interface/idocumentdetect.md) | Document detection interface |
| [IImageFilter](references/api/interface/iimagefilter.md) | Image filter interface |
| [IPageData](references/api/interface/ipagedata.md) | Page data interface |
| [CreateDocumentOptions](references/api/interface/createdocumentoptions.md) | Options for creating documents |
| [MergeDocumentOptions](references/api/interface/mergedocumentoptions.md) | Options for merging documents |
| [TransferOptions](references/api/interface/transferoptions.md) | Options for transferring pages between documents |
| [SavePngSettings](references/api/interface/idocument/savepngsettings.md) | PNG save settings |
| [SaveJpegSettings](references/api/interface/idocument/savejpegsettings.md) | JPEG save settings |
| [SavePdfSettings](references/api/interface/idocument/savepdfsettings.md) | PDF save settings |
| [SaveTiffSettings](references/api/interface/idocument/savetiffsettings.md) | TIFF save settings |
| [PrintSettings](references/api/interface/idocument/printsettings.md) | Print settings |
| [Source](references/api/interface/idocument/source.md) | Document source interface |

### Viewer Configuration Interfaces

| File | Content |
| --- | --- |
| [BrowseViewerConfig](references/api/interface/browseviewerconfig.md) | Configuration for BrowseViewer |
| [BrowseViewerConstructorOptions](references/api/interface/browseviewerconstructoroptions.md) | Constructor options for BrowseViewer |
| [CaptureViewerConfig](references/api/interface/captureviewerconfig.md) | Configuration for CaptureViewer |
| [CaptureViewerConstructorOptions](references/api/interface/captureviewerconstructoroptions.md) | Constructor options for CaptureViewer |
| [EditViewerConfig](references/api/interface/editviewerconfig.md) | Configuration for EditViewer |
| [EditViewerConstructorOptions](references/api/interface/editviewerconstructoroptions.md) | Constructor options for EditViewer |
| [CustomViewerConstructorOptions](references/api/interface/customviewerconstructoroptions.md) | Constructor options for CustomViewer |
| [PerspectiveViewerConfig](references/api/interface/perspectiveviewerconfig.md) | Configuration for PerspectiveViewer |
| [PerspectiveViewerConstructorOptions](references/api/interface/perspectiveviewerconstructoroptions.md) | Constructor options for PerspectiveViewer |
| [UiConfig](references/api/interface/uiconfig.md) | UI configuration for viewers |
| [ThumbnailConfig](references/api/interface/thumbnailconfig.md) | Thumbnail display configuration |
| [KeyboardInteractionConfig](references/api/interface/keyboardinteractionconfig.md) | Keyboard interaction configuration |


### Annotation Interfaces

| File | Content |
| --- | --- |
| [AnnotationConfig](references/api/interface/annotationconfig.md) | Annotation configuration |
| [AnnotationToolbarButton](references/api/interface/annotationinterface/annotationtoolbarbutton.md) | Toolbar button configuration |
| [Point](references/api/interface/annotationinterface/point.md) | Point coordinate |
| [TextContent](references/api/interface/annotationinterface/textcontent.md) | Text content |
| [RectangleStyle](references/api/interface/annotationinterface/rectanglestyle.md) | Rectangle annotation style |
| [RectAnnotationOptions](references/api/interface/annotationinterface/rectannotationoptions.md) | Rectangle annotation options |
| [EllipseStyle](references/api/interface/annotationinterface/ellipsestyle.md) | Ellipse annotation style |
| [EllipseAnnotationOptions](references/api/interface/annotationinterface/ellipseannotationoptions.md) | Ellipse annotation options |
| [LineStyle](references/api/interface/annotationinterface/linestyle.md) | Line annotation style |
| [LineAnnotationOptions](references/api/interface/annotationinterface/lineannotationoptions.md) | Line annotation options |
| [InkStyle](references/api/interface/annotationinterface/inkstyle.md) | Ink annotation style |
| [InkAnnotationOptions](references/api/interface/annotationinterface/inkannotationoptions.md) | Ink annotation options |
| [TextBoxStyle](references/api/interface/annotationinterface/textboxstyle.md) | Text box annotation style |
| [TextBoxAnnotationOptions](references/api/interface/annotationinterface/textboxannotationoptions.md) | Text box annotation options |
| [TextTypewriterStyle](references/api/interface/annotationinterface/texttypewriterstyle.md) | Typewriter annotation style |
| [TextTypewriterAnnotationOptions](references/api/interface/annotationinterface/texttypewriterannotationoptions.md) | Typewriter annotation options |
| [StampStyle](references/api/interface/annotationinterface/stampstyle.md) | Stamp annotation style |
| [StampAnnotationOptions](references/api/interface/annotationinterface/stampannotationoptions.md) | Stamp annotation options |
| [PolygonStyle](references/api/interface/annotationinterface/polygonstyle.md) | Polygon annotation style |
| [PolygonAnnotationOptions](references/api/interface/annotationinterface/polygonannotationoptions.md) | Polygon annotation options |
| [PolylineStyle](references/api/interface/annotationinterface/polylinestyle.md) | Polyline annotation style |
| [PolylineAnnotationOptions](references/api/interface/annotationinterface/polylineannotationoptions.md) | Polyline annotation options |
| [HighlightStyle](references/api/interface/annotationinterface/highlightstyle.md) | Highlight annotation style |
| [HighlightAnnotationOptions](references/api/interface/annotationinterface/highlightannotationoptions.md) | Highlight annotation options |
| [UnderlineStyle](references/api/interface/annotationinterface/underlinestyle.md) | Underline annotation style |
| [UnderlineAnnotationOptions](references/api/interface/annotationinterface/underlineannotationoptions.md) | Underline annotation options |
| [StrikeoutStyle](references/api/interface/annotationinterface/strikeoutstyle.md) | Strikeout annotation style |
| [StrikeoutAnnotationOptions](references/api/interface/annotationinterface/strikeoutannotationoptions.md) | Strikeout annotation options |

### Style Interfaces

| File | Content |
| --- | --- |
| [Style Interfaces Overview](references/api/interface/styleinterface/index.md) | Style interfaces index |
| [BaseStyle](references/api/interface/styleinterface/basestyle.md) | Base page style |
| [CanvasStyle](references/api/interface/styleinterface/canvasstyle.md) | Canvas display style |
| [CheckboxStyle](references/api/interface/styleinterface/checkboxstyle.md) | Checkbox style |
| [PageNumberStyle](references/api/interface/styleinterface/pagenumberstyle.md) | Page number style |
| [QuadSelectionStyle](references/api/interface/styleinterface/quadselectionstyle.md) | Quad selection style |
| [AnnotationSelectionStyle](references/api/interface/styleinterface/annotationselectionstyle.md) | Annotation selection style |

### Event & Other Interfaces

| File | Content |
| --- | --- |
| [IPaginationChangedEvent](references/api/interface/ipaginationchangedevent.md) | Pagination change event |
| [IQuadModifiedEvent](references/api/interface/iquadmodifiedevent.md) | Quad modification event |
| [ITextSearchedInfo](references/api/interface/itextsearchedinfo.md) | Text search result info |
| [ITextSelectedInfo](references/api/interface/itextselectedinfo.md) | Text selection info |
| [IUndoRedoStateChangedEvent](references/api/interface/iundoredostatechangedevent.md) | Undo/redo state change event |
| [DDVError](references/api/interface/ddverror.md) | Error object |
| [VError](references/api/interface/verror.md) | Error object |
| [ConfigResult](references/api/interface/configresult.md) | Configuration result |
| [PlayCallbackInfo](references/api/interface/playcallbackinfo.md) | Playback callback info |
| [Rect](references/api/interface/rect.md) | Rectangle interface |
| [RectXY](references/api/interface/rectxy.md) | Rectangle with x,y |
| [DetectResult](references/api/interface/detectresult.md) | Detection result |
| [DocumentDetectConfig](references/api/interface/documentdetectconfig.md) | Document detection config |
| [DocumentDetectResult](references/api/interface/documentdetectresult.md) | Document detection result |
| [ImageFilterItem](references/api/interface/imagefilteritem.md) | Image filter item |
| [SearchTextOptions](references/api/interface/searchtextoptions.md) | Text search options |
| [TextSearchResult](references/api/interface/textsearchresult.md) | Text search result |
| [UpdatedSource](references/api/interface/updatedsource.md) | Updated source info |
| [UpdatedPdfSource](references/api/interface/updatedpdfsource.md) | Updated PDF source info |
| [PageImageInfo](references/api/interface/pageimageinfo.md) | Page image info |
| [PageVisualInfo](references/api/interface/pagevisualinfo.md) | Page visual info |

### Enumerations

| File | Content |
| --- | --- |
| [EnumAnnotationRenderMode](references/api/enumeration-type/enumannnotationrendermode.md) | Annotation render mode |
| [EnumDocumentDetectionStatus](references/api/enumeration-type/enumdocumentdetectionstatus.md) | Document detection status |
| [EnumImageDataType](references/api/enumeration-type/enumimagedatatype.md) | Image data type |
| [EnumImageFilterType](references/api/enumeration-type/enumimagefiltertype.md) | Image filter type |
| [EnumLineEnding](references/api/enumeration-type/enumlineending.md) | Line ending style |
| [EnumPDFCompressionType](references/api/enumeration-type/enumpdfcompressiontype.md) | PDF compression type |
| [EnumPDFPageType](references/api/enumeration-type/enumpdfpagetype.md) | PDF page type |
| [EnumStampIcon](references/api/enumeration-type/enumstampicon.md) | Stamp icon type |
| [EnumTIFFCompressionType](references/api/enumeration-type/enumtiffcompressiontype.md) | TIFF compression type |
| [Quad](references/api/enumeration-type/quad.md) | Quadrilateral type |

