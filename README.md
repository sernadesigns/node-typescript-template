# Node Typescript Template

This template is meant to help you get started with a basic node application with a typescript compiler.

## Template Creation Steps

Under the hood. These were the steps taken to create this template.

_1. Install dependencies globally_

```
yarn global add node typescript
```

_2. Generate package.json file_

`-y` will skip the questions that npm will prompt in the `package.json` setup. If you would like more control of your setup, omit this flag.

```
npm init -y
```

_3. Install devDependencies_

- **nodemon** - A tool for developing `node.js` applications for automatically restarting the application when file changes are detected
- **concurrently** - A tool allowing multiple commands to be run concurrently

```
yarn add --dev nodemon concurrently
```

_4. Generate tsconfig.json file_

Will generate a `tsconfig.json` file.

```
tsc --init
```

_5. Generate folder structure_

- **src** - Directory to contain all source files of the application
- **build** - Directory to output compiled files from the `typescript compiler`

```
mkdir src build
```

_6. Update tsconfig.json_

Informs `typescript` of the root directory and output directory locations.

```diff
{
  "compilerOptions": {
    ...
    // "outFile": "./",
-   // "outDir": "./",
+   "outDir": "./build",
-   // "rootDir": "./",
+   "rootDir": "./src",
    // "composite": true,
    ...
  }
}
```

_7. Configure scripts in package.json_

- **start:build** - Start up the `typescript` compiler and watch input files
- **start:run** - Start up node server and run `build/index.js` file
- **start** - Run `start:build` and `start:run` scripts concurrently

```js
// package.json
scripts: {
  "start:build": "tsc -w",
  "start:run": "nodemon build/index.js",
  "start": "concurrently npm:start:*",
}
```
