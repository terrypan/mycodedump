# Windows 7 #
## Rebuilding the Icon Cache Database ##
If some Applications (like Firefox) don't display their application icons in the task panel anymore, the win7 icon cache may be corrupt. The following steps may solve the problem and bring the icons back to your task panel.

  1. Close all folder windows that are currently open.
  1. Launch Task Manager using the CTRL+SHIFT+ESC key sequence, or by running taskmgr.exe.
  1. In the Process tab, right-click on the Explorer.exe process and select End Process.
  1. Click the End process button when asked for confirmation.
  1. From the File menu of Task Manager, select New Task (Run.)
  1. Type CMD.EXE, and click OK
  1. In the Command Prompt window, type the commands one by one and press ENTER after each command:
```
CD /d %userprofile%\AppData\Local
DEL IconCache.db /a
EXIT
```
  1. In Task Manager, click File, select New Task (Run.)
  1. Type EXPLORER.EXE, and click OK.