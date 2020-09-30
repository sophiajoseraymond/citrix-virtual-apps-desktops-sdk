
# New-Provvm
Creates a new virtual machine.
## Syntax
```
New-ProvVM -ProvisioningSchemeName <String> -ADAccountName <String[]> [-FastBuild] [-NetworkMapping <Hashtable>] [-AutoAssignVLAN] [-SecurityGroup <String[]>] [-MachinesPerAssistant <Int32>] [-MaxAssistants <Int32>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

New-ProvVM -ProvisioningSchemeUid <Guid> -ADAccountName <String[]> [-FastBuild] [-NetworkMapping <Hashtable>] [-AutoAssignVLAN] [-SecurityGroup <String[]>] [-MachinesPerAssistant <Int32>] [-MaxAssistants <Int32>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Lets you create new virtual machines with the configuration specified by a provisioning scheme.

The virtual machines are created using all of the storage specified in the provisioning scheme. The storage is used in a round robin mechanism. For the duration of this task, the AD accounts are locked (by the AD Identity Service), which stops the same accounts being used by other virtual machine creation tasks.


## Related Commands

* [Get-ProvVM](../Get-ProvVM/)
* [Remove-ProvVM](../Remove-ProvVM/)
* [Lock-ProvVM](../Lock-ProvVM/)
* [Unlock-ProvVM](../Unlock-ProvVM/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme in which the virtual machines are created. | true | false |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme in which the virtual machines are created. | true | false |  |
| ADAccountName | A list of the Active Directory account names that are used for the virtual machines. The accounts must be provided in a domain-qualified format. This parameter accepts Identity objects as returned by the New-AcctADAccount cmdlet, or any PSObject with string properties "Domain" and "ADAccountName". | true | false |  |
| FastBuild | Indicates whether or not the command can improve speed by using optimizations in the creation process. This may mean that machines you create cannot be booted until ResetVM operations have been performed by the Broker and Machine Identity Services. | false | false |  |
| NetworkMapping | Specifies how the attached NICs are mapped to networks. If this parameter is omitted, provisioned VMs are created with network settings as inherited from the provisioning scheme. If this parameter is supplied, machines are created with the number of NICs specified in the map, and each NIC is attached to the specified network. | false | false |  |
| AutoAssignVLAN | Indicates whether or not the VLAN of the network should be automatically assigned to the new VM or if the VLAN from the master image should be used | false | false | false |
| SecurityGroup | The security groups to apply to machines created in Cloud Hypervisors | false | false |  |
| MachinesPerAssistant | The number of concurrent volume operations that may be performed by each volume worker helper machine | false | false |  |
| MaxAssistants | The maximum number of volume worker help machines that may be created for this operation. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This cannot be specified for tasks that are run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid<br>    When The Runasynchronously Identifier Is Specified, This Guid Is Returned And Provides The Task Identifier.<br>System.Management.Automation.Pscustomobject<br>    This Object Provides Details Of The Task That Was Run And Contains The Following Information:<br>        Taskid &lt;Guid&gt;<br>            The Identifier For The Task That Was Performed.<br>        Active &lt;Boolean&gt;<br>            Indicates Whether The Task Is Still Processing Or Is Complete.<br>        Host &lt;String&gt;<br>            The Name Of The Host On Which The Task Is Running Or Was Run.<br>        Datestarted &lt;Datetime&gt;<br>            The Date And Time That The Task Was Initiated.<br>        Type &lt;Citrix.Xdinterservicetypes.Jobtype&gt;<br>            The Type Of Task. For Newly Provisioned Vm Tasks, This Is Always "Newvirtualmachine".<br>        Metadata &lt;Citrix.Machinecreation.Sdk.Metadata\[\]&gt;<br>            The List Of Metadata Stored Against The Task. For New Tasks This Is Empty Until Metadata Is Added.<br>        Workflowstatus &lt;System.Workflow.Runtime.Workflowstatus&gt;<br>            Indicates The Status Of The Workflow That Is Used To Process The Task.<br>        Provisioningschemename &lt;String&gt;<br>            The Name Of The Provisioning Scheme That The Task Was For.<br>        Provisioningschemeuid &lt;Guid&gt;<br>            The Unique Identifier Of The Provisioning Scheme That The Task Was For.<br>        Masterimage &lt;String&gt;<br>            The Path (In The Hosting Unit Provider) Of The Virtual Machine Snapshot That Was Used As The Master Image For The Task.<br>        Identitypoolname &lt;String&gt;<br>            The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The New Provisioning Scheme Uses.<br>        Identitypooluid &lt;Guid&gt;<br>            The Unique Identifier Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The New Provisioning Scheme Uses.<br>        Hostingunitname &lt;String&gt;<br>            The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Uses.<br>        Hostingunituid<br>            The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Uses.<br>        Taskstate &lt;Citrix.Desktopupdatemanager.Sdk.Provisionvmstate&gt;<br>            The State Of The Task.  This Can Be Any Of The Following:<br>            Processing<br>                Indicates That The Task Is In Its Initial State.<br>            Locatingresources,<br>                Indicates That The Task Is Locating Information From Other Services.<br>            Hostingunitnotfound<br>                Indicates That The Required Hosting Unit Could Not Be Located.<br>            Provisioningschemenotfound<br>                Indicates That The Required Provisioning Scheme Could Not Be Located.<br>            Provisioning<br>                Indicates That The Task Is At The Provisioning Stage.<br>            Identitypoolnotfound<br>                Indicates That The Required Identity Pool Could Not Be Located.<br>            Taskalreadyrunningforprovisioningscheme<br>                Indicates That The Provisioning Scheme Already Has Another Task Running.<br>            Hypervisorinmaintenancemode<br>                Indicates That The Hypervisor Is Not Available For Normal Use.<br>            Noavailablestorage<br>                Indicates That No Storage Is Available For The Hypervisor.<br>            Noavailablenetwork<br>                Indicates That No Network Is Available For The Hypervisor.<br>            Finalizing<br>                Indicates That The Task Is Finalizing.<br>            Finished<br>                Indicates That The Task Is Complete.<br>            Finishedwitherrors<br>                Indicates That The Task Is Complete But There Were Errors. Specific Details Of Errors Are Included With Each Failed Virtual Machine.<br>            Removing<br>                Indicates That The Task Is Removing Virtual Machines From The Hypervisor.<br>            Failed<br>                The Job Failed For Reasons Specified In Taskstateinformation.<br>            Canceled<br>                Indicates That The Task Was Stopped By User Intervention (Using Stop-Provtask).<br>        Taskstateinformation<br>            Provides More Detailed Information About The Current Task State.<br>        Virtualmachinestocreatecount &lt;Int&gt;<br>            The Total Number Of Virtual Machines That The Task Is Trying To Create.<br>        Virtualmachinescreatedcount &lt;Int&gt;<br>            The Number Of Virtual Machines That The Task Has Created So Far. Details Of The Machines That Were Created Are In The Createdvirtualmachines Parameter.<br>        Virtualmachinescreationfailedcount &lt;Int&gt;<br>            The Number Of Virtual Machines That The Task Has Failed To Create. Details Of The Machines That Were Not Created Are In The Failedvirtualmachines Parameter.<br>        Failedvirtualmachines &lt;Citrix.Desktopupdatemanager.Sdk.Virtualmachinecreation\[\]&gt;<br>            Adaccountname &lt;String&gt;<br>                The Domain Qualified Ad Account Name Of The Machine.<br>            Adaccountsid &lt;String&gt;<br>                The Ad Account Sid Of The Machine Account.<br>            Diagnosticinformation &lt;Citrix.Machinecreation.Sdk.Exceptionsurrogate\[\]&gt;<br>                A Collection Of Handled Error States Which Caused The Provisioning To Fail.<br>                    Exceptiontype &lt;String&gt;<br>                      The Type Of Exception This Object Represents<br>                    Message  &lt;String&gt;<br>                      The Exception Message<br>                    Details  &lt;String&gt;<br>                      The Full Exception Content Including Stack Trace<br>                    Innerexception &lt;Citrix.Machinecreation.Sdk.Exceptionsurrogate&gt;<br>                      Information Relating To Any Contributing Error State<br>            Status &lt;String&gt;<br>            Statusadditionalinformation &lt;String&gt;<br>            Vmid &lt;String&gt;<br>                The Virtual Machine Identifier Within The Hypervisor In Which The Vm Resides.<br>            Vmname &lt;String&gt;<br>                The Display Name Of The Virtual Machine Within The Hypervisor In Which The Vm Resides.<br>        Createdvirtualmachines &lt;Citrix.Desktopupdatemanager.Sdk.Virtualmachinecreation\[\]&gt;<br>            See Failedvirtualmachines For Details Of The Object Parameters.

## Notes
Only one long-running task in each provisioning scheme can be processed at a time.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed<br>    for various reasons.<br>    WorkflowHostUnavailable<br>    The task could not be started because the database connection is inactive.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified.<br>    When running asynchronously, the cmdlet terminates before the job does,<br>    so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs<br>    on the controller being used, or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type NewVirtualMachine, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    CreatingVirtualMachines<br>    ReleasingAccountLocks
## Examples

### Example 1
```
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName "domain\Account"

TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a

Active                             : False

Host                               : DUMTESTDDC

DateStarted                        : 18/05/2010 10:54:32

Type                               : NewVirtualMachine

Metadata                           : {}

WorkflowStatus                     : Completed

MasterImage                        : /Base.vm/Base.snapshot

ProvisioningSchemeName             : MyScheme

ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42

CurrentOperation                   :

TaskState                          : Finished

TaskStateInformation               :

HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName                    : XenHU

IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName                   : idPool1

VirtualMachinesToCreateCount       : 1

VirtualMachinesCreatedCount        : 1

VirtualMachinesCreationFailedCount : 0

CreatedVirtualMachines             : {DOMAIN\Account$}

FailedVirtualMachines              : {}

ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3

ProvisioningStatus                 : Completed
```
#### Description
Creates a new virtual machine using the AD account "domain\\account" in the provisioning scheme "MyScheme".
### Example 2
```
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName "domain\Account" -RunAsynchronously

Guid

----

6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```
#### Description
Creates a new virtual machine using the AD account "domain\\account" in the provisioning scheme "MyScheme" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;&lt;br&gt;i.e.&lt;br&gt;C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a&lt;br&gt;Active                             : False&lt;br&gt;Host                               : MyHost&lt;br&gt;DateStarted                        : 18/05/2010 10:54:32&lt;br&gt;Type                               : NewVirtualMachine&lt;br&gt;Metadata                           : {}&lt;br&gt;WorkflowStatus                     : Completed&lt;br&gt;MasterImage                        : /Base.vm/Base.snapshot&lt;br&gt;ProvisioningSchemeName             : MyScheme&lt;br&gt;ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42&lt;br&gt;TaskState                          : Finished&lt;br&gt;TaskStateInformation               :&lt;br&gt;HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501&lt;br&gt;HostingUnitName                    : XenHU&lt;br&gt;IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16&lt;br&gt;IdentityPoolName                   : idPool1&lt;br&gt;VirtualMachinesToCreateCount       : 1&lt;br&gt;VirtualMachinesCreatedCount        : 1&lt;br&gt;VirtualMachinesCreationFailedCount : 0&lt;br&gt;CreatedVirtualMachines             : {DOMAIN\\Account\$}&lt;br&gt;FailedVirtualMachines              : {}&lt;br&gt;ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3&lt;br&gt;ProvisioningStatus                 : Completed
### Example 3
```
C:\PS>$accounts = Get-AcctAdAccount -IdentityPool MyPool -State Available

