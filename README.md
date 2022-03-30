# jslibdevkit

A little tool I built to help manage my JavaScript (TypeScript) library projects in multiple repos in a convention-based way, ironically written in Ruby.

## What it does

It provides a command `dk setup` that I can run in a new (blank) folder or an existing project.

When run in a blank directory, it sets up a TypeScript project. Once the command is finished I can edit `src/index.ts` and begin building my library.

When run in an existing project, it performs an **automated maintenance** of that project. See these PRs for examples of automated maintenance in action:

- https://github.com/dtinth/ui-stock/pull/2
- https://github.com/dtinth/bsearch/pull/2
- https://github.com/dtinth/sync-external-store/pull/1
- https://github.com/dtinth/google-sign-in-controller/pull/1
- https://github.com/dtinth/chain/pull/1
- https://github.com/dtinth/ride/pull/1

Maintenance tasks (these are all idempotent):

- **It ensures that the project uses `pnpm` as the dependency management tool.**
  - `yarn.lock` and `package-lock.json` files are removed.
- **It creates/updates `package.json` file.**
  - Tools for building/testing/linting a TypeScript project (heft & api-extractor) are added to `devDependencies`.
  - Tools that are superseded by another tool are removed.
  - It also sets up `build` `test` `prepare` `format` `api` scripts.
  - It also sets up `files` `main` `module` `types` `docModel` fields so that the package has proper TypeScript support.
- **It sets up TypeScript.**
  - A `tsconfig.json` is set up (customizable) to be based on `tsconfig-base.json`.
- **It sets up a release process.**
  - GitHub Action workflow files are created to publish packages to npm registry automatically.
