---
external help file: PSITPro5_Management.xml
online version: http://go.microsoft.com/fwlink/p/?linkid=290485
schema: 2.0.0
---

# Debug-Process
## SYNOPSIS
Debugs one or more processes running on the local computer.

## SYNTAX

### UNNAMED_PARAMETER_SET_1
```
Debug-Process [-Name] <String[]> [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_2
```
Debug-Process [-Id] <Int32[]> [-Confirm] [-WhatIf]
```

### UNNAMED_PARAMETER_SET_3
```
Debug-Process -InputObject <Process[]> [-Confirm] [-WhatIf]
```

## DESCRIPTION
The Debug-Process cmdlet attaches a debugger to one or more running processes on a local computer.
You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.

This cmdlet attaches the debugger that is currently registered for the process.
Before using this cmdlet, verify that a debugger is downloaded and correctly configured.

## EXAMPLES

### Example 1: Attach a debugger to a process on the computer
```
PS C:\>Debug-Process -Name "Windows Powershell"
```

This command attaches a debugger to the Windows PowerShell process on the computer.

### Example 2: Attach a debugger to all processes that begin with the specified string
```
PS C:\>Debug-Process -Name "SQL*"
```

This command attaches a debugger to all processes that have names that begin with SQL.

### Example 3: Attach a debugger to multiple processes
```
PS C:\>Debug-Process "Winlogon", "Explorer", "Outlook"
```

This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.

### Example 4: Attach a debugger to multiple process IDs
```
PS C:\>Debug-Process -Id 1132, 2028
```

This command attaches a debugger to the processes that have process IDs 1132 and 2028.

### Example 5: Use Get-Process to get a process then attach a debugger to it
```
PS C:\>Get-Process "Windows PowerShell" | Debug-Process
```

This command attaches a debugger to the Windows PowerShell processes on the computer.
It uses the Get-Process cmdlet to get the Windows PowerShell processes on the computer, and it uses a pipeline operator (|) to send the processes to the Debug-Process cmdlet.

To specify a particular PowerShell process, use the ID parameter of Get-Process.

### Example 6: Attach a debugger to a current process on the local computer
```
PS C:\>$PID | Debug-Process
```

This command attaches a debugger to the current Windows PowerShell processes on the computer.

The command uses the $PID automatic variable, which contains the process ID of the current Windows PowerShell process.
Then, it uses a pipeline operator (|) to send the process ID to the Debug-Process cmdlet.

For more information about the $PID automatic variable, see about_Automatic_Variables.

### Example 7: Attach a debugger to the specified process on multiple computers
```
PS C:\>Get-Process -ComputerName "Server01", "Server02" -Name "MyApp" | Debug-Process
```

This command attaches a debugger to the MyApp processes on the Server01 and Server02 computers.

The command uses the Get-Process cmdlet to get the MyApp processes on the Server01 and Server02 computers.
It uses a pipeline operator to send the processes to the Debug-Process cmdlet, which attaches the debuggers.

### Example 8: Attach a debugger to a process that uses the InputObject parameter
```
PS C:\>$P = Get-Process "Windows PowerShell"
PS C:\>Debug-Process -InputObject $P
```

This command attaches a debugger to the Windows PowerShell processes on the local computer.

The first command uses the Get-Process cmdlet to get the Windows PowerShell processes on the computer.
It saves the resulting process object in the variable named $P.

The second command uses the InputObject parameter of the Debug-Process cmdlet to submit the process object in the $P variable.

## PARAMETERS

### -Id
Specifies the process IDs of the processes to be debugged.
The Id parameter name is optional.

To find the process ID of a process, type Get-Process.

```yaml
Type: Int32[]
Parameter Sets: UNNAMED_PARAMETER_SET_2
Aliases: PID,ProcessId

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject
Specifies the process objects that represent processes to be debugged.
Enter a variable that contains the process objects or a command that gets the process objects, such as the Get-Process cmdlet.
You can also pipe process objects to this cmdlet.

```yaml
Type: Process[]
Parameter Sets: UNNAMED_PARAMETER_SET_3
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies the names of the processes to be debugged.
If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name. 
The Name  parameter is optional.

```yaml
Type: String[]
Parameter Sets: UNNAMED_PARAMETER_SET_1
Aliases: ProcessName

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### System.Int32, System.Diagnostics.Process, System.String
You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.

## OUTPUTS

### None
This cmdlet does not generate any output.

## NOTES
* This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class. For more information about this method, see AttachDebugger Methodhttp://go.microsoft.com/fwlink/?LinkId=143640 at http://go.microsoft.com/fwlink/?LinkId=143640.

*

## RELATED LINKS

[Debug-Process](ba768230-a5ed-4b80-8e1f-3cba8413aa78)

[Get-Process](b30db241-c0f6-40d3-ab3b-ab86342b36c1)

[Start-Process](cd3a57db-5549-47b3-92d7-5bfc9009e785)

[Stop-Process](3864dc3d-34ec-4ebd-8132-776346c00871)

[Wait-Process](861eb7b3-a18e-4445-9a69-2c65c420866f)

[about_Automatic_Variables](68bc622f-eb7e-4cf5-9c56-a289737efc99)
