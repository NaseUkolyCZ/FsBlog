@{
    Layout = "post";
    Title = "Hello fable-import-sharepoint";
    Date = "2016-12-20T01:15:30";
    Tags = "";
    Description = "";
}

# Hello [fable-import-sharepoint](https://github.com/hsharpsoftware/fable-import-sharepoint)

## TL;DR

## Preface
Two months ago I became a part of a project team assigned a very interesting task - to rewrite a highly customized DMS on a top of Microsoft SharePoint.
I was not for the first time I was writing for SharePoint - in fact, it was my fourth project this year, but this time it was a little bit special.
The projects we wrote during the summer and autumn were [provider-hosted SharePoint Add-ins](https://msdn.microsoft.com/en-us/library/office/fp142381.aspx).
We wrote them as server applications running on the top of [Suave](https://suave.io/) [hosted in IIS](https://blog.vbfox.net/2016/03/31/Suave-in-IIS-hello-world.html) 
with the front end using [React](https://facebook.github.io/react/) and [Redux](http://redux.js.org/).
These are the technologies we have been using for years and [were proven to work for us and help us to write code faster](http://fsharp.org/testimonials/#synctoday-1).

## SharePoint Designer Only
The new project was completely different. From all the SharePoint integration and customization options, only those accessible using SharePoint Designer were allowed.
At the same time the user requirements were quite high which was understandable taking into the account they were used to the application created directly for their needs.
Most of them were related to the user experience in terms of:

* information they see on the screen (add or remove)
* actions (links, buttons, menu items) accessible on the particular screen (add or remove)
* specialized validation (file name including wild cards against a specific list)
* multiple file upload
* cascade workflows with App-Steps
* very strict user permissions (e.g. upload only, cannot read the file later)

It was clear soon that not only heavy UI changes will need to be done, but also iterating for list items, starting workflows and so on.

## JavaScript Legacy
There are different ways how to modify SharePoint pages. I did not want to modify HTML directly mainly because the application 
is in fact running on multiple sites so it would be extremely difficult to sync the changes.
The other ways was to deploy JavaScript to Site Assets, include it in the MasterPage and let it add or hide the elements that we needed.

Now let me get back in the history for a while. I first met JavaScript in about 2001 when we were developing 
large Dealer Management System for BMW importer and dealers. At that time we switched from writing ASP applications backed with Delphi COM+ components to
the very first betas of Microsoft .NET. There were no ASP.NET yet and we wanted to write an intranet/extranet application so we have to invent an application architecture
by ourselves.

We were very much influenced by that time latest news from Microsoft like [SQL XML features](https://msdn.microsoft.com/en-us/library/ms950789.aspx) so we decided
most of the logic would be done by the SQL server generating XML that was later transformed by static XSLT files into the final XHTML.

Everything was very fine except for the users demanding some advanced features on the client side like the suggestions as they typed, validations before form submit etc.
And that was when we started to write JavaScript.

Of course it was terrible. There were no jQuery at that time. No advanced frameworks like Angular or React. Niente. Just the plain JavaScript.

For the developers with the Delphi, Visual Basic and later C# background with static types and the compile step checking for typos etc. it was simply a nightmare. 
Endless nights when we were trying to hunt bugs strange bugs in Internet Explorer. All the funny stories about comparing apples to oranges and getting 
[the most difficult-to-understand results you can imagine](http://charlieharvey.org.uk/page/javascript_the_weird_parts).

So it is not difficult to imagine for the next 10 years if a feature was requested by a project/product manager the answer was sometimes "It would need to be done in 
JavaScript, so ..." supported by nodding and affirmative grunts by the survivors of the previous project.

## Modern JavaScript

About ten years later we were writing a ASP.NET MVC application for call centre agents build on the top of Microsoft Dynamics CRM. With the help of jQuery the code was much more readable
now, but we still have to fight a lot of bugs in the runtime (and even production as part of the application was dynamically generated!). Not nice.

Heard about something called Angular at that time, but the server side generated HTML approach was still too strong.

Fast forward to mid-2015. We are writing an application for managing the front office clerks and their shifts. We decided to use ASP.NET Core and Angular. 
Had a lot of fun and although I did mostly the back end, but it looked like Angular is very usable and ready to replace the ASP.NET MVC.

When 2016 kicked in, I am helping my friends to add new Angular front end to their ASP.NET WebPages application from late 2000s. It is not my first Angular application, but for the first time
(and definitely not for the last) we were adding Angular SPA to server generated application already many years in production.

## F#

I have described my path to programming in F# [several](https://github.com/fsharping/Docs/tree/master/004-FSharp%20v%20praxi) [times](http://fsharp.org/testimonials/#synctoday-1).

## [Fable](http://fable.io/) to the rescue

So when I summed up