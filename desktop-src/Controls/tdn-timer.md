---
title: TDN\_TIMER notification code
description: Sent by a task dialog approximately every 200 milliseconds.
ms.assetid: 5a162d97-6912-45bc-8151-1ea56cc459ea
keywords:
- TDN_TIMER notification code Windows Controls
topic_type:
- apiref
api_name:
- TDN_TIMER
api_location:
- Commctrl.h
api_type:
- HeaderDef
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
ms.prod: windows
ms.technology: desktop
---

# TDN\_TIMER notification code

Sent by a task dialog approximately every 200 milliseconds. This notification code is sent when the TDF\_CALLBACK\_TIMER flag has been set in the **dwFlags** member of the [**TASKDIALOGCONFIG**](/windows/win32/Commctrl/ns-commctrl-_taskdialogconfig?branch=master) structure that was passed to the [**TaskDialogIndirect**](/windows/win32/Commctrl/nf-commctrl-taskdialogindirect?branch=master) function. This notification code is received only through the task dialog callback function, which can be registered using the **TaskDialogIndirect** method.


```C++
TDN_TIMER    

   WPARAM wParam;
   LPARAM lParam;
```



## Parameters

<dl> <dt>

*wParam* 
</dt> <dd>

A **DWORD** that specifies the number of milliseconds since the dialog was created or this notification code returned **S\_FALSE**.

</dd> <dt>

*lParam* 
</dt> <dd>

Must be zero.

</dd> </dl>

## Return value

To reset the tickcount, the application must return **S\_FALSE**, otherwise the tickcount will continue to increment.

## Requirements



|                                     |                                                                                       |
|-------------------------------------|---------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                        |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/>                                  |
| Header<br/>                   | <dl> <dt>Commctrl.h</dt> </dl> |



 

 




