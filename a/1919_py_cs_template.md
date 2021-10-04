<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link rel="stylesheet" type="text/css" href="bc.css">
<script src="https://cdn.rawgit.com/google/code-prettify/master/loader/run_prettify.js" type="text/javascript"></script>
</head>

<!---

- https://github.com/jeremytammik/RevitLookup/pull/91
  https://github.com/jeremytammik/RevitLookup/releases/tag/2022.0.0.16
  integrated pull request #91 by @mphelt to add PartUtilsStream
  https://github.com/mphelt
  Adds PartUtilsStream that populates highlighted entries:
  a/img/revitlookup_PartUtilsStream.png
  Duplicated OriginalCategoryId shows value as f.e. OST_Walls instead of < null >.
  Duplicated GetSourceElementIds shows a 'flattened' list of elements instead of original list of LinkElementIds.
  Duplicated GetSourceElementOriginalCategoryIds uses EnumerableAsString to show value as f.e. 'OST_Walls, OST_Walls'.

- C# templates for Revit
  Роман Карпович <nice3point@gmail.com>
  Hi Jeremy, I made some really cool templates for creating revit plugins. With a build system, creating installers and bundles for the Autodesk Store. Ready-made files for AzureDevOps, GitHubActions have been written. A minimum of steps for starting and routine work, all GUIDs are generated by themselves when creating a project. Added the ability to merge several DLLs into one, just specify the names of the merged files. For Debug configurations, all files are copied to the addons folder by themselves. It is also possible to add unique configurations, for example, a configuration for AdskStore, where you can check whether a plugin is purchased or not, in the second case, display an informational message and redirect to a page in the store. You can test them here https://github.com/Nice3point/RevitTemplates and share them on your blog. Video with an example in the attached files.
  FirstSteps.mp4 -- https://drive.google.com/file/d/1Pm0tygJNRcXP_8O8XCsk2C5Jt3FQFCym/view
  StoreVersion.mp4 -- https://drive.google.com/file/d/1bPveyMoGi0U9MVTT0UxWVPK7gXb2amJu/view
  https://github.com/Nice3point/RevitTemplates

- C# and IronPython Hosting for Revit addins
  https://forums.autodesk.com/t5/revit-api-forum/c-and-ironpython-hosting-for-revit-addins/m-p/10629723
  
- CPython and Python 3
  PyRevit and Revit 2022 w/ Dynamo
  https://forums.autodesk.com/t5/revit-api-forum/pyrevit-and-revit-2022-w-dynamo/m-p/10638367

twitter:

add #thebuildingcoder

A neat RevitLookup enhancement for snooping PartUtils, a couple of Python related topics and a powerful new Revit add-in template for the #RevitAPI #DynamoBim @AutodeskForge @AutodeskRevit #bim #ForgeDevCon https://autode.sk/snoopparts

A neat RevitLookup enhancement, powerful new Revit add-in template, and a couple of Python related topics
&ndash; RevitLookup handles <code>PartUtils</code>
&ndash; Nice3point Revit add-in C&#35; template
&ndash; IronPython hosting in C&#35; add-in
&ndash; Python 3, CPython, pyRevit and Dynamo...

linkedin:

A neat RevitLookup enhancement for snooping PartUtils, a couple of Python related topics and a powerful new Revit add-in template for the #RevitAPI

https://autode.sk/snoopparts

- RevitLookup handles PartUtils
- Nice3point Revit add-in C# template
- IronPython hosting in C# add-in
- Python 3, CPython, pyRevit and Dynamo...

#bim #DynamoBim #ForgeDevCon #Revit #API #IFC #SDK #AI #VisualStudio #Autodesk #AEC #adsk

the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread

<center>
<img src="img/" alt="" title="" width="600"/>
<p style="font-size: 80%; font-style:italic"></p>
</center>

**Question:** 

**Answer:**

**Response:**  

Many thanks to  for this very helpful explanation!

<pre class="code">
</pre>

-->

### Snooping Parts, C&#35; Templates and Python Topics

A neat RevitLookup enhancement, powerful new Revit add-in template, and a couple of Python related topics:

