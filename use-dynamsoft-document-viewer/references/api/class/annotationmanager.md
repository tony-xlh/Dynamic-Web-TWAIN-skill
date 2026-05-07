---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - AnnotationManager Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, AnnotationManager Class
breadcrumbText: AnnotationManager Class
description: Dynamsoft Document Viewer Documentation API Reference AnnotationManager Class Page
permalink: /api/class/annotationmanager.html
---

# AnnotationManager Class

The `Dynamsoft.DDV.annotationManager` instance will be created automatically as soon as DDV is initialized. Please refer to [`annotationManager`]({{ site.api }}namespace/ddv.html#static-annotationmanager).

## API Index

**Methods**

| API Name                       | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| [`applyRedactions()`](#applyredactions)          | Apply redaction annotations. |
| [`createAnnotation()`](#createAnnotation)          | Create an annotation instance. |
| [`getAnnotationsByUids()`](#getannotationsbyuids)   | Get annotations by annotation uids.                          |
| [`getAnnotationsByPage()`](#getannotationsbypage)   | Get annotations in specified page.                           |
| [`getAnnotationsByDoc()`](#getannotationsbydoc)    | Get all annotations in specified document.                   |
| [`deleteAnnotations()`](#deleteannotations)      | Delete specified annotations.                                |
| [`bringAnnotationForward()`](#bringannotationforward) | Bring the specified annotation forward.                      |
| [`sendAnnotationBackward()`](#sendannotationbackward) | Send the specified annotation backward.                      |
| [`bringAnnotationToFront()`](#bringannotationtofront) | Bring the specified annotation in front of all other annotations. |
| [`sendAnnotationToBack()`](#sendannotationtoback)   | Send the specified annotation behind all other annotations.  |
{% comment %}
| [`importXfdf()`](#importxfdf)             | Import annotations in an XFDF(XML) string to the specified document. |
| [`exportXfdf()`](#exportxfdf)             | Export all annotations from the specified document as an XFDF(XML) string. |
{% endcomment %}


**Events**

| API Name | Description                                        |
| -------- | -------------------------------------------------- |
| [`on()`](#on)     | Bind a listener to the specified event.            |
| [`off()`](#off)    | Unbind event listener(s) from the specified event. |


***Integrated Events***

| Event Name      | Description                               |
| --------------- | ----------------------------------------- |
| [`annotationsAdded`](#annotationsadded) | Triggered when new annotation(s) is added. |
| [`annotationsDeleted`](#annotationsdeleted) | Triggered when annotation(s) is deleted.     |
| [`annotationLayerChanged`](#annotationlayerchanged) | Triggered when annotation's layer is changed.     |
| [`annotationsModified`](#annotationsmodified) | Triggered when annotation(s) is modified.     |


## Methods

### applyRedactions()

Apply redaction annotations.

**Syntax**

```typescript
applyRedactions(pageUid: string, annotationUids?: string[]): Promise<boolean>;
```

**Parameters**

`pageUid`: Specify the page to apply redaction annotations.

`annotationUids`: Specify the array of uids of redaction annotations to apply for one page. If it is empty, all the redaction annotations on the specified page will be used.

**Return value**

A Promise object which indicates whether the operation is successful or not.

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.
 -80105 | *XXX(API)*: The specified page(s) do not exist.   
 -80324 | The specified annotation(s) contain annotations other than redaction annotations.
 -80325 | The specified page does not contain redaction annotations.
 -80327 | The specified annotation(s) are not on the specified page or do not exist.


### createAnnotation()
Create an annotation instance and add the created instance to the specified page.

**Syntax**

```typescript
createAnnotation<K extends keyof AnnotationsTypeMapOuter>(pageUid: string, type: K, annotationOptions?: AnnotationsTypeMapOuter[K]["options"]): AnnotationsTypeMapOuter[K]["return"];
```

**Parameters**

`pageUid`: Specify the page to add the annotation.

`type`: Specify the type of annotation to create.
```typescript
type AnnotationType = "rectangle" | "redaction" | "ellipse" | "polygon" | "polyline" | "line" | "ink" | "textBox" | "textTypewriter" | "stamp" | "highlight" | "underline"| "strikeout";
```

`annotationOptions`: The annotation options. Please refer to [the options list](/api/interface/annotationinterface/index.md#options).

**Return value**

The instance of annotation. Please refer to [Annotation](/api/class/annotation/index.md).

**Code Snippet**

- To creat new annotations.

    ```typescript
    // Given that editViewer is an existing instance of EditViewer and a document is currently open.
    const pageUid = editViewer.indexToUid(0);

    const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle");
    const ellipse = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "ellipse");
    const polygon = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "polygon");
    const polyline = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "polyline");
    const line = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "line");
    const ink = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "ink");
    const textBox = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "textBox");
    const textTypewriter = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "textTypewriter");
    const highlight = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "highlight");
    const underline = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "underline");
    const strikeout = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "strikeout");
    const redaction = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "redaction");
    const stamp = await Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "stamp");
    ```


**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match. 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license. 
 -80050 | DDV.Core.init() has not been set up yet.  
 -80051 | DDV.Core.init() has not been completed.
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported.
 -80105 | *XXX(API)*: The specified page(s) do not exist.   
 -80328 | Rectangle-type redaction requires exactly one rect.

### getAnnotationsByUids()

Get annotations by annotation uids.

**Syntax**

```typescript
getAnnotationsByUids(annotationUids: string[]): Annotation[];
```

**Parameters**

`annotationUids`: The array of the annotation uids.

**Return value**

An array of [Annotation](/api/class/annotation/index.md) objects.

**Warning**

 Error Code  | Error Message                                        | API return value 
-------------|-----------------------------------------------------|---------------
 -80100      | *XXX(API)*: *XXX(ParameterName)* is invalid.   | []
 -80102      | *XXX(API)*: *XXX(ParameterName)* is missing.  | []
 -80106      | *XXX(API)*: The specified annotation does not exist.| []

### getAnnotationsByPage()

Get annotations in specified page.

**Syntax**

```typescript
getAnnotationsByPage(pageUid: string): Annotation[];
```

**Parameters**

`pageUid`: Specify the page.

**Return value**

An array of [Annotation](/api/class/annotation/index.md) object.

**Warning**

 Error Code  | Error Message                                        | API return value  
-------------|-----------------------------------------------------|---------------
 -80100      | *XXX(API)*: *XXX(ParameterName)* is invalid.   | []
 -80102      | *XXX(API)*: *XXX(ParameterName)* is missing.  | []
 -80105      | *XXX(API)*: The specified page(s) do not exist. | []

### getAnnotationsByDoc()

Get all annotations in specified document.

**Syntax**

```typescript
getAnnotationsByDoc(docUid: string): Annotation[];
```

`docUid`: Specify the doc.

**Return value**

An array of [Annotation](/api/class/annotation/index.md) objects.

**Warning**

 Error Code  | Error Message                                        | API return value     
--------|-----------------------------------------------------|--------------- 
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | []
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.   | []
 -80104 | *XXX(API)*: The specified document(s) do not exist.  | []


### deleteAnnotations()

Delete specified annotations.

**Syntax**

```typescript
deleteAnnotations(annotationUids: string[]): boolean;
```

**Parameters**

`annotationUids`: Specify the array of annotation uids to delete.

**Return value**

`true`

`false`

**Warning**

 Error Code  | Error Message                                           | API return value     
-------------|--------------------------------------------------------|---------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.           | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.          | `false`
 -80106 | *XXX(API)*: The specified annotation does not exist.  | `false`

### bringAnnotationForward()

Bring the specified annotation forward.

**Syntax**

```typescript
bringAnnotationForward(annotationUid: string): boolean;
```

**Parameters**

`annotationUid`: Specify the annotation uid to bring forward.

**Return value**

`true`: Successfully.

`false`: Failed.

**Warning**

 Error Code  | Error Message                                           | API return value     
-------------|--------------------------------------------------------|---------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.           | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.          | `false`
 -80106 | *XXX(API)*: The specified annotation does not exist.  | `false`

### sendAnnotationBackward()

Send the specified annotation backward.

**Syntax**

```typescript
sendAnnotationBackward(annotationUid: string): boolean;
```

**Parameters**

`annotationUid`: Specify the annotation uid to send backward.

**Return value**

`true`: Successfully.

`false`: Failed.

**Warning**

 Error Code  | Error Message                                           | API return value     
-------------|--------------------------------------------------------|---------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.           | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.          | `false`
 -80106 | *XXX(API)*: The specified annotation does not exist.  | `false`

### bringAnnotationToFront()

Bring the specified annotation in front of all other annotations.

**Syntax**

```typescript
bringAnnotationToFront(annotationUid: string): boolean;
```

**Parameters**

`annotationUid`: Specify the annotation uid to bring to front.

**Return value**

`true`: Successfully.

`false`: Failed.

**Warning**

 Error Code  | Error Message                                           | API return value     
-------------|--------------------------------------------------------|---------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.           | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.          | `false`
 -80106 | *XXX(API)*: The specified annotation does not exist.  | `false`

### sendAnnotationToBack()

Send the specified annotation behind all other annotations.

**Syntax**

```typescript
sendAnnotationToBack(annotationUid: string): boolean;
```

**Parameters**

`annotationUid`: Specify the annotation uid to send to back.

**Return value**

`true`: Successfully.

`false`: Failed.

**Warning**

 Error Code  | Error Message                                           | API return value     
-------------|--------------------------------------------------------|---------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.           | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.          | `false`
 -80106 | *XXX(API)*: The specified annotation does not exist.  | `false`

{% comment %}
### importXfdf()

Import annotations in an XFDF(XML) string to the specified document.

**Syntax**

```typescript
importXfdf(docUid: string, xfdf: string): Prmoise<Annotation[]>;
```

**Parameters**

`docUid`: Specify the document.

`xfdf`: The XFDF(XML) string to import.

**Return value**

An array of imported [Annotation](/api/class/annotation/index.md) objects.

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match. 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license. 
 -80050 | DDV.Core.init() has not been set up yet.  
 -80051 | DDV.Core.init() has not been completed.
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.       
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.
 -80104 | *XXX(API)*: The specified document(s) do not exist.

 **Warning**

  Error Code  | Error Message                                        
--------|-----------------------------------------------------  
 -80203 | Failed to read some annotations because they are not supported by Dynamsoft Document Viewer so far.

### exportXfdf()

Export all annotations from the specified document as an XFDF(XML) string.

**Syntax**

```typescript
exportXfdf(docUid: string): Promise<string>;
```

**Parameters**

`docUid`: Specify the document.

**Return value**

The XFDF(XML) string. 

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                    
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match. 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license. 
 -80050 | DDV.Core.init() has not been set up yet.  
 -80051 | DDV.Core.init() has not been completed.
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.       
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.
 -80104 | *XXX(API)*: The specified document(s) do not exist. 

{% endcomment %}

## Events

### on()

Bind a listener to the specified event. 

**Syntax**

```typescript
on(eventName: EventName, listener:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It should be [an integrated event name](#integrated-events).

`listener`: Specify the listener.

**Code Snippet**

```typescript
// Bind a listener to the integrated event annotationsModified.
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.modifiedAnnotations[0].uid);
    console.log(e.modifiedAnnotations[0].newOptions);
    console.log(e.actions);
};

Dynamsoft.DDV.annotationManager.on("annotationsModified", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported.

### off()

Unbind event listener(s) from the specified event. 

**Syntax**

```typescript
off(eventName: EventName, listener?:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It should be [an integrated event name](#integrated-events).

`listener`: Specify the listener. If no listener is specified, unbind all event listeners from the specified event

**Code Snippet**

```typescript
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.modifiedAnnotations[0].uid);
    console.log(e.modifiedAnnotations[0].newOptions);
    console.log(e.actions);
};

Dynamsoft.DDV.annotationManager.on("annotationsModified", eventFunc);

// Unbind the specified event listener.
Dynamsoft.DDV.annotationManager.off("annotationsModified", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported.

### Integrated events

#### annotationsAdded

Triggered when new annotation(s) is added.

**Callback**

An EventObject.

**Attributes**

`annotationUids`: The array of new added annotations uids.

#### annotationsDeleted

Triggered when annotation(s) is deleted.

**Callback**

An EventObject.

**Attributes**

`annotationUids`: The array of deleted annotations uids.

#### annotationLayerChanged

Triggered when annotation's layer is changed.

**Callback**

An EventObject.

**Attributes**

`oldAnnotationUidList `: The list of old annotation uids, arranged in hierarchical order from bottom to top for each page.

`newAnnotationUidList`: The list of new annotation uids, arranged in hierarchical order from bottom to top for each page.

#### annotationsModified

Triggered when annotation(s) is modified.

**Callback**

An EventObject.

**Attributes**

`modifiedAnnotations`: The array of the objects which include below properties.

- `uid`: The modified annotation uid.
- `oldOptions`: The modified annotation old options.
- `newOptions`: The modified annotation new options.

`actions`: The array of actions. Supported actions:

- `moved`
- `resized`
- `rotated`
- `flagsChanged`
- `appearanceChanged`
- `contentChanged`
