<h1> Symlink Manager</h1>

Symlink Manager easily manage to symbolic link processes of your dependency packages.

<img src="https://i.ibb.co/tDFxKZc/Screen-Shot-2019-07-07-at-23-25-16.png" height="auto" width="70%" />

## Installation & Usage

```bash
yarn add symlink-manager --dev

# or if you are using npm

npm install symlink-manager --save-dev
```

Insert the following line in scripts of your package.json file.

```js
  // ...
  "scripts": {
    "symlink": "symlink",
    // ...
  },
```

Symlink-manager will help you for direction.

```bash
yarn symlink

# or if you are using npm

npm run symlink
```

Symlink-manager supports Angular. (Only supoorts created with "ng generate lib" libraries).

```bash
yarn symlink --angular
```

Symlink-manager supports Yarn.

```bash
yarn symlink --yarn
```

If you are not using Angular, you must add symlink.config.json for your configuration.

symlink.config.json example:

```js
{
  "yarn": true,
  "packages": [
    {
      // required
      // your main dependency folder path. The folder must have package.json.
      "libraryFolderPath": "packages/core",
      // required
      // this folder for symbolic link. You may enter the same value as libraryFolderPath.
      "linkFolderPath": "dist/core",
      // optional
      // your build command.
      "buildCommand": "ng build core",
      // optional
      // output -> cd packages/core && ng build core
      "buildCommandRunPath": "packages/core"
    }
  ]
}
```

For more:
<br>
<a href="https://github.com/mehmet-erim/symlink-manager/tree/master/examples/angular">See the Angular example project and document</a>

## Without symlink-manager for Angular

- After 6th step (<a href="https://github.com/mehmet-erim/symlink-manager/tree/master/examples/angular">Check the 6 steps</a>), run `ng build core --watch`
- Open new terminal window and go dist/core (`cd dist/core`)
- Run `npm link`
- Go back to main folder (`cd ../../)
- Run `npm link @symlink/core``

Repeat it for every package.

Do not forget, symlink-manager do this automatically. Symlink-manager can create symbolic link a lot of packages in one terminal window
