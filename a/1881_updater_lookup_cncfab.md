<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link rel="stylesheet" type="text/css" href="bc.css">
<script src="https://cdn.rawgit.com/google/code-prettify/master/loader/run_prettify.js" type="text/javascript"></script>
</head>

<!---

- simple updater example added to The Building Coder samples
  https://forums.autodesk.com/t5/revit-api-forum/iupdater-simple-example-needed/m-p/9893248

- CncFab updated and in use

- RevitLookup update and how to submit a pull request
  https://github.com/RevitArkitek
  #65 &ndash; Unhandled exception on View.GetTemplateParameterIds 
  https://github.com/jeremytammik/RevitLookup/issues/65
  #66 &ndash; Adds handlers for GetTemplateParameterIds and GetNonControlledTemplateParameterIds
  https://github.com/jeremytammik/RevitLookup/pull/66
  integrated pull request #66 by @RevitArkitek adding handlers for `View` methods `GetTemplateParameterIds` and `GetNonControlledTemplateParameterIds`
  https://github.com/jeremytammik/RevitLookup/releases/tag/2021.0.0.8

twitter:

A nice new minimal simple dynamic model updater DMU example, ExportCncFab SortMark enhancement and handling RevitLookup exception on view GetTemplateParameterIds with the #RevitAPI @AutodeskForge @AutodeskRevit #bim #DynamoBim #ForgeDevCon https://autode.sk/dmucncfab

A nice new minimal DMU example and updates and enhancements to several other important sample applications
&ndash; Simple dynamic model updater example
&ndash; ExportCncFab <code>SortMark</code> update
&ndash; RevitLookup exception on view <code>GetTemplateParameterIds</code>...

linkedin:

A nice new minimal simple dynamic model updater DMU example, ExportCncFab SortMark enhancement and handling RevitLookup exception on view GetTemplateParameterIds with the #RevitAPI

https://autode.sk/dmucncfab

- Simple dynamic model updater example
- ExportCncFab <code>SortMark</code> update
- RevitLookup exception on view <code>GetTemplateParameterIds</code>...

#bim #DynamoBim #ForgeDevCon #Revit #API #IFC #SDK #AI #VisualStudio #Autodesk #AEC #adsk 

the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread

<center>
<img src="img/" alt="" title="" width="600"/>
<p style="font-size: 80%; font-style:italic"></p>
<p style="font-size: 80%; font-style:italic">
<a href=""></a>
</p>
</center>

-->

### Simple IUpdater and other TBC Updates

A nice new minimal DMU example, updates and enhancements to other important sample applications:

