<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link rel="stylesheet" type="text/css" href="bc.css">
<script src="https://cdn.rawgit.com/google/code-prettify/master/loader/run_prettify.js" type="text/javascript"></script>
</head>

<!---

- Leandro Teles <lteles@thebimdev.com>
  Visual Studio extension

- Nina for Revit
  https://github.com/franpossetto/Nina
  A collection of tiny tools to work faster in Revit. Most of these commands are availables in Revit but as options in second windows. As they are actions that the users repeats very often, the goal is to be able to access them quickly, using keyboard shorcuts.
  pyRevit extension to toggle point cloud visibility
  https://forums.autodesk.com/t5/revit-api-forum/pyrevit-extension-to-toggle-point-cloud-visibility/m-p/10559876

- I just read an interesting article from this week's The Economist about how the temperature on Earth keeps rising.
  The recommended solution is to reduce greenhouse gas emissions, especialy methane, and actively remove carbon dioxide from the atmosphere to prevent the warming of our planet. Here's the link to the news article (you may need to subscribe to read the full article):
  https://www.economist.com/science-and-technology/the-ipcc-delivers-its-starkest-warning-yet-about-climate-change/21803522

- I also recently finished Jonathan Safran Foer's *We are the weather* and can highly recommend it to anyone interested in an analysis of what each of us can do about the problem right here and now. Basically, he recommends we eat less meat and consume less animal products. According to the reliable sources he quotes, raising animals is contributing somewhere between 14.5% and 51% of *all* greenhouse gases, more than airplanes, cars, industry, construction, heating, anything and everything else.
  Carbon farming, carbon removal by agriculture and land management,  might help on a global scale: https://www.carboncycle.org/carbon-farming; for me, as an individual, i see just four immediate relevant options: don't fly; don't drive; don't have children; don't consume animal products. rather full of 'don't's.... i prefer to look at the positive side of things, and what i do want to do. that takes longer to explain, though :-)
  https://autodesk.slack.com/archives/C0KBT3859/p1629308234337400

twitter:

add #thebuildingcoder

Two useful #RevitAPI community contributions, Nina for Revit, the BIMdev VS extension, and thoughts on global warming @AutodeskForge @AutodeskRevit #bim #DynamoBim #ForgeDevCon https://autode.sk/vsextension

Two useful community contributions and some thoughts on global warming
&ndash; Nina for Revit
&ndash; The BIMdev VS extension
&ndash; The Economist on climate change
&ndash; We are the weather...

linkedin:

Two useful #RevitAPI community contributions and some thoughts on global warming:

https://autode.sk/vsextension

- Nina for Revit
- The BIMdev VS extension
- The Economist on climate change
- We are the weather...

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

### Nina and a VS Revit Add-In Extension

Two useful community contributions and some thoughts on global warming:

