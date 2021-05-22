---
title: 'Why I prefer not to write vanilla JavaScript'
date: 2021-04-12T17:42:15+02:00
draft: true
comments: true
include_toc: true
TocOpen: false
---

OOP ([Object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming)) isn't well implemented these days in browsers.

-   Private class functions are missing ([Proposal for ECMAScript 2019](https://github.com/tc39/proposal-private-methods))
-   Interfaces are missing ([Proposal for ECMAScript 2019](https://github.com/tc39/proposal-first-class-protocols)) (see an example [here](https://docs.google.com/presentation/d/1HnxJl4Iodf3I23e-ZDkw4F1LEkMRGUBFq6xxR0a9a_k/edit#slide=id.g3e3a1a53c0_0_69))

TypeScript helps you out with that (throwing a transpiler error that the function could not be found).
