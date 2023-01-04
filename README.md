# Single SPA with Capacitor
This is an example of using multiple Angular applications of different versions combined into a single Capacitor application.

> Note: This example is based on one by Joel Denning from the Single SPA samples [here](https://single-spa.js.org/docs/examples).

## About this Repo
There are several folders:
- **app1** - This contains an Angular 11 application
- **app2** - This contains an Angular 9 application
- **navbar** - This contains an Angular application which provides the navigation between the 2 apps
- **root-html-file** - This contains the single spa index.html which combines it all together for development
- **cap-app** - This has a capacitor application and a Single SPA index.html. The folder `dist` is a copy of built assets of `app1`, `app2` and `navbar`.

The Capacitor Application is a shell containing `index.html` which specifies the import map for each of the apps. Note that it uses an import map with path `localhost/app1` as `localhost` is the path where capacitor serves the local assets.

## Run the Capacitor App
Using Node 16, run the following to install, build all apps and copy into a Capacitor application:
```sh
cd cap-app
npm run prepare
npx cap run ios
```

## About Single SPA
[Single SPA](https://single-spa.js.org/) is a framework for building Microfrontends. At its core, it is simply using [Import Maps](https://caniuse.com/import-maps) which is a Javascript API allowing the use of `import` to import ES modules in the browser. On top of this Single SPA provides additional features that a single web app that will combine Microfrontends will need.

## Local development
It is preferred to only run one app at a time. But if you need to run them all locally, you can do so with the following instructions

```sh
# First terminal tab
cd root-html-file
npm install
npm start
```
```sh
# Second terminal tab
cd app1
npm install
npm start
```

```sh
# Third terminal tab
cd app2
npm install
npm start
```

```sh
# Fourth terminal tab
cd navbar
npm install
npm start
```

Now go to http://localhost:4200 in a browser. Note that you can change any of the ports for the projects by modifying the Import Map inside of `root-html-file/index.html`.

