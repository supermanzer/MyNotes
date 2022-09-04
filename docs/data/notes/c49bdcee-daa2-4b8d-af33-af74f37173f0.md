
### [Project Github Repo](https://github.com/supermanzer/NuxtDRFMDN)

This project is a playground of sorts for various ideas and technologies I am curious about implementing in a web application. Often times I will find myself working through a tutorial while learning some new tech and find myself curious about how I would integrate it into a larger project. One of the points of developing the **Local Library** application is to have that larger project into which I can attempt to insert various technologies and application workflows I am curious about. 

The application built here is based upon the excellent [Django tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django) created by the bright folks at Mozilla Developer Network. This tutorial took me from a general, if basic, understanding of implementing Django to a level of mastery that made me confident I could build production software tools with it. It's become a core part of my goto toolkit when building database powered applcations.


## Redesign
After realizing I missed an opportunity to be a bit more rigorous in first designing my application (I do tend to start and end with code), I'm takig advantage of a pause in development on this project to look at it with fresh eyes.  To that end I will be capturing my revised design and implementation in a separate set of wiki pages.

### [[Redesign Page|projects.localibrary.redesign]]


## Functionality Problem Solving
The links below represent a few of the areas where I have tried to think through some aspect of functionality I wanted to implement.

* [[projects.localibrary.models.dependent-status.approaches]]  - Using Django query annotations to simplify modifying book copy statuses
* [[projects.localibrary.user-notifications]] - Defining both front and back end componets to be employed in providing users notifications about things like late fees and reserved books


### Long Term Goals - Tentative:
*  Go from monolith (current design) to SOA
    * Identify publicly available services that could replace some functionality (ID/Auth)
    * Redesign custom services for different aspects of current monolith (e.g. "payments")
    * Evaluate trade-offs & risks: scaling, data replication/incosistencies.


![[projects.localibrary.next-steps]]
