<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link rel="stylesheet" type="text/css" href="bc.css">
<script src="https://cdn.rawgit.com/google/code-prettify/master/loader/run_prettify.js" type="text/javascript"></script>
</head>

<!---

- ACS Integration Partner Summit 2022
  https://forge.autodesk.com/blog/acs-integration-partner-summit-2022
  registration
  https://autodesk.registration.goldcast.io/events/636f754d-f617-4a4f-8fa9-38108c6f19d7

- maintain relationships copying elements
  PhaseCreated & PhaseDemolished after using CopyElements()
  https://forums.autodesk.com/t5/revit-api-forum/phasecreated-amp-phasedemolished-after-using-copyelements/m-p/10964247

- Unsplash
  https://unsplash.com
  Unsplash has over a million free high-resolution photos. Explore these popular photo categories on Unsplash. All photos here are free to download and use under the Unsplash License.

twitter:

ACC, the Autodesk Construction Cloud, its APIs, the upcoming ACC summit and maintaining relationships between Revit elements when copying with the #RevitAPI @AutodeskForge @AutodeskRevit #bim #DynamoBim #ForgeDevCon https://autode.sk/copyrelationship

We take a look at maintaining relationships between Revit elements when copying, at ACC, the Autodesk Construction Cloud, and its APIs
&ndash; ACC Model Properties API
&ndash; ACC integration partner summit
&ndash; Maintain relationships copying elements
&ndash; Unsplash with free images...

linkedin:

We take a look at ACC, the Autodesk Construction Cloud, its APIs, the upcoming ACC summit and maintaining relationships between Revit elements when copying with the #RevitAPI

https://autode.sk/copyrelationship

- ACC Model Properties API
- ACC integration partner summit
- Maintain relationships copying elements
- Unsplash with free images...

#bim #DynamoBim #ForgeDevCon #Revit #API #IFC #SDK #AI #VisualStudio #Autodesk #AEC #adsk

the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread

<center>
<img src="img/" alt="" title="" width="600"/>
<p style="font-size: 80%; font-style:italic"></p>
</center>

-->

### ACC Summit, Model Properties, Copy Relationships

We take a look at maintaining relationships between Revit elements when copying, at ACC, the Autodesk Construction Cloud, and its APIs:

