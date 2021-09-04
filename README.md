# vue3-husky

### First you need to install husky

```sh
npm install husky --save-dev
```

### Then You need to install lint-stage

```sh
npm install lint-staged --save-dev
```

### ( Option ) install commit-lint

```sh
npm install @commitlint/cli @commitlint/config-conventional --save-dev
```

### ( Option ) install typescript-eslint

```sh
npm install @typescript-eslint/eslint-plugin @typescript-eslint/parser --save-dev
```

### ( Option ) install eslint

- vite

```sh
npm install eslint eslint-config-prettier eslint-define-config eslint-plugin-prettier eslint-plugin-vue --save-dev
```

- vue-cli

```sh
npm install eslint eslint-define-config  eslint-plugin-vue --save-dev
```

### ( Option ) install style-lint

```sh
npm install stylelint stylelint-config-prettier stylelint-config-standard stylelint-order --save-dev
```

### ( Option ) install prettier

```sh
npm install prettier pretty-quick --save-dev
```

### Write Package.json Script

- "is-ci" package is optional !!

```sh
npm install is-ci --save-dev
```

- prepare for husky command

```
"scripts": {
    ...
    "install:husky": "is-ci || husky install",
    "postinstall": "npm run install:husky"
},
```

- prepare for lint command ( All are optional except `"lint:lint-staged"`, which is required. )

```
"scripts": {
    ...
    "lint:eslint": "eslint \"{src,mock}/**/*.{vue,ts,tsx}\" --fix",
    "lint:prettier": "prettier --write --loglevel warn \"src/**/*.{js,json,tsx,css,less,scss,vue,html,md}\"",
    "lint:stylelint": "stylelint --fix \"**/*.{vue,less,postcss,css,scss}\" --cache --cache-location node_modules/.cache/stylelint/",
    "lint:lint-staged": "lint-staged -c ./.husky/lintstagedrc.js",
    "lint:pretty": "pretty-quick --staged",
},
```
