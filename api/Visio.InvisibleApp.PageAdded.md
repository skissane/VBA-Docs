---
title: InvisibleApp.PageAdded Event (Visio)
ms.prod: visio
api_name:
- Visio.InvisibleApp.PageAdded
ms.assetid: e3a27500-16c3-f0d5-be44-9389b7bd3055
ms.date: 06/08/2017
---


# InvisibleApp.PageAdded Event (Visio)

Occurs after a new page is added to a document.


## Syntax

Private Sub  _expression_ _'PageAdded'(**_ByVal Page As [IVPAGE]_**)

 _expression_ A variable that represents an [InvisibleApp](./Visio.InvisibleApp.md) object.


### Parameters



|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Page_|Required| **[IVPAGE]**|The page that was added.|

## Remarks

If you are using Microsoft Visual Basic or Visual Basic for Applications (VBA), the syntax in this topic describes a common, efficient way to handle events.

If you want to create your own  **Event** objects, use the **Add** or **AddAdvise** method. To create an **Event** object that runs an add-on, use the **Add** method as it applies to the **EventList** collection. To create an **Event** object that receives notification, use the **AddAdvise** method. To find an event code for the event you want to create, see[Event codes](../visio/Concepts/event-codesvisio.md).


## Example

This example shows how to create a class module to handle events fired by a source object in Microsoft Visio, for example, the  **Document** object. The module consists of the function **VisEventProc** , which uses a **Select Case** block to check for three events: **DocumentSaved** , **PageAdded** , and **ShapesDeleted** . Other events fall under the default case (**Case Else**). Each **Case** block constructs a string ( _strMessage_ ) that contains the name and event code of the event that fired. Finally, the function displays the string in the Immediate window.

Copy this sample code into a new class module in VBA or Visual Basic, naming the module clsEventSink. You can then use an event-sink module to create an instance of the clsEventSink class and  **Event** objects that send notifications of event firings to the class instance. To see how to create an event-sink module, refer to the example for the **AddAdvise** method.




```vb
 
Implements Visio.IVisEventProc 
 
'Declare visEvtAdd as a 2-byte value 
'to avoid a run-time overflow error 
Private Const visEvtAdd% = &;H8000 
 
Private Function IVisEventProc_VisEventProc( _ 
 ByVal nEventCode As Integer, _ 
 ByVal pSourceObj As Object, _ 
 ByVal nEventID As Long, _ 
 ByVal nEventSeqNum As Long, _ 
 ByVal pSubjectObj As Object, _ 
 ByVal vMoreInfo As Variant) As Variant 
 
 Dim strMessage As String 
 
 'Find out which event fired 
 Select Case nEventCode 
 Case visEvtCodeDocSave 
 strMessage = "DocumentSaved (" &; nEventCode &; ")" 
 Case (visEvtPage + visEvtAdd) 
 strMessage = "PageAdded (" &; nEventCode &; ")" 
 Case visEvtCodeShapeDelete 
 strMessage = "ShapesDeleted(" &; nEventCode &; ")" 
 Case Else 
 strMessage = "Other (" &; nEventCode &; ")" 
 End Select 
 
 'Display the event name and the event code 
 Debug.Print strMessage 
 
End Function
```