- [ACC Model Properties API](#2)
- [ACC integration partner summit](#3)
- [Maintain relationships copying elements](#4)
- [Unsplash with free images](#5)
- [Happy Twosday](#6)


####<a name="2"></a> ACC Model Properties API

A new exciting Forge API may prove especially useful to Revit users,
the [BIM 360/ACC Model Properties API](https://forge.autodesk.com/blog/bim-360acc-model-properties-api).

It provides a powerful new tool to query, filter and compare properties of models. 

For example, previously, if you were interested in only MEP elements (e.g., pipes and ducts) with a subset of their properties, you were required to download the entire model data and to parse the massive body if BIM data yourself. With this new tool, you can download only the elements and properties that you are interested in.
The actual query operation is performed in the cloud, so you have much less data to download.
This causes a considerable performance gain, especially dealing with large models.
Of course, as a developer, you have more functionality to take advantage of with less coding.
With more and more people interested in analysing models, moving toward a model-based approach, and sharing models saved in Docs, among various disciplines and phases, we foresee a lot of potential use cases using this tool.

For more information, check out the article mentioned above,
the comparison of [Model Properties API versus Model Derivative API](https://forge.autodesk.com/blog/model-properties-api-vs-model-derivative-api) and
the other [Forge community blog posts about ACC APIs](https://forge.autodesk.com/apis-and-services/autodesk-construction-cloud-acc-apis).

####<a name="3"></a> ACC Integration Partner Summit

If you are interested in learning more about Autodesk Construction Cloud products and making use of 
the [Autodesk Construction Cloud (ACC) APIs](https://forge.autodesk.com/apis-and-services/autodesk-construction-cloud-acc-apis),
you are invited you to join the [ACC Integration Partner Summit 2022](https://autodesk.registration.goldcast.io/events/636f754d-f617-4a4f-8fa9-38108c6f19d7),
a virtual event on March 17, 2022.

Your Autodesk hosts will be Jim Lynch, SVP & GM of ACS, Josh Cheney, Senior Manager of Strategic Alliances, Jim Gray, Director of Product, ACS Service Infrastructure, and Anna Lazar, Strategic Alliances & Partnerships.

For more information about the event, please refer to the community blog article
on [ACC Integration Partner Summit 2022](https://forge.autodesk.com/blog/acs-integration-partner-summit-2022),
or jump directly to
the [registration form](https://autodesk.registration.goldcast.io/events/636f754d-f617-4a4f-8fa9-38108c6f19d7).

<center>
<img src="img/acc_summit_2022.jpg" alt="ACC Integration Partner Summit" title="ACC Integration Partner Summit" width="400"/> <!-- 1060 -->
</center>

####<a name="4"></a> Maintain Relationships Copying Elements

Returning to the pure .NET desktop Revit API, some interesting aspects of maintaining relationships between elements were discussed in
the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread
on [PhaseCreated and PhaseDemolished after using `CopyElements`](https://forums.autodesk.com/t5/revit-api-forum/phasecreated-amp-phasedemolished-after-using-copyelements/m-p/10964247):

**Question:** I'm trying to copy elements from one document into another, which I'm managing fine.
The issue I'm facing is that, despite having the origin document phases present in the destination document (same phase names at least), the copied elements' `Phase Created` and `Phase Demolished` do not match the original elements'.

I checked if the ElementIds returned by `CopyElements` come up in the same order as the given ElementIds, but unfortunately that was not the case, and once the elements are copied, I'm struggling to make a connection between origin and destination so I can match the phases.

I read the discussion
on [copying elements, types and parameters](https://forums.autodesk.com/t5/revit-api-forum/copying-elements-types-and-parameters/m-p/9542634), 
but it didn't help.

**Answer 1:** I believe that when you collect a bunch of elements and copy them all together in one single operation, Revit will try to maintain and restore all their mutual relationships in the target database.
Therefore, it might help if you add all possible references these elements have to other source database elements to the set of elements to copy.
These references will include the element instances themselves, their types, phases, levels, views, materials, and whatever other objects you are interested in.
Then you will have to test and see what Revit can do to try to avoid creating duplicates of them in the target database and map them to existing target objects instead.

This behaviour is hinted at in the list
of [extensible storage features](https://thebuildingcoder.typepad.com/blog/2011/06/extensible-storage-features.html#7).

**Answer 2:** That’s standard behaviour for the Revit User Interface.
Elements that are pasted into a view do not get their phases from the copied elements.
Instead, they get their phases from the phase of the view they are pasted into.
For example, if the view pasted into has a new construction phase, that’s the phase that the elements will inherit for their created in phase.

It’s possible to check the phases of every element copied, store those in an array, and then apply the phases to the new elements.
I created an add-in that does exactly that and posted the code online:

- [Copy Similar Code](https://sites.google.com/site/revitapi123/copy-similar-code)
> Here is the C# code for an app I wrote that copies and pastes Revit elements and gives the pasted elements the same phase and workset of the copied elements. 

You will have to do some extra work to deal with the fact that you are pasting into a different document, but that should be fairly easy to do.

**Response:** Thanks for the help, @jeremy.tammik and @sragan.

@sragan I was doing exactly what you suggested but I was getting inconsistent results when comparing the elements from the source model against the destination model. I then tried a few different ways and ended up realising that the `CopyElements` does return the same order of the given `ElementId` list, which then solved my problem.

When I collected the elements in my source document, I also collected their `Phase Created` and `Phase Demolished` and stored all 3 in a list:

<pre class="code">
  List&lt;KeyValuePair&lt;ElementId, KeyValuePair&lt;string, string&gt;&gt;&gt;()
</pre>

This allowed me to compare the output of `CopyElements` with that list and apply the settings of each element individually.

Many thanks to Fabio for raising this issue and Steve Ragan for sharing and explaining his effective solution!

####<a name="5"></a> Unsplash with Free Images

I am a fan of open source, the creative commons license, free stuff, good will, sharing and learning together as a community.
Consequently, I share everything I can in public in the hope that it will come in useful for others as well and help make the world a better place.

In a similar vein, a colleague involved in community work pointed
out [Unsplash](https://unsplash.com):

> Unsplash has over a million free high-resolution photos grouped in popular photo categories.
All photos are free to download and use under
the [Unsplash License](https://unsplash.com/license).

<center>
<img src="img/clark_van_der_beken_dtFnCDYHA2Q_unsplash.jpg" alt="Unsplash" title="Unsplash" width="300"/> <!-- 1000 -->
</center>

####<a name="6"></a> Happy Twosday

This Tuesday, February 22, 2022, is both a Tuesday and a spectacular, unique Twosday, the date being both a palindrome and an ambigram:

<center>
<img src="img/2022-02-22_twosday.png" alt="Twosday" title="Twosday" width="400"/> <!-- 1196 -->
</center>

According to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) international standard covering the worldwide exchange and communication of date- and time-related data, this is wrong, of course, and should be written the other way around, as 2022-02-22...