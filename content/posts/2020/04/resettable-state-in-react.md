---
title: 'Resettable state in React'
date: 2020-04-22T00:00:00+02:00
draft: false
comments: true
include_toc: true
TocOpen: false
---

Hey everyone!

Finally a new blog post from me!

Yesterday someone on a Discord server I'm also in posted a link to this repository: https://github.com/shiftyp/object-hooks-test.

The repository contains a custom React hook with which you can reset your state to the initial state.

I have been using React now for about 1 - 1,5 years and I never thought about resetting the state to its initial state.

Quickly (in 7 minutes) I smashed together a custom react hook which exactly does this one thing... and I published it on NPM too!

You can find it here: https://www.npmjs.com/package/react-resettable-state

And also being an open source enthusiast I published the source code as well under the MIT license: https://github.com/YannickFricke/react-resettable-state.

(Publishing the code, setting up the GitHub Actions (for testing and releasing) took much longer than writing the hook LOL)

## What are the benefits of using this package?

Oh that's a good question! The Readme file in the repository contains two examples (right now).

The [first example](https://codesandbox.io/s/react-resettable-state-counter-example-knun5) is about a basic counter (yes we all know that kind of example).

The [second one](https://codesandbox.io/s/react-resettable-state-form-example-sk1dw) is about form data.

If you have another idea of new examples feel free to make a pull request! I would love to see more use cases.

## How do I use the package?

The readme file also includes a code example for JavaScript. If you are using TypeScript take a look at the examples (since they are written in TypeScript).

So far,

Yannick Fricke

PS: Stay healthy in these times! <3
