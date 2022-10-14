# @dsa-ui

This is a design system built with [Stencil](https://stenciljs.com/), [Tailwind](https://tailwindcss.com/), and [Storybook](https://tailwindcss.com/) for Democratic Socialists of America sites and applications by the DSA National Tech Committee.

## Getting Started

### Quick Tour

This repo currently has two sibling repositories, `./react` and `./wc`.

Each corresponds to a published package: `@dsa-ui/react` for native React components and `@dsa-ui/wc` for web components that can be used in any other framework (or no framework).

>#### `./.vs-code`

Contains some settings and extension suggestions helpful for working with this toolset. Feel free to add other tweaks or disregard them if they do not suit your needs.

>#### `./react`

This is a __generated__ native React library. __You should not work in this package or change any files__ unless you are making adjustments to the `package.json` or other non-generated file for publishing purposes.
Any changes to the components should be made in `./wc`.

>#### `./wc`

_This is where the magic happens._ Development, testing, stories, and publishing are controlled from this directory.

>>#### `/src`

Generated types and a static site for development. These can be ignored.

>>>#### `/components`

Each component has its own directory. Each contains a `.tsx` file that contains the component itself as well as tests and stylesheets (which can be ignored in favor of tailwind).

>>#### `/stories`

Story files, which can be simple like `my-component.stories.tsx` (which takes advantage of auto-generation) or complex. Each file can hold multiple stories with different arguments and arrangements to test and doc different states.

### Start Development

```bash
npm run init
npm start
```

>- Starts a build of web components, watches for changes
>- Builds a custom elements manifest that helps Storybook generate helpful docs
>- Starts a Storybook server on `http://localhost:6006`
>
_Note: The cem mapping complexity can be removed if we move Storybook to the React project. However, that would require rebuilding the React project on every change, which would add latency to the hot reload._

### Build For Production

```bash
npm run build
```

>Builds web components and syncs the React library.

### Run Tests

```bash
npm test
```

## Naming Components

Use the prefix `dsa`, i.e., `dsa-button` or `dsa-card`.

## Using these components

First of all, [publish to NPM](https://docs.npmjs.com/getting-started/publishing-npm-packages).

### Script tag

- Put a script tag similar to this `<script type='module' src='https://unpkg.com/@dsa-ui/wc@0.0.1/dist/my-component.esm.js'></script>` in the head of your `index.html`
- Then you can use the library anywhere in your template, JSX, html etc

### Node Modules

- Run `npm i @dsa-ui/wc`
or
`npm i @dsa-ui/react`
- Put a script tag similar to this `<script type='module' src='node_modules/@dsa-ui/wc/dist/my-component.esm.js'></script>` in the head of your index.html
- OR, add an import statement within the root component of your application

```ts
import { defineCustomElements } from '@dsa-ui/wc';
defineCustomElements();
```

- OR, add an import for any individual component

```ts
import { HelloWorld } from 'my-library/dist/components/hello-world';
customElements.define('hello-world', HelloWorld);
```

- Then you can use the element anywhere in your template, JSX, html etc

### More strategies and use cases can be found within the Stencil docs

![Built With Stencil](https://img.shields.io/badge/-Built%20With%20Stencil-16161d.svg?logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDE5LjIuMSwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MTIgNTEyOyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI%2BCjxzdHlsZSB0eXBlPSJ0ZXh0L2NzcyI%2BCgkuc3Qwe2ZpbGw6I0ZGRkZGRjt9Cjwvc3R5bGU%2BCjxwYXRoIGNsYXNzPSJzdDAiIGQ9Ik00MjQuNywzNzMuOWMwLDM3LjYtNTUuMSw2OC42LTkyLjcsNjguNkgxODAuNGMtMzcuOSwwLTkyLjctMzAuNy05Mi43LTY4LjZ2LTMuNmgzMzYuOVYzNzMuOXoiLz4KPHBhdGggY2xhc3M9InN0MCIgZD0iTTQyNC43LDI5Mi4xSDE4MC40Yy0zNy42LDAtOTIuNy0zMS05Mi43LTY4LjZ2LTMuNkgzMzJjMzcuNiwwLDkyLjcsMzEsOTIuNyw2OC42VjI5Mi4xeiIvPgo8cGF0aCBjbGFzcz0ic3QwIiBkPSJNNDI0LjcsMTQxLjdIODcuN3YtMy42YzAtMzcuNiw1NC44LTY4LjYsOTIuNy02OC42SDMzMmMzNy45LDAsOTIuNywzMC43LDkyLjcsNjguNlYxNDEuN3oiLz4KPC9zdmc%2BCg%3D%3D&colorA=16161d&style=flat-square)
