---
Description: Retrieves a value that specifies a Pre-production certificate hierarchy.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\mbaldwin
ms.assetid: 1fe9d5f8-fce4-41af-81de-c6137631631c
ms.prod: windows-server-dev
ms.technology: active-directory-rights-management
ms.tgt_platform: multiple
title: Constants.KeyHierarchyPreproduction property
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
---

# Constants.KeyHierarchyPreproduction property

The **KeyHierarchyPreproduction** property retrieves a value that specifies a Pre-production certificate hierarchy.

This property is read-only.

## Syntax


```VB
Constants.KeyHierarchyPreproduction
```



## Property value

This property returns an integer value (0x1).

## Remarks

This property can be used with the [**KeyHierarchy**](serverlicensorcertificate-keyhierarchy-property.md) property on the [**ServerLicensorCertificate**](serverlicensorcertificate-object.md) object. For more information about certificate hierarchies, see [Setting Up the Pre-production Development Environment](https://msdn.microsoft.com/library/cc542540) and [Certificate Hierarchy](https://msdn.microsoft.com/library/cc530431).

## Examples


```VB
DIM config_manager
DIM admin_role

' *******************************************************************
' Create and initialize a ConfigurationManager object.

SUB InitObject()

  CALL WScript.Echo( "Create ConfigurationManager object...")
  SET config_manager = CreateObject _
    ("Microsoft.RightsManagementServices.Admin.ConfigurationManager")      
  CheckError()
    
  CALL WScript.Echo( "Initialize...")
  admin_role=config_manager.Initialize(false,"localhost",80,"","","")
  CheckError()

END SUB

' *******************************************************************
' Retrieve the server licensor certificate and key hierarchy.

SUB GetSLC()

  DIM slc
  DIM environment
  DIM constant

  ' Retrieve the Constants object.
  SET constant = config_manager.Constants

  ' Retrieve the ServerLicensorCertificate object.
  SET slc = config_manager.Enterprise.ServerLicensorCertificate
  CheckError()

  ' Retrieve the certificate hierarchy.
  environment = slc.KeyHierarchy
  IF environment = constant.KeyHierarchyPreproduction THEN
    CALL WScript.Echo("Environment = Pre-Production.")
  ELSEIF  environment = constant.KeyHierarchyProduction THEN
    CALL WScript.Echo("Environment = Production.")
  ELSEIF environment = constant.KeyHierarchyOther THEN
    CALL WScript.Echo("Environment = Other.")
  ELSE
    CALL WScript.Echo("KeyHierarchy error.")
  END IF

END SUB

' *******************************************************************
' Error checking function.

FUNCTION CheckError()
  CheckError = Err.number
  IF Err.number <> 0 THEN
    CALL WScript.Echo( vbTab & "*****Error Number: " _
                       & Err.number _
                       & " Desc:" _
                       & Err.Description _
                       & "*****")
    WScript.StdErr.Write(Err.Description)
    WScript.Quit( Err.number )
  END IF
END FUNCTION
```



## Requirements



|                                     |                                                                                                                         |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | None supported<br/>                                                                                               |
| Minimum supported server<br/> | Windows Server 2008<br/>                                                                                          |
| Assembly<br/>                 | <dl> <dt>Microsoft.RightsManagementServices.Admin.dll</dt> </dl> |



## See also

<dl> <dt>

[**Constants**](constants-object.md)
</dt> <dt>

[**KeyHierarchyOther**](constants-keyhierarchyother-property.md)
</dt> <dt>

[**KeyHierarchyProduction**](constants-keyhierarchyproduction-property.md)
</dt> </dl>

 

 



