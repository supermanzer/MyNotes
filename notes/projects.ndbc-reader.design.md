---
id: bvip3z5lby4gsw8f7wmru81
title: Design
desc: ''
updated: 1663434506822
created: 1662326984420
---
_Capturing ongoing notes regarding software architecture and design of the NDBC Python package_

---
To assist in defining the design I wish to achieve, I will be following the book [Architecture Patterns with Python](https://www.oreilly.com/library/view/architecture-patterns-with/9781492052197/).  I will skip that parts I do not feel apply but this is the reference I will be using to sketch out the design of this package in terms of commonly used design patterns and software architecture.

I had worked through this book a little earlier but I always find it hard to attach meaning, and therefore retain knowledge, when the project being worked on isn't something I care about.  For this effort I will be working through the chapters in the book and applying those aspects that I think pertain to the design of the NDBC package.

**No functionality should change as a result of this refactor**

Ideally this approach will instead make maintenance easier and make it more plain where modifications need to be made to provide the additional functionalities I have planned for this package.