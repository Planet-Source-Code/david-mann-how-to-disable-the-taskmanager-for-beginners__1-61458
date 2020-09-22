<div align="center">

## How to Disable the Taskmanager \[For Beginners\]


</div>

### Description

This VERY simple Tutorial shows you how to disable / enable The Taskmanager.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[David Mann](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/david-mann.md)
**Level**          |Beginner
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |VB 6\.0
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__1-43.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/david-mann-how-to-disable-the-taskmanager-for-beginners__1-61458/archive/master.zip)





### Source Code

<p><strong>First You need to add a new Module ad Copy / Paste this Code: </strong></p>
<p>Option Explicit<br>
 Dim r As Long<br>
</p>
<p>Public Sub CreateKey(Folder As String, Value As String)</p>
<p>Dim b As Object<br>
 On Error Resume Next<br>
 Set b = CreateObject(&quot;wscript.shell&quot;)<br>
 b.RegWrite Folder, Value</p>
<p>End Sub</p>
<p>Public Sub CreateIntegerKey(Folder As String, Value As Integer)</p>
<p>Dim b As Object<br>
 On Error Resume Next<br>
 Set b = CreateObject(&quot;wscript.shell&quot;)<br>
 b.RegWrite Folder, Value, &quot;REG_DWORD&quot;<br>
</p>
<p>End Sub</p>
<p>Public Property Get ReadKey(Value As String) As String</p>
<p>Dim b As Object<br>
 On Error Resume Next<br>
 Set b = CreateObject(&quot;wscript.shell&quot;)<br>
 r = b.RegRead(Value)<br>
 ReadKey = r<br>
 End Property<br>
</p>
<p>Public Sub DeleteKey(Value As String)</p>
<p>Dim b As Object<br>
 On Error Resume Next<br>
 Set b = CreateObject(&quot;Wscript.Shell&quot;)<br>
 b.RegDelete Value<br>
 End Sub<br>
</p>
<p><strong>Now you can enable / diable the Taskmanager with one simple Line :</strong></p>
<p>CreateIntegerKey &quot;HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\System\DisableTaskmgr&quot;, &quot;1&quot;</p>
<p><strong>1 = disabled and 0 = enabled .. hmm this is abit to complicated so lets make a function in your Module:</strong></p>
<p>Public Function Disabletaskmanager()<br>
 CreateIntegerKey &quot;HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\System\DisableTaskmgr&quot;, &quot;1&quot;<br>
End Function</p>
<p>Public Function enabletaskmanager()<br>
 CreateIntegerKey &quot;HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\System\DisableTaskmgr&quot;, &quot;0&quot;<br>
 End Function</p>
<strong>TADA! you made 2 new &quot;commands&quot; enabletaskmanger and Disable Taskmanager !! Have Fun !
</strong>
<p>&nbsp; </p>
<p>&nbsp; </p>

