<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link rel="stylesheet" type="text/css" href="bc.css">
<script src="https://cdn.rawgit.com/google/code-prettify/master/loader/run_prettify.js" type="text/javascript"></script>
</head>

<!---

- Tag Width/Height or Accurate BoundingBox of IndependentTag
  https://forums.autodesk.com/t5/revit-api-forum/tag-width-height-or-accurate-boundingbox-of-independenttag/m-p/11274095

- not trivial to solve: tags without Overlapping
  https://forums.autodesk.com/t5/revit-api-forum/tags-without-overlapping/m-p/11275579

- Auto Tagging without overlap
  https://forums.autodesk.com/t5/revit-api-forum/auto-tagging-without-overlap/td-p/9996808
  
- Python and Dynamo Autotag Without Overlap
  https://thebuildingcoder.typepad.com/blog/2021/02/splits-persona-collector-region-tag-modification.html#5

- OS add-in:
  One click convert detail elements to Detail Family
  https://forums.autodesk.com/t5/revit-api-forum/one-click-convert-detail-elements-to-detail-family/td-p/11230155
  Peter [PitPaf](https://forums.autodesk.com/t5/user/viewprofilepage/user-id/12564927) of [Piotr Żuraw Architekt](https://www.zurawarchitekt.pl)

twitter:

How to determine tag extents, width, height and an open source single-click detail family generator add-in with the #RevitAPI @AutodeskForge @AutodeskRevit #bim #DynamoBim #ForgeDevCon https://autode.sk/detailcomponent

Today, we highlight two nice contributions from the Revit API discussion forum
&ndash; Determining tag extents
&ndash; One-click detail family generator...

linkedin:

How to determine tag extents, width, height and an open source single-click detail family generator add-in with the #RevitAPI

https://autode.sk/detailcomponent

- Determining tag extents
- One-click detail family generator...

#bim #DynamoBim #ForgeDevCon #Revit #API #IFC #SDK #AI #VisualStudio #Autodesk #AEC #adsk

the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread

<center>
<img src="img/" alt="" title="" width="600" height=""/>
<p style="font-size: 80%; font-style:italic"></p>
</center>

-->

### Tag Extents and Lazy Detail Components

Today, let's highlight two really nice contributions from the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160):

- [Determining tag extents](#2)
    - [Unrotate rotated tags](#2.2)
- [One-click detail family generator](#3)

First, though, a little aphorism to ponder:

<p class="quote">Yesterday, I was clever and tried to change the world.
<br/>Today, I am wise and try to change myself.</p>
<p class="author">&ndash; Rumi</p>

####<a name="2"></a> Determining Tag Extents

We repeatedly discussed how to ensure that tags do not overlap, both here and in
the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160),
e.g., in the threads
on [tags without overlapping](https://forums.autodesk.com/t5/revit-api-forum/tags-without-overlapping/m-p/11275579)
and [auto tagging without overlap](https://forums.autodesk.com/t5/revit-api-forum/auto-tagging-without-overlap/td-p/9996808).

A hard-coded algorithm to achieve partial success was presented in the latter and reproduced 
in [Python and Dynamo autotag without overlap](https://thebuildingcoder.typepad.com/blog/2021/02/splits-persona-collector-region-tag-modification.html#5).
A more complete solution using a more advanced algorithm is now available commercially,
called [Smart Annotation](https://bimlogiq.com/products/smart-annotataion) by [BIMLOGiQ](https://bimlogiq.com).

One prerequisite for achieving this task is determining the extents of a tag.

[AmitMetz](https://forums.autodesk.com/t5/user/viewprofilepage/user-id/9455666) very
kindly shares sample code for a method to achieve this in the thread
on [tag width/height or accurate `BoundingBox` of `IndependentTag`](https://forums.autodesk.com/t5/revit-api-forum/tag-width-height-or-accurate-boundingbox-of-independenttag/m-p/11274095).
Says he:
 
Following the helpful comments above, here is a method that returns tag dimensions.

A few comments on the implementation:

- First, we need to make sure the LeaderEndCondition is free in order to find the LeaderEndPoint.
- Move the tag and it's elbow to LeaderEndPoint.
- We get the correct BoundingBox only after moving the tag and it's elbow, and committing the Transaction.
- I tried to use an unwrapped `transaction.rollback` without `TransactionGroup`, but it didn't work.
  So, if we want to keep the tag in its original location, we have to commit the transaction and then roll back the transaction group.

<pre class="code">
<span style="color:gray;">///</span><span style="color:green;">&nbsp;</span><span style="color:gray;">&lt;</span><span style="color:gray;">summary</span><span style="color:gray;">&gt;</span>
<span style="color:gray;">///</span><span style="color:green;">&nbsp;Determine&nbsp;tag&nbsp;extents,&nbsp;width&nbsp;and&nbsp;height</span>
<span style="color:gray;">///</span><span style="color:green;">&nbsp;</span><span style="color:gray;">&lt;/</span><span style="color:gray;">summary</span><span style="color:gray;">&gt;</span>
<span style="color:blue;">public</span>&nbsp;<span style="color:blue;">static</span>&nbsp;Tuple&lt;<span style="color:blue;">double</span>,&nbsp;<span style="color:blue;">double</span>&gt;&nbsp;<span style="color:#74531f;">GetTagExtents</span>(
&nbsp;&nbsp;IndependentTag&nbsp;<span style="color:#1f377f;">tag</span>)
{
&nbsp;&nbsp;Document&nbsp;<span style="color:#1f377f;">doc</span>&nbsp;=&nbsp;tag.Document;

&nbsp;&nbsp;<span style="color:green;">//Dimension&nbsp;to&nbsp;return</span>
&nbsp;&nbsp;<span style="color:blue;">double</span>&nbsp;<span style="color:#1f377f;">tagWidth</span>;
&nbsp;&nbsp;<span style="color:blue;">double</span>&nbsp;<span style="color:#1f377f;">tagHeight</span>;
 
&nbsp;&nbsp;<span style="color:green;">//Tag&#39;s&nbsp;View&nbsp;and&nbsp;Element</span>
&nbsp;&nbsp;View&nbsp;<span style="color:#1f377f;">sec</span>&nbsp;=&nbsp;doc.GetElement(tag.OwnerViewId)&nbsp;<span style="color:blue;">as</span>&nbsp;View;
&nbsp;&nbsp;XYZ&nbsp;<span style="color:#1f377f;">rightDirection</span>&nbsp;=&nbsp;sec.RightDirection;
&nbsp;&nbsp;XYZ&nbsp;<span style="color:#1f377f;">upDirection</span>&nbsp;=&nbsp;sec.UpDirection;
&nbsp;&nbsp;Reference&nbsp;<span style="color:#1f377f;">pipeReference</span>&nbsp;=&nbsp;tag.GetTaggedReferences().First();
&nbsp;&nbsp;<span style="color:green;">//Reference&nbsp;pipeReference&nbsp;=&nbsp;tag.GetTaggedReference();&nbsp;//Older&nbsp;Revit&nbsp;Version</span>
 
&nbsp;&nbsp;<span style="color:blue;">using</span>&nbsp;(TransactionGroup&nbsp;<span style="color:#1f377f;">transG</span>&nbsp;=&nbsp;<span style="color:blue;">new</span>&nbsp;TransactionGroup(doc))
&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;transG.Start(<span style="color:#a31515;">&quot;Determine&nbsp;Tag&nbsp;Dimension&quot;</span>);
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:blue;">using</span>&nbsp;(Transaction&nbsp;<span style="color:#1f377f;">trans</span>&nbsp;=&nbsp;<span style="color:blue;">new</span>&nbsp;Transaction(doc))
&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;trans.Start(<span style="color:#a31515;">&quot;Determine&nbsp;Tag&nbsp;Dimension&quot;</span>);
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tag.LeaderEndCondition&nbsp;=&nbsp;LeaderEndCondition.Free;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;XYZ&nbsp;<span style="color:#1f377f;">leaderEndPoint</span>&nbsp;=&nbsp;tag.GetLeaderEnd(pipeReference);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tag.TagHeadPosition&nbsp;=&nbsp;leaderEndPoint;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tag.SetLeaderElbow(pipeReference,&nbsp;leaderEndPoint);
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;trans.Commit();
&nbsp;&nbsp;&nbsp;&nbsp;}
 
&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:green;">//Tag&nbsp;Dimension</span>
&nbsp;&nbsp;&nbsp;&nbsp;BoundingBoxXYZ&nbsp;<span style="color:#1f377f;">tagBox</span>&nbsp;=&nbsp;tag.get_BoundingBox(sec);
&nbsp;&nbsp;&nbsp;&nbsp;tagWidth&nbsp;=&nbsp;(tagBox.Max&nbsp;-&nbsp;tagBox.Min).DotProduct(rightDirection);
&nbsp;&nbsp;&nbsp;&nbsp;tagHeight&nbsp;=&nbsp;(tagBox.Max&nbsp;-&nbsp;tagBox.Min).DotProduct(upDirection);
 
&nbsp;&nbsp;&nbsp;&nbsp;transG.RollBack();
&nbsp;&nbsp;}
&nbsp;&nbsp;<span style="color:#8f08c4;">return</span>&nbsp;Tuple.Create(tagWidth,&nbsp;tagHeight);
}
</pre>

Many thanks to Amit for this nice implementation!

####<a name="2.2"></a> Unrotate Rotated Tags

Steven Micaletti, VDC Software & Technology Developer added
a [comment on this method](https://www.linkedin.com/feed/update/urn:li:activity:6952994276876169216?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A6952994276876169216%2C6953115731991433216%29), saying:

> Good stuff; however, the GetTagExtents() implementation is missing a critical step &ndash; rotating the Pipe.
The Pipe in the thread is at an angle, while the tag is not, and this is not generally how MEP elements are tagged.
MEP tag families usually have the "rotate with component" option enabled, and in that scenario the bounding box returned is unusable.
We must first disconnect and rotate the pipe to be model axis aligned before we set the TagHeadPosition, get the BoundingBox, and RollBack() the Transaction.

Thank you, Steven, for pointing this out!

####<a name="3"></a> One-Click Detail Family Generator

Another nice solution and entire open source sample add-in is shared by
Peter [PitPaf](https://forums.autodesk.com/t5/user/viewprofilepage/user-id/12564927) of [Piotr Żuraw Architekt](https://www.zurawarchitekt.pl)
presenting [one click convert detail elements to detail family](https://forums.autodesk.com/t5/revit-api-forum/one-click-convert-detail-elements-to-detail-family/td-p/11230155):

> I'm working on a Revit add-in to automate and simplify creation of detail Components families.

> This is helps create detail components on the fly just in model view.

> It allows the user to draw parts of a detail with lines and fill regions in model view and change it to a component without opening the family editor.

> Here I want to share with you the first version of this add-in, including source code and compiled install files:

> <p style="text-align:center"><a href="https://github.com/PitPaf/LazyDetailComponent">github.com/PitPaf/LazyDetailComponent</a></p>

> Feel free to use it if you find it interesting. I appreciate all your comments.

<center>
<img src="img/lazy_detail_component.png" alt="Lazy detail component" title="Lazy detail component" width="438"/> <!-- 438 -->
</center>

Many thanks to Peter for implementing, documenting and sharing this nice solution!