- [Simple dynamic model updater example](#2)
- [ExportCncFab `SortMark` update](#3)
- [RevitLookup exception on view `GetTemplateParameterIds`](#4)

####<a name="2"></a> Simple Dynamic Model Updater Example

Alan Clarke shared a nice new simple Dynamic Model Updater or DMU sample in
the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread
on [`IUpdater`, simple example needed](https://forums.autodesk.com/t5/revit-api-forum/iupdater-simple-example-needed/m-p/9893248),
saying:

> Hi Jeremy, I just want to share my solution, with help from a friend.
I hope this is simple enough of an example and helpful for others.
This is an `IExternalCommand` example.

I like it and integrated it
into [The Building Coder samples](https://github.com/jeremytammik/the_building_coder_samples)
[release 2021.0.150.10](https://github.com/jeremytammik/the_building_coder_samples/releases/tag/2021.0.150.10).

Here is the [diff to the previous release](https://github.com/jeremytammik/the_building_coder_samples/compare/2021.0.150.9...2021.0.150.10).

In doing so, I noticed they already did include another nice DMU sample in the module `CmdElevationWatcher` that reacts to elevation view creation.
It compares the use of DMU versus the `DocumentChanged` event to track that happening, discussed in the article
on [`DocumentChanged` versus Dynamic Model Updater](https://thebuildingcoder.typepad.com/blog/2012/06/documentchanged-versus-dynamic-model-updater.html).

Here is my slightly modified version of your code:

<pre class="code">
[<span style="color:#2b91af;">Transaction</span>(&nbsp;<span style="color:#2b91af;">TransactionMode</span>.Manual&nbsp;)]
<span style="color:blue;">class</span>&nbsp;<span style="color:#2b91af;">CmdSimpleUpdaterExample</span>&nbsp;:&nbsp;<span style="color:#2b91af;">IExternalCommand</span>
{
&nbsp;&nbsp;<span style="color:blue;">class</span>&nbsp;<span style="color:#2b91af;">SimpleUpdater</span>&nbsp;:&nbsp;<span style="color:#2b91af;">IUpdater</span>
&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">const</span>&nbsp;<span style="color:blue;">string</span>&nbsp;Id&nbsp;=&nbsp;<span style="color:#a31515;">&quot;d42d28af-d2cd-4f07-8873-e7cfb61903d8&quot;</span>;
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UpdaterId</span>&nbsp;_updater_id&nbsp;{&nbsp;<span style="color:blue;">get</span>;&nbsp;<span style="color:blue;">set</span>;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;SimpleUpdater(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">Document</span>&nbsp;doc,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">AddInId</span>&nbsp;addInId&nbsp;)
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_updater_id&nbsp;=&nbsp;<span style="color:blue;">new</span>&nbsp;<span style="color:#2b91af;">UpdaterId</span>(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;addInId,&nbsp;<span style="color:blue;">new</span>&nbsp;<span style="color:#2b91af;">Guid</span>(&nbsp;Id&nbsp;)&nbsp;);
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;RegisterUpdater(&nbsp;doc&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;RegisterTriggers();
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:blue;">void</span>&nbsp;RegisterUpdater(&nbsp;<span style="color:#2b91af;">Document</span>&nbsp;doc&nbsp;)
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">if</span>(&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.IsUpdaterRegistered(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_updater_id,&nbsp;doc&nbsp;)&nbsp;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.RemoveAllTriggers(&nbsp;_updater_id&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.UnregisterUpdater(&nbsp;_updater_id,&nbsp;doc&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.RegisterUpdater(&nbsp;<span style="color:blue;">this</span>,&nbsp;doc&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:blue;">void</span>&nbsp;RegisterTriggers()
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">if</span>(&nbsp;<span style="color:blue;">null</span>&nbsp;!=&nbsp;_updater_id&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&amp;&amp;&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.IsUpdaterRegistered(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_updater_id&nbsp;)&nbsp;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.RemoveAllTriggers(&nbsp;_updater_id&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UpdaterRegistry</span>.AddTrigger(&nbsp;_updater_id,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">new</span>&nbsp;<span style="color:#2b91af;">ElementCategoryFilter</span>(&nbsp;<span style="color:#2b91af;">BuiltInCategory</span>.OST_Walls&nbsp;),&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">Element</span>.GetChangeTypeAny()&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:blue;">void</span>&nbsp;Execute(&nbsp;<span style="color:#2b91af;">UpdaterData</span>&nbsp;data&nbsp;)
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">Document</span>&nbsp;doc&nbsp;=&nbsp;data.GetDocument();
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">ICollection</span>&lt;<span style="color:#2b91af;">ElementId</span>&gt;&nbsp;ids&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;=&nbsp;data.GetModifiedElementIds();
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">IEnumerable</span>&lt;<span style="color:blue;">string</span>&gt;&nbsp;names&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;=&nbsp;ids.Select&lt;<span style="color:#2b91af;">ElementId</span>,&nbsp;<span style="color:blue;">string</span>&gt;(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id&nbsp;=&gt;&nbsp;doc.GetElement(&nbsp;id&nbsp;).Name&nbsp;);
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">TaskDialog</span>.Show(&nbsp;<span style="color:#a31515;">&quot;Simple&nbsp;Updater&quot;</span>,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">string</span>.Join&lt;<span style="color:blue;">string</span>&gt;(&nbsp;<span style="color:#a31515;">&quot;,&quot;</span>,&nbsp;names&nbsp;)&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:blue;">string</span>&nbsp;GetAdditionalInformation()
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">return</span>&nbsp;<span style="color:#a31515;">&quot;NA&quot;</span>;
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:#2b91af;">ChangePriority</span>&nbsp;GetChangePriority()
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">return</span>&nbsp;<span style="color:#2b91af;">ChangePriority</span>.MEPFixtures;
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:#2b91af;">UpdaterId</span>&nbsp;GetUpdaterId()
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">return</span>&nbsp;_updater_id;
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:blue;">string</span>&nbsp;GetUpdaterName()
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">return</span>&nbsp;<span style="color:#a31515;">&quot;SimpleUpdater&quot;</span>;
&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;}
 
&nbsp;&nbsp;<span style="color:blue;">public</span>&nbsp;<span style="color:#2b91af;">Result</span>&nbsp;Execute(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">ExternalCommandData</span>&nbsp;commandData,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">ref</span>&nbsp;<span style="color:blue;">string</span>&nbsp;message,
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">ElementSet</span>&nbsp;elements&nbsp;)
&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">UIApplication</span>&nbsp;uiapp&nbsp;=&nbsp;commandData.Application;
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">Document</span>&nbsp;doc&nbsp;=&nbsp;uiapp.ActiveUIDocument.Document;
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">AddInId</span>&nbsp;addInId&nbsp;=&nbsp;uiapp.ActiveAddInId;
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#2b91af;">SimpleUpdater</span>&nbsp;su&nbsp;=&nbsp;<span style="color:blue;">new</span>&nbsp;<span style="color:#2b91af;">SimpleUpdater</span>(&nbsp;doc,&nbsp;addInId&nbsp;);
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">return</span>&nbsp;<span style="color:#2b91af;">Result</span>.Succeeded;
&nbsp;&nbsp;}
}
</pre>

Many thanks to Alan for putting together and sharing this.

####<a name="3"></a> ExportCncFab SortMark Update

Another nice sample was also enhanced, prompted
by [SteelcoreSystems](https://github.com/SteelcoreSystems)'
[issue #1 &ndash; Add Instance Shared Parameter Value in Exported Filename](https://github.com/jeremytammik/ExportCncFab/issues/1) on
the ExportCncFab add-in to export Revit wall parts to DXF or SAT for CNC fabrication:

> I would like to know how to add an additional shared parameter instance value to the exported SAT/DXF filenames. The current SAT/DXF filename method only exports the "host level name_parentId_partId"

> Only exporting the Revit element id makes it difficult and time consuming to determine what part was exported after exporting many elements. I have added an instance shared parameter to my Revit models and assigned it to parts. The goal is to have this instance shared parameter value included within each exported filename.

> When exporting, I get the following default file name:
    <pre class="code">
      [Level Name]_136667_136683.sat
    </pre>

> I would like for the file name to be exported with the "SortMark" instance value:
    <pre class="code">
      [Level Name]_[SortMark]_136667_136683.sat
      Level 0_3SB-10_13667_136683.sat
    </pre>

> Here is an image of the modified code:

<center>
<img src="img/cncfab_sortmark.png" alt="ExportCncFab SortMark" title="ExportCncFab SortMark" width="400"/> <!-- 604 -->
</center>

Before buckling down to this, I migrated ExportCncFab from Revit 2019 to Revit 2020 and Revit 2021.
That was trivial.

Then I implemented the required enhancement that you can see in
the [diff for adding the sort mark](https://github.com/jeremytammik/ExportCncFab/compare/2021.0.0.0...2021.0.0.1).

**Response:** Great Work! I made the adjustments and on the first try everything exported perfectly.
I greatly appreciate you making it easy to assign any parameter name for value exporting.

Under the ExportCncFab/ExportParameters.cs file at line 32, I was able to change
const string `_sort_mark` = `"CncFabSortMark"` to my desired parameter.

Also, I have been able to customize the code for exporting floor parts, wall parts, and structural steel framing elements.
So far, it has worked perfectly with every `OST` family I have tested.
It is a great app!

Many thanks to SteelcoreSystems for raising this issue and your nice appreciation.

####<a name="4"></a> RevitLookup Exception on View GetTemplateParameterIds

We also updated RevitLookup to handle
the [issue #65 &ndash; Unhandled exception on View.GetTemplateParameterIds](https://github.com/jeremytammik/RevitLookup/issues/65) raised
by [RevitArkitek](https://github.com/RevitArkitek).

I suggested submitting a pull request for this functionality, which involved talking them through the basic steps required for this fundamental GitHub collaboration operation: fork, clone, modify, commit, pull.

**Question:** In a view (whether it's a view template or not), I click on `GetTemplateParameterIds`, a `NullReferenceException` is thrown.

**Answer:** Thank you for pointing it out.
Are you a programmer?
Do you have Visual Studio or something similar installed?
Can you run RevitLookup and Revit.exe in the debugger and see where this happens?
In that case, can you please wrap the offending line of code in a try/catch handler to handle the exception?
And submit a pull request with the fixed code?
That would be great!
Thank you!

Later: I searched the RevitLookup source code globally to try to understand how this can occur.
I searched, found and analysed all occurrences of SnoopableObjectWrapper and GetUnderlyingType, and they all make perfect sense and look perfectly all right to me.
GetTemplateParameterIds is a member on the View class.
It is called dynamically, and I cannot tell from your report how to trigger such a call.
Therefore, it would be helpful if you could do so.
The problem is probably trivial to fix and faster done than writing this long message.
Looking forward to your pull request!
Thank you!

**Response:** When I debugged, Object in public Type GetUnderlyingType() => Object.GetType(); was null.
I changed to public Type GetUnderlyingType() => Object?.GetType();
Then, in the Objects.AddObjectsToTree I had to handle the null being returned.
After that, it would open the next dialog.

**Answer:** Thank you! That helps narrow it down tremendously.
Could you share the handling code in `AddObjectsToTree`, or submit a pull request for the changes?
Have you made any other modifications and improvements? Cheers!

**Response:** I'm going to do a little testing, and then try to do a Pull request.
I've never done that before. Thanks!

Later: I figured out that the main issue was further up the code and had to add a couple of handlers for these objects.
Unfortunately, it won't let me push my commit.
GitHub desktop doesn't recognize my username/password.
Not sure how to proceed.

**Answer:** Wow, that sounds very good!
Looking forward very much to see your approach.
Yes, that is completely normal.
You cannot commit straight to my repository, since you might wreck the project for me.
That is obvious and expected.
The solution is easy: (i) fork my repository to your own copy of it. (ii) clone your repository, make changes, and commit as you please. (iii) in your forked directory, submit a pull request. that enables me to see the changes you made and merge them back into my main original source repo.
It all makes total sense and is utterly powerful and convenient.
You have learned something useful.
Search for something like [github fork commit pull merge](https://duckduckgo.com/?q=github+fork+commit+pull+merge).
That gives many hits.
One is [How to Fork Github Repository, Create Pull Request and Merge?](https://crunchify.com/how-to-fork-github-repository-create-pull-request-and-merge)

That interaction promptly resulted
in [pull request #66 &ndash; Adds handlers for GetTemplateParameterIds and GetNonControlledTemplateParameterIds](https://github.com/jeremytammik/RevitLookup/pull/66) that
I integrated into [RevitLookup release 2021.0.0.8](https://github.com/jeremytammik/RevitLookup/releases/tag/2021.0.0.8).

Since then, I created another [release 2021.0.0.9](https://github.com/jeremytammik/RevitLookup/releases/tag/2021.0.0.9) to
locally disable warning CS0618, `DisplayUnitType` is obsolete, for one specific use case.

Very many thanks to RevitArkitek for their valuable contribution!
