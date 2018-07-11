---
title: Masters.BeforeMasterDelete Event (Visio)
keywords: vis_sdr.chm10819040
f1_keywords:
- vis_sdr.chm10819040
ms.prod: visio
api_name:
- Visio.Masters.BeforeMasterDelete
ms.assetid: 6f950fa3-3cb6-d3ef-330d-2b38956d6ff3
ms.date: 06/08/2017
---


# Masters.BeforeMasterDelete Event (Visio)

Occurs before a master is deleted from a document.


## Syntax

Private Sub  _expression_ _'BeforeMasterDelete'(**_ByVal Master As [IVMASTER]_**)

 _expression_ A variable that represents a [Masters](./Visio.Masters.md) object.


### Parameters



|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Master_|Required| **[IVMASTER]**|The master that is going to be deleted.|

## Remarks

If you're using Microsoft Visual Basic or Visual Basic for Applications (VBA), the syntax in this topic describes a common, efficient way to handle events.

If you want to create your own  **Event** objects, use the **Add** or **AddAdvise** method. To create an **Event** object that runs an add-on, use the **Add** method as it applies to the **EventList** collection. To create an **Event** object that receives notification, use the **AddAdvise** method. To find an event code for the event you want to create, see[Event codes](../visio/Concepts/event-codesvisio.md).

