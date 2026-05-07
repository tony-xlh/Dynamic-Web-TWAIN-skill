---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Annotation Management
keywords: Documentation, Dynamsoft Document Viewer, Features, Annotation Management
breadcrumbText: Annotation Management
description: Dynamsoft Document Viewer Documentation Features, Annotation Management
---

# Annotation Management

Starting from DDV 2.0, annotation is supported.

Annotations can be created using the built-in UI of Edit Viewer as well as code. This guide will focus on using the code.

## Annotation creation

### Supported annotation types

Up to now, the annotation types supported by DDV are as follows:

- [Rectangle]({{ site.api }}class/annotation/rectangle.html)
- [Ellipse]({{ site.api }}class/annotation/ellipse.html)
- [Polygon]({{ site.api }}class/annotation/polygon.html)
- [Polyline]({{ site.api }}class/annotation/polyline.html)
- [Line]({{ site.api }}class/annotation/line.html)
- [Ink]({{ site.api }}class/annotation/ink.html)
- [TextBox]({{ site.api }}class/annotation/textbox.html)
- [TextTypewriter]({{ site.api }}class/annotation/texttypewriter.html)
- [Stamp]({{ site.api }}class/annotation/stamp.html)
- [Highlight]({{ site.api }}class/annotation/highlight.html)
- [Underline]({{ site.api }}class/annotation/underline.html)
- [Strikeout]({{ site.api }}class/annotation/strikeout.html)
- [Redaction](/api/class/annotation/redaction.md)

### Create a specified type annotation instance

To add an annotation to the page, first of all, you need to create an annotation instance. Take the rectangle annotation as an example,

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);
const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle"); // Create a default Rectangle annotation instance.
```

The following properties of the annotation can be accessed from the created instance.

- Annotation Uid
    
    Each annotation possesses a unique annotation uid. 
    
    ```typescript
    const annotUid = rect.uid;
    ```

- Page uid where the annotation is located

    ```typescript
    const annotPageUid = rect.pageUid;
    ```

    if the annotation is deleted, the `pageUid` will return `''`.

{% comment %}

- Axis-aligned bounding box (AABB)

    ```typescript
    const annotAabb = rect.aabb;
    ```

{% endcomment %}

- Creation date & Modification date

    ```typescript
    const creationDate = rect.creationDate; //D:YYYYMMDDHHmmSSOHH'mm'
    const modificationDate = rect.modificationDate; //D:YYYYMMDDHHmmSSOHH'mm'
    ```

    if the annotation is deleted, the `modificationDate` will return `''`.

    If the annotation is created but not be modified after adding, `modificationDate` equals to `creationDate`. 

### Modify the annotation options while creating

If no specific options are passed during the creation of the annotation instance, the generated annotation will have default options.

If you wish to create a custom-configured annotation, you can pass in the specified configuration during creation.

For example, to create a rectangle annotation whose border color is red and background is green.

```typescript
const rectOptions = {
    borderColor: "red",
    background: "green",
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle", rectOptions);
```

### Modify the annotation options dynamically after creating

After creating the annotation, if you want to dynamically modify its configuration, you can use `updateOptions()` method.

For example, to modify an existing rectangle annotation. 

```typescript
const newRectOptions = {
    borderWidth: 2.66,
};

rect.updateOptions(newRectOptions);
```

Even after the annotation has been created to the page by [`createAnnotation()`]({{ site.api }}class/annotationmanager.html#createAnnotation), updating the options will lead to instant changes in the displayed annotation on the page.

### Create an annotation instance after image cropping

After cropping, if no specific options are passed during the creation of the annotation instance, the generated annotation will use default options, which might result in it being invisible.

If you want the annotation to be visible, you can pass specific configurations during its creation.

For example, after cropping an image, if you wish to create a rectangle annotation at position (10, 10) within the visible area.

```typescript
const pageData = await editViewer.currentDocument.getPageData(editViewer.getCurrentPageUid());

const rectOptions = {
    x: pageData.cropBox.left + 10,
    y: pageData.cropBox.top + 10,
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle", rectOptions);
```

### More features

#### Add image to the page by using Stamp Annotation

Observing the structure of [`StampAnnotationOptions`]({{ site.api }}interface/annotationinterface/stampannotationoptions.html), the data type of stamp is `EnumStampIcon` or `Blob`. When stamp is set to `EnumStampIcon`, it indicates that the generated annotation will be displayed as a standard business stamp icon, with the default value being `DRAFT`. When stamp is set to `EnumStampIcon`, it indicates that the generated annotation will be displayed as a standard business stamp icon, with the default value being `DRAFT`. When stamp is set to a Blob, such as the blob of a custom image, it means the annotation will be displayed as an image.

The supported types of standard business stamps are as follows:

| EnumStampIcon | Corresponding stamp |
| ------------- | ------------------- |
| REJECTED      | ![Stamp Rejected](/assets/imgs/stampRejected.png)                    |
| ACCEPTED      | ![Stamp Accepted](/assets/imgs/stampAccepted.png)                    |
| INITAL_HERE   | ![Stamp InitalHere](/assets/imgs/stampInitalHere.png)                    |
| SIGN_HERE     | ![Stamp SignHere](/assets/imgs/stampSignHere.png)                    |
| WITNESS       | ![Stamp Witness](/assets/imgs/stampWitness.png)                    |
| APPROVED      | ![Stamp Approved](/assets/imgs/stampApproved.png)                    |
| NOT_APPROVED  | ![Stamp NotApproved](/assets/imgs/stampNotApproved.png)                    |
| DRAFT         | ![Stamp Draft](/assets/imgs/stampDraft.png)                    |
| FINAL         | ![Stamp Final](/assets/imgs/stampFinal.png)                    |
| COMPLETED     | ![Stamp Completed](/assets/imgs/stampCompleted.png)                    |
| CONFIDENTIAL  | ![Stamp Confidential](/assets/imgs/stampConfidential.png)                    |
| VOID          | ![Stamp Void](/assets/imgs/stampVoid.png)                    |

If set to `blob`, the custom image will be added as the stamp.

```typescript
var blob = /*Sample image blob*/;

const stampOptions = {
    stamp: blob,
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const stamp = await Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "stamp", stampOptions);
```

#### Configure the styling for the part content of text within TextBox annotation or TextTypewriter annotation

The `textContents` attribute in the [`TextBoxAnnotationOptions`]({{ site.api }}interface/annotationinterface/textboxannotationoptions.html) and [`TextTypewriterAnnotationOptions`]({{ site.api }}interface/annotationinterface/texttypewriterannotationoptions.html) accepts an array of [`TextContent`]({{ site.api }}interface/annotationinterface/textcontent.html), which means that even within the same text annotation, you can configure specified text content with different styles.

For example,

```typescript
const testTextContents = [
    {
        content: "Dynamsoft Document Viewer ",
        color: "red",
    },
    {
        content: "Annotation feature",
        color: "green",
        underline: true,
    }
];

const textBoxAnnotationOptions = {
    textContents: testTextContents,
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const textBox = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "textBox", textBoxAnnotationOptions);
```

## Delete annotation(s)

- Delete all annotations which are located on the specified page using [`getAnnotationsByPage()`]({{ site.api }}class/annotationmanager.html#getannotationsbypage) and [`deleteAnnotations()`]({{ site.api }}class/annotationmanager.html#deleteannotations).

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const curPageUid = editViewer.getCurrentPageUid();; // Get the page uid of current page in the edit viewer

const annotations = Dynamsoft.DDV.annotationManager.getAnnotationsByPage(curPageUid);

const annotationUids = annotations.map(obj=>obj.uid);

Dynamsoft.DDV.annotationManager.deleteAnnotations(annotationUids);
```

- Delete all annotations which are located in the specified doc using [`getAnnotationsByDoc()`]({{ site.api }}class/annotationmanager.html#getannotationsbydoc) and [`deleteAnnotations()`]({{ site.api }}class/annotationmanager.html#deleteannotations).

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const curDocUid = editViewer.currentDocument.uid; // Get the doc uid of current document which is open in the edit viewer

const annotations = Dynamsoft.DDV.annotationManager.getAnnotationsByDoc(curDocUid);

const annotationUids = annotations.map(obj=>obj.uid);

Dynamsoft.DDV.annotationManager.deleteAnnotations(annotationUids);
```

- Delete selected annotations using [`getSelectedAnnotations`]({{ site.api }}class/editviewer.html#getselectedannotations) and [`deleteAnnotations()`]({{ site.api }}class/annotationmanager.html#deleteannotations).

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const annotations = editViewer.getSelectedAnnotations(); // Get the selected annotations

const annotationUids = annotations.map(obj=>obj.uid);

Dynamsoft.DDV.annotationManager.deleteAnnotations(annotationUids);
```

## Change layer of an annotation

In the same page, annotations maintain a hierarchical relationship with each other. If you intend to alter the hierarchical level of an annotation, you can employ the following methods.

- Bring forward using [`bringAnnotationForward()`]({{ site.api }}class/annotationmanager.html#bringannotationforward)

    ```typescript
    Dynamsoft.DDV.annotationManager.bringAnnotationForward(rect.uid);
    ```

- Send backward using [`sendAnnotationBackward()`]({{ site.api }}class/annotationmanager.html#sendannotationbackward)

    ```typescript
    Dynamsoft.DDV.annotationManager.sendAnnotationBackward(rect.uid);
    ```

- Bring to front using [`bringAnnotationToFront()`]({{ site.api }}class/annotationmanager.html#bringannotationtofront)

    ```typescript
    Dynamsoft.DDV.annotationManager.bringAnnotationToFront(rect.uid);
    ```

- Send to back using [`sendAnnotationToBack()`]({{ site.api }}class/annotationmanager.html#sendannotationtoback)

    ```typescript
    Dynamsoft.DDV.annotationManager.sendAnnotationToBack(rect.uid);
    ```

## Redaction

A redaction annotation identifies content that is intended to be removed from the document. Redaction involves two processes:

* Content identification. A user creates redact annotations that specify the pieces or regions of content that should be removed. Up until the next step is performed, the user can see, move and redefine these annotations.
* Content removal. The user instructs the viewer application to apply the redact annotations, after which the content in the area specified by the redact annotations is removed. In the removed content's place, some marking appears to indicate the area has been redacted. Also, the redact annotations are removed from the PDF document.

1. Create redaction annotations by searching text.

   ```js
   const searcher = editViewer.currentDocument.createTextSearcher("content to redact",{caseSensitive:false});
   const results = await searcher.getResults(0); //search the results on the first page
   for (const result of results) {
     Dynamsoft.DDV.annotationManager.createAnnotation(
       editViewer.getCurrentPageUid(),
       "redaction",
       { "rects": result.rects }
     );
   }
   ```
   
   In Dynamsoft Document Viewer, there are two types of redaction annotation: text and rectangle. Text-type redaction annotation can be created by selecting text and can have multiple rectangles in `rects`. Rectangle redaction can only have one rectangle in `rects` and can be adjusted freely.

2. Apply the redaction annotation.

   ```js
   let success = await Dynamsoft.DDV.annotationManager.applyRedactions(editViewer.getCurrentPageUid());
   ```