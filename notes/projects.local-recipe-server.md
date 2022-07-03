---
id: ZG5dy128q8nTg2wptcunO
title: Local Recipe Server
desc: ''
updated: 1645905278846
created: 1642286111673
---

## Motivation
I love cooking and recipes.  Unfortunately I have amassed enough magazines and cookbooks that, when I want to make a particular recipe, I give up half way because finding it so laborious.  I realized I don't need hard copies, I need a searchable database with an appealing interface.  Also I've gathered more than a few Raspberry Pis and I wanted to do something cool with one (or more) of them.

Also a pet peeve of mine is how many recipe websites take up your entire phone/tablet sceen with banner adds, random stories only vaguely related to the recipe at hand, and overlapping vidoes you must carefull exit out of to avoid being redirected to some page about home loans, exciting new athletic socks, stock tips, etc.  I wanted to build an interface for viewing a recipe that was JUST THE RECIPE.

## Project Definition
The purpose of this project is to allow users to run a server on their local (home) wireless network that does 2 things related to recipes.

1. Take photographs of recipes in cookbooks or magazines and save them to the server
1. View recipes broken down by ingredients and steps in a mobile friendly interface

## [[projects.local-recipe-server.user-interfaces]]

The user interacts with this application through two distinct interfaces with separate areas of concern.

* Photo upload interface [Create Recipe]
* Recipe search/view interface [List/Retrieve Recipe]

## [[projects.local-recipe-server.data-models]]

A rough sketch of the data structures we will use to provide data persistence and all those nifty searching and filtering mechanisms.

## [[projects.local-recipe-server.services]]
These are encapsulated pieces of business logic that perform the tricky custom bits of the application.

## [[projects.local-recipe-server.api]]
The endpoints provided by the server and consumed by the client application to provide the user with CRUD capabilities for recipes.

## Potential Pi Architecture
This will depend on the processing power and storage needs of all the above requirements.  Given the above definitions are already biting off a fair amount of development work I will likely try to keep this to a single Raspberry Pi 4B.  I'll use a 128GB flash drive for storage so that _should_ provide the capacity to store a decent amount of recipes.  While I will likely be using Docker containers to build this application (2 minimum - Client App Server, API Server), I will start with all of them running on a single Pi.  If this proves too much work I will consider tackling the whole distributed k8s mess but for now I'll try to keep it simple. 

With simplicity in mind I plan to stick to just using the SQLite database.  It functions perfectly well with solid performance when accessed by a single process.  Since this application is desinged for a single user making sequential requests, this should be sufficient.

## STRETCH Goal
This project will begin using a basic modern web site architecture using a REST API and a Vue.js front-end (my preferred framework).  This should allow for the development of an Android App that communicates with the REST API.  It's an area of development I have absolutely no experience in but it might be fun to try.
