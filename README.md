# Turborepo Bun Example

This example init from the basic Next turborepo example: https://github.com/vercel/turbo/tree/main/examples/basic

Instead of `npx create-turbo@latest` I used `bunx create-turbo@latest` to init the repo.
While that worked fine, turborepo doesn't seem to support bun yet really (it only allows pnpm, yarn, or npm).

All I've done is swap out pnpm for bun and added the minimum necessary bun config. See the commits for details.

## What's Working

1. `bun install` appears to be fine

## What's Not Working

1. Running `bun run` from anywhere but the root fails, even with something simple: `bun eslint --version`
2. Any TurboRepo command fails without a `packageManager` specified in `package.json` (seems like bun isn't really supported yet)

## Reproduction Steps

1. `bun install`
2. `bun run eslint --version` (from root succeeds)
3. `cd packages/ui` (or any other package)
4. `bun run eslint --version` (fails)

You can try this with any script. For example, I added a simple `clean` script that just rm's node_modules. It works from the root, but not from any package.

Haven't tried much beyond that yet, but will report back as I do.

## Below is the default turbostarter readme

(Note it might not accurately reflect, I just left it for reference)

----

This is an official starter Turborepo.

## Using this example

Run the following command:

```sh
npx create-turbo@latest
```

## What's inside?

This Turborepo includes the following packages/apps:

### Apps and Packages

- `docs`: a [Next.js](https://nextjs.org/) app
- `web`: another [Next.js](https://nextjs.org/) app
- `ui`: a stub React component library shared by both `web` and `docs` applications
- `eslint-config-custom`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `tsconfig`: `tsconfig.json`s used throughout the monorepo

Each package/app is 100% [TypeScript](https://www.typescriptlang.org/).

### Utilities

This Turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting

### Build

To build all apps and packages, run the following command:

```
cd my-turborepo
pnpm build
```

### Develop

To develop all apps and packages, run the following command:

```
cd my-turborepo
pnpm dev
```

### Remote Caching

Turborepo can use a technique known as [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup), then enter the following commands:

```
cd my-turborepo
npx turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

```
npx turbo link
```

## Useful Links

Learn more about the power of Turborepo:

- [Tasks](https://turbo.build/repo/docs/core-concepts/monorepos/running-tasks)
- [Caching](https://turbo.build/repo/docs/core-concepts/caching)
- [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching)
- [Filtering](https://turbo.build/repo/docs/core-concepts/monorepos/filtering)
- [Configuration Options](https://turbo.build/repo/docs/reference/configuration)
- [CLI Usage](https://turbo.build/repo/docs/reference/command-line-reference)
