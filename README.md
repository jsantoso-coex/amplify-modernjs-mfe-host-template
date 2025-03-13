# Overview
This template was created using a combination of Modern.js and AWS Amplify Gen 2
Steps taken to create this template:
1. Create a new Modern.js app
```bash
npx @modern-js/create amplify-modernjs-mfe-host-template
```

2. Add Amplify Gen 2 in the project
```bash
pnpm create amplify@latest
```

3. Modern.js came with Git hook that runs linting and auto formatting when the changes are staged. Amplify generated resources.ts that cause issues with linting, hence I have to remove the Git hook.

4. Run
```bash
pnpm uninstall simple-git-hooks lint-staged
```
5. Remove these lines from package.json
```
"lint-staged": {
    "*.{js,ts,cjs,mjs,d.cts,d.mts,jsx,tsx,json,jsonc}": [
      "biome check --files-ignore-unknown=true"
    ]
  },
  "simple-git-hooks": {
    "pre-commit": "npx lint-staged"
  },
```
6. `./.git/hooks/precommit` file didn't get deleted after uninstalling `simple-git-hooks`, so I had to delete the file manually.

7. Test Modern.js is still running
```bash
pnpm run dev
```

8. Login to AWS if you haven't.
```bash
aws sso login
```

Deploy the template to AWS Amplify Sandbox.
```bash
npx ampx sandbox
```

9. To delete the Sandbox, run
```bash
npx ampx sandbox delete
```


## Setup

Install the dependencies:

```bash
pnpm install
```

## Get Started

Start the dev server:

```bash
pnpm dev
```

Enable optional features or add a new entry:

```bash
pnpm new
```

Build the app for production:

```bash
pnpm build
```

Preview the production build locally:

```bash
pnpm serve
```

For more information, see the [Modern.js documentation](https://modernjs.dev/en).
