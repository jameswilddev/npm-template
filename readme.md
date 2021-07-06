# npm-template [![Continuous Integration](https://github.com/npm-template/workflows/Continuous%20Integration/badge.svg)](https://github.com/npm-template/actions) [![License](https://img.shields.io/github/license/npm-template.svg)](https://github.com/npm-template/blob/master/license) [![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com/)

A template repository for a publicly published NPM package written in TypeScript with linting, unit tests (including coverage) and publishing from a GitHub Action.

## Creating a repository from this template repository

After clicking "Use this template" on this repository, there are some steps you need to take to make it your own.

First, search for and replace all references to `npm-template`.  Update the description in [package.json](./package.json).

Then, ensure that you have a `NPM_TOKEN` GitHub secret configured with automation access to the package to be published.

## Dependency updates

Renovate is configured to automatically merge updates to NPM dependencies once CI passes; this should be safe given that by default, 100% test coverage is required.

Renovate will not be able to detect changes to this template repository, however.  To apply updates, you must do (first time):

```sh
git remote add template https://github.com/npm-template
```

Then, every subsequent time:

```sh
git fetch template
git merge template/origin
git push
```

## Developing

After cloning, run `npm install` to install dependencies.  Run `npm test` to run ESLint, compile TypeScript and run tests.  This can be started from Visual Studio Code by pressing (cmd/ctrl) + shift + B.

The expected file structure is that all code will be grouped into a directory per module, with an `index.ts` or `index.tsx` file containing the implementation, and a `unit.ts` or `unit.tsx` file containing tests.  It is recommended to import from the root `index.ts` or `index.tsx` file as this will result in full coverage.

## Publishing

Create a GitHub release, and the GitHub Action will automatically publish to NPM using the GitHub release's tag name as the NPM package's version.