C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName $t -RunAsyncronously
```
#### Description
Creates a new virtual machine using all of the available AD accounts from the identity pool "MyPool" in the provisioning scheme "MyScheme" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;&lt;br&gt;For example:&lt;br&gt;C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a&lt;br&gt;Active                             : False&lt;br&gt;Host                               : MyHost&lt;br&gt;DateStarted                        : 18/05/2010 10:54:32&lt;br&gt;Type                               : NewVirtualMachine&lt;br&gt;Metadata                           : {}&lt;br&gt;WorkflowStatus                     : Completed&lt;br&gt;MasterImage                        : /Base.vm/Base.snapshot&lt;br&gt;ProvisioningSchemeName             : MyScheme&lt;br&gt;ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42&lt;br&gt;TaskState                          : Finished&lt;br&gt;TaskStateInformation               :&lt;br&gt;HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501&lt;br&gt;HostingUnitName                    : XenHU&lt;br&gt;IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16&lt;br&gt;IdentityPoolName                   : idPool1&lt;br&gt;VirtualMachinesToCreateCount       : 1&lt;br&gt;VirtualMachinesCreatedCount        : 1&lt;br&gt;VirtualMachinesCreationFailedCount : 0&lt;br&gt;CreatedVirtualMachines             : {DOMAIN\\Account\$}&lt;br&gt;FailedVirtualMachines              : {}&lt;br&gt;ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3&lt;br&gt;ProvisioningStatus                 : Completed
