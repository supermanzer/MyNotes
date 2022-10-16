---
id: duen0yrxw82q24wdr2wkiau
title: Style Issues
desc: ''
updated: 1665251935581
created: 1665250142487
---

_Thoughts, questions, and difficulties experienced when it comes to styling my site in a cohesive manner_

---

## Dark/Light Mode

I now have a configured a `DarkMode` switcher that hooks into the global `$vuetify.theme.isDark` property.  This allows me to toggle Dark mode on/off.  However there are some scenarios that I am running into where working with a global `dark: true|false` is proving difficult.

### Nav Headers
While the general light/dark mode makes sense in most situations, on pages where I have large hero images with a darkening gradient overlay I will need a way to enforce `dark: true` without actually changing this setting.  CHanging the setting would require a user to reset this value every time they navigate to a page that requires dark mode and then to another page. 

After typing this it becomes clear that the best option here would be to use a `darkMode` prop for the `NavHeader` component that defaults to `false`.  Then I would create a computed property that determines the styling applied to all text in the NavBar by the following formula: 
```
  this.darkMode || this.$vuetify.theme.isDark
```

Then, when loading any page that uses a `layout` that requires specific styling regardless of the selected theme mode, I can simply pass the prop of `:darkMode="true"`.

### Custom Content

At earlier stages of development I wrote style rules directly on various components.  While this makes it easier for me to rapidly adjust styling and get a feel for how different styles look, if left in place it makes changing overall styles a huge [PITA](https://www.netlingo.com/word/pita.php#:~:text=Pain%20In%20The%20Ass,jargon%20or%20text%20message%20shorthand). So now, as the stylistic focus of my site shifts to defining cohesive global styles, my focus will be on those components with hard-coded styles and how I can use Vue's [Class and Style Bindings](https://vuejs.org/guide/essentials/class-and-style.html) to achieve some component specific styles while still adhering to a global style approach that is responsive to a user's selection of Light or Dark mode.