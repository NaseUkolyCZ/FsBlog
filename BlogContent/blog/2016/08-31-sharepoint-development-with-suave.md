@{
    Layout = "post";
    Title = "SharePoint Development with Suave";
    Date = "2017-08-31T04:16:31";
    Tags = "";
    Description = "";
}

This month we finished 3 [SharePoint Online projects](https://products.office.com/en-us/sharepoint/sharepoint-online-collaboration-software) done 
with [React](https://facebook.github.io/react/), [Orleans actor framework](https://dotnet.github.io/orleans/) and hosted in [Azure Web Apps](https://azure.microsoft.com/cs-cz/services/app-service/web/) 
using [Suave](https://suave.io/).

We were replacing huge homebuilt Excel or Access fileserver-shared files with SharePoint Online from Office 365 as the structured data storage 
and [provider-hosted SharePoint Add-ins](https://msdn.microsoft.com/en-us/library/office/fp142381.aspx) for the user interface.
We did some Proof-Of-Concepts on the top of the SharePoint standard interface, but the users were not very happy and demanded feature-rich experience.

In these projects we had to overcome a few of obstacles like:

- how to get the OAuth tokens and work with them when the user needs to access the data stored in the SharePoint Online
- how to work with a SharePoint Online list having 10.000+ items
- how to build a small-enough framework (API and API client) to implement calls between React frontend and Orleans backend

At the end we have a structure allowing us:

- create React frontend in F# using [Fable](http://fable.io/)
- create functional actor backend in Orleans
- to have continuous integration including the UI tests

for any server-based web application based on SharePoint Online.
