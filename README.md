### Start git

> git init

### Create file .gitignore with content

    node_modules
    coverage
    dist

### Start npm

> npm init -y

### Add nodemon

> yarn add -D nodemon

### Add typescript

> npm install --global yarn

> yarn add -D typescript @types/node

> yarn add -D ts-node

### Start typescript

> tsc --init

**if you have problems with bash: tsc command not found**

> npm install typescript -g

> tsc --init

in the tsconfig.json file add

    {
      "compilerOptions": {
        "target": "es2016" /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */,
        "module": "commonjs" /* Specify what module code is generated. */,
        "rootDir": "src",
        "outDir": "./dist" /* Specify the root folder within your source files. */,
        "moduleResolution": "node" /* Specify how TypeScript looks up a file from a given module specifier. */,
        "forceConsistentCasingInFileNames": true /* Ensure that casing is correct in imports. */,
        "strict": true /* Enable all strict type-checking options. */,
        "skipLibCheck": true /* Skip type checking all .d.ts files. */,
        "paths": {
          "@/*": ["*"]
        },
        "baseUrl": "src"
      }
    }

### Add Prettier and Eslint

> yarn add -D prettier eslint

### Start Eslint

> npx eslint --init

      Options
      To check syntax and find problems
      JavaScript modules (import/export)
      None of these
      Does your project use TypeScript? Yes
      Where does your code run? Node (notice: space to choose)
      What format do you want your config file to be in? JSON
      Would you like to install then now? Yes
      Which package manage do you want to use? yarn

**in the .eslintrc.json add**

      inside env
      "jest": true
      inside parseOptions
      "project": ["./tsconfig.json"]

### Install Extensions EsLint amd Prettier

**Config**

- _Choose Editor:Format On Save and Default Formatter (Select Pretter -Code formatter)_ \*

### To avoid conflicts between EsLint and Prettier install

> yarn add -D eslint-config-prettier

**inside .eslintrc.json change tha line**
  
 "extends": [
"eslint:recommended",
"plugin:@typescript-eslint/recommended",
"prettier"
]

**Add package.json files**

    "build": "tsc",
    "husky:prepare": "husky install",
    "start:dev": "nodemon --watch 'src/' --exec 'ts-node src/index.ts' -e ts",
    "test": "jest --passWithNoTests",
    "test:watch": "yarn test --watch",
    "test:staged": "yarn test --findRelatedTests",
    "test:push": "yarn test --coverage"

### Install Husky

> yarn add -D husky lint-staged

> yarn husky:prepare
> **Config add file .lintstagedrc.json**

    {
      "\*.ts": [
      "yarn eslint 'src/**' --fix",
      "yarn prettier --check 'src/**'",
      " yarn prettier --write .",
      "yarn test:staged"
      ]
    }

**Add config**

> npx husky add .husky/pre-commit "yarn lint-staged"

> npx husky add .husky/pre-puch "yarn test:push"

> npx husky add .husky/commit-msg ".git/hooks/commit-msg \$1"

###Install Jest

> yarn add -D jest @types/jest ts-jest

### Install Express

> yarn add express
> yarn add -D @types/express

### Install

> yarn add -D git-commit-msg-linter
> npx husky add .husky/commit-msg ".git/hooks/commit-msg \$1"
