
# New-Brokerrebootschedulev2
Creates a new reboot schedule for a desktop group.
## Syntax

```
New-BrokerRebootScheduleV2 [-Name] <String> -DesktopGroupName <String> -RebootDuration <Int32> [-Day <RebootScheduleDays>] [-DayInMonth <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-FrequencyFactor <Int32>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-RestrictToTag <String>] [-StartDate <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-WeekInMonth <RebootScheduleWeeks>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
New-BrokerRebootScheduleV2 [-Name] <String> -DesktopGroupUid <Int32> -RebootDuration <Int32> [-Day <RebootScheduleDays>] [-DayInMonth <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-FrequencyFactor <Int32>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-RestrictToTag <String>] [-StartDate <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-WeekInMonth <RebootScheduleWeeks>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
The New-BrokerRebootScheduleV2 cmdlet is used to define a reboot schedule for a desktop group.


## Related Commands

* [Get-BrokerRebootScheduleV2](../Get-BrokerRebootScheduleV2/)
* [Set-BrokerRebootScheduleV2](../Set-BrokerRebootScheduleV2/)
* [Remove-BrokerRebootScheduleV2](../Remove-BrokerRebootScheduleV2/)
* [Rename-BrokerRebootScheduleV2](../Rename-BrokerRebootScheduleV2/)
* [Start-BrokerRebootCycle](../Start-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The name of the new reboot schedule. | true | true (ByPropertyName) |  |
| RebootDuration | Approximate maximum number of minutes over which the scheduled reboot cycle runs. | true | true (ByPropertyName) |  |
| DesktopGroupName | The name of the desktop group that this reboot schedule is applied to. | true | true (ByPropertyName) |  |
| DesktopGroupUid | The Uid of the desktop group that this reboot schedule is applied to. | true | true (ByPropertyName) |  |
| Day | For weekly schedules, the days of the week on which the scheduled reboot-cycle starts (one or more of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday). | false | true (ByPropertyName) |  |
| DayInMonth | For monthly schedules, the day in the month on which the scheduled reboot-cycle starts (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday). | false | true (ByPropertyName) |  |
| Description | An optional description for the reboot schedule. | false | true (ByPropertyName) |  |
| Enabled | Boolean that indicates if the new reboot schedule is enabled. | false | true (ByPropertyName) |  |
| Frequency | Frequency with which this schedule runs (either Weekly or Daily or Monthly). | false | true (ByPropertyName) |  |
| FrequencyFactor | The frequency factor for the reboot schedule. It indicates how often the schedule should run with respect to the frequency. For example, if the FrequencyFactor is set to 2, it means every two days from the StartDate when the Frequency is Daily, every two weeks from StartDate when the Frequency is Weekly, and similarly for monthly. It defaults to 1 if not provided. StartDate property needs to be provided if the frequency factor is greater than 1. | false | true (ByPropertyName) |  |
| IgnoreMaintenanceMode | Boolean value to reboot machines in maintenance mode | false | true (ByPropertyName) | false |
| MaxOvertimeStartMins | Maximum delay in minutes after which the scheduled reboot will not take place. | false | true (ByPropertyName) | 0 |
| RestrictToTag | If set the reboot schedule only applies to machines in the desktop group with the specified tag. | false | true (ByPropertyName) |  |
| StartDate | The date on which the first schedule is expected to run, date is in ISO 8601 Format (YYYY-MM-DD). The actual start date to match the frequency pattern need not be provided. For example, if today is Monday and the schedule is set to run every Sunday for every four weeks, there is no need to identify the date on which Sunday falls after four weeks. Today's date ((Get-Date).Date.ToString('yyyy-MM-dd')) can be provided and the service would adjust the start date to reflect the actual date i.e, the Sunday four weeks from today. Get-BrokerRebootScheduleV2 cmdlet will reflect the actual start date. | false | true (ByPropertyName) |  |
| StartTime | Time of day at which the scheduled reboot cycle starts (HH:MM). | false | true (ByPropertyName) |  |
| UseNaturalReboot | Boolean value indicating whether the machines should reboot whenever they happen to have no sessions, rather than at equally spaced times within the cycle duration. | false | true (ByPropertyName) | false |
| WarningDuration | Time prior to the initiation of a machine reboot at which warning message is displayed in all user sessions on that machine. If the warning duration is zero then no message is displayed. In some cases the time required to process a reboot schedule may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | true (ByPropertyName) |  |
| WarningMessage | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot. | false | true (ByPropertyName) |  |
| WarningRepeatInterval | Time to wait after the previous reboot warning before displaying the warning message in all user sessions on that machine again. If the warning repeat interval is zero then the warning message is not displayed after the initial warning. | false | true (ByPropertyName) |  |
| WarningTitle | The window title used when showing the warning message in user sessions on a machine scheduled for reboot. | false | true (ByPropertyName) |  |
| WeekInMonth | For monthly schedules, the week in the month on which the scheduled reboot-cycle starts (one of First, Second, Third, Fourth, Last). | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Rebootschedulev2

## Examples

### Example 1

```
C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "02:00" -Enabled $true -RebootDuration 120
```

#### Description
Schedules the machines in the desktop group named 'BankTellers' to be rebooted every night between 2 AM and 4 AM.
### Example 2

```
C:\PS> New-BrokerRebootScheduleV2 -Name 'Saturday reboots' -DesktopGroupUid 17 -Frequency Weekly -Day Saturday -StartTime "01:00" -Enabled $true -RebootDuration 240 -WarningTitle "WARNING: Reboot pending" -WarningMessage "Save your work" -WarningDuration 10
```

#### Description
Schedules the machines in the desktop group having Uid 17 to be rebooted every Saturday early morning between 1 AM and 5 AM. Ten minutes prior to rebooting, each machine will display a message box with the title "WARNING: Reboot pending" and message "Save your work" in every user session.
### Example 3

```
C:\PS> New-BrokerRebootScheduleV2 -Name 'Saturday reboots' -DesktopGroupUid 17 -Frequency Weekly -FrequencyFactor 4 -Day "Saturday,Sunday" -StartDate "2021-02-03" -StartTime "01:00" -Enabled $true -RebootDuration 240 -WarningTitle "WARNING: Reboot pending" -WarningMessage "Save your work" -WarningDuration 10
```

#### Description
Schedules the machines in the desktop group having Uid 17 to be rebooted Saturday and Sunday early morning between 1 AM and 5 AM for every four weeks starting from Feb 6, 2021. Ten minutes prior to rebooting, each machine will display a message box with the title "WARNING: Reboot pending" and message "Save your work" in every user session.
### Example 4

```
C:\PS> New-BrokerRebootScheduleV2 -Name 'Monthly reboots' -DesktopGroupUid 17 -Frequency Monthly -DayInMonth Saturday -WeekInMonth Last -StartTime "01:00" -Enabled $true -RebootDuration 240 -WarningTitle "WARNING: Reboot pending" -WarningMessage "Save your work" -WarningDuration 10
```

#### Description
Schedules the machines in the desktop group having Uid 17 to be rebooted the last Saturday of the month early morning between 1 AM and 5 AM for every month. Ten minutes prior to rebooting, each machine will display a message box with the title "WARNING: Reboot pending" and message "Save your work" in every user session.
### Example 5

```
C:\PS> New-BrokerRebootScheduleV2 -Name 'Monthly reboots' -DesktopGroupUid 17 -Frequency Monthly -FrequencyFactor 2 -StartDate "2021-02-03" -DayInMonth Sunday -WeekInMonth First -StartTime "01:00" -Enabled $true -RebootDuration 240 -WarningTitle "WARNING: Reboot pending" -WarningMessage "Save your work" -WarningDuration 10
```

#### Description
Schedules the machines in the desktop group having Uid 17 to be rebooted the first Sunday of the month early morning between 1 AM and 5 AM for every two months, starting from Feb 7, 2021 which is the first Sunday of Feburary, 2021. Ten minutes prior to rebooting, each machine will display a message box with the title "WARNING: Reboot pending" and message "Save your work" in every user session.
### Example 6

```
C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "03:00" -Enabled $true -RebootDuration 120 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
```

#### Description
Schedules the machines in the desktop group named 'BankTellers' to be rebooted every night between 3 AM and 5 AM. Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.
### Example 7

```
C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "03:00" -Enabled $true -RebootDuration 120 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5 -RestrictToTag 'Daily Reboot'
```

#### Description
Schedules only machines with the tag 'Daily Reboot' in the desktop group named 'BankTellers' to be rebooted every night between 3 AM and 5 AM. Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.
