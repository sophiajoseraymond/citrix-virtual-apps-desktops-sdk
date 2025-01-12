﻿
# Get-Applibappdisk
Gets the list of AppDisks.
## Syntax

```
Get-AppLibAppDisk [[-AppDiskName] <String>] [-AppDiskUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Lets you retrieve the list of defined AppDisks.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk. | false | false |  |
| AppDiskUid | The unique identifier of the AppDisk. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
| ReturnTotalRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| Skip | See about\_Prov\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Prov\_Filtering for details. | false | false |  |
| Filter | See about\_Prov\_Filtering for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdisk
This object provides details of the AppDisk and contains the following information:  
          AppDiskUid &lt;Guid&gt;  
          The unique identifier for the AppDisk.  
          AppDiskName &lt;string&gt;  
          The name of the AppDisk.  
          Description &lt;string&gt;  
          A description of the AppDisk.  
          HostingUnitUid &lt;Guid&gt;  
          The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
          HostingUnitName &lt;string&gt;  
          The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
          VirtualDiskID &lt;DateTime&gt;  
          The MCS disk identifier for the AppDisk.  
          TaskId &lt;Guid&gt;  
          The identifier of any current task that is running for the AppDisk.  
          DiskLocalUid  &lt;Guid&gt;  
          The AppDNA identifier for the disk.  
          DiskLocalVersion  &lt;Guid&gt;  
          The AppDNA version specifier for the disk.  
          Scopes &lt;ScopeReference\[\]&gt;  
          The Delegated Administration scopes in which the AppDisk falls  
          Task &lt;Task&lt;  
          The state of any current task that is running for the AppDisk.  
          State &lt;AppDiskState&gt;  
          The overall lifecycle state of the AppDisk  
          StateString &lt;string&gt;  
          The overall lifecycle state of the AppDisk as a string  
          AppDNAState &lt;AppDNAState&gt;  
          The AppDNA lifecycle state of the AppDisk  
          AppDNAStateString &lt;string&gt;  
          The AppDNA lifecycle state of the AppDisk as a string  
          NewVersionCreationInProgress &lt;bool&gt;  
          A value indicating whether a new version of this AppDisk is currently being created
## Notes
In the case of failure, the following errors can result.  
    Error Codes  
    -----------  
    PartialData  
    Only a subset of the available data was returned.  
    CouldNotQueryDatabase  
    The query to get the database was not defined.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error.  
    CommunicationError  
    An error occurred while communicating with the service.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    InvalidFilter  
    A filtering expression was supplied that could not be interpreted for this cmdlet.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Get-AppLibAppDisk  
  
          AppDiskUid                  : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
          AppDiskName                 : Disk1  
  
          Description                 : Microsoft Office 2013  
  
          MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16  
  
          MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79  
  
          HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
          HostingUnitName             : HostUnit1  
  
          TaskId                      : 00000000-0000-0000-0000-000000000000  
  
          DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6  
  
          DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6  
  
          DiskParentVersion           :  
  
          Scopes                      :  
  
          Task                        :  
  
          State                       : Ready  
  
          StateString                 : Ready  
  
          AppDNAState                 : NoData  
  
          AppDNAStateString           : NoData  
  
          AppDiskUid                  : 43d82099-1fd7-4617-93f0-25b160813905  
  
          AppDiskName                 : Disk2  
  
          Description                 : Finance Suite  
  
          MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16  
  
          MasterDiskID                : 022cd6e4-34cb-3f7c-e02a-44ac404483b4  
  
          HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
          HostingUnitName             : HostUnit1  
  
          TaskId                      : 00000000-0000-0000-0000-000000000000  
  
          DiskLocalUid                : 5713AB4B-A021-4D9D-A04C-D80BB1126C19  
  
          DiskLocalVersion            : 72967010-CA6F-467B-9D46-499EF595F02B  
  
          DiskParentVersion           :  
  
          Scopes                      :  
  
          Task                        :  
  
          State                       : Ready  
  
          StateString                 : Ready  
  
          AppDNAState                 : NoData  
  
          AppDNAStateString           : NoData
```

#### Description
Returns all of the available AppDisks.
### Example 2

```
C:\PS>Get-AppDisk -AppDiskName Disk[0-1]  
  
          AppDiskUid                  : 7585f0de-192e-4847-a6d8-22713c3a2f42  
  
          AppDiskName                 : Disk1  
  
          Description                 : Microsoft Office 2013  
  
          MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16  
  
          MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79  
  
          HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
          HostingUnitName             : HostUnit1  
  
          TaskId                      : 00000000-0000-0000-0000-000000000000  
  
          DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6  
  
          DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6  
  
          Scopes                      :  
  
          Task                        :  
  
          State                       : Ready  
  
          StateString                 : Ready  
  
          AppDNAState                 : NoData  
  
          AppDNAStateString           : NoData
```

#### Description
Returns all of the AppDisks that have the name 'Disk0' or 'Disk1'.
