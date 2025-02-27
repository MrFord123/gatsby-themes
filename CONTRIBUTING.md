# Contributing

Hi! I'm excited that you're interested in contributing to this project! Contributing should be enjoyable and productive for everyone, so please be kind to others and reach out if you have any questions or concerns (this project follows a [Code of Conduct](CODE_OF_CONDUCT.md)).

All contributions are welcome, including opening and commenting on issues and pull requests, adding or updating the docs, bug fixes, and suggestions for new features.

Changes to themes need to evaluated in more detail (e.g. if they would be breaking). The time to review a pull request depends on the complexity involved, so please be patient if a particular feature takes longer to review than others. Especially since this project is currently only maintained by me, LekoArts.

## Prerequisites

- [Node.js](http://nodejs.org/) >= v14 must be installed.
- [Yarn](https://yarnpkg.com/en/docs/install)

## Local Development

This repository uses [Yarn Workspaces][] and [changesets][] to develop multiple packages together as a monorepo. Be sure to install [Yarn][] before setting up the development environment.

Clone the repository:

```sh
git clone git@github.com:LekoArts/gatsby-themes.git
```

Install the dependencies:

```sh
yarn
```

After yarn has linked packages and installed the dependencies in the repo, you can inspect the locally available workspaces with:

```sh
yarn workspaces info
```

As all themes are set up with a respective example page (to view the theme/changes), you could for example run the "gatsby-theme-emilia" workspace with the example "emilia" like:

```sh
yarn workspace emilia develop
```

## Tests

### Vitest

Unit tests are run with [Vitest][], and are included where appropriate (mostly for utils/helper functions). Feel free to improve the code base with additional tests!

Running tests:

```sh
yarn test:ci
```

Running tests in watch mode:

```sh
yarn test:watch
```

### Cypress

Most of the themes' functionality is tested with [Cypress][] as it allows real-world testing which is most important for me when developing themes. The tests are written in TypeScript, too, and hence need to be compiled before usage. Run the following script for development:

```sh
bash ./scripts/e2e-dev.sh "example-name"
```

In the case of `examples/emma` the "example-name" would be "emma".

The script starts `tsc` in _watch_ mode (for the files in `cypress/e2e`) and outputs them to `cypress/e2e/build` + starts `start-server-and-test` with Gatsby's development server and Cypress. Once the Cypress GUI opens select the fitting test (the others won't work, only the respective test + `smoke.js`!).

GitHub Actions will run the `e2e-build.sh` script — you can use it to run the tests headless.

You can skip the e2e tests if you use `docs` or `www` in your branch name, e.g. `docs/improve-readme` or `www/add-new-entry`.

## Pull Requests

When opening a pull request, please be sure to update any relevant documentation in the READMEs or write some additional Vitest/Cypress tests to ensure functionality. Also include a high-level list of changes.

### Changesets

This repository uses [changesets][] to do versioning. What that means for contributors is that you need to add a changeset by running `yarn changeset` which contains what packages should be bumped, their associated semver bump types, and some markdown which will be inserted into changelogs.

[yarn]: https://yarnpkg.com
[yarn workspaces]: https://yarnpkg.com/en/docs/workspaces
[changesets]: https://github.com/changesets/changesets
[vitest]: https://vitest.dev/
[cypress]: https://cypress.io
