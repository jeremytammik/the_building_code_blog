<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link rel="stylesheet" type="text/css" href="bc.css">
<script src="run_prettify.js" type="text/javascript"></script>
<!---
<script src="https://google-code-prettify.googlecode.com/svn/loader/run_prettify.js" type="text/javascript"></script>
-->
</head>

<!---

#dotnet #csharp #geometry
#fsharp #dynamobim
#restapi #python
#grevit
#responsivedesign #typepad
#ah8 #augi #au2015 #dotnet
#stingray #adsklabs #cloud #rendering
#3dweb #3dviewapi #html5 #threejs #webgl #3d #apis #mobile #vr #ecommerce
#Markdown #Fusion360 #Fusion360Hackathon #revitapi #adsk #3dwebcoder #aec #bim
#Mongoose #javascript
#au2015 #rtceur
#RestSharp #restapi #mongodb #nodejs

Revit API, Jeremy Tammik, akn_include

Sharing, #DynamoBIM and a Chinese Book #revitapi #3dwebcoder #bim #aec #adsk #adskdevnetwrk #dynamobim

I returned from the Autodesk Cloud Accelerator in Prague, where I finished off cleaning up the FireRating in the Cloud sample and made some good inroads into the new CompHound project. Some learning resources and sharing philosophy
&ndash; Håvard Vasshaug on Learning Dynamo and Sharing Content
&ndash; Open Source BIM, IFC and FreeCAD
&ndash; Chinese Revit API Book...

-->

### Sharing, Dynamo and a Chinese Book

