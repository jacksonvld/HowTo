# Necessário baixar o software e executar o script no mesmo diretório

CONST ForReading = 1  
Set objNetwork = WScript.CreateObject("WScript.Network")  
strUserName = objNetwork.UserName  
Set fso = CreateObject("Scripting.FileSystemObject")  
Set ObjShell = Createobject("wscript.shell")  
Set FileSystem = CreateObject("Scripting.FileSystemObject")  
strDBFileLocation = "cert8.db"  

mydir = Replace(WScript.ScriptFullName,WScript.ScriptName,"")  
strProfileLocation = "C:\Users\" & strUserName & "\AppData\Roaming\Mozilla\Firefox\profiles.ini"  

If (fso.FileExists(strProfileLocation)) Then  
strData = FileSystem.OpenTextFile(strProfileLocation ,ForReading).ReadAll  
arrLines = Split(strData,vbCrLf)  

For Each strLine in arrLines  
If Left(strLine, 14) = "Path=Profiles/" then  
strProfileName = Right(strLine,(len(strLine) - 14))  
End if  
Next  

strProfileFolder = "C:\Users\" & strUserName & "\AppData\Roaming\Mozilla\Firefox\Profiles\" & strProfileName  

'if (fso.FolderExists(strProfileFolder)) Then  
'myfile = strProfileFolder & "\cert8.db"  
'oldfile = strProfileFolder & "\cert8.old"  
'FileSystem.CopyFile myfile, oldfile, True  
'End if  

Certcmd = "bin\certutil.exe" & " " & "-A -d " & strProfileFolder & " " & "-i" & " " & "ca.crt" & " -n" & " ca.crt -t" & " " & """CT,c,c"""  

Objshell.run Certcmd,0,True  

Else  
Wscript.Quit()  
End if  
