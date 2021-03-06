# Office 365: Manage single sign-on with Office 365
## Requires
- Visual Studio 2012
## License
- Apache License, Version 2.0
## Technologies
- Office 365
## Topics
- Windows PowerShell
- Single Sign-On
## Updated
- 02/27/2013
## Description

<p id="header"><span class="label">Summary:</span> This sample demonstrates how to use Windows PowerShell from a C# application to manage Office 365 single sign-on settings and to create new associated domains. The sample requires you to have a user administrator
 account in an Office 365 organization and to install the Microsoft Online Services Sign-In Assistant and the Microsoft Online Services Module for Windows PowerShell.</p>
<div id="mainSection">
<div id="mainBody">
<div class="introduction">
<h1 class="heading">Description of the sample</h1>
<div class="section" id="sectionSection0">This is a Visual C# sample application using Windows Presentation Foundation (WPF) to demonstrate how to use Windows PowerShell cmdlets called from managed code to make administrative configuration changes for an
 Office 365 organization.</div>
<h1 class="heading">Prerequisites</h1>
<div class="section" id="sectionSection1">
<p>The following are required to be configured or installed on the computer you will use to build and run the sample:</p>
<ul>
<li>
<p>Office 365 Enterprise subscription.</p>
</li><li>
<p>User account credentials that have at least User Management administrator privileges in the Office 365 organization.</p>
</li><li>
<p>Windows 7 or Windows Server 2008 R2 with Windows PowerShell installed.</p>
</li><li>
<p>Visual Studio 2012 including components for Windows Forms applications installed.</p>
</li><li>
<p>.NET Framework 3.5.1 installed and enabled in Visual Studio.</p>
</li><li>
<p><a href="http://www.microsoft.com/en-in/download/details.aspx?id=28177" target="_blank">Microsoft Online Services Sign-In Assistant</a> installed.</p>
</li><li>
<p><a href="http://go.microsoft.com/fwlink/p/?LinkId=281794" target="_blank">Microsoft Online Services Module for Windows PowerShell</a> installed and configured as described in the following paragraphs.</p>
</li></ul>
<p>To run the sample, you must enable remote control of Office 365 by performing the following steps.</p>
<h3 class="procedureSubHeading">Enable Office 365 remote control</h3>
<div class="subSection">
<ol>
<li>
<p>On the desktop, locate the shortcut for the Microsoft Online Services Module for Windows PowerShell.</p>
</li><li>
<p>Right-click the shortcut and choose <span class="ui">Run as Administrator</span>.</p>
</li><li>
<p>Click <span class="ui">Yes</span> if the <span class="ui">User Account Control</span> dialog box opens.</p>
</li><li>
<p>In Windows PowerShell, run the command <span class="ui">Get-ExecutionPolicy</span>.</p>
</li><li>
<p>If the command returned <span class="ui">RemoteSigned</span>, your computer is already configured properly to manage Office 365 remotely by using Windows PowerShell.</p>
</li><li>
<p>If the command returned is not <span class="ui">RemoteSigned</span> (typically
<span class="ui">Restricted</span>), run the command <span class="ui">Set-ExecutionPolicy RemoteSigned</span>, and then enter
<span class="ui">Y</span> when prompted.</p>
</li><li>
<p>In Windows PowerShell, run the command <span class="ui">Get-ExecutionPolicy</span> and verify it returns
<span class="ui">RemoteSigned</span>.</p>
</li><li>
<p>Close Windows PowerShell.</p>
</li></ol>
</div>
</div>
<h1 class="heading">Key components of the sample</h1>
<div class="section" id="sectionSection2">
<p>The sample is a Windows Forms application that contains the following:</p>
<ul>
<li>
<p>A main application window that displays a grid listing Office 365 single sign-on domains associated with the organization.</p>
</li><li>
<p>A dialog box to enter the administrator logon credentials.</p>
</li><li>
<p>A dialog box to set new single sign-on domain information.</p>
</li></ul>
</div>
<h1 class="heading">Open and build the sample</h1>
<div class="section" id="sectionSection3">
<p>Before using the sample, you should visit the Office 365 administration portal and verify the administrator account's privileges. That account must have at least User Management administrator privileges in the organization.</p>
<ol>
<li>
<p>Open Visual Studio 2012.</p>
</li><li>
<p>Click <span class="ui">File</span>, point to <span class="ui">Open</span>, and then click
<span class="ui">Project/Solution</span>.</p>
</li><li>
<p>Navigate to the directory into which you extracted the sample files.</p>
</li><li>
<p>In the <span class="ui">O365_SingleSignOn_cs</span> folder, select <span class="ui">
O365_SingleSignOn_cs.sln,</span> and click <span class="ui">OK</span>.</p>
</li></ol>
<p>The sample builds and Solution Explorer opens, as shown in the following figure.</p>
<img id="76586" src="http://i1.code.msdn.s-msft.com/office-365-manage-single-9cd8b579/image/file/76586/1/o365psmanagesinglesignon-001.png" alt="O365_SingleSignOn_cs in VS2012 Solution Explorer" width="281" height="285"></div>
<h1 class="heading">Run and test the sample</h1>
<div class="section" id="sectionSection4">
<ol>
<li>
<p>In Visual Studio click <span class="ui">Run</span>, or press F5, to build and start debugging the sample.</p>
</li><li>
<p>In the <span class="ui">Enter Credentials</span> dialog box, shown in the following figure, enter the user name and password for the administrator account, and click
<span class="ui">Login</span>.</p>
<p><img id="76587" src="http://i1.code.msdn.s-msft.com/office-365-manage-single-9cd8b579/image/file/76587/1/o365psmanagesinglesignon-002.png" alt="O365 Manage Single SignOn credentials dialog box" width="323" height="158"></p>
<p>&nbsp;</p>
</li><li>
<p>The main window opens in full-screen mode after you enter the credentials, as shown in the following figure. (Domain names are obscured in the figure.)</p>
<p><img id="76588" src="http://i1.code.msdn.s-msft.com/office-365-manage-single-9cd8b579/image/file/76588/1/o365psmanagesinglesignon-003.png" alt="O365 Manage Single SignOn main window" width="800" height="353"></p>
<p>&nbsp;</p>
</li><li>
<p>To create a new single sign-on domain, click <span class="ui">Create Domain</span>. The
<span class="ui">Add Domain</span> dialog box opens, as shown in the following figure. Fill in the
<span class="ui">Domain Name</span> field, select the appropriate <span class="ui">
Domain Type</span>, and then click <span class="ui">Add Domain</span>.</p>
<p><img id="76589" src="http://i1.code.msdn.s-msft.com/office-365-manage-single-9cd8b579/image/file/76589/1/o365psmanagesinglesignon-004.png" alt="O365 Manage Single SignOn New Domain dialog" width="376" height="183"></p>
<p>&nbsp;</p>
</li><li>
<p>To close the sample, click the <span class="ui">Close</span> button in the upper-right corner of the window.</p>
</li></ol>
</div>
<h1 class="heading">Troubleshooting</h1>
<div class="section" id="sectionSection5">
<p>The following table lists the common configuration and environment errors that help troubleshoot issues preventing the sample from building or deploying successfully.</p>
<div class="caption"></div>
<div class="tableSection">
<table cellspacing="2" cellpadding="5" width="50%" frame="lhs">
<tbody>
<tr>
<th>
<p>Problem</p>
</th>
<th>
<p>Solution</p>
</th>
</tr>
<tr>
<td>
<p>The <span class="ui">Login</span> dialog box reports &quot;Unable to authenticate your credentials.&quot;</p>
</td>
<td>
<p>Make sure that your user name is in the format: &lt;<em>username</em>&gt;@&lt;<em>domain</em>&gt; and that your password is correct.</p>
</td>
</tr>
<tr>
<td>
<p>Windows PowerShell or the application reports &quot;The term 'Connect-MsolService' is not recognized as the name of a cmdlet, function, script file, or operable program&hellip;.&quot;</p>
</td>
<td>
<p>Your user account doesn't have permission to run Windows PowerShell, or you have not installed the Microsoft Online Services Module for Windows PowerShell, or the execution policy is not set to
<strong>RemoteSigned</strong> as described in the &quot;Prerequisites&quot; section.</p>
</td>
</tr>
<tr>
<td>
<p>Windows PowerShell or the application reports &quot;Failed to connect to Active Directory Federation service 2.0 on the local machine. Please try running Set-MsolADFSContext before running this command again.&quot;</p>
</td>
<td>
<p>This error means that you have not installed and configured Active Directory Federation Services (AD FS) 2.0 to create a Federated Domain on your local machine. So install and configure AD FS 2.0 on your machine.</p>
</td>
</tr>
</tbody>
</table>
</div>
</div>
<h1 class="heading">Change log</h1>
<div class="section" id="sectionSection6">
<div class="caption"></div>
<div class="tableSection">
<table cellspacing="2" cellpadding="5" width="50%" frame="lhs">
<tbody>
<tr>
<th>
<p>Version</p>
</th>
<th>
<p>Date</p>
</th>
</tr>
<tr>
<td>
<p>First version</p>
</td>
<td>
<p>February 28, 2013</p>
</td>
</tr>
</tbody>
</table>
</div>
</div>
<h1 class="heading">Related content</h1>
<div class="section" id="sectionSection7">
<p><a href="http://msdn.microsoft.com/en-us/library/dd835506(v=vs.85).aspx" target="_blank">Windows PowerShell on MSDN</a></p>
<p><a href="http://onlinehelp.microsoft.com/en-us/office365-enterprises/hh125002.aspx" target="_blank">Windows PowerShell cmdlets for Office 365</a></p>
</div>
</div>
</div>
</div>
