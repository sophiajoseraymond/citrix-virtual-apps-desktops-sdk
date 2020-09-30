
# Enable-Citrixtrace
Enables saving of trace files on disk at a given persistDirectory.
## Syntax
```
Enable-CitrixTrace -Listen <String> [<CommonParameters>]
```
## Detailed Description
This cmdlet Enables or disables saving of trace files on disk at a given persistDirectory:


## Related Commands

* [Disable-CitrixCallHome](../Disable-CitrixCallHome/)
* [Enable-CitrixCallHome](../Enable-CitrixCallHome/)
* [Set-CitrixCallHomeSchedule](../Set-CitrixCallHomeSchedule/)
* [Get-CitrixCallHomeSchedule](../Get-CitrixCallHomeSchedule/)
* [Start-TelemetryUpload](../Start-TelemetryUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Listen | Specify the parameters passed to listeners. Json-formatted. | true | false |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Configure Citrix Call Home For Saving Traces On Disk
```
C:\PS>Enable-CitrixTrace -Listen '{"trace":{"enabled": true,"persistDirectory": "C:\\Users\\Public","maxSizeBytes": 1000000, "sliceDurationSeconds": 300}}'
```Enables saving of trace files on disk at a given persistDirectory. Max size of trace files stored is configured via maxSizeBytes and sliceDurationSeconds defines duration in seconds of the slice/block of traces.
