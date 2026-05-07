---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - BrowseViewer Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, BrowseViewer Class
breadcrumbText: BrowseViewer Class
description: Dynamsoft Document Viewer Documentation API Reference BrowseViewer Class Page
permalink: /api/class/browseviewer.html
---

# BrowseViewer Class

Browse Viewer is used to display pages in multiple-mode, pages can be multiple selected in this viewer.

## API Index

**Create and Destroy Instances** 

| API Name       | Description                                   |
| ------------ | --------------------------------------------- |
| [`BrowseViewer()`](#browseviewer) | Default constructor of a `BrowseViewer` instance. |
| [`destroy()`](#destroy)             | Destroy the `BrowseViewer` instance.                             |

**Viewer Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`bindContainer()`](#bindcontainer)     | Bind the viewer to the specified container.                  |
| [`unbindContainer()`](#unbindcontainer) | Unbind the viewer from the specified container.              |
| [`isBoundContainer`](#isboundcontainer) | Return whether the viewer is bound to a container. |
| [`getStyle()`](#getstyle)            | Get the style object of `BrowseViewer`.                        |
| [`getVisiblePagesInfo()`](#getVisiblePagesInfo)               | Get the visible pages info                |
| [`updateStyle()`](#updatestyle)        | Update the style object of `BrowseViewer`.                     |
| [`getUiConfig()`](#getuiconfig)         | Get current `UiConfig` object.                               |
| [`updateUiConfig()`](#updateuiconfig)     | Update `UiConfig` object.                                    |
| [`show()`](#show)                | Show the viewer.                                             |
| [`hide()`](#hide)                | Hide the viewer.                                             |
| [`isVisible`](#isvisible)        | Return whether the viewer is shown or hidden.      |
| [`multiselectMode`](#multiselectmode) | Specify or return whether to allow multiple pages to be selected at once. |

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
| [`getSelectedPageIndices()`](#getselectedpageindices) | Get indices of selected pages.                               |
| [`selectPages()`](#selectpages)            | Select pages by specified indices.                           |
| [`selectAllPages()`](#selectallpages)         | Select all pages.                                            |


**Display Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`setRowAndColumn()`](#setrowandcolumn)        | Set rows and columns of displayed pages.                     |

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
| [`selectedPagesChanged`](#selectedpageschanged) |
| [`scroll`](#scroll) |
| [`pagesDragged`](#pagesdragged)         |
| [`pagesDropped`](#pagesdropped)         |
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

### BrowseViewer()

Default constructor of a `BrowseViewer` instance.

**Syntax**

```typescript
new Dynamsoft.DDV.BrowseViewer(options?: BrowseViewerConstructorOptions);
```

**Parameters**

`options`: The constructor options for a `BrowseViewer` instance. Please refer to [`BrowseViewerConstructorOptions`](/api/interface/browseviewerconstructoroptions.md).

**Code Snippet**

```typescript
const browseViewer = new Dynamsoft.DDV.BrowseViewer({
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

Destroy the `BrowseViewer` instance.

**Syntax**

```typescript
destroy(): void;
```

**Code Snippet**

```typescript
browseViewer.destroy();
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
browseViewer.bindContainer("viewercontainer");
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
browseViewer.unbindContainer();
```

### isBoundContainer

Return whether the viewer is bound to a container.

**Syntax**

```typescript
readonly isBoundContainer: boolean;
```

### getStyle()

Get the style object of `BrowseViewer`.

**Syntax**

```typescript
getStyle(browseViewerStyleName: BrowseViewerStyleName): BrowseViewerStyle | null;
```

**Parameters**

`browseViewerStyleName`: A `BrowseViewerStyleName` can be one of eight types.

```typescript
type BrowseViewerStyleName = "canvasStyle" | "pageStyle" | "selectedPageStyle" | "currentPageStyle" | "hoveredPageStyle" | "placeholderStyle" | "pageNumberStyle" | "checkboxStyle";
```

**Return values**

The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html).

**Code Snippet**

```typescript
// Get pageStyle object;
const pageStyle = browseViewer.getStyle("pageStyle");
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

Update the style object of `BrowseViewer`.

**Syntax**

```typescript
updateStyle(browseViewerStyleName: BrowseViewerStyleName, browseViewerStyle: BrowseViewerStyle): boolean;
```

**Parameters**

`browseViewerStyleName`: A `BrowseViewerStyleName` can be one of eight types.

```typescript
type BrowseViewerStyleName = "canvasStyle" | "pageStyle" | "selectedPageStyle" | "currentPageStyle" | "hoveredPageStyle" | "placeholderStyle" | "pageNumberStyle" | "checkboxStyle";
```

`browseViewerStyle`: The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html).

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

- First method

    ```typescript
    // Get style object
    const pageStyle = browseViewer.getStyle("pageStyle");

    // Modify the style object
    pageStyle.background = "red";
    pageStyle.border = "1px solid green";

    // Update page style
    browseViewer.updateStyle("pageStyle", pageStyle);
    ```

- Second method

    ```typescript
    // Update the style object directly
    browseViewer.updateStyle("pageStyle", {
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
const viewerUi = browseViewer.getUiConfig();
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
const sidebar = {
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    style: {
        width: "80px",
    },
    children: [
        Dynamsoft.DDV.Elements.Load,
        Dynamsoft.DDV.Elements.DeleteAll,
    ],
};

const viewerUi = browseViewer.getUiConfig();

viewerUi.children.splice(0,0,sidebar);

browseViewer.updateUiConfig(viewerUi); // Configure a sidebar which includes "Load" and "DeleteAll" elements.
```
Or,

```typescript
const header = {
    type: Dynamsoft.DDV.Elements.Layout,
    style: {
        height: "80px",
    },
    children: [
        Dynamsoft.DDV.Elements.Pagination,
        Dynamsoft.DDV.Elements.DeleteAll,
    ],
};

const viewerUi =  {
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    children: [
        header,
        Dynamsoft.DDV.Elements.MainView,
    ],
}

browseViewer.updateUiConfig(viewerUi); // Configure a header which includes "Pagination" and "DeleteAll" elements.
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
browseViewer.show();
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
browseViewer.hide();
```

### isVisible

Return whether the viewer is shown or hidden.

**Syntax**

```typescript
readonly isVisible: boolean;
```

**Remark**

- The viewer is shown automatically when it is created which means the default value of `isVisible` is `true`.

### multiselectMode

Specify or return whether to allow multiple pages to be selected at once.

**Syntax**

```typescript
multiselectMode: boolean; 
```

**Example**

```typescript
browseViewer.multiselectMode = true;
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   

**Remark**

If it is not specified in [`viewerConfig`]({{ site.api }}interface/browseviewerconstructoroptions.html#viewerconfig) while creating the viewer additionally, its default value is `false`.

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
browseViewer.openDocument("lnn0ll9o124");

// OR
// Assume there is a document object firstDoc.
const docUid = firstDoc.uid;
browseViewer.openDocument(docUid);
browseViewer.openDocument(firstDoc);
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
browseViewer.closeDocument();
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
const currentDoc = browseViewer.currentDocument;
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
const pageCount = browseViewer.getPageCount();
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
browseViewer.goToPage(3);
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
const currentIndex = browseViewer.getCurrentPageIndex();
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
const curPageUid = browseViewer.getCurrentPageUid();
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
const firstPageUid = browseViewer.indexToUid(0);
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
const curPageUid = browseViewer.getCurrentPageUid();
browseViewer.uidToIndex(curPageUid);
```

**Warning**

 Error Code  | Error Message                                             | API Return Value
--------|----------------------------------------------------------|------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.        | `-1`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.       | `-1`
 -80105 | *XXX(API)*: The specified page(s) do not exist.  | `-1`
 -80304 | No document opened.                                      | `-1`
 -80305 | There is no image in the current document.               | `-1`

### getSelectedPageIndices()

Get indices of selected pages.

**Syntax**

```typescript
getSelectedPageIndices(): number[];
```

**Return Value**

The array of the selected pages' indices.

**Example**

```typescript
const selPages = browseViewer.getSelectedPageIndices();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `[]`

**Remark**

- If no page is selected in the viewer, returns [].
- The order of the returned array elements is based on the order in which the pages are selected. For example, if select the pages with the index 6, 5, 2 in order, the returned array will be [6,5,2].

### selectPages()

Select pages by specified indices.

**Syntax**

```typescript
selectPages(indices: number[]): string[];
```

**Parameters**

`indices`: Specify the indices of the pages to be selected. If set to an empty array `[]`, no pages will be selected.

**Return Value**

The array of selected pages' uids.

**Example**

```typescript
// Select the first and second pages.
browseViewer.selectPages([0,1]);
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `[]`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `[]`
 -80304 | No document opened.                                 | `[]`

### selectAllPages()

Select all pages.

**Syntax**

```typescript
selectAllPages(): string[];
```

**Return Value**

The array of selected pages' uids.

**Example**

```typescript
browseViewer.selectAllPages();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `[]`
 -80305 | There is no image in the current document.          | `[]`


## Display Control

### setRowAndColumn()

Set rows and columns of displayed pages.

**Syntax**

```typescript
setRowAndColumn(
    rows: number, 
    columns: number 
): boolean;
```
**Parameters**

`rows`: The number of rows. The maximum value is 20.

`columns`: The number of columns. The maximum value is 20.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Example**

```typescript
browseViewer.setRowAndColumn(5,8); // Display the page in five rows and eight columns.
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.     | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`

**Remark**

- If it is not specified in [`viewerConfig`]({{ site.api }}interface/browseviewerconstructoroptions.html#viewerconfig) while creating the viewer additionally, its default rows is 4 and columns is 6.

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
browseViewer.rotate(90, [0,1]);

// Rotate current page 90 degrees counterclockwise.
browseViewer.rotate(-90);
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
browseViewer.saveOperations();
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

browseViewer.on("resized", eventFunc);
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

browseViewer.on("resized", eventFunc);

// Unbind the specified event listener.
browseViewer.off("resized", eventFunc);
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

#### selectedPagesChanged

Triggered when the page(s) is selected.

***Callback***

 `SelectedPagesChangedEvent`: An EventObject.

***Attributes***

`oldIndices[]`: The array of old selected pages indices.

`oldPageUids[]`: The array of old selected pages uids.

`newIndices[]`: The array of new selected pages indices.

`newPageUids[]`: The array of new selected pages uids.

#### scroll

Triggered when the viewer is scrolled. It will return the native event object.

#### pagesDragged

Triggered when page(s) is dragged.

***Callback***

 `PageDraggedEvent`: An EventObject.

***Attributes***

`indices[]` : The array of the dragged pages indices.

`pageUids[]`: The array of the dragged pages uids.

#### pagesDropped

Triggered when page(s) is dropped.

***Callback***

 `PageDroppedEvent`: An EventObject.

***Attributes***

`indicesBefore[]`: The array of the dropped pages indices before dropping.

`indicesAfter[]`: The array of the dropped pages indices after dropping.

`pageUids[]`: The array of the dropped pages uids.


#### visibilityChanged

Triggered when the viewer's visibility is changed. It will return an `isVisible` boolean value.

#### paginationChanged

Triggered when the viewer's current page number or the page count is changed. It will return an [`IPaginationChangedEvent`](/api/interface/ipaginationchangedevent.md) object.

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