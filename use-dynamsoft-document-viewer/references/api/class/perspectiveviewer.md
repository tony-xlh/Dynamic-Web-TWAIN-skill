---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - PerspectiveViewer Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, PerspectiveViewer Class
breadcrumbText: PerspectiveViewer Class
description: Dynamsoft Document Viewer Documentation API Reference PerspectiveViewer Class Page
permalink: /api/class/perspectiveviewer.html
---

# PerspectiveViewer Class

Perspective Viewer is used to do page boundaries manual adjustment & perspective transformation. The page data displayed on this viewer is its original data.

## API Index

**Create and Destroy Instances** 

| API Name       | Description                                   |
| ------------ | --------------------------------------------- |
| [`PerspectiveViewer()`](#perspectiveviewer) | Default constructor of a `PerspectiveViewer` instance. |
| [`destroy()`](#destroy)             | Destroy the `PerspectiveViewer` instance.                             |

**Viewer Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`bindContainer()`](#bindcontainer)     | Bind the viewer to the specified container.                  |
| [`unbindContainer()`](#unbindcontainer) | Unbind the viewer from the specified container.              |
| [`isBoundContainer`](#isboundcontainer) | Return whether the viewer is bound to a container. |
| [`getStyle()`](#getstyle)            | Get the style object of `PerspectiveViewer`.                        |
| [`getVisiblePagesInfo()`](#getVisiblePagesInfo)               | Get the visible pages info                |
| [`updateStyle()`](#updatestyle)        | Update the style object of `PerspectiveViewer`.                     |
| [`getUiConfig()`](#getuiconfig)         | Get current `UiConfig` object.                               |
| [`updateUiConfig()`](#updateuiconfig)     | Update `UiConfig` object.                                    |
| [`show()`](#show)                | Show the viewer.                                             |
| [`hide()`](#hide)                | Hide the viewer.                                             |
| [`isVisible`](#isvisible)        | Return whether the viewer is shown or hidden.      |

**Document and Page Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`openDocument()`](#opendocument)        | Open the specified document by document uid.                 |
| [`closeDocument()`](#closedocument)       | Close current document.                                      |
| [`currentDocument`](#currentdocument)   | Return the object of the current document.         |
| [`getPageCount()`](#getpagecount)        | Get the page count in the viewer.                            |
| [`goToPage()`](#gotopage)            | Navigate to the specified page by index.                     |
| [`getCurrentPageIndex()`](#getcurrentpageindex) | Get the index of current page.                               |
| [`getCurrentPageUid()`](#getcurrentpageuid)   | Get the uid of the current page.                             |
| [`indexToUid()`](#indextouid)          | Get the uid of the specified page by its index.                      |
| [`uidToIndex()`](#uidtoindex)          | Get the index of the specified page by its uid. |

**Perspective Transformation**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`setQuadSelection()`](#setquadselection)    | Set a quadrilateral selection on the current page.              |
| [`getQuadSelection()`](#getquadselection)    | Get the quadrilateral selection.                                |
| [`resetQuadSelection()`](#resetquadselection)  | Reset the quadrilateral selection to the original one.          |
| [`applyPerspective()`](#applyperspective)         | Performs a perspective transformation in current page based on the specified quadrangle. |

**Edit Operations**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`rotate()`](#rotate)              | Rotate the specified pages.                                  |
| [`saveOperations()`](#saveoperations)      | Save the edit operations in pages to document.               |

**Events**

| API Name | Description                                        |
| -------- | -------------------------------------------------- |
| [`on()`](#on)     | Bind a listener to the specified event.            |
| [`off()`](#off)    | Unbind event listener(s) from the specified event. |

***Integrated Events***

| Event Name          |
| ------------------- |
| [`resized`](#resized)             |
| [`pageRendered`](#pagerendered)        |
| [`currentIndexChanged`](#currentindexchanged) |
| [`currentPageChanged`](#currentpagechanged)  |
| [`quadModified`](#quadmodified)    |
| [`click`](#click)               |
| [`dblclick`](#dbclick)            |
| [`rightclick`](#rightclick)          |
| [`visibilityChanged`](#visibilitychanged)                   |
| [`paginationChanged`](#paginationchanged)                   |
| [`pointerdown`](#pointerdown)                   |
| [`pointermove`](#pointermove)                   |
| [`pointerup`](#pointerup)                   |
| [`pageover`](#pageover)                   |
| [`pageout`](#pageout)                   |


## Create and Destroy Instances

### PerspectiveViewer()

Default constructor of a `PerspectiveViewer` instance.

**Syntax**

```typescript
new Dynamsoft.DDV.PerspectiveViewer(options?: PerspectiveViewerConstructorOptions);
```

**Parameters**

`options`: The constructor options for a `PerspectiveViewer` instance. Please refer to [`PerspectiveViewerConstructorOptions`]({{ site.api }}interface/perspectiveviewerconstructoroptions.html).

**Code Snippet**

```typescript
const perspectiveViewer = new Dynamsoft.DDV.PerspectiveViewer({
    container: document.getElementById("viewer"),
});
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                                     
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                           
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license.  
 -80050 | DDV.Core.init() has not been set up yet.  
 -80051 | DDV.Core.init() has not been completed.   

### destroy()

Destroy the `PerspectiveViewer` instance.

**Syntax**

```typescript
destroy(): void;
```

**Code Snippet**

```typescript
perspectiveViewer.destroy();
```

**Remark**

- The editing operations (rotating) in pages will be saved to document automatically when destroy the viewer instance.

**See Also**

[saveOperations](#saveoperations)

## Viewer Control

### bindContainer()

Bind the viewer to the specified container.

**Syntax**

```typescript
bindContainer(container: string | HTMLElement): void;
```

**Parameters**

`container`: The container which is used to show the viewer. Its `id` or `HTMLElement` is acceppted.

**Code Snippet**

```typescript
// Assume there is a container with id "viewercontainer" on the page.
perspectiveViewer.bindContainer("viewercontainer");
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80301 | The specified container does not exist. 

**Remark**

- A viewer can only be bound to one container at once. If you bind the viewer to another container when it has been bound to a container, the viewer will be bound to the new container and unbound from the old container automatically. 

### unbindContainer()

Unbind the viewer from the specified container.

**Syntax**

```typescript
unbindContainer(): void;
```

**Code Snippet**

```typescript
perspectiveViewer.unbindContainer();
```

### isBoundContainer

Return whether the viewer is bound to a container.

**Syntax**

```typescript
readonly isBoundContainer: boolean;
```

### getStyle()

Get the style object of `PerspectiveViewer`.

**Syntax**

```typescript
getStyle(perspectiveViewerStyleName: PerspectiveViewerStyleName): PerspectiveViewerStyle | null;
```

**Parameters**

`perspectiveViewerStyleName`: A `PerspectiveViewerStyleName` can be one of three types.

```typescript
type PerspectiveViewerStyleName = "canvasStyle" | "pageStyle" | "quadSelectionStyle";
```

**Return values**

The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html)..

**Code Snippet**

```typescript
// Get pageStyle object;
const pageStyle = perspectiveViewer.getStyle("pageStyle");
```

**Warning**

 Error Code  | Error Message                                                            | API Return Value
--------|-------------------------------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `null`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `null`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `null`

### getVisiblePagesInfo()

Get the visible pages info.

**Syntax**

```typescript
getVisiblePagesInfo(): PageVisualInfo[];
```

**Return values**

Array of the `PageVisualInfo` object. Please refer to [`PageVisualInfo`](/api/interface/pagevisualinfo.md).

### updateStyle()

Update the style object of `PerspectiveViewer`.

**Syntax**

```typescript
updateStyle(perspectiveViewerStyleName: PerspectiveViewerStyleName, perspectiveViewerStyle: PerspectiveViewerStyle): boolean;
```

**Parameters**

`perspectiveViewerStyleName`: A `PerspectiveViewerStyleName` can be one of three types.

```typescript
type PerspectiveViewerStyleName = "canvasStyle" | "pageStyle" | "quadSelectionStyle";
```

`perspectiveViewerStyle`: The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html).

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

- First method

    ```typescript
    // Get style object
    const pageStyle = perspectiveViewer.getStyle("pageStyle");

    // Modify the style object
    pageStyle.background = "red";
    pageStyle.border = "1px solid green";

    // Update page style
    perspectiveViewer.updateStyle("pageStyle", pageStyle);
    ```

- Second method

    ```typescript
    // Update the style object directly
    perspectiveViewer.updateStyle("pageStyle", {
        background: "red",
        border: "1px solid green",
    });
    ```

**Warning**

 Error Code  | Error Message                                                            | API Return Value
--------|-------------------------------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `false`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `false`


**Remark**

- The updates are independent of whether the viewer is displayed and are updated in real time.

### getUiConfig()

Get current `UiConfig` object.

**Syntax**

```typescript
getUiConfig(): UiConfig;
```

**Return Value**

The [`UiConfig`]({{ site.api }}interface/uiconfig.html) object.

**Code Snippet**

```typescript
const viewerUi = perspectiveViewer.getUiConfig();
```

### updateUiConfig()

Update `UiConfig` object.

**Syntax**

```typescript
updateUiConfig(uiConfig: UiConfig): boolean;
```

**Parameters**

`uiConfig`: The [`UiConfig`]({{ site.api }}interface/uiconfig.html) to update.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
const viewerUi = Dynamsoft.DDV.getDefaultUiConfig("perspectiveViewer");
const header = viewerUi.children[0];
header.children.splice(0,0,Dynamsoft.DDV.Elements.Load); //Add Load element in header.
perspectiveViewer.updateUiConfig(viewerUi);
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`
 -80313 | The element *XXX(ElementName)* is not supported in *XXX(ClassName)* class.      | `false`

**Remark**

- The updates are independent of whether the viewer is displayed and are updated in real time.

### show()

Show the viewer.

**Syntax**

```typescript
show(): void;
```

**Code Snippet**

```typescript
perspectiveViewer.show();
```

**Remark**

- The viewer is shown automatically when it is created.

### hide()

Hide the viewer.

**Syntax**

```typescript
hide(): void;
```

**Code Snippet**

```typescript
perspectiveViewer.hide();
```

### isVisible

Return whether the viewer is shown or hidden.

**Syntax**

```typescript
readonly isVisible: boolean;
```

**Remark**

- The viewer is shown automatically when it is created which means the default value of `isVisible` is `true`.

## Document and Page Control

### openDocument()

Open the specified document.

**Syntax**

```typescript
openDocument(docUid: string | doc: IDocument): void;
```

**Parameters**

`docUid`: The uid of the specified document. 

`doc`: The object of the document to open. Please refer to [IDocument]({{ site.api }}interface/idocument/index.html).

**Code Snippet**

```typescript
// Assume there is a document whose id is "lnn0ll9o124".
perspectiveViewer.openDocument("lnn0ll9o124");

// OR
// Assume there is a document object firstDoc.
const docUid = firstDoc.uid;
perspectiveViewer.openDocument(docUid);
perspectiveViewer.openDocument(firstDoc);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: docUid or doc is invalid.   
 -80102 | *XXX(API)*: docUid or doc is missing.   
 -80104 | *XXX(API)*: The specified document(s) do not exist.  

**Remark**

- If another ducument is opened when there is a document already opened, the opened document will be closed automatically.

### closeDocument()

Close current document.

**Syntax**

```typescript
closeDocument(): boolean; 
```

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
perspectiveViewer.closeDocument();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `false`

### currentDocument

Return the object of the current document.

**Syntax**

```typescript
readonly currentDocument: IDocument | null;
```

**Code Snippet**

```typescript
const currentDoc = perspectiveViewer.currentDocument;
```

**See Also**

[IDocument]({{ site.api }}interface/idocument/index.html)

### getPageCount()

Get the page count in the viewer.

**Syntax**

```typescript
getPageCount(): number;
```

**Return Value**

The page count.

**Code Snippet**

```typescript
const pageCount = perspectiveViewer.getPageCount();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `-1`

### goToPage()

Navigate to the specified page by index.

**Syntax**

```typescript
goToPage(index: number): number;
```

**Parameters**

`index`: The index of the page which need to navigate to.

**Return Value**

The index of the page which navigate to.

**Code Snippet**

```typescript
// Navigate to page 4.
perspectiveViewer.goToPage(3);
```

**Warning**

 Error Code  | Error Message                                             | API Return Value
--------|----------------------------------------------------------|------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.        | `-1`
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.    | `-1`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.       | `-1`
 -80304 | No document opened.                                      | `-1`
 -80305 | There is no image in the current document.               | `-1`

### getCurrentPageIndex()

Get the index of the current page.

**Syntax**

```typescript
getCurrentPageIndex(): number; 
```

**Return Value**

The index of the current page.

**Code Snippet**

```typescript
const currentIndex = perspectiveViewer.getCurrentPageIndex();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `-1`
 -80305 | There is no image in the current document.          | `-1`

### getCurrentPageUid()

Get the uid of the current page.

**Syntax**

```typescript
getCurrentPageUid(): string;
```

**Return Value**

The uid of the current page.

**Code Snippet**

```typescript
const curPageUid = perspectiveViewer.getCurrentPageUid();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `''`
 -80305 | There is no image in the current document.          | `''`

### indexToUid()

Get the uid of the specified page by its index.

**Syntax**

```typescript
indexToUid(index: number): string;
```

**Parameters**

`index`: The index of the specified page.

**Return Value**

The uid of the page.

**Code Snippet**

```typescript
// Get the first page's uid
const firstPageUid = perspectiveViewer.indexToUid(0);
```

**Warning**

 Error Code  | Error Message                                             | API Return Value
--------|----------------------------------------------------------|------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.        | `''`
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.    | `''`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.       | `''`
 -80304 | No document opened.                                      | `''`
 -80305 | There is no image in the current document.               | `''`

### uidToIndex()

Get the index of the specified page by its uid.

**Syntax**

```typescript
uidToIndex(pageUid: string): number;
```

**Parameters**

`pageUid`: The uid of the specified page.

**Return Value**

The index of the page.

**Code Snippet**

```typescript
const curPageUid = perspectiveViewer.getCurrentPageUid();
perspectiveViewer.uidToIndex(curPageUid);
```

**Warning**

 Error Code  | Error Message                                             | API Return Value
--------|----------------------------------------------------------|------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.        | `-1`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.       | `-1`
 -80105 | *XXX(API)*: The specified page(s) do not exist.  | `-1`
 -80304 | No document opened.                                      | `-1`
 -80305 | There is no image in the current document.               | `-1`

## Perspective Transformation

### setQuadSelection()

Set a quadrilateral selection on the current page.

**Syntax**

```typescript
setQuadSelection(quad: Quad): boolean;
```

**Parameters**

`quad`: A quadrangle. Please refer to [`Quad`]({{ site.api }}enumeration-type/quad.html).

**Example**

```typescript
const quad = [
    [80,200],
    [180,120],
    [115,340],
    [70,330]
];

perspectiveViewer.setQuadSelection(quad);
```

**Warning**

 Error Code  | Error Message                                              | API Return Value
--------|-----------------------------------------------------------|-------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.         | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.        | `false`
 -80304 | No document opened.                                       | `false`
 -80305 | There is no image in the current document.                | `false`
 -80312 | The specified quad exceeds the bounds of the current page.| `false`


**Remark**

- In the viewer, only one quadrilateral selection can exist on the page at a time, which means if there is a quadrilateral selection existed when a new selection is drawn, the old one will be clear automatically.

### getQuadSelection()

Get the quadrilateral selection.

**Syntax**

```typescript
getQuadSelection(): Quad | null;
```

**Return value**

A quadrangle. Please refer to [`Quad`]({{ site.api }}enumeration-type/quad.html).

**Example**

```typescript
const quad = perspectiveViewer.getQuadSelection();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|---------------------
 -80304 | No document opened.                                 | `null`
 -80305 | There is no image in the current document.          | `null`

### resetQuadSelection()

Reset the quadrilateral selection to the original one. The original selection means the last saved one.

**Syntax**

```typescript
resetQuadSelection(indices?: number[]): boolean;
```

**Parameters**

`indices`: The array of the pages indices which will be reset. If not set, the current page will be reset.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Example**

```typescript
perspectiveViewer.resetQuadSelection();
```

**Warning**

 Error Code  | Error Message                                              | API Return Value
--------|-----------------------------------------------------------|-------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.         | `false`
 -80304 | No document opened.                                       | `false`
 -80305 | There is no image in the current document.                | `false`


### applyPerspective()

Performs a perspective transformation in current page based on the specified quadrangle.

**Syntax**

```typescript
applyPerspective(quad: Quad): Promise<Blob>;
```

**Parameters**

`quad`: The quadrangle to be transferred. Please refer to [`Quad`]({{ site.api }}enumeration-type/quad.html).

**Return value**

The Blob of the result image after perspective transformation.

**Example**

```typescript
const quad = perspectiveViewer.getQuadSelection();

await perspectiveViewer.applyPerspective(quad);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80304 | No document opened.                                 
 -80305 | There is no image in the current document. 
 -80312 | The specified quad exceeds the bounds of the current page.         

## Edit Operations

### rotate()

Rotate the specified pages.

**Syntax**

```typescript
rotate(
    angle: number,
    indices?: number[] 
): boolean; 
```

**Parameters**

`angle`: Specify the angle. Only multiples of 90 degrees are supported. Clockwise rotation is positive, counterclockwise rotation is negative.

`indices`: The array of the pages indices which will be rotated. If not set, the current page will be rotated.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
// Rotate the first and second pages 90 degrees clockwise.
perspectiveViewer.rotate(90, [0,1]);

// Rotate current page 90 degrees counterclockwise.
perspectiveViewer.rotate(-90);
```

**Warning**

 Error Code  | Error Message                                                       | API Return Value
--------|-------------------------------------------------------------------------|-------------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `false`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `false`
 -80304 | No document opened.                                                     | `false`
 -80305 | There is no image in the current document.                              | `false`

### saveOperations()

> *This method takes effect only for [rotate](#rotate) operation.*

Save the edit operations in pages to document.

**Syntax**

```typescript
saveOperations(): boolean;
```

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
perspectiveViewer.saveOperations();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|-----------------
 -80304 | No document opened.                                 | `false`

## Events

### on()

Bind a listener to the specified event. 

**Syntax**

```typescript
on(eventName: EventName, listener:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It can be [an integrated event name](#integrated-events) or a custom event name configured through [`UiConfig`-`events`]({{ site.api }}interface/uiconfig.html#events).

`listener`: Specify the listener.

**Code Snippet**

```typescript
// Bind a listener to the integrated event resized.
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.oldWidth);
    console.log(e.newWidth);
};

perspectiveViewer.on("resized", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  


### off()

Unbind event listener(s) from the specified event. 

**Syntax**

```typescript
off(eventName: EventName, listener?:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It can be [an integrated event name](#integrated-events) or a custom event name configured through [`UiConfig`-`events`]({{ site.api }}interface/uiconfig.html#events).

`listener`: Specify the listener. If no listener is specified, unbind all event listeners from the specified event.

**Code Snippet**

```typescript
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.oldWidth);
    console.log(e.newWidth);
};

perspectiveViewer.on("resized", eventFunc);

// Unbind the specified event listener.
perspectiveViewer.off("resized", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

### Integrated Events

#### resized

Triggered when the viewer is resized.

**Callback**

`ResizedEvent`: An EventObject.

**Attributes**

`oldWidth`: The old width of the viewer.

`oldHeight`: The old height of the viewer.

`newWidth`: The new width of the viewer.

`newHeight`: The new height of the viewer.

#### pageRendered

Triggered when a page has been completely rendered. We only render the pages that are visible on the screen, so this event won't get fired for every page in the document at once. This event will get called when the user scrolls up and down the document, or when a page is rotated, or anything else that makes it rerender.

**Callback**

`PageRenderedEvent`: An EventObject.

**Attributes**

`index`: The index of the rendered page.

`pageUid`: The pageUid of the rendered page.

#### currentIndexChanged

Triggered when currentIndex is changed.

**Callback**  

`CurrentindexChangedEvent`: An EventObject.

**Attributes**

`oldIndex`: The old current index.

`newIndex`: The new current index. If there is no index in the viewer, return `-1`.

#### currentPageChanged

Triggered when current page is changed.

**Callback**

`CurrentPageChangedEvent`: An EventObject.

**Attributes**

`oldPageUid`: The uid of the page which is old current index. If the old page is removed, return `''`.

`newPageUid`: The uid of the page which is new current index. If there is no index in the viewer, return `''`.

#### quadModified

Triggered when the quadrilateral selection is modified. Please refer to [`IQuadModifiedEvent`](/api/interface/iquadmodifiedevent.md).

#### paginationChanged

Triggered when the viewer's current page number or the page count is changed. It will return an [`IPaginationChangedEvent`](/api/interface/ipaginationchangedevent.md) object.

#### visibilityChanged

Triggered when the viewer's visibility is changed. It will return an `isVisible` boolean value.

#### pointerdown

Triggered when a pointer becomes active buttons state. It will return an [`IPointerEvent`](/api/interface/ipointerevent.md) object.

#### pointermove

Triggered when a pointer changes coordinates. It will return an [`IPointerEvent`](/api/interface/ipointerevent.md) object.

#### pointerup

Triggered when a pointer is no longer active buttons state. It will return an [`IPointerEvent`](/api/interface/ipointerevent.md) object.

#### pageover

Triggered when a pointer is moved into a page's hit test boundaries. It will return an [`IPointerEvent`](/api/interface/ipointerevent.md) object.

#### pageout

Triggered when a pointer is moved out of the hit test boundaries of a page. It will return an [`IPointerEvent`](/api/interface/ipointerevent.md) object.

#### Mouse Events

##### click

Triggered when click in the viewer's viewing area. On mobile device, triggered when tap in the viewer's viewing area.

##### dblclick

Triggered when double click in the viewer's viewing area.

##### rightclick

Triggered when right click in the viewer's viewing area. On mobile device, triggered when long-tap in the viewer's viewing area.

**Callback for mouse events**

 `IPointerEvent`: An EventObject.

**Attributes**

`index`: The page index.

`pageUid`: The page uid.

`imageX`: The relative x-coordinate of the click pointer on the image.

`imageY`: The relative y-coordinate of the click pointer on the image.

`canvasX`: The relative x-coordinate of the click pointer on the canvas.

`canvasY`: The relative x-coordinate of the click pointer on the canvas.

`nativeEvent`: [`PointerEvent`](https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent)