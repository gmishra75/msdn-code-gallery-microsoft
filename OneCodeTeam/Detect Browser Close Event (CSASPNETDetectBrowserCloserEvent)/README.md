# Detect Browser Close Event (CSASPNETDetectBrowserCloserEvent)
## Requires
- Visual Studio 2010
## License
- MS-LPL
## Technologies
- ASP.NET
## Topics
- Webpage
## Updated
- 07/22/2012
## Description
===========================================================================<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;CSASPNETDetectBrowserCloserEvent Project Overview<br>
===========================================================================<br>
<br>
Summary:<br>
<br>
As we know, HTTP is a stateless protocol, the browser doesn't keep connecting<br>
to the server. When user try to close the browser using alt-f4, browser close(X) <br>
and right click on browser and close -&gt; this all is done and is working fine,<br>
it's not possible to tell the server that the browser is closed. The sample<br>
demonstrates how to detect the browser close event with iframe.<br>
<br>
/////////////////////////////////////////////////////////////////////////////<br>
Demo the Sample.<br>
<br>
Step1: Browse the Default.aspx page from the sample. It will display the current<br>
online clientlist.<br>
<br>
Step2: Browse the Default.aspx page again<br>
[Note]<br>
If use IE, you should click File -&gt; New Session, and then copy the address to the new
<br>
window's address bar.It is best to browse the page on another computer or other browser.<br>
[/Note]<br>
You will see two records on the page. The other page will auto-refresh after <br>
several seconds, and it will also show two records.<br>
<br>
Step3: Please close one of the page. After several seconds, you will see there is<br>
only one record on the page.<br>
<br>
/////////////////////////////////////////////////////////////////////////////<br>
Code Logical:<br>
<br>
Step1: Create a C# ASP.NET Empty Web Application in Visual Studio 2010.<br>
<br>
Step2: Add a C# class file which named 'ClientInfo' in Visual Studio 2010.<br>
You can find the complete code in ClientInfo.cs file.<br>
<br>
Step3: Add a Global Application class file which named 'Global' in Visual <br>
Studio 2010.You can find the complete code in Global.asax file. It is used<br>
to detect the browser whether closed, and will auto delete off-line client.<br>
<br>
Step4: Open the C# behind code view to write timer_Elapsed event.<br>
You can find the complete version in the Global.asax.cs file.<br>
[code]<br>
protected void timer_Elapsed(object sender, ElapsedEventArgs e)<br>
{<br>
&nbsp; &nbsp;ClientInfo client = new ClientInfo();<br>
&nbsp; &nbsp;List&lt;ClientInfo&gt; clientList = (List&lt;ClientInfo&gt;)Application[&quot;ClientInfo&quot;];<br>
<br>
&nbsp; &nbsp;for (int i = 0; i &lt; clientList.Count; i&#43;&#43;)<br>
&nbsp; &nbsp;{<br>
&nbsp; &nbsp; &nbsp; &nbsp;if (clientList[i].RefreshTime &lt; DateTime.Now.AddSeconds(0 - 5)<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;|| clientList[i].ActiveTime &lt; DateTime.Now.AddMinutes(0 - 20))<br>
&nbsp; &nbsp; &nbsp; &nbsp;{<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;client = ClientInfo.GetClinetInfoByClientID(clientList, clientList[i].ClientID);<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;clientList.Remove(client);<br>
&nbsp; &nbsp; &nbsp; &nbsp;}<br>
&nbsp; &nbsp;}<br>
<br>
&nbsp; &nbsp;Application[&quot;ClientInfo&quot;] = clientList;<br>
}<br>
[/code]<br>
<br>
Step5: Add a Default ASP.NET page into the Web Application as the page<br>
which used to display the online client.<br>
<br>
Step6: Add a ScriptManager, a UpdatePanel, a Timer and a iframe into the <br>
page as the .aspx code below.<br>
[code]<br>
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;<br>
&lt;head runat=&quot;server&quot;&gt;<br>
&nbsp; &nbsp;&lt;title&gt;&lt;/title&gt;<br>
&lt;/head&gt;<br>
&lt;body&gt;<br>
&nbsp; &nbsp;&lt;form id=&quot;form1&quot; runat=&quot;server&quot;&gt;<br>
&nbsp; &nbsp;
<div><br>
&nbsp; &nbsp; &nbsp; &nbsp;&lt;asp:ScriptManager ID=&quot;ScriptManager1&quot; runat=&quot;server&quot;&gt;<br>
&nbsp; &nbsp; &nbsp; &nbsp;&lt;/asp:ScriptManager&gt;<br>
&nbsp; &nbsp; &nbsp; &nbsp;&lt;asp:UpdatePanel ID=&quot;UpdatePanel1&quot; runat=&quot;server&quot;&gt;<br>
&nbsp; &nbsp; &nbsp; &nbsp;&lt;/asp:UpdatePanel&gt;<br>
&nbsp; &nbsp; &nbsp; &nbsp;&lt;asp:Timer ID=&quot;Timer1&quot; runat=&quot;server&quot; Interval=&quot;3000&quot;&gt;<br>
&nbsp; &nbsp; &nbsp; &nbsp;&lt;/asp:Timer&gt;<br>
&nbsp; &nbsp;</div>
<br>
&nbsp; &nbsp;&lt;/form&gt;<br>
&nbsp; &nbsp;&lt;iframe id=&quot;Detect&quot; src=&quot;DetectBrowserClosePage.aspx&quot; style=&quot;border-width: 0px; border-style:none;<br>
&nbsp; &nbsp; &nbsp; &nbsp;width: 0px; height: 0px; overflow: hidden&quot;&gt;&lt;/iframe&gt;<br>
&lt;/body&gt;<br>
&lt;/html&gt;<br>
[/code]<br>
<br>
Step7: Open the C# behind code view to write Page_Load function.<br>
You can find the complete version in the Default.aspx.cs file.<br>
[code]<br>
protected void Page_Load(object sender, EventArgs e)<br>
{<br>
&nbsp; &nbsp;ClientInfo client = new ClientInfo();<br>
&nbsp; &nbsp;List&lt;ClientInfo&gt; clientList = (List&lt;ClientInfo&gt;)Application[&quot;ClientInfo&quot;];<br>
<br>
&nbsp; &nbsp;client = ClientInfo.GetClinetInfoByClientID(clientList, this.Session.SessionID);<br>
&nbsp; &nbsp;client.ActiveTime = DateTime.Now;<br>
<br>
&nbsp; &nbsp;for (int i = 0; i &lt; clientList.Count; i&#43;&#43;)<br>
&nbsp; &nbsp;{<br>
&nbsp; &nbsp; &nbsp; &nbsp;Response.Write(clientList[i].ClientID.ToString());<br>
&nbsp; &nbsp; &nbsp; &nbsp;Response.Write(&quot;<br>
&quot;);<br>
&nbsp; &nbsp;}<br>
}<br>
[/code]<br>
<br>
Step8: Add a DetectBrowserClosePage ASP.NET page into the Web Application as the page<br>
which as the iframe for Default.aspx.<br>
<br>
Step9: Set the page refresh per second as the .aspx code below.<br>
[code]<br>
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;<br>
&lt;head runat=&quot;server&quot;&gt;<br>
&nbsp; &nbsp;&lt;title&gt;&lt;/title&gt;<br>
&nbsp; &nbsp; &nbsp; &lt;meta http-equiv=&quot;refresh&quot; content=&quot;1&quot; /&gt;<br>
&lt;/head&gt;<br>
&lt;body&gt;<br>
&nbsp; &nbsp;&lt;form id=&quot;form1&quot; runat=&quot;server&quot;&gt;<br>
&nbsp; &nbsp;
<div><br>
&nbsp; &nbsp;</div>
<br>
&nbsp; &nbsp;&lt;/form&gt;<br>
&lt;/body&gt;<br>
&lt;/html&gt;<br>
[/code]<br>
<br>
Step10: Open the C# behind code view to write Page_Load function.<br>
You can find the complete version in the DetectBrowserClosePage.aspx.cs file.<br>
[code]<br>
protected void Page_Load(object sender, EventArgs e)<br>
{<br>
&nbsp; &nbsp;ClientInfo client = new ClientInfo();<br>
&nbsp; &nbsp;List&lt;ClientInfo&gt; clientList = (List&lt;ClientInfo&gt;)Application[&quot;ClientInfo&quot;];<br>
<br>
&nbsp; &nbsp;client = ClientInfo.GetClinetInfoByClientID(clientList, this.Session.SessionID);<br>
&nbsp; &nbsp;client.RefreshTime = DateTime.Now;<br>
}<br>
[/code]<br>
/////////////////////////////////////////////////////////////////////////////<br>
References:<br>
<br>
MSDN: <br>
# ASP.NET Session State<br>
http://msdn.microsoft.com/en-us/library/ms178581(VS.100).aspx<br>
/////////////////////////////////////////////////////////////////////////////<br>
