
# Publish-Provmastervmimage
Update the master image associated with the provisioning scheme.
## Syntax
```
Publish-ProvMasterVMImage [-ProvisioningSchemeName] <String> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Publish-ProvMasterVMImage -ProvisioningSchemeName <String> [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Publish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Publish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to update the hard disk image used to provision virtual machines. If the provisioning scheme is a 'CleanOnBoot' type, then the next time that virtual machines are started, their hard disks are updated to this new image.  Regardless of the 'CleanOnBoot' type, all new virtual machines created after this command will use this new hard disk image.

A background task will be created to remove the old hard disk copies.  You can locate and monitor this task using the Get-ProvTask cmdlet.

A snapshot or VM template is used rather than a VM, so that the content of the hard disk for the provisioning scheme can be easily determined.

As the snapshot or VM template are specified using a path into the Citrix Host Service PowerShell Provider, the Citrix Host Service PowerShell snap-in must also be loaded for this cmdlet to be used.

The previous hard disk image path is stored into the history (see Get-ProvSchemeMasterVMImageHistory).  The data stored in the history allows for a rollback to be undertaken, to revert to the previous hard disk image if required.


## Related Commands

* [Get-ProvSchemeMasterVMImageHistory](../Get-ProvSchemeMasterVMImageHistory/)
* [Get-ProvScheme](../Get-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The provisioning scheme to which the hard disk image should be updated. | true | true (ByPropertyName) |  |
| MasterImageVM | The path in the hosting unit provider to the virtual machine snapshot or VM template that will be used.  This identifies the hard disk to be used and the default values for the memory and processors.  This must be a path to a Snapshot or Template item in the hosting unit that the hosting unit name or hosting unit Uid refers to.<br>Valid paths are of the format; XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;VMName&gt;.vm\\&lt;SnapshotName&gt;.snapshot XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;TemplateName&gt;.template | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The provisioning scheme identifier to which the hard disk image should be updated. | true | false |  |
| VhdTemplateSource | A file path to a source VHD template to be used when performing application scanning during image preparation. The presence of this parameter in conjunction with VhdResultDestination implies that application scanning is to be performed | false | false |  |
| VhdResultDestination | A file path (including file name) where the VHD disk file containing the results of application scanning should be written. | false | false |  |
| AppScanResultsFile | File name to which the results of application scanning should be written. | false | false |  |
| FunctionalLevel | The FunctionalLevel of the VDA installed on the given MasterImageVM. | false | false |  |
| RunAsynchronously | Indicates whether or not the cmdlet should return before it is complete.  If specified, the command returns an identifier for the task that was created.  You can monitor this task using the get-ProvTask cmdlet. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history will be removed from the database once the task has finished.  This cannot be specified for tasks that are run asynchronously. | false | false | false |
| DoNotStoreOldImage | Specifies that the current image should not be added to the image history list for the provisioning scheme. This is useful when rolling back to a previous image. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid<br>    When "Runasynchronously" Is Specified, This Identifier Is Returned To Provide The Task Identifier.<br>System.Management.Automation.Pscustomobject<br>    This Object Provides Details Of The Task Run And Contains The Following Information:<br>        Taskid &lt;Guid&gt;<br>            The Identifier For The Task That Was Performed.<br>        Active &lt;Boolean&gt;<br>            Indicates Whether The Task Is Still Processing Or Is Complete.<br>        Host &lt;String&gt;<br>            The Name Of The Host On Which The Task Is Running Or Was Run.<br>        Datestarted &lt;Datetime&gt;<br>            The Date And Time That The Task Was Initiated.<br>        Type &lt;Citrix.Xdinterservicetypes.Jobtype&gt;<br>            The Type Of The Task.  For New Provisioning Scheme Tasks This Is Always "Newprovisioningscheme".<br>        Metadata &lt;Citrix.Machinecreation.Sdk.Metadata\[\]&gt;<br>            The List Of Metadata Stored Against The Task.  For New Tasks This Will Be Empty Until Metadata Is Added.<br>        Workflowstatus &lt;System.Workflow.Runtime.Workflowstatus&gt;<br>            Indicates The Status Of The Workflow That Is Being Used To Process The Task.<br>        Provisioningschemename &lt;String&gt;<br>            The Name Of The Provisioning Scheme That The Task Was For.<br>        Provisioningschemeuid &lt;Guid&gt;<br>            The Unique Identifier Of The Provisioning Scheme That The Task Was For.<br>        Masterimage &lt;String&gt;<br>            The Path (In The Hosting Unit Provider) Of The Virtual Machine Snapshot Or Vm Template That Was Used As The Master Image For The Task.<br>        Identitypoolname &lt;String&gt;<br>            The Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>        Identitypooluid &lt;Guid&gt;<br>            The Unique Identifier Name Of The Identity Pool (From The Adidentity Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>        Hostingunitname &lt;String&gt;<br>            The Name Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>        Hostingunituid<br>            The Unique Identifier Of The Hosting Unit (From The Hosting Unit Powershell Snap-In) That The New Provisioning Scheme Will Use.<br>        Taskstate &lt;Citrix.Desktopupdatemanager.Sdk.Newprovisioningschemestate&gt;<br>            The State Of The Task.  This Can Be Any Of The Following:<br>                Processing<br>                    Indicates That The Task Has Just Begun And Has Not Done Anything Yet.<br>                Locatingresources,<br>                    Indicates That The Workflow Is Locating Resources From Other Services.<br>                Hostingunitnotfound<br>                    Indicates That The Task Failed Because The Required Hosting Unit Could Not Be Located.<br>                Virtualmachinesnapshotnotfound<br>                    Indicates That The Task Failed Because The Required Snapshot Or Vm Template Could Not Be Located.<br>                Consolidatingmasterimage<br>                    Indicates That The Task Is Consolidating The Master Image.<br>                Replicatingconsolidatedimagetoallstorage<br>                    Indicates That The Task Is Replicating The Consolidated Master Image.<br>                Storingprovisioningscheme<br>                    Indicates That The Task Is Storing The Provisioning Scheme Data To The Database.<br>                Finished<br>                    Indicates That The Task Has Completed With No Errors.<br>                Provisioningschemealreadyexists<br>                    Indicates That The Task Failed Because A Provisioning Scheme With The Same Name Already Exists.<br>                Identitypoolnotfound<br>                    Indicates That The Task Failed Because The Identity Pool Specified Could Not Be Found.<br>                Mastervmimageisnotpartofprovisioningschemehostingunit,<br>                    Indicates That The Hosting Unit That The Master Image Originated From Is Not The Same Hosting Unit That The Provisioning Scheme Is Defined To Use.<br>                Mastervmimageisnotasnapshot<br>                    Indicates That The Task Failed Because The Master Vm Image Path Does Not Refer To A Snapshot Or A Vm Template Item.<br>                Provisioningschemenotfound<br>                    Could Not Find A Provisioning Scheme With The Specified Name.<br>                Taskalreadyrunningforprovisioningscheme<br>                    A Task For A Provisioning Scheme With The Same Name Is Already Running.<br>                Invalidmastervmconfiguration<br>                    The Vm Snapshot Or Vm Template Specified As The Master Had An Invalid Configuration.<br>                Invalidmastervmstate<br>                    The Vm Snapshot Or Vm Template Specified As The Master Is Currently In An Invalid State.<br>                Insufficientresources<br>                    Indicates That The Task Failed Because The Hypervisor Did Not Have Enough Resources To Complete The Task.<br>                Storagenotfound<br>                    Indicates That No Associated Storage Was Found In The Hosting Unit.<br>                Canceled<br>                    Indicates That The Task Was Stopped By User Intervention (Using Stop-Provtask).<br>        Taskstateinformation &lt;String&gt;<br>            Holds String Data Providing More Details About The Current Task State.<br>        Taskprogress<br>            The Progress Of The Task 0-100%.

## Notes
Only one long-running task per provisioning scheme can be processed at any one time.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    WorkflowHostUnavailable<br>    The task could not be started because the database connection is inactive.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type PublishImage, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    ConsolidatingMasterImage<br>    PreparingMasterImage<br>    ReplicatingMasterImage<br>    CommittingScheme
## Examples

### Example 1
```
c:\PS>Publish-ProvMasterVMImage -ProvisioningSchemeName MyScheme -MasterImageVM XDHyp:\H

stingUnits\HostUnit1\RhoneCC_baseXP.vm\base.snapshot

TaskId                 : 248f102f-073f-45fe-aea9-1819a6d6dd1f

Active                 : False

Host                   : MyHost

DateStarted            : 17/05/2010 17:37:57

Type                   : PublishImage

Metadata               : {}

WorkflowStatus         : Completed

ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName : MyScheme

MasterImage            : /RhoneCC_baseXP.vm/base.snapshot

HostingUnitName        : HostUnit1

HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

ADIdentityPoolName     :

ADIdentityPoolUid      : 03743136-e43b-4a87-af74-ab71686b3c16

CurrentOperation       :

TaskState              : Finished

TaskStateInformation   :
```
#### Description
Updates the master hard disk image for the provisioning Scheme "MyScheme" to use the "base.snapshot" hard disk image.
