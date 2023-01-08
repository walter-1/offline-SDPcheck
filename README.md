# offline-SDPcheck
PowerShell based script set for analysis of SDP reports (former known as RFLcheck)

**Download** latest version from aka.ms/getRFL (or  https://github.com/walter-1/offline-SDPcheck/releases/ )

## Purpose
rapidly determine missing MS hotfixes or monthly cumulative updates on server or client machines, and more automated checks...

## Check_RFL/SDP setup and installation instructions
You can install SDPcheck on a TeamServer or locally on your PC (RFL will auto-update)

We recommend to use a team share 'ToolsShare' on a TeamServer `\\TeamServer`, in order to minimize monthly maintenance.
If you are sharing the RFL scripts on a different \\TeamServer\ToolsShare adjust line $RFLroot in \\TeamServer\ToolsShare\RFL\_SDPcheck.ini, and also replace 'localhost\\ToolsShare'  in file Rfl-Check_ShellExtension.reg

The line for $RFLroot should reflect your actual share location

	$RFLroot = "\\localhost\ToolsShare\RFL\"

If  using a TeamServer (task for TeamServer Admin):
1. Create a new Share named 'ToolsShare' on the TeamServer
2. Expand the RFL.zip into the folder \\TeamServer\ToolsShare\ (files will be expanded in subfolder \RFL)
3. in file \\TeamServer\ToolsShare\RFL\_SDPcheck.ini replace line $RFLroot = "\\localhost\ToolsShare\rfl" with $RFLroot = "\\TeamServer\ToolsShare\RFL"
4. Edit the RFL-Check_ShellExtension.reg file and global replace '\\\\LocalHost\\ToolsShare' with '\\\\TeamServer\\ToolsShare'
5. on your own PC: download locally and DoubleClick the reg file \\TeamServer\ToolsShare\RFL\RFL-Check_ShellExtension.reg


If  using only your own PC (no TeamServer):
1. Create a new Share named 'ToolsShare' on local disk
2. Expand the RFL.zip into the folder \\LocalHost\ToolsShare\ (files will be expanded in subfolder \RFL)
3. N/A - \\TeamServer\ToolsShare\RFL\_SDPcheck.ini already includes correct line $RFLroot = "\\localhost\ToolsShare\rfl"
4. N/A - (RFL-Check_ShellExtension*.reg files already point to '\\\\LocalHost\\ToolsShare')
3. on your own PC: DoubleClick the reg file \\LocalHost\ToolsShareRFL\RFL-Check_ShellExtension.reg

Now you can use the Explorer context menu on any extracted SDP folder.

The RFLcheck will automaticaly try to open resulting `*.txt` files in your favorite text Editor (default is NotePad.exe);

**hint**: if you register `*.txt` files to be opend with a more sophisticated editor like Notepad++ or TextPad, all result files will open as additional Tabs in your text Editor.

Note: SDP/RFLcheck will automatically update, when a new version is available.

## What is RFLcheck? 
RFLcheck is a set of Explorer Plugin and PowerShell scripts that enables engineers to identify missing Hotfixes in a customer supplied SDP report. 
Useful add-ons are 
- checks for 3rd party drivers (Pstat), 
- checks for incorrect or changed Registry settings, 
- PerformanceMonitorAnalysis (PMA), 
- Pstat-Compare, 
- Event-summary up to 6h before SDP collection, 
- check for specific Events, 
- re-Arrange-SDPFolders (for Cluster)

For details see MS internal KB3070416
