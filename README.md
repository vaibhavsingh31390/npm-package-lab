# npm-package-lab

A hands-on project for learning how to build, configure, publish, version, and use custom NPM packages.

The [greeting_package/](greeting_package/) directory is the example package built while working through these steps — see its [README](greeting_package/README.md) for package-specific usage and build details.

## Steps

1.  `npm init`
2.  `npm i --save-dev typescript`
3.  `npm i --save-dev rollup@latest @rollup/plugin-typescript@latest rollup-plugin-delete@latest`
4.  Add the following to `package.json`:
    ```json
    {
      "type": "module",
      "main": "lib/index.cjs",
      "exports": {
        "import": {
          "default": "./lib/index.esm.js",
          "types": "./lib/types/index.d.ts"
        },
        "require": {
          "import": {
            "default": "./lib/index.cjs",
            "types": "./lib/types/index.d.ts"
          }
        }
      },
      "scripts": {
        "build": "rollup -c"
      },
      "files": ["lib"]
    }
    ```
5.  `npm whoami` (to check if you're already logged in to the npm registry)
6.  `npm login` (to authenticate with your npm account, if not already logged in)
7.  `npm publish --dry-run` (to test what is going to be published)
8.  `npm version patch|minor|major` (to bump the package version before publishing)
9.  `npm publish` (to publish the package to the npm registry)