I returned from the
[Autodesk Cloud Accelerator in Prague](http://autodeskcloudaccelerator.com/prague),
where I finished off cleaning up the
[FireRating in the Cloud](https://github.com/jeremytammik/FireRatingCloud) sample
and made some good inroads into the new
[CompHound project](https://github.com/CompHound/CompHound.github.io).

Today, I want to highlight some learning resources and sharing philosophy:

- [Håvard Vasshaug on Learning Dynamo and Sharing Content](#2)
- [Open Source BIM, IFC and FreeCAD](#3)
- [Chinese Revit API Book](#4)
    - [Table of Contents](#5)


Before getting to that, here is my
[Cloud Accelerator Prague photo album](https://www.flickr.com/photos/jeremytammik/sets/72157656369939043) with
some pictures from last week:

<center>
<a data-flickr-embed="true"
  href="https://www.flickr.com/photos/jeremytammik/albums/72157656369939043"
  title="Autodesk Cloud Accelerator Prague">
    <img src="https://farm6.staticflickr.com/5818/21435184406_b8b8b659c9_z.jpg"
      width="640" height="480" alt="Autodesk Cloud Accelerator Prague" />
</a>
<script async src="https://embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>
</center>

<!---
https://flic.kr/s/aHskgX8hSF
https://www.flickr.com/photos/jeremytammik/sets/72157656369939043
-->



#### <a name="2"></a>Håvard Vasshaug on Learning Dynamo and Sharing Content

<!---
[Håvard Vasshaug](http://vasshaug.net/author/hvasshaug) is the author of the
[Ruby Python Shell](https://github.com/hakonhc/RevitRubyShell) and
made a number of contributions here to The Building Coder in the past.
-->

[Håvard Vasshaug](http://vasshaug.net/author/hvasshaug) published a really nice, professional and convincing in-depth discussion on
[Learning Dynamo](http://vasshaug.net/2015/09/18/learn-dynamo).

That led me to explore his site a teeny weeny bit more, for instance to discover the
[Vasshaug content libraries](http://vasshaug.net/content), including:

- Vasshaug Rebar Revit Library
- Dark Revit Content Library
- Flat Content by Andy Milburn and others. Downloaded, modified and standardized.
- Waffle Slab Void System for cutting Concrete Floors and obtaining a waffle slab.
- Steel Pile family with multiple voids for cutting concrete.
- Adaptive Component families for modelling Post Tension reinforcing bars.

There is some really valuable stuff in there.

I fully concur with Håvard's statement:

> I am inspired by sharing communities, and believe the international architecture, engineering and construction industry would do well to revise its visions about sharing knowledge and content. The idea that a company’s assets are files and folders, and that its employees will grow by keeping their knowledge to themselves is outdated at best.

Thank you very much for sharing all this, Håvard!


#### <a name="3"></a>Open Source BIM, IFC and FreeCAD

On the topic of sharing, I also just noticed a whole host of open source BIM tools that I was unaware of:

- [BIMcollective](http://opensourcebim.org), a collective of open source developers that develop BIM software tools.
- [IfcOpenShell](http://ifcopenshell.org), the open source IFC toolkit and geometry engine
- [FreeCAD](http://www.freecadweb.org), a parametric 3D modeler, open-source, highly customizable, scriptable and extensible, multiplatfom (Windows, Mac and Linux), reads and writes open file formats such as STEP, IGES, STL, SVG, DXF, OBJ, IFC, DAE and many others.

I wish I had time to dive into it all.



#### <a name="4"></a>Chinese Revit API Book

Finally, a very nice piece of news: a group of Chinese Autodesk engineers have published the first Chinese book on the Revit API. They received numerous customer questions about how to use the Revit API and how to use it effectively, igniting their passion to share their knowledge.

The book starts with a basic API introduction, then includes general platform API, RST/RME specific APIs, covers macros, etc.

It is now available. Here is a
[presentation of its publication](http://blog.csdn.net/lushibi/article/details/48653343) and a
[purchase link](https://detail.tmall.com/item.htm?_u=m1vm4lrf259d&id=521852354085).

The authors include:

- Lily, Tau, Elaine (Pangu team now)
- Janet (Nexus team now)
- Stephen (Michelangelo team now)
- Aaron (Dev Tech/ADN now)

The book is suitable for Revit API beginners, covering basics, allowing a novice to quickly learn the Revit API framework and proceed into Revit secondary development ranks. It covers all areas of architectural, structural, mechanical, electrical, family creation and Revit secondary development guidance.

It includes a lot of example code, pictures and tables to allow readers a better understanding. In a total of 15 chapters, it covers: function (event, interface, macros), class hierarchy (application class, a document class, elements, family, etc.), different Professional (architectural, structural, MEP related professional API), the development of Revit plug-ins for data read, create, modify, import, export and so on, API and .NET technologies to create a rich user interface, providing a better user experience, extending Revit itself, make Revit and other software platforms interact, data verification, inspection and automatic operation, improved data availability and efficiency of the design.

#### <a name="5"></a>Table of Contents

1. Revit API Overview
    1. Understanding Revit and Revit API
    2. Revit API what you can do
    3. Using the Revit API preparations
    4. Online Resources
    5. Development Tools
2. Revit API basics
    1. External commands IExternalCommand and external applications IExternalApplication
    2. Revit application class and document class (Application & Document)
    3. Transaction processing (Transaction)
    4. Practical example
3. Element (Element)
    1. Element base
    2. Element Edit
    3. Filter element
4. Architectural Modeling
    1. Elevation and Grids
    2. Host element (HostObject)
    3. Family instance (FamilyInstance)
    4. Family instance (FamilyInstance) creation
    5. Room and Area (Room and Area)
    6. Line element (CurveElement)
    7. Hole (Opening)
5. Notes (Documentation)
    1. Dimensioning (Dimension)
    2. Text annotation (Text)
    3. Detailing (Detail)
    4. Mark (Tag)
6. Geometry (Geometry)
    1. Overview
    2. Exercise: Get a wall of geometric data
    3. Geometric primitive class
    4. Geometry auxiliary class
    5. Geometry collections
    6. Exercise: Get a beam geometry data
7. Family (Family)
    1. Introduction to Family
    2. Related to the main API class
    3. Management family type and family arguments
    4. Management of the geometry
    5. Visibility management of the geometry
    6. Edit Family and Load Family
    7. Other
8. View (Views)
    1. Overview
    2. Three-dimensional view (View3D)
    3. Plan view (Plan View)
    4. Drawing View (View Drafting)
    5. Section View (View Section)
    6. Reference callout view and detail view
    7. Drawing View (Sheet)
    8. Schedule (View Schedule)
9. Event (Events)
    1. Introduction Event
    2. Registration and cancellation of events
    3. Cancellable event
    4. Database Event
    5. Interface events
    6. Idle event (Idling Event)
    7. External events (External Event)
10. Ribbon Extensibility (Ribbon UI)
    1. Based on the introduction
    2. Tab page (RibbonTab)
    3. Panel (RibbonPanel)
    4. Command button (PushButton)
    5. Dropdown button (PulldownButton)
    6. Dropdown memory buttons (SplitButton)
    7. Drop-down combo box (ComboBox)
    8. Drop-down combo box options (ComboBoxMember)
    9. Select the button set and toggle buttons (RadioButtonGroup & ToggleButton)
    10. Text box (TextBox)
    11. Revit style task dialogs (Task Dialog)
11. Revit Structure Modeling
    1. Structural model elements
    2. Analysis Model (AnalyticalModel)
12. Material (Material)
    1. Material Introduction
    2. Identification materials
    3. Patterning material information
    4. Appearance information materials
    5. Physical and heat information materials
    6. Setting Materials
13. Plumbing Modeling
    1. Duct / pipe (Duct / Pipe)
    2. Electrical connections (Connector)
    3. Plumbing model (MEPModel)
    4. Plumbing system (MEPSystem)
    5. Plumbing set up
    6. Space and partitioning (Space & Zone)
14. Macro (Macro)
    1. What is a macro
    2. Revit Macros Introduction
    3. Revit macros developed basic workflow
    4. Modify and delete modules and macros
    5. Run the macro in the Macro Manager
    6. Debugging macros
    7. Macro Security
    8. Standard Revit API and the Revit macro uses the API differences
15. Other languages ​​(VB.NET, C++, CLI, F#)
    1. VB.NET
    2. C++ / CLI
    3. F#

So much exciting stuff to look at!

Let's get going.

<!---

#### <a name="5"></a>Revit Object Unique ID's & IFC GUID's

https://www.linkedin.com/grp/post/3690870-6045569862351228928?trk=groups-post-b-all-cmnts


Paul Marsland MSc CEng MIET LCC Chief Electrical Engineer at NG Bailey



I am developing a suite of field tools to capture and synchronise data remotely with a central Revit model. I currently have a fully working set of tools that work as required. I am working on a number of plug-ins for applications such as Revit, Revit Viewer, Navisworks, Design Review and hopefully an IFC viewer.

My intention is to collect and capture data remotely using various model/drawing viewing interfaces. Whilst I have the system fully working I am a little disappointed that Autodesk opt to utilise their own set of Identifiers and Unique-Identifiers within Revit and only appear to support the GUID's (as utilised by IFC) in a limited fashion.

Whilst Revit does generate GUID's (those used in IFC) for all objects, these are only created on export. The problem and inconsistency this causes probably needs a little explaining.

Revit Objects when they are created are assigned an ElementID. This is the equivalent of an AutoCAD handle, basically the next internal database number that is unique in the model but would be duplicated in any other model. The ElementID is also not always consistent. When multiple users are working on a Revit model each user essentially works on a copy of the central model and synchronises their work back to this periodically. Because each user will generate objects that each take the next sequential ElementID, upon synchronisation Revit re-assigns any duplicated ElementID's. In addition to ElementID's Revit also generates a UniqueID. This is guaranteed to be unique and consists of two parts. The first part is made up of what is called an EpisodeID (This is a unique identifier for the particular Revit session, so each user session on a shared model would be allocated a different EpisodeID). The second part of the Revit UniqueID is the original ElementID that was assigned. The ElementID may get changed upon synchronisation with the central model but the UniqueID will always retain the original one)

Upon Export (eg: to IFC, dwf etc) Revit generates a GUID. In most cases this can be created by XORing the EpisodeID with the ElementID. For IFC this GUID is then compressed [base64 encoded] to produce the shorter but equivalent IFC GUID.

The problem I have found is that the IFC GUID cannot be used reliably as a two way identifier for the object (unless you generate the IFC GUID for every object in the Revit model and compare this with the IFC GUID you are looking for until a match is made, which is not a very efficient solution). The simple solution is to use the Revit UniqueID (but this does not export to all formats by default).

It seems crazy to me that Revit does not just assign a GUID for every object as and when it is created, this could then be used as the unique identifier to the object regardless of the file format. (Whilst Autodesk may argue that this is essentially what they do, unless the information used to generate the IFC GUID is retained there is no quick/efficient way to match the IFC GUID back to the associated object)

I have discovered most of the above by trial and error, (and by reading Jeremy Tammik's excellent blogs), so it’s possible I may be overlooking something. Does anyone have any ideas or suggestions as to how best to uniquely identify Revit objects. At present the tools I have developed primarily use the Revit UniqueID as the "master" identifier but I also maintain SQL lookup tables to the IFC GUID's and other identifiers so I can efficiently two-way match and synchronise data to the correct object regardless of which file format I happen to be using.

PM

Paul Marsland MSc CEng MIET LCC

Hans Lammerts

Paul, take notice of this post

http://www.revitforum.org/architecture-general-revit-questions/3016-guid-numbers-3.html#post147997

Paul Marsland MSc CEng MIET LCC

Thanks Hans

The post you refer to however only discusses some of the things I have mentioned above. What I would like is a single Unique Identifier to objects that is persistent and the same regardless of what format the model is exported to of viewed in (which would make perfect sense). As it is we have several identifiers that can be combined (mathematically) to create the IFC GUID, but to get back from the IFC GUID to an identifier that Revit can use to locate objects in its database we need some of the original identifiers (which would have to be passed on to each format you are working in) or as mentioned above you create the IFC GUID for every object in the database until you find a match with the one you are looking for (very inefficient). The solution (as I see it) would require Revit to either use an IFC compliant GUID as it own internal identifier (although this may limit its own object search capabilities) or to generate the IFC GUID at the point an object is created and keep it persistent ( but this would increase file size as every object would then carry additional data). Does anyone know how other systems work with IFC GUID's?

PM

Hans Lammerts

I think that would be a 'feature request' to Autodesk.

Saul Henrion Verpoorten

BIMone has an Add-in which can Search for GUID's. Maybe this something worth checking out. It's free of charge.

Angel Velez

Hi Paul,

Your post seems to accurately reflect the current state of Revit. I have a couple of comments:

1. You can, as part of the advanced options of the alternate UI for IFC export, save the IFC GUID in the file after the export in the IFC GUID built-in parameter. While this would indeed increase file size as every object would then carry additional data, so would having a GUID for every object, so it's pretty much a wash. Because of the way the UniqueId and IFC GUIDs are generated, they correctly take no extra space in the element.

2. As you state, vanilla Revit doesn't have a great way to search for elements by GUID, either UniqueId or IFC GUID. It is fairly easy to have add-ons that allow this, though, and (for example) Link IFC, on reload, does exactly this search to determine if an object is new or changed. This sort of search should be able to be efficient with a little caching up front.

3. Regardless of 1 and 2 above, improving how you can search by some sort of consistent GUID (vs. a "UniqueID' that is too long for a GUID) for elements in Revit natively is a good request.

Regards,
Angel

Sagi Darali

Paul, just out of curiosity, how long would it take to generate the GUIDs and cache them in memory as a first step before synching? Usually that kind of mathematical calculations on an element collection are almost instantaneous, and it is a perfect case for applying parallel processing to increase speed (if needed).

Dr Muhammad Tariq Shafiq

Paul has explained the Revit mechanism very well, thank you. Other BIM authoring tools do the same, for example ArchiCAD stick its internal database number on the element and rely on that for all the matching/comparison operations for change management and synchronization. IFC GUIDS are only used when exported and each tool has its own mechanism to assign IFC GUIDs. These GUIDs are persistent if generated from same authoring tool. But what about if a composite (a.k.a Federated) model has parts from two different BIM authoring tools. GUIDs in this case will be not be reliable. If object GUIDs are same, it is clearly a match to compare or merge two objects as GUIDs are designed to be unique, however, two objects can still constitute a comparable pair even if there GUIDs are different (because of authoring tool differences).

The point is that GUIDs are helpful but there is need to consider other characteristics, such as location (same bounding box), containment (same address), Name, specifications, function etc., to track similar objects in addition to using GUDS. This has to be done in the IFC schema (Perhaps by adding an IfcChangeSet similar to IfcOwnerHistory) and then implement in BIM authoring tools for consistency & interoperability.

Paul Marsland MSc CEng MIET LCC

Sagi, for a small model generating the GUID's would be very quick, but on large models with tens of thousands of objects it would take time. I assume that the quickest way to reference an element in Revit would be by using its ElementID as this is a sequential number used as its own internal database reference. Given that the UniqueID is created from the EpisodeID and the initially allocated ElementID (that can be switched by Revit when Models are synchonised) the UniqueID as Angel states above is not an efficient way of searching for objects (but it is essentially a unique identifier and Revit does have built in mechanisms to search using the UniqueID). This begs the question, Why don't Autodesk simply choose to use the IFC GUID as the unique identifier in Revit, this could even be base 64 encoded reducing file sizes further, and gaining all the benefits of a common single identifier in all exported formats.

Angel Velez

To the two points above:

1. In a federated model, if you have objects generated in a different system, they would come with their own IFC GUID. On export, any object that has an IFC GUID already assigned will not generate a new one. So if you import a wall and re-export it, the IFC GUID will be the original one from the first IFC file.

2. I think at this point changing the unique identifier in Revit would have a certain number of repercussions for API developers, so it can't be changed lightly. That said, I think it is something to consider.

Sagi Darali

Paul, I have successfully achieved 100s of millions of calculations on string and numerical collections in between 3-10 seconds using parallel processing in .NET (on quad core i7 CPU), so I'm guessing that pre-processing the GUIDs from Revit UIDs and caching them is very feasible. This process is not dealing with any geometry, it is only reading the UIDs collection which should be very quick, and 10K is a small number that can run on a single CPU thread. I believe this is a good solution until Autodesk decides to store the GUIDs in the model.

Paul Marsland MSc CEng MIET LCC

Sagi, I will write an algorithm and test it on some typical sized models, if it works successfully without a noticeable delay to the user I will be happy. I expect your suggestion of caching a lookup up table in memory would be the most efficient approach.

Terra Kyle

I am definitely a proponent of Autodesk switching to the IFC GUID as the “common single identifier”. A wall that I have run up against is trying to Copy/Monitor an imported IFC file. I am developing a workflow for exchange between Vectorworks Architect and Revit. The process involves the Autodesk recommended shuttle file concept; opening the IFC file, saving it as an RVT file, and linking it into a Revit project. I was trying to take this workflow a step further by taking advantage of Copy/Monitor. However, I was stymied by the fact that Revit uses the Element ID to perform Copy/Monitor functions and NOT the IFC GUID (as verified by Angel; I appreciate the response on this and am sorry for not getting back to you). The element ID changes every time a new open operation is performed, unless nothing has changed (meaning new elements have been added; I have had mixed success when elements just move or change). Link IFC is a great step forward by Autodesk, but it has many problems that make the shuttle file workflow more desirable. Of course, it would be even more desirable if I could get Copy/Monitor to work ;) Just trying to get everyone in the same sandbox.

Saul Henrion Verpoorten

Applications like Tekla and archicad have the feature of checking if any model changes have occured. This shows one time the more that Revit has not reaches adulthood yet. A lot of work to do by autodesk. Also performance is a big issue.

Angel Velez

Hi Saul, if you use Link IFC with Revit 2015 or 2016 and reload the IFC file, it will only create new elements if the IFC GUID doesn't match an existing IFC GUID in the file, otherwise it just updates the geometry. The workflow Terra describes is to use Open IFC - which isn't intended for reloading, but instead for a one time data transfer - and then linking that file in. That has some advantages, but in general if you only need a reference model, Link IFC is faster, has higher fidelity, and matches elements by IFC GUID. If you are having problems with performance, fidelity, or reload with the new Link IFC functionality, do let us know and we'll look into it.

Saul Henrion Verpoorten

When you link an IFC in Revit 2015 As a reference model Revit converts the IFC into a .rvt in the background. Using thus As a reference doesn't have the same functionality As when I open the IFC with Revit and save it As an RVT. When for example a reference model from archicad is loaded As link IFC the alignment of elements to the linked file isn't possible. When the same file is opened with Revit saved As .rvt it has this functionality. Why does Revit do this?

George "Tom" MacKnight

I guess Bentley is the only software I know that keeps its own element identifier as well as a GUID in its native format. Most others only create a GUID when the model is exported. That means that the GUID can be constantly changing under your feet. In the case of Autodesk, and other products, this means you can't reliably trace an entity across revisions of a model in the various disparate graphic formats it will take in Revit, IFC, Navisworks or imports and exports to other software, At least not without jumping some immense hurdles. Most times it is useless to try and do so. It is unfortunate that persistence of an entity isn't considered a virtue or a necessity. It is one of the prime reasons that IFC fails in being a foundation/integration format between software platforms.

Stefan Boeykens

From my experience, the IFC guid in ArchiCAD is also stable. There is an internal (application) guid and there is an IFC guid (whether you export to IFC or not does not matter). And there is a user-editable ID, which is only a simple string and which can be (ab)used for whatever you want.

Having an internal IFC guid as the only identifier would probably not work that well in applications where objects might be created by importing an IFC (such as ArchiCAD, Revit, AECOSIM, SketchUp etc...). So the approach of having an application-specific ID (called BATID when looking at an IFC in Solibri) and an IFC-compatible guid seems the best approach.

In a project were are consulting right now, we also encountered issue related to guid. The aggregate model (comprised of six IFC models, originating from Revit) shows duplicate Revit Session IDs and even duplicate IFC IDs.

Duplicate Revit IDs are e.g. openings and the object they reside in (which is a single Revit object, but multiple entities in IFC). But having multiple guid is a serious problem, when you start relying on a guid to be "unique" and a pathway back to the original object in the original model file.less

Angel Velez

Saul: In vanilla 2015, referencing a linked IFC wasn't possible. This was "fixed" in 2015 R2 and beyond. The .ifc.rvt file that is created "knows" the IFC file that it comes from, so when that IFC file is changed, the .ifc.rvt is updated. It is true, as I said before, that the linked objects have less functionality than through the Open IFC command, and we are always interested in feedback about what functionality(ies) people are looking for to make them more useful.

Tom: When you read in an object via IFC, either Open or Link, the IFC GUID will be preserved. You can see it as a shared parameter, and if it is re-exported, that GUID, not a calculated one, will be used.

Stefan: Prior to Revit 2014, there were cases where GUIDs were duplicated. This has been fixed since Revit 2014. If you export anything since then where multiple objects have the same GUID, that's a serious issue that we'd like to see.

Thanks for all of your feedbacks and feel free to contact me with specific issues or requests.

Angel





<center>
<img src="" alt="" width="400"/>
</center>


#### <a name="2"></a>FireRating in the Cloud Enhancements

My real goal is to switch back and continue work on the new
[CompHound component tracker](http://the3dwebcoder.typepad.com/blog/2015/09/comphound-restsharp-mongoose-put-and-post.html#2) as
fast as possible, in preparation for the upcoming conference presentations at
[RTC Europe](http://www.rtcevents.com/rtc2015eu) in Budapest end of October and
[Autodesk University](http://au.autodesk.com) in Las Vegas in December.

However, since the
[FireRating in the Cloud](https://github.com/jeremytammik/FireRatingCloud) sample
is more generic and fundamental, I want to clean it up to utter perfection first, before expanding into new areas.

[FireRating in the Cloud](https://github.com/jeremytammik/FireRatingCloud) covers the connection of Revit database and element data to a cloud-hosted external database.

The [CompHound component tracker](https://github.com/CompHound) will add a user interface, reports, and a 3D model viewer and navigator to that.

Here is a list of the recent firerating enhancements:

- [Using RestSharp for Rest API GET](http://the3dwebcoder.typepad.com/blog/2015/09/using-restsharp-for-rest-api-get.html)
- [Mongodb Upsert](http://the3dwebcoder.typepad.com/blog/2015/09/mongodb-upsert.html)
- C# DoorData and Node.js DoorService Classes
    - [DoorData Container Class](http://the3dwebcoder.typepad.com/blog/2015/09/c-doordata-and-nodejs-doorservice-classes.html#3)
    - [REST GET returns a list of deserialised DoorData instances](http://the3dwebcoder.typepad.com/blog/2015/09/c-doordata-and-nodejs-doorservice-classes.html#4)
    - [Passing a DoorData instance to the Put method](http://the3dwebcoder.typepad.com/blog/2015/09/c-doordata-and-nodejs-doorservice-classes.html#5)
    - [Implementing a REST API router DoorService class](http://the3dwebcoder.typepad.com/blog/2015/09/c-doordata-and-nodejs-doorservice-classes.html#6)



Using [Handlebars](http://handlebarsjs.com)...

http://localhost:3001/html/instances

http://localhost:3001/api/v1/instances

http://localhost:3001/api/v1/instances/48891eaa-9041-405b-a10f-f06585de3cbb-0001de6d

Antonio Manzani
La Costola di Adamo
detective story
full of love for humanity
anger also
p. 268-269
2015-09-18: Antonio Manzini, La costola di Adamo [it] [i love rocco schiavione and antonio manzani better still; radical militant violent personal integrity, regardless of law and order, serving a higher and personal truth; the topic is political and sociological, femmicide; read the last sentence of the acknowledgements before starting the book; i wish there were more rocco stories]
Domenica sono andata in chiesa. Non volevo sentire la messa. Voleva guardare la chiesa. Ho sbagliato orario. Sono entrata e c'era proprio la messa. Il prete ha letto la Genesi, 2:21.23. Me la sono riletta a casa. Dice: Allora l'eterno Iddio fece cadere un profondo sonno sull'uomo, che s'addormento. E prese una delle costole di lui; e richiuse la carne al posto d'essa. E l'eterno Iddio , con la costola che aveva tolta all'uomo, formo una donna e la condusse all'uomo. E l'uomo disse: "Questa finalmente e ossa delle mie ossa e carne della mia carne. Ella sara chiamata donna perche e stata tratta dall'uomo."
Mi sono messa a pensare. A sentire la storiella, la donna nasce dall'uomo, anzi ne e proprio un pezzo. E l'uomo impazzisce per la donna, la ama. In realta ama se stesso. Ama un pezzo di se, non un altro da se. Vive e fa i figli e fa l'amore con se stesso. Un amore concentrato sulla propria persona che niente ha che fare con l'amore. Credo che sia quanto di piu perverso abbia mai letto. Il maschio e innamorato solo di se. Questo dicono le Sacre Scritture. L'inferiorita femmenile non c'entra. E solo

#### <a name="7"></a>Creating a Roof

http://stackoverflow.com/questions/32718999/creating-a-roof-function/32732012#32732012

**Question:**
I'm having trouble to create a roof via code. I know how to create a stairs for example : I start a StairsEditScope and use CreateSketchedLanding with all the right parameters to create my stairs and just commit the StairsEditScope, but for a roof i cant find a clue on how to create it from scratch, any leads?

**Answer:**
Revit provides different kinds of roofs. It is best to understand the various types from an end user point of view before starting to drive them programmatically. The simplest one is defined by a horizontal outline. You can create a roof from such an outline using the Document.NewFootPrintRoof method. Such a roof can be flat, or you can specify a slope for each edge of the outline profile. The Building Coder Xtra labs provide a working sample in the external command Lab2_0_CreateLittleHouse in Labs2.cs:

https://github.com/jeremytammik/AdnRevitApiLabsXtra/blob/master/XtraCs/Labs2.cs

Here are some other roof-related posts on The Building Coder:

RoomsRoofs SDK Sample
Roof Eave Cut
Creating an Extrusion Roof

I hope this helps.

Cheers, Jeremy.

<!- 0015 0198 1215 ->
<ul>
<li><a href="http://thebuildingcoder.typepad.com/blog/2008/09/roomsroofs-sdk.html">RoomsRoofs SDK Sample</a></li>
<li><a href="http://thebuildingcoder.typepad.com/blog/2009/08/roof-eave-cut-in-revit-and-aca.html">Roof Eave Cut in AutoCAD Architecture and Revit</a></li>
<li><a href="http://thebuildingcoder.typepad.com/blog/2014/09/events-again-and-creating-an-extrusion-roof.html">Events, Again, and Creating an Extrusion Roof</a></li>
</ul>

-->