- [RevitLookup handles `PartUtils`](#2)
- [Nice3point Revit add-in C&#35; template](#3)
- [IronPython hosting in C&#35; add-in](#4)
- [Python 3, CPython, pyRevit and Dynamo](#5)

####<a name="2"></a> RevitLookup Handles PartUtils

RevitLookup now displays `PartUtils` information.

[mphelt](https://github.com/mphelt) submitted
[pull request #91 to add `PartUtilsStream`](https://github.com/jeremytammik/RevitLookup/pull/91),
integrated in [RevitLookup release 2022.0.0.16](https://github.com/jeremytammik/RevitLookup/releases/tag/2022.0.0.16).

The new `PartUtils` stream also populates the following highlighted entries:

<center>
<img src="img/revitlookup_PartUtilsStream.png" alt="Snoop PartUtils" title="Snoop PartUtils" width="354"/> <!-- 354 -->
</center>

- Duplicated `OriginalCategoryId` shows value as f.e. `OST_Walls` instead of <code>&lt;null&gt;</code>
- Duplicated `GetSourceElementIds` shows a flattened list of elements instead of original list of `LinkElementIds`
- Duplicated `GetSourceElementOriginalCategoryIds` uses `EnumerableAsString` to show value as f.e. 'OST_Walls, OST_Walls'

Many thanks to [mphelt](https://github.com/mphelt) for this important enhancement!


####<a name="3"></a> Nice3point Revit Add-In C&#35; Template 

We mentioned several alternatives to
my very simple [Visual Studio Revit add-in wizard](https://github.com/jeremytammik/VisualStudioRevitAddinWizard) in
the past.

I just added a list of them to the GitHub repo readme and
the corresponding [topic group](https://thebuildingcoder.typepad.com/blog/about-the-author.html#5.20).

Roman Karpov, aka Роман Карпович, now shares another one, saying:

> I made some really cool templates for creating Revit plugins.
They include a build system, creating installers, creating bundles for the Autodesk AppStore, ready-made files for AzureDevOps, and GitHubActions.
They require a minimum of steps for starting and routine work.
All GUIDs are automatically generated when creating a project.
Added the ability to merge several DLLs into one; just specify the names of the merged files.
For Debug configurations, all files are copied to the add-ins folder by themselves.
It is also possible to add unique configurations; for example, a configuration for AdskStore, where you can check whether a plugin has been purchased or not; if not, display an informational message and redirect to a page in the store.

> You can test them at [Nice3point/RevitTemplates](https://github.com/Nice3point/RevitTemplates).

> Check out the example videos:

- [FirstSteps.mp4](https://drive.google.com/file/d/1Pm0tygJNRcXP_8O8XCsk2C5Jt3FQFCym/view)
- [StoreVersion.mp4](https://drive.google.com/file/d/1bPveyMoGi0U9MVTT0UxWVPK7gXb2amJu/view)
- [Nice3point/RevitTemplates](https://github.com/Nice3point/RevitTemplates)

Thank you very much for sharing these, Роман!


####<a name="4"></a> IronPython Hosting in C&#35; Add-In

Daniel Gerčák shares a solution implementing his
own [IronPython](https://ironpython.net) hosting in a Revit add-in in
the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread
on [C&#35; and IronPython hosting for Revit addins](https://forums.autodesk.com/t5/revit-api-forum/c-and-ironpython-hosting-for-revit-addins/m-p/10629723):


**Question:** I try to run IronPython scripts via IronPython.Hosting in C#, inspired by Nick Cosentino's
article [Python, Visual Studio, and C&#35;, so sweet](https://www.codeproject.com/Articles/657698/Python-Visual-Studio-and-Csharp-So-Sweet).

The purpose of such effort is to create easy distributable and accessible addins in our company which are developed by a small group of non IT experts on the IronPython platform due to its flexibility and lower demandings for coding skills.
Yes, I've heard about RevitPythonShell, but this is not exactly what would make sufficient result.

I was able to run classes using references to `RevitAPI` and `RevitAPIUI` but receive empty objects trying to use `RevitServices`:

<pre class="prettyprint">
from RevitServices.Persistence import DocumentManager
doc = DocumentManager.Instance.CurrentDBDocument
uiapp = DocumentManager.Instance.CurrentUIApplication
uidoc = DocumentManager.Instance.CurrentUIApplication.ActiveUIDocument
</pre>

I wonder if my intention to run such scripts is useless effort due to some restrictions in source code or is there some way to deal with this issue.

Here is a piece of code for better overview of what I am trying to achieve,
[totalSelectedVolume.zip](zip/dg_totalSelectedVolume.zip),
containing totalSelectedVolumeCommand.cs and totalSelectedVolume.py.
The former implements an external command and executes the latter via the `IronPython.Hosting` `ExecuteFile` method, performing the actual computation.

**Answer:** You can take a look at the open source implementations
of [RevitPythonShell](https://github.com/architecture-building-systems/revitpythonshell)
and [pyRevit](https://github.com/eirannejad/pyRevit) to
discover how they have addressed this same issue.

**Response:** I did a little research and I was successful.

The point was to create a new variable within the IronPython engine and assign the `commandData.Application` object to it so that you can access it from the Python environment.
I named it the same way as it is in RPS, `__revit__`, in order to keep compatibility with scripts developed for RPS.
Since I've tested it only by using simple Python code, I don't guarantee its functionality with more complex scripts.
Additional settings might be required.

The execute function looks like this.

<pre class="code">
&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;Result&nbsp;Execute(
&nbsp;&nbsp;&nbsp;&nbsp;ExternalCommandData&nbsp;commandData,
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">ref</span>&nbsp;<span style="color:blue;">string</span>&nbsp;message,
&nbsp;&nbsp;&nbsp;&nbsp;ElementSet&nbsp;elements&nbsp;)
&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;UIApplication&nbsp;_revit&nbsp;=&nbsp;commandData.Application;
&nbsp;&nbsp;&nbsp;&nbsp;UIDocument&nbsp;uidoc&nbsp;=&nbsp;_revit.ActiveUIDocument;
&nbsp;&nbsp;&nbsp;&nbsp;Document&nbsp;doc&nbsp;=&nbsp;uidoc.Document;
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">var</span>&nbsp;flags&nbsp;=&nbsp;<span style="color:blue;">new</span>&nbsp;Dictionary&lt;<span style="color:blue;">string</span>,&nbsp;<span style="color:blue;">object</span>&gt;()&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;<span style="color:#a31515;">&quot;Frames&quot;</span>,&nbsp;<span style="color:blue;">true</span>&nbsp;},
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;<span style="color:#a31515;">&quot;FullFrames&quot;</span>,&nbsp;<span style="color:blue;">true</span>&nbsp;}&nbsp;};
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">var</span>&nbsp;py&nbsp;=&nbsp;IronPython.Hosting.Python.CreateEngine(&nbsp;flags&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">var</span>&nbsp;scope&nbsp;=&nbsp;IronPython.Hosting.Python.CreateModule(&nbsp;py,&nbsp;<span style="color:#a31515;">&quot;__main__&quot;</span>&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;scope.SetVariable(&nbsp;<span style="color:#a31515;">&quot;__commandData__&quot;</span>,&nbsp;commandData&nbsp;);
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:green;">//&nbsp;add&nbsp;special&nbsp;variable:&nbsp;__revit__&nbsp;to&nbsp;be&nbsp;globally&nbsp;visible&nbsp;everywhere:</span>
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">var</span>&nbsp;builtin&nbsp;=&nbsp;IronPython.Hosting.Python.GetBuiltinModule(&nbsp;py&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;builtin.SetVariable(&nbsp;<span style="color:#a31515;">&quot;__revit__&quot;</span>,&nbsp;_revit&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;py.Runtime.LoadAssembly(&nbsp;<span style="color:blue;">typeof</span>(&nbsp;Autodesk.Revit.DB.Document&nbsp;).Assembly&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;py.Runtime.LoadAssembly(&nbsp;<span style="color:blue;">typeof</span>(&nbsp;Autodesk.Revit.UI.TaskDialog&nbsp;).Assembly&nbsp;);
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">try</span>
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;py.ExecuteFile(&nbsp;<span style="color:#a31515;">&quot;totalSelectedVolume.py&quot;</span>&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">catch</span>(&nbsp;Exception&nbsp;ex&nbsp;)
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TaskDialog&nbsp;myDialog&nbsp;=&nbsp;<span style="color:blue;">new</span>&nbsp;TaskDialog(&nbsp;<span style="color:#a31515;">&quot;IronPython&nbsp;Error&quot;</span>&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;myDialog.MainInstruction&nbsp;=&nbsp;<span style="color:#a31515;">&quot;Couldn&#39;t&nbsp;execute&nbsp;IronPython&nbsp;script&nbsp;totalSelectedVolume.py:&nbsp;&quot;</span>;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;myDialog.ExpandedContent&nbsp;=&nbsp;ex.Message;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;myDialog.Show();
&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">return</span>&nbsp;Result.Succeeded;
&nbsp;&nbsp;}
</pre>

Here is [IronPython_engine.zip](zip/dg_IronPython_engine.zip) containing a complete testing project.

Many thanks to Daniel for his research and useful solution!

####<a name="5"></a> Python 3, CPython, pyRevit and Dynamo

Continuing with Python related issues, here is a quick update on upcoming releases of pyRevit and Dynamo and their support for Python 3, prompted by 
EatRevitPoopCad (love the handle) in their discussion
of [PyRevit and Revit 2022 w/ Dynamo](https://forums.autodesk.com/t5/revit-api-forum/pyrevit-and-revit-2022-w-dynamo/m-p/10638367):

**Question:** I believe I saw somewhere that IronPython will not be supported with Revit 2022 and/or the Dynamo version it will come with...
Some of my plugins use IronPython, which isn't a big deal, I can convert them to whatever the "New python" Dynamo will use...
But what about... let's say PyRevit?
I know it runs on IronPython.
Does that mean it will not work?
Or can you still install an older version of Dynamo in Revit 2022 that will support IronPython?

**Answer:** The Revit API is based on .NET.
Therefore, everything and anything that supports .NET can be used to work with the Revit API.
IronPython is designed to enable usage of Python with .NET.
I see no reason why it should stop working.
What gave you that idea?

That said, you might also try to discuss pyRevit related issues directly with its creator Ehsan in
the [pyRevit repository](https://github.com/eirannejad/pyRevit) via
the appropriate [channels](https://github.com/eirannejad/pyRevit#staying-updated).

**Response:** Thanks for clearing that up, Jeremy.

I saw this on a webinar and misunderstood it, and only used IronPython inside Dynamo.
Basically, the new Dynamo is transitioning
from [IronPython](https://ironpython.net)
to [CPython](https://github.com/python/cpython).
Revit 2021 came with Dynamo and IronPython by default.
Revit 2022 comes with Dynamo that has IronPython and CPython, and recommends using CPython.
I am assuming in the future it will drop IronPython.

This won't affect pyRevit the way I thought it would; Dynamo and pyRevit are independent of each other.

Please refer to the article
on the [top 5 new features for Dynamo for Revit 2022](https://www.caddmicrosystems.com/blog/top-5-new-features-for-dynamo-for-revit-2022):
 
> One of the biggest things the Dynamo Core team has been working on is the transition from IronPython which limits Python to version to 2.7 to CPython which allows the use of python 3 syntax. This is HUGE for using python to access addition elements in the Revit API, as well as to handle more complex logic scenarios. As of the initial launch of Revit 2022, both ironpython and Cpython are installed as python engines and the engine used can vary within a single dynamo script (although that is not advised).
IronPython remains the default Python engine, but can be changed in the settings.
To help with the transition, there is a transition tool that will help migrate your python script from ironpython to Cpython.

Many thanks to EatRevitPoopCad for the interesting background information.
I was unaware of it until now.
Myself, I just use (normal, standalone) Python for command line scripts and am still in a very slow and much overdue transitioning process from 2.7 to 3+...