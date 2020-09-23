<div align="center">

## How to use authentication while sending mails using SMTP with ASP\.NET\.


</div>

### Description

This article demonstrates how to authenticate a SMTP server in an ASP.NET application.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Kaustav N](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/kaustav-n.md)
**Level**          |Beginner
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |C\#, VB\.NET, ASP\.NET
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__10-9.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/kaustav-n-how-to-use-authentication-while-sending-mails-using-smtp-with-asp-net__10-1725/archive/master.zip)





### Source Code

<html>
<head>
<meta http-equiv="Content-Language" content="en-us">
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
<title>Authenticate a SMTP Server in ASP.NET -- By Kaustav Neogy</title>
</head>
<table border="0" cellpadding="0" cellspacing="0" style="border-collapse: collapse" bordercolor="#111111" width="100%" id="AutoNumber1">
 <tr>
 <td width="100%">
 <p align="justify"><font face="Verdana">In .NET we can use the
 System.Web.Mail Namespace to send mails. The SMTPMail Class provides
 properties and methods for sending messages using the Collaboration Data
 Objects for Windows 2000 (CDOSYS) message component. However there exists no
 direct way to use authentication with a SMTP Server. Here’s a quick
 workaround to it.<br>
&nbsp;</font></td>
 </tr>
 <tr>
 <td width="100%"> </td>
 </tr>
 <tr>
 <td width="100%">&nbsp;</td>
 </tr>
 <tr>
 <td width="100%"><b><font face="Verdana">Code:<br>
 </font></b></td>
 </tr>
 <tr>
 <td width="100%">&nbsp;</td>
 </tr>
 <tr>
 <td width="100%"><font face="Verdana" size="2" color="#0000FF">Public Sub
 Send_Mail_With_Auth(ByVal szTo As String, ByVal szFrom As String, ByVal
 szSubject As String, ByVal szBody As String)<br>
 <br>
 Dim myMsg<br>
 Dim myConfig<br>
 Dim Flds<br>
 <br>
 Const cdoSendUsingPort = 2<br>
 Const cdoBasic As Integer = 1<br>
 <br>
 myMsg = CreateObject("CDO.Message")<br>
 myConfig = CreateObject("CDO.Configuration")<br>
 Flds = myConfig.Fields<br>
 <br>
 With Flds<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Item("http://schemas.microsoft.com/cdo/configuration/sendusing") =
 cdoSendUsingPort<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Item("http://schemas.microsoft.com/cdo/configuration/smtpserver") = "your_smtp_server"<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Item("http://schemas.microsoft.com/cdo/configuration/smtpconnectiontimeout")
 = 10<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Item("http://schemas.microsoft.com/cdo/configuration/sendusername") =
 "username"<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Item("http://schemas.microsoft.com/cdo/configuration/sendpassword") =
 "password"<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Item("http://schemas.microsoft.com/cdo/configuration/smtpauthenticate") =
 cdoBasic<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Update()<br>
 End With<br>
 <br>
 With myMsg<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Configuration = myConfig<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .To = szTo<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .From = szFrom<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Subject = szSubject<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .HTMLBody = szBody<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 .Send()<br>
 End With<br>
 <br>
 myMsg = Nothing<br>
 myConfig = Nothing<br>
 Flds = Nothing<br>
 <br>
 End Sub</font></td>
 </tr>
 <tr>
 <td width="100%"> </td>
 </tr>
</table>
</html>

