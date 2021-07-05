---
title: "Why I switched to hugo"
date: 2021-04-12T17:42:15+02:00
draft: false
comments: true
include_toc: true
TocOpen: false
categories: ["Hugo"]
---

# Background

## Starting with Next.js

Next.js is a neat time saver when you wanna do RAD ([Rapid Application Development](https://en.wikipedia.org/wiki/Rapid_application_development)).

You can [create new routes (pages)](https://nextjs.org/docs/basic-features/pages) by creating new files! Let me show you an example:

| Filename                    | Route        |
| :-------------------------- | :----------- |
| ./src/pages/home.tsx        | /home        |
| ./src/pages/login.tsx       | /login       |
| ./src/pages/user/create.tsx | /user/create |
| ./src/pages/user/[id].tsx   | /user/:id    |

> Note to the last route:
>
> `id` is a parameter that gets passed down to the React component

This is very nice when you quickly want to scaffold new routes (pages) and potentially new content for the pages.

### The first try: Next.js

> Having Next.js as wrapper should give me the possibility to create my new homepage very quickly.
>
> Me - in the past

ATTENTION:

You might not have the same issues as me with Next.js!

It was in the release days of Next.js version 9.3.0 where I tried out the brand new features called `getStaticPaths` and `getServerSideProps`.

They allow you to read the contents of a file or doing an API request before a static site is generated.
This is ideal for a small blog with some extra pages. I was able to generate a completely static website out of the source code.

But... I have to admit... there is a downside...

Unfortunately Next.js + Node + Frontmatter threw an OOM (Out-of-Memory) error!
So I was in charge of finding another technology that also supports React and TypeScript.

Nothing easier than that! At that point of time I set up a dozen React + TypeScript projects from scratch.

### Recap

Next.js is an awesome piece of software! Having the problem with the OOM errors threw me back! Built-in SSR ([Server-Side Rendering](https://en.wikipedia.org/wiki/Server-side_scripting)), custom routes + API routes and React components are a killer feature of Next.js which I wanted to use.

## Writing from scratch

So I started over and created a fresh directory and initialized the `package.json` file.

Doing some steps:

-   Installing the dependencies listed below
-   Creating the configuration files (tsconfig.json, webpack.config.js)
-   Setting up scripts (build, build:watch, dev)
-   Creating the source directory (./src)

Dependencies:

-   `react` for rendering
-   `react-dom` for using React.JS in a browser environment
-   `react-router-dom` for routing between pages and the blog posts
-   `slugify` for generating the blog post urls
-   `react-helmet` for manipulating tags inside the header tag
-   `webpack` for generating the website
-   `ts-loader` for loading TypeScript files into webpack
-   `scss-loader` for loading SCSS files into webpack
-   `@types/react` for React.JS TypeScript typings
-   `@types/react-dom` for react-dom TypeScript typings
-   `@types/react-router-dom` for react-router-dom TypeScript typings
-   `@types/node` for basic JavaScript types like Promises

And there we go - we added everything we need for bundling our TypeScript application.

> Nowadays I would rather recommend [Parcel](https://www.npmjs.com/package/parcel) than webpack - because Parcel follows the "Convention over Configuration" rule.
>
> That means that end users (developers, you?) can simply start the development server and parcel does the heavy work in the background (asset processing, type stripping, bundling, etc).

After the base is set up you only have to define the router + routes and the "static pages" (like homepage, imprint, projects) and you are done.

### Recap

React + TypeScript are an awesome match! Getting all the type checking stuff for variables, functions and classes ensures, that you won't call anything which is not defined.

The interfaces in TypeScript are also nice to use when it comes to defining data structures like this:

```typescript
interface User {
    id: number;
    username: string;
    password: string;
    email: string;
}
```

If your IDE supports the language server protocol (LSP) then you get auto-completion out of the box for all the stuff!

One of the good sides of TypeScript is, that's it doesn't allow you to get properties / calling functions on `nullable` properties.

But [nullish coalescing](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-7.html#nullish-coalescing) to the rescue! We can chain our calls and only need to join them with a question mark (?):

```typescript
interface User {
    id: number;
    username: string;
    password: string;
    // Email is now optional (nullable)
    email?: string;
}

const user: User = {
    id: 1,
    username: "Testuser",
    password: "Testpassword",
};

let upperCasedEmail = user.email?.toUpperCase();
console.assert(
    upperCasedEmail === undefined,
    "upperCasedEmail should be undefined"
);

upperCasedEmail = user.email?.toUpperCase() ?? "";
console.assert(
    upperCasedEmail === "",
    "upperCasedEmail should be an empty string"
);
```

Also while implementing everything from scratch (bundler, transpiler, etc.) has downsides:

-   It's not possible to get all defined routes from the react-router-dom package
    -   You can't generate a `sitemap.xml`
    -   You can't generate an RSS feed

Not having a sitemap nor an RSS feed had a due date: I needed to eliminate those downsides!

I wanted to be able to let Google and other search engines my homepage and I wanted to notify readers of this blog via RSS about new posts.

So I needed another solution in the foreseeable future... let's come to the new website!

# The new website

## Why I chose hugo

Hugo is a static site generator that works with Markdown files. The blog posts also use frontmatter to define metadata like title, publish date, draft status, are comments allowed (a theme setting), etc. Pages can be easily created by creating new Markdown files.

If I remember correctly... I wanted to use Markdown files with frontmatter... so this is kind of a throwback into the past!

I like the idea of writing Markdown for blog posts because of its ability to style the text and format source code.

Hugo also had all the missing requirements I mentioned in the section before and also includes some more features:

-   Using themes (a thing that I don't miss while creating my site from scratch)
-   Creating real static pages (not only one HTML page with a react-dom mount (no SSR + SSG))
-   Comments for pages (I could have implemented this also in the previous attempt)

Now the homepage has an RSS feed available [here](/index.xml) and the [sitemap](/sitemap.xml) is also generated automatically.

## Comments for blog posts

For the new comment section I use [utteranc.es](https://utteranc.es/).

It's a nice open-source service that uses GitHub issues to provide the comment functionality.

# Conclusion

Hugo is pretty nice when you have a homepage which content does not change frequently and should have a good SEO performance (due to static site generation).

But like everything - also Hugo has downsides: you cant generate pages based on data (JSON / YAML / TOML).

Single pages ([data templates](https://gohugo.io/templates/data-templates)) which display the data are not a problem, but you can't generate complete pages (pages with a title + metadata + content). That's something Gatsby can do for you.

I hope you like the new homepage as much as I do!

So far,

Yannick Fricke
