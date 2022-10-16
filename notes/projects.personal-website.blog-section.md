---
id: oyqp1vd5331bbhw5x1ndkxj
title: Blog Section
desc: ''
updated: 1665951264802
created: 1665948629348
---
_Notes on the design and functionality of the blog portion of my personal site_

---

## Home Page
I think for this section it would make the most sense to display a list view of articles sorted chronologically (most recent first) on the left and a menu of topics and tags on the right.

### List View Component
This should be a reusable component that displays title, date created/updated, and a brief description of the article.

### Nav Sidebar
I am thinking that I will use the top level directors (within the `blog` directory) to define general categories of blog post.  These will be represented by an accordion menu. Clicking the category name text will filter the list menu on the right.  However there is a dropdown carat icon that will expand the accordion and show a list of blog post titles (sorted in reverse chronological order).  Clicking an individual title should take the user to a detail view for that article.

One aspect I'm a little undecided about is whether to retain the sidebar when showing the detail section.  It would reduce the available space and add distraction.  However it would allow faster navigation from one article to another.  A third option from either full display or no menu is to either use a [popover sidenav](https://vuetifyjs.com/en/components/navigation-drawers/#bottom-drawer). This might interfere with the sidenav component in `default` layout.  In that case I could try using a [minified design](https://vuetifyjs.com/en/components/navigation-drawers/#expand-on-hover) with `expand_on_hover`.