- [Nina for Revit](#2)
- [The BIMdev VS extension](#3)
- [The Economist on climate change](#4)
- [We are the weather](#5)

####<a name="2"></a> Nina for Revit

Another nice community contribution
is [Nina for Revit](https://github.com/franpossetto/Nina)
by Francisco [franpossetto](https://github.com/franpossetto) Possetto:

> A collection of tiny tools to work faster in Revit.
Most of these commands are available in Revit, but as options in secondary windows.
Since these actions are repeated often, the goal is to access them quickly, using keyboard shortcuts.

<center>
<img src="img/nina_for_revit.png" alt="Nina for Revit" title="Nina for Revit" width="350"/> <!-- 719 -->
</center>

Many thanks to Francisco for these, and pointing them out in his answer to
the [Revit API discussion forum](http://forums.autodesk.com/t5/revit-api-forum/bd-p/160) thread
on a [pyRevit extension to toggle point cloud visibility](https://forums.autodesk.com/t5/revit-api-forum/pyrevit-extension-to-toggle-point-cloud-visibility/m-p/10559876).

####<a name="3"></a> The BIMdev VS Extension

Leandro [theBIMdev](https://github.com/theBIMdev) Teles very kindly shares a new Visual Studio extension for Revit add-ins,
[BIMDev Revit Tools RevitExtension](https://github.com/theBIMdev/RevitExtension).

Some personal background (skip if not interested):
I’m originally from Brazil but grew up in New York and now live near Seattle.
I have been in the manual labour side of the residential construction industry since I was 18 (I am now 38).
Because of my personal circumstances, I was never able to receive any formal education or degrees but have always loved programming and software development.
This love became my favourite hobby, making me great at googling and pushing myself to learn all that I could.
Almost 4 years ago I was introduced to Revit and became certified in it, which marked the start of my employment at The Conco Companies. Conco is a commercial concrete contracting company in the west coast of the US.
I was hired as a 'VDC modeler' in the estimating department, and for the first time in my life, I had a desk job. While performing my duties in this role I discovered the great potential that Revit provides in the form of the Revit API.
I was able to take all my informal experience and apply it to developing addins that were very helpful to the department.
I was finally getting paid to do what I love, even if I couldn’t do it all of the time (after all, estimates still had to go out).
As of June of this year I left Conco and started my own company (BIMDev LLC), a one-man operation.
I connected and have been working closely with another developer who incidentally has a similar story but has been doing this much longer and is better known in the community, Michael Kilkelly of [ArchSmarter.com](https://archsmarter.com).
My former company, Conco, also agreed to become one of my clients, and between the 2 I  have been very busy creating addins (and enjoying every second).
 
The extension:
One of the things that Michael opened my eyes to is the amazing convenience of using Visual Studio’s 'Shared Project' template to keep most code for an addin in a single place, and then using conditional compilation symbols where the different versions of Revit differ.
Based on this concept, I created an extension for visual studio that does the following:

- The solution generated by this template consists of one project for each Revit version from 2018 forward.
- Each project references a single 'Resources' project for files, images, and icons they have in common.
- Each project references a single 'Shared' project where all code they have in common resides. See the documentation on Shared Projects.
- The Compilation Symbol for each project is set to Revit2018, Revit2019, etc.
- RevitAPI.dll, RevitAPIUI.dll, and AdWindows.dll are all included and referenced in the template using the latest version for each Revit year in the corresponding project.
- Each project will have its own Revit manifest file (.addin), and that file is set to Copy Always to the output directory. A new GUID is automatically generated for the AddinId.
- Post-build events are generated to copy any .dll and .addin files from the output directory of each project to the respective installed Revit addin folder.

There are at least 2 additional major features that I envision this extension having:

Present a form to the user where he can choose if the addin should be an 'Application' or a 'Command', choose if he wants the post-build events mentioned above, and fill out additional details that will auto-populate the `.addin` manifest and the `AssemblyInfo.cs` files.
Have a separate folder in the 'ProgramData\Autodesk\Revit' directory named 'Addins_Experimental'. Then detect when a debugging session begins, rename the 'Addins' folder to 'Addins_Actual', and change 'Addins_Experimental' to 'Addins'. When the debugging session ends, reverse the name changes. The idea here is to make it so that addins that are in active development can be loaded in isolation from any others, and running Revit without the debugger only loads the production-ready addins that a user has installed.
 
The community aspect:
I already have about 40 hours sunk into this extension so far, and I have decided
to [make the project public on GitHub](https://github.com/theBIMdev/RevitExtension).
I opted to put it under the GLP-3 license (as opposed to MIT) because I’m still a very small name in this space, and my new company could still fail, so asking people who do take my code to mention my name felt like a good idea.
I have also published the extension as it is so far to
the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=BIMDevLLC.BIMDevRevitTools).
Lastly, I have a problem I am trying to resolve, and I have asked the question both
on [StackOverflow](https://stackoverflow.com/questions/68607050/use-envdte-in-a-vsix-extension-to-add-a-reference-to-a-shared-project-in-a-multi) as
well as [Microsoft](https://docs.microsoft.com/en-us/answers/questions/497120/use-envdte-in-a-vsix-extension-to-add-a-reference.html#comment-503791).
 
My extension seems to be one of only 4 that appear in the Visual Studio Marketplace when you search for 'Revit'.
Another is the template that you maintain, and none but mine seem to use the 'Shared Project' functionality or be as ambitious.
That makes me think that this is really something that could benefit the community.
This is a project I intend to maintain long term, especially since it is a tool that I myself intend to use regularly.
I would really love to hear any suggestions you and the community may have for this extension.
I look forward to participating much more in the Revit software development community now that I am on my own.
 
Here are the links:

- [RevitExtension GitHub repository](https://github.com/theBIMdev/RevitExtension)
- [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=BIMDevLLC.BIMDevRevitTools)
- [StackOverflow question](https://stackoverflow.com/questions/68607050/use-envdte-in-a-vsix-extension-to-add-a-reference-to-a-shared-project-in-a-multi)
- [Microsoft question](https://docs.microsoft.com/en-us/answers/questions/497120/use-envdte-in-a-vsix-extension-to-add-a-reference.html#comment-503791)
 
Thank you for your attention, and I’m sure we’ll cross paths again in the forums.
 
 Many thanks to Leandro for this tool, and good luck with your new enterprise.

####<a name="4"></a> The Economist on Climate Change

I read a scary article in The Economist about how the temperature on Earth keeps rising:
[The IPCC delivers its starkest warning yet about climate change](https://www.economist.com/science-and-technology/the-ipcc-delivers-its-starkest-warning-yet-about-climate-change/21803522)
&ndash; The effects of a hotter planet are visible around the world (you may need to subscribe to read the full article).
They discuss how to reduce greenhouse gas emissions, especially methane, and actively remove carbon dioxide from the atmosphere to prevent the warming of our planet.

####<a name="5"></a> We are the Weather

On the same topic, I recently finished Jonathan Safran Foer's book [*We are the weather*](https://wearetheweatherbook.com).

I highly recommend it to anyone interested in an analysis of what each of us can do about the climate change problem right here and now.
Basically, he recommends we eat less meat and consume less animal products in general.
According to the reliable sources he quotes, raising animals is contributing somewhere between 14.5% and 51% of *all* greenhouse gases, more than airplanes, cars, industry, construction, heating, anything and everything else.

[Carbon farming](https://www.carboncycle.org/carbon-farming), carbon removal by agriculture and land management, might help on a global scale;
however, for an individual, he identifies just four immediate relevant options:

- don't fly
- don't drive
- don't have children
- don't consume animal products

The fourth is something we can act on immediately, the next time we sit down to have a meal.

This list is rather focus on *don'ts*...
I prefer to look at the positive side of things, and what I <b><i>do</i></b> want to do.
That takes longer to explain, though :-)