_Notes on the design and functionality of the blog portion of my personal site_

---

## Home Page
I think for this section it would make the most sense to display a list view of articles sorted chronologically (most recent first) on the left and a menu of topics and tags on the right.

### List View Component
This should be a reusable component that displays title, date created/updated, and a brief description of the article.

### Nav Sidebar
I am thinking that I will use the top level directories (within the `blog` directory) to define general categories of blog post.  These will be represented by an accordion menu. Clicking the category name text will filter the list menu on the right.  However there is a dropdown carat icon that will expand the accordion and show a list of blog post titles (sorted in reverse chronological order).  Clicking an individual title should take the user to a detail view for that article.

One aspect I'm a little undecided about is whether to retain the sidebar when showing the detail section.  It would reduce the available space and add distraction.  However it would allow faster navigation from one article to another.  A third option from either full display or no menu is to either use a [popover sidenav](https://vuetifyjs.com/en/components/navigation-drawers/#bottom-drawer). This might interfere with the sidenav component in `default` layout.  In that case I could try using a [minified design](https://vuetifyjs.com/en/components/navigation-drawers/#expand-on-hover) with `expand_on_hover`.



### Algorithms and Content
There are two ways I can think of to allow the sidebar, both category and tag filters, to alter the content displayed in the list/detail view.  

* **Store/State** This approach is to use Vuex global state.  This will entail creating a `blog` namespace, similar to `nav`, with it's own `state`, `getters`, and `mutators`.  This is a not inconsiderable addition of complexity.  However it does abstract the details of the implementation to the Vuex methods, which is appealing.

* **Props/Events** This approach is the more classic Vue mechanism of propagating changes from one component to another.  THe components being acted on generate events that the parent(s) listen for.  The local state is contained on the parent and passed down as props to the display components.  In this scenario the blog home page would need to store all the state and perform the changes based on the events triggered. Navigating to a detail view would (_I think_) clear the state but that could be the behavior I want.  

I was planning on having the side nav trigger a return to the list view **and** the associated filtering of blog results.  That may be prove difficult to achieve in one or the other options spelled out here.  I may need to re-evaluate this approach entirely after I get a little farther into development of the blog sidenav component.

## Update

Categories proved to be too much of an extra hurdle and present organizational difficulties in terms of blog topics (is my NDBC software `tech` or `science`?).  I have scrapped that in favor of wider usage of tags and the ability to toggle between an inclusive and exclusive filtering (`any` versus `all`).