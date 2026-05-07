---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Error List
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Error List
breadcrumbText: API Reference
description: Dynamsoft Document Viewer Documentation API Reference Error List Page
permalink: /api/errorlist.html
---

# Error List

## License Related Errors

 Error Code | Error Message                                          
 ---------- | ------------------------------------------------------ 
 -80001     | License string is invalid.                             
 -80002     | *XXX(LicenseModuleName)* module license has expired.                        
 -80003     | *XXX(LicenseModuleName)* module license is missing.                         
 -80004     | *XXX(LicenseModuleName)* module license version does not match.             
 -80005     | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license. 

## Initialize Related Errors

 Error Code | Error Message                                    
 ---------- | ------------------------------------------------ 
 -80050     | DDV.Core.init() has not been set up yet. 
 -80051     | DDV.Core.init() has not been completed.  
 -80052     | *XXX(API)*: Resource is not found from the specified engineResourcePath.
 -80053     | *XXX(API)*: The resource version at the specified engineResourcePath does not match this version of Dynamsoft Document Viewer.

## Common Errors

 Error Code | Error Message                                                
 ---------- | ------------------------------------------------------------ 
 -80100     | *XXX(API)*: *XXX(ParameterName)* is invalid.          
 -80101     | *XXX(API)*: *XXX(ParameterName)* is out of range.     
 -80102     | *XXX(API)*: *XXX(ParameterName)* is missing.          
 -80103     | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. 
 -80104     | *XXX(API)*: The specified document(s) do not exist.  
 -80105     | *XXX(API)*: The specified page(s) do not exist.      
 -80106     | *XXX(API)*: The specified annotation does not exist.
 -80108     | *XXX(API)*: The document has been destroyed.
 -80109     | *XXX(API)*: The page has been destroyed.


## Document Related Errors

 Error Code | Error Message                                 
 ---------- | --------------------------------------------- 
 -80200     | File type is not supported.                   
 -80201     | docUid does not allow duplicate.              
 -80202     | Failed to read the PDF file because it's encrypted and the correct password is not provided. 
 -80203     | Failed to read some annotations because they are not supported by Dynamsoft Document Viewer so far.
 -80204     | PDFs containing XFA (XML Forms Architecture) forms are not supported.
 -80205     | The pageData has been destroyed.
 -80206     | The DocTextSearcher has been destroyed.

## Viewer Releated Errors

 Error Code | Error Message                                                
 ---------- | ------------------------------------------------------------ 
 -80301     | The specified container does not exist.                      
 -80302     | minZoom value cannot be larger than maxZoom value.           
 -80304     | No document opened.                                          
 -80305     | There is no image in the current document.                   
 -80306     | The value for zoom is larger than maxZoom value.             
 -80307     | The value for zoom is smaller than minZoom value.            
 -80308     | EditViewer.setParallelScrollCount: Not available in current displayMode. 
 -80309     | The specified rect exceeds the bounds of page index *X(IndexNum)*. 
 -80310     | No operations to undo.                                       
 -80311     | No operations to redo.                                       
 -80312     | The specified quad exceeds the bounds of the current page.   
 -80313     | The element *XXX(ElementName)* is not supported in *XXX(ClassName)* class.               
 -80314     | *XXX(API)*: Not available in current toolMode.       
 -80315     | DocumentDetect needs to be configured by Dynamsoft.DDV.setProcessingHandler to enable the document detection feature. 
 -80316     | ImageFilter needs to be configured by Dynamsoft.DDV.setProcessingHandler to enable the image filter feature. 
 -80317     | The specified annotation(s) is not on the current page or does not exist.
 -80318     | The document contains unsupported fonts, which may result in font loss after saving.
 -80319     | ReadOnly annotation or noView annotation cannot be selected.
 -80320     | Unknown annotation or incomplete annotation cannot be selected.
 -80321     | Flattened annotation cannot be selected.
 -80322     | No results found.
 -80323     | The redaction annotation has already been applied.
 -80324     | The specified annotation(s) contain annotations other than redaction annotations.
 -80325     | The specified page does not contain redaction annotations.
 -80326     | The annotation has already been deleted.
 -80327     | The specified annotation(s) are not on the specified page or do not exist.
 -80328     | Rectangle-type redaction requires exactly one rect.

## Camera Releated Errors

 Error Code | Error Message                               
 ---------- | ------------------------------------------- 
 -80400     | The specified camera does not exist.        
 -80401     | The specified camera is occupied.           
 -80402     | No video stream is played.                  
 -80403     | Not HTTPS, failed to play the video stream. 
 -80404     | The camera does not support a flashlight.   
 -80405     | No camera available.                        
 -80406     | The selected camera is denied by browser.   
 -80407     | No bound container.                         


## Wasm Error

 Error Code | Error Message  
------------|----------------
 -81000     | *WASM Error*     

## External Error

 Error Code | Error Message  
------------|----------------
 -81100     | *External Error*     
 