# O projeto foi criado seguindo os seguintes passos

- [O projeto foi criado seguindo os seguintes passos](#o-projeto-foi-criado-seguindo-os-seguintes-passos)
  - [Criacao do projeto](#criacao-do-projeto)
  - [Setup do Eslint e Prettier](#setup-do-eslint-e-prettier)
    - [Instalando Eslint](#instalando-eslint)
    - [Instalando Prettier](#instalando-prettier)
    - [Configurando .eslintrc.json e .prettierrc.json](#configurando-eslintrcjson-e-prettierrcjson)
    - [Configurando vscode](#configurando-vscode)

## Criacao do projeto

Init do projeto utilizando a CLI do `create react app` utilizando como base o template de typescript

```sh
# npx create-react-app <project_name> --template typescript
```

## Setup do Eslint e Prettier

### Instalando Eslint

Instalando Eslint como dependência de desenvolvimento

```sh
# yarn add eslint @eslint/create-config -D
```

Inicializando as configurações do eslint

```sh
# yarn eslint --init
```

Ao executar o comando ele irá fazer algums perguntas, responda na seguinte ordem:

```
> To check syntax, find problems, and enforce code style
> JavaScript modules (import/export)
> React
> Yes
> Browser
> Use a popular style guide
> Airbnb: https://github.com/airbnb/javascrip
> JSON
> Yes
```

Instalando dependências para ajustar imports:

```sh
yarn add eslint-plugin-import @typescript-eslint/parser eslint-import-resolver-typescript -D
```

### Instalando Prettier

```sh
# yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
```

### Configurando .eslintrc.json e .prettierrc.json

No arquivo `.eslintrc.json` adicione o seguinte conteúdo:

```json
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": [
    "plugin:react/recommended",
    "airbnb",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "plugins": ["react", "react-hooks", "@typescript-eslint", "prettier"],
  "rules": {
    "prettier/prettier": "error",
    "import/no-unresolved": "error",
    "react/jsx-filename-extension": "off",
    "import/extensions": "off",
    "import/prefer-default-export": "off"
  },
  "settings": {
    "import/resolver": {
      "typescript": {}
    }
  }
}
```

Crie um arquivo `.prettierrc.json` com o seguinte conteúdo:

```json
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
```

### Configurando vscode

Na raiz do projeto cria o seguinte arquivo `.vscode/settings.json` com o seguinte conteúdo:

```json
{
  "eslint.alwaysShowStatus": true,
  "editor.formatOnSave": true,
  // turn it off for JS and JSX, we will do this via eslint
  "[javascript, javascriptreact]": {
    "editor.formatOnSave": false
  },
  // tell the ESLint plugin to run on save
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  },
  // Defining default formatter for json files
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

Não se esqueça de instalar as extensoes do `Prettier` e do `Eslint` no seu vscode.

Criando arquivo `.eslintignore` e `.prettierignore` com o seguinte conteúdo:

```
node_modules
public
```