
# Remove-Provvm
Removes virtual machines.
## Syntax
```
Remove-ProvVM [-ProvisioningSchemeName] <String> -VMName <String[]> [-ForgetVM] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ProvVM [-ProvisioningSchemeUid] <Guid> -VMName <String[]> [-ForgetVM] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Lets you remove VMs from the Machine Creation Services and the hypervisor that they run on.


## Related Commands

* [Get-ProvVM](./Get-ProvVM/)
* [New-ProvVM](./New-ProvVM/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme from which virtual machines will be removed. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme from which the virtual machines are removed. | true | false |  |
| VMName | List of VM names that will be removed from the provisioning scheme. | true | true (ByValue, ByPropertyName) |  |
| ForgetVM | The named VMs will only be removed from the provisioning scheme database, but will remain in the hypervisor. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If this is specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task finishes. This cannot be specified for tasks that are run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid<br>    When The Runasynchronously Identifier Is Specified, This Guid Is Returned And Provides The Task Identifier.<br>System.Management.Automation.Pscustomobject<br>    This Object Provides Details Of The Task That Was Run And Contains The Following Information:<br>        Taskid &lt;Guid&gt;<br>            The Identifier For The Task That Was Performed.<br>        Active &lt;Boolean&gt;<br>            Indicates Whether The Task Is Still Processing Or Is Complete.<br>        Host &lt;String&gt;<br>            The Name Of The Host On Which The Task Is Running Or Was Run.<br>        Datestarted &lt;Datetime&gt;<br>            The Date And Time That The Task Was Initiated.<br>        Type &lt;Citrix.Xdinterservicetypes.Jobtype&gt;<br>            The Type Of Task. For New Remove-Vm Tasks, This Is Always "Removevirtualmachine".<br>        Metadata &lt;Citrix.Machinecreation.Sdk.Metadata\[\]&gt;<br>            The List Of Metadata Stored For The Task. For New Tasks, This Is Empty Until Metadata Is Added.<br>        Workflowstatus &lt;System.Workflow.Runtime.Workflowstatus&gt;<br>            Indicates The Status Of The Workflow That Is Used To Process The Task.<br>        Provisioningschemename &lt;String&gt;<br>            The Name Of The Provisioning Scheme That The Task Is For.<br>        Provisioningschemeuid &lt;Guid&gt;<br>            The Unique Identifier Of The Provisioning Scheme That The Task Is For.<br>        Taskstate &lt;Citrix.Desktopupdatemanager.Sdk.Provisionvmstate&gt;<br>            The State Of The Task.  This Can Be Any Of The Following:<br>            Processing<br>                Indicates That The Task Is In Its Initial State.<br>            Locatingresources,<br>                Indicates That The Task Is Locating Information From Other Services.<br>            Hostingunitnotfound<br>                Indicates That The Required Hosting Unit Could Not Be Located.<br>            Provisioningschemenotfound<br>                Indicates That The Required Provisioning Scheme Could Not Be Located.<br>            Provisioning<br>                Indicates That The Task Is At The Provisioning Stage.<br>            Identitypoolnotfound<br>                Indicates That The Required Identity Pool Could Not Be Located.<br>            Taskalreadyrunningforprovisioningscheme<br>                Indicates That The Provisioning Scheme Already Has Another Task Running.<br>            Finalizing<br>                Indicates That The Task Is Finalizing.<br>            Finished<br>                Indicates That The Task Is Complete.<br>            Finishedwitherrors<br>                Indicates That The Task Is Complete But There Were Errors. Specific Details Of Errors Are Included With Each Failed Virtual Machine.<br>            Removing<br>                Indicates That The Task Is Removing Virtual Machines From The Hypervisor.<br>            Failed<br>                Job Failed For Reasons Specified In Taskstateinformation.<br>            Canceled<br>                Indicates That The Task Was Stopped By User Intervention (Using Stop-Provtask)<br>        Taskstateinformation<br>            Provides More Detailed Information About The Current Task State.<br>        Virtualmachinestoremovecount &lt;Int&gt;<br>            The Total Number Of Virtual Machines That The Task Is Trying To Remove.<br>        Virtualmachinesremovedcount &lt;Int&gt;<br>            The Number Of Virtual Machines That The Task Has Removed So Far.  Details Of The Machines That Have Been Removed Are In The Removedvirtualmachines Parameter.<br>        Virtualmachinesfailedcount &lt;Int&gt;<br>            The Number Of Virtual Machines That The Task Has Failed To Remove.  Details Of The Machines That Failed Are In The Failedvirtualmachines Parameter.<br>        Failedvirtualmachines &lt;Citrix.Desktopupdatemanager.Sdk.Virtualmachinecreation\[\]&gt;<br>            Adaccountname &lt;String&gt;<br>                The Domain-Qualified Ad Account Name Of The Machine.<br>            Adaccountsid &lt;String&gt;<br>                The Ad Account Sid Of The Machine Account.<br>            Diagnosticinformation &lt;Citrix.Machinecreation.Sdk.Exceptionsurrogate\[\]&gt;<br>                A Collection Of Handled Error States Which Caused The Provisioning To Fail.<br>                    Exceptiontype &lt;String&gt;<br>                      The Type Of Exception This Object Represents<br>                    Message  &lt;String&gt;<br>                      The Exception Message<br>                    Details  &lt;String&gt;<br>                      The Full Exception Content Including Stack Trace<br>                    Innerexception &lt;Citrix.Machinecreation.Sdk.Exceptionsurrogate&gt;<br>                      Information Relating To Any Contributing Error State<br>            Status &lt;String&gt;<br>            Statusadditionalinformation &lt;String&gt;<br>            Vmid &lt;String&gt;<br>                The Virtual Machine Identifier In The Hypervisor.<br>            Vmname &lt;String&gt;<br>                The Display Name Of The Virtual Machine In The Hypervisor.<br>        Removedvirtualmachines &lt;Citrix.Desktopupdatemanager.Sdk.Virtualmachinecreation\[\]&gt;<br>            See Failedvirtualmachines For Details Of The Object Parameters.<br>        Progressestimator<br>            Gives An Estimate Of The Number Of Virtual Machines Processed, Averaging Over Virtual Machines That Were Both Partly And Completely Processed.

## Notes
Only one long-running task for each provisioning scheme can be processed at a time.<br>    This task still operates if the hosting unit or VMs in the hypervisor are missing. This removes the data from the Citrix Machine Creation Services, but the VMs remain in the hypervisor.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    WorkflowHostUnavailable<br>    The task could not be started because the database connection is inactive.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type RemoveVirtualMachine, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    RemovingVirtualMachines
## Examples

### Example 1
```
c:\PS>,(Get-ProvVM -ProvisioningSchemeName XenPS) | Remove-ProvVM XenPS

TaskId                       : cfb506a5-cc7e-4a49-ac7b-dd960029d0d3

Active                       : False

Host                         : DDC

DateStarted                  : 10/10/2012 16:39:45

Metadata                     : {}

WorkflowStatus               : Completed

ProvisioningSchemeUid        : e1afc8fb-3f52-42ea-9a17-305fdb0b6ee4

ProvisioningSchemeName       : XenPS

TaskState                    : Finished

TaskStateInformation         :

VirtualMachinesToRemoveCount : 2

RemovedVirtualMachines       : {XD\IP0001$, XD\IP0002$}

FailedVirtualMachines        : {}

VirtualMachinesRemovedCount  : 2

VirtualMachinesFailedCount   : 0

ProgressEstimator            : 2

Type                         : RemoveVirtualMachine

Status                       : Finished

CurrentOperation             :

TaskProgress                 : 100

TaskExpectedCompletion       : 10/10/2012 16:39:50

LastUpdateTime               : 10/10/2012 16:39:50

ActiveElapsedTime            : 5

DateFinished                 : 10/10/2012 16:39:50

TerminatingError             :
```
#### Description
Remove all VMs from provisioning scheme XenPS
