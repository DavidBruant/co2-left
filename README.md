# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte);

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm init svelte@next

# create a new project in my-app
npm init svelte@next my-app
```

> Note: the `@next` is temporary

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

Before creating a production version of your app, install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.

### Apprentissage en vrac

Objectif : 2560 GtCO2
Uniquement avec les émissions depuis 1750 : 1696 GtCO2

émissions + land use change depuis 1850 : 2431 GtCO2

émissions 1750 - 1850 : 5 GtCO2
land use change 1750 - 1850 (regression linéaire entre 1850 et 1900) : 101 GtCO2

2431 + 5 + 101 = 2537, close enough

Par 10 ans : 
- 396 (15%) pour 2011 - 2020
- 340 (13%) pour 2001 - 2010
- 286 (11%) pour 1991 - 2000

Par 20 ans :
- 737 (29%) pour 2001 - 2020
- 538 (21%) pour 1981 - 2000
- 395 (15%) pour 1961 - 1980
- 243 (9%) pour 1941 - 1960
- 173 (7%) pour 1921 - 1940