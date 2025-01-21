## Comando para criar uma nova API "express, typescript, jest, eslint, prettier husk ling-staged"

- Crie um pasta, e inicialize os comando abaixo
- Atualização 01/2025

```bash
npm init -y
```
```bash
npm install express @prisma/client dotenv cors express-async-errors zod
```
```bash
npm install @prisma/client typescript ts-node-dev eslint prettier jest @types/node @types/express ts-jest @typescript-eslint/parser @typescript-eslint/eslint-plugin husky lint-staged --save-dev
```

 - Adicione o TypeScript
```bash
touch tsconfig.json
```

```bash
{
  "compilerOptions": {
    "target": "ES2017",
    "module": "CommonJS",
    "strict": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist",
    "rootDir": "./src",
    "skipLibCheck": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

* Configure o Eslint
```bash
touch .eslint.json .eslintrcignore
``` 
```bash
{
  "env": {
    "node": true,
    "es2021": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": 12,
    "sourceType": "module"
  },
  "plugins": ["@typescript-eslint"],
  "rules": {}
}
```

* Configure o Prettier
```bash
touch .prettier.json .eslintrcignore
``` 
```bash
{
  "semi": false,
  "singleQuote": true,
  "trailingComma": "es5",
  "printWidth": 80
}
``` 

* Configure o jest para rodar com typescript

```bash
npx ts-jest config:init
```
```bash
/** @type {import('ts-jest').JestConfigWithTsJest} */
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  modulePathIgnorePatterns: ['dist'],
};
```

```bash
npx husky-init && npm install
```
```bash
npm set-script prepare "husky install"
```
```bash
npm install -D lint-staged
```
```bash
npx husky add .husky/pre-commit "npx lint-staged"
```

* Atualizar o package.json

```bash
"lint-staged": {
  "**/*.{ts,js}": [
    "eslint --fix",
    "prettier --write"
  ]
}
"scripts": {
  "dev": "ts-node-dev --respawn --transpile-only src/index.ts",
  "build": "tsc",
  "start": "node dist/index.js",
  "lint": "eslint . --ext .ts",
  "test": "jest",
  "format": "prettier --write ."
}
```
* Configure o prisma
```bash
npx prisma init
```

## Comando para remover as imagens ##
docker image rm -f <nome_da_imagem>

## Comando para criar nova imagens ##
docker build --no-cache -t <nome_da_imagem> -f ./Dockerfile .

Para implementar isso ao docker compose 'services'

```
services:
  <app>:
    container_name: <container_name>
    image: <image>
```


## Como criar um pequeno projeto Vite, React, React Native, Expo Eslint e Prettier

Para os primeiros passos, verificar ou instalar node npm ou yarn

Feito isso:

```bash
yarn create vite
```

```bash
expo init
```

> Selecione as opções a desejar...

Instalações de ferramentas de padronização e ajuste de código

> Instalar EditorConfig for VsCode

```bash
yarn add -D eslint && yarn eslint --init
``` 

> Selecione as opções a desejar...

- Para yarn, não instalar os pacotes adicionais, mas sim, selecionar os pacotes gerado, e rodar com yarn add -D 
- Seguir os comandos abaixo


```bash
yarn add -D eslint-plugin-react eslint-plugin-react-hooks
``` 

Instalar o prettier

```bash
yarn add -D prettier eslint-plugin-prettier eslint-config-prettier
``` 

Crie .prettierrc.json

```bash
{
  "semi": true,
  "trailingComma": "all",
  "singleQuote": false,
  "printWidth": 80,
  "arrowParens": "avoid"
}
```

Editar o arquivo .eslintrc.json da raiz

```bash
"settings": {
  "react": {
    "version": "detect"
  }
}
```

```bash
"extends": [
  "eslint:recommended",
  "plugin:react/recommended",
  "plugin:@typescript-eslint/recommended",
  "plugin:react-hooks/recommended",
  "plugin:prettier/recommended"
]
```

```bash
"rules": {
  "react/props-types": "off",
  "react/react-in-jsx-scope": "off",
  "@typescript-eslint/explicit-module-boundary-types": "off"
}
```

```bash
"plugins": [
  "react",
  "@typescript-eslint",
  "prettier"
],
```

Crie .eslintignore e .prettierignore

```bash
touch .eslintignore && tocuh .prettierignore
```

```bash
node_modules
dist
build
# outros
android
ios
.expo
.vscode
```

## Como criar um pequeno projeto API com NodeJs

Adicionar eslint para api com nodejs 

Use a mesma ação de comando acima para adicionar o Eslint

Adicionar typescript

```bash
npm install typescript ts-node @types/node -D
```

Crie touch tsconfig.json na raiz do projeto e adicione

```bash
touch tsconfig.json
```

```bash
{
  "compilerOptions": {
    "sourceMap": true,
    "outDir": "dist",
    "strict": true,
    "lib": ["esnext"],
    "esModuleInterop": true
  }
}
```

## Adicionar essas configurações após o comando do ESLint acima

```bash
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "rules": {
    "no-console": "warn"
  }
}

```

Crie as settings do .vscode/settings.json

```bash
touch .vscode/settings.json
```

```bash
{
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true 
  }
}
```
