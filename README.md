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

## Comandos para criar e habilitar portas no window com wsl2 ##

Abra um terminal se sua preferência como administrador
Copie e cole os comando abaixo

Para listar as portas já habilitadas no netsh

```
netsh interface portproxy show v4tov4
```

Para adicionar uma nova porta

* listenport: porta a habilitar
* listenaddress: ip a habilitar, "ip da localhost"
* connectport: ip da ponte
* connectaddress: ip do wsl

```
netsh interface portproxy add v4tov4 listenport=<porta> listenaddress=0.0.0.0 connectport=<porta> connectaddress=<ip>
```

Para cria as portas desejada, rode o comando abaixo e adicione as portas desejadas

```
New-NetFirewallRule -DisplayName "WSL2 Port Bridge" -Direction Inbound -Action Allow -Protocol TCP -LocalPort <80,443,10000,3000,5000,19000...>
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

Adicionar essas configurações após o comando do ESLint acima

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
