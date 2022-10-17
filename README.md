# Ignite Lab #3 - Do Figma ao React

![image](https://user-images.githubusercontent.com/12506432/195759740-3fd7e15d-afe7-4c8e-9e11-1767b2ac78bf.png)

Evento disponibilizado pela [RocketSeat](https://www.rocketseat.com.br/)

## Tema: Design System com Figma, React e StoryBook

<img alt="GitHub Contributors" src="https://img.shields.io/github/contributors/alissonif/ignite-lab-design-system"/>

Projeto desenvolvido durante a semana de 10/10/2022 a 13/11/2022, onde pude ter contato com várias ferramentas para a construção de um Design System como, Figma, React, StoryBook e TailwindCSS.

## A aplicação teve as seguintes etapas de construção

- Projeto no Figma
- Design System - Criação dos componentes
- Documentação no Storybook
- Deploy automatizado com GitHub Actions
- Criação do Front-End em Vite
- Implementação de testes com Jest no Storybook.

## Tecnologias e ferramentas utilizadas

- [React.JS (Vite)](https://vitejs.dev/)
- [TypeScript](https://www.typescriptlang.org/)
- [Radix UI](https://www.radix-ui.com/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Storybook](https://storybook.js.org/)
- [Addon A11y](https://www.npmjs.com/package/@storybook/addon-a11y)
- [Github Actions](https://github.com/features/actions)
- [Jest](https://jestjs.io/pt-BR/)
- [MSW](https://mswjs.io/)

Durante as aulas, pude conhecer como montar uma estrutura visual de um design system na prática com o Figma e como porta-lo para o código disponibilizando assim os dados para testes dos componentes via StoryBook,
deploy automatizado com GitHub Actions e simulação do Front-End em Vite.

![page](https://user-images.githubusercontent.com/113787415/196235116-7e2e0a6b-afff-4f7e-a105-edd5abc4b013.PNG)

</div>

---

## Projeto no Figma

[https://www.figma.com/file/2ws9TBu6IweT00RnFdCo6a/Ignite-Lab-Design-System?node-id=14%3A162](https://www.figma.com/file/2ws9TBu6IweT00RnFdCo6a/Ignite-Lab-Design-System?node-id=14%3A162)

Pagina de Login:

![image](https://user-images.githubusercontent.com/12506432/195759270-ae386b8b-4737-408b-9a74-f961af057651.png)

Estrutura dos Componentea gerados:

![image](https://user-images.githubusercontent.com/12506432/195759371-72ff7fff-39ac-46ae-896e-8a9059408f21.png)

## Configurando o Projeto

## Iniciando o repositório do Git

Aqui eu inicio o meu repositório no git

```bash
git init
```

## Iniciando a pasta do projeto

Iniciando o projeto com o NodeJS

```bash
npm init -y
```

## Configuração inicial do .gitignore

```.gitignore
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

node_modules
dist
dist-ssr
*.local

# Editor directories and files
.vscode/*
!.vscode/extensions.json
.idea
.DS_Store
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?
```

## Removendos pastas padrões para criação da estrutura do projeto

Arquivos Removidos

- src/App.css
- src/index.css
- src/assets/react.svg

Arquivos editados

- App.tsx
- main.tsx

## Instalando o TailwindCSS

```bash
npm install -D tailwindcss  postcss autoprefixer
npx tailwindcss init -p
```

## Configurando o globals.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Exportando os Tokens do Figma para o projeto

Aqui eu gero o arquivo com os Tokens gerados no figma

- tailwind.config.cjs
  - fontSize
  - colors
  - fontFamily

Adicionando a fonte inter do GoogleFonts

```html
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet" />
    <title>Ignite Lab Design System</title>
  </head>
  <body>
    <div id="root"></div>
```

Configurando os Tokens no TailwindCSS

```cjs
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './src/**/*.tsx',
  ],
  theme: {
    fontSize: {
      'xs': 14,
      'sm': 16,
      'md': 18,
      'lg': 20,
      'xl': 24,
      '2xl': 32,
    },
    colors: {
      black: '#000',
      white: '#fff',
      transparent: 'transparent',
      gray: {
        900: '#121214',
        800: '#202024',
        400: '#7c7c8a',
        200: '#c4c4cc',
        100: '#e1e1e6',
      },
      cyan:{
        500: '#81d8f7',
        300: '#98e1fb',
      }
    },
    extend: {
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
      }
    },
  },
  plugins: [],
}
```

Instalando o CSLX

```bash
npm install --save clsx
```

## Adicionando o RadixUI-Slot

```bash
npm install @radix-ui/react-slot
```

## Adicionando o phosphor-react

```bash
npm i phosphor-react 
```

## Adicionando o RadixUI-Checkbox

```bash
npm install @radix-ui/react-checkbox
```

## Criando os componentes

Componentes criados

- Heading.tsx
- Text.tsx
- Button.tsx
- TextInput.tsx
- Checkbox.tsx

## Adicionando o StoryBook

```bash
npm i @storybook/storybook-deployer --save-dev
npx sb init --builder @storybook/builder-vite --use-npm 
```

Adicionando o StoryBook no packages.json

```json
{
  "name": "lab-ds",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "storybook": "start-storybook -p 6006",
    "build-storybook": "build-storybook"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@babel/core": "^7.19.3",
    "@storybook/addon-actions": "^6.5.12",
    "@storybook/addon-essentials": "^6.5.12",
    "@storybook/addon-interactions": "^6.5.12",
    "@storybook/addon-links": "^6.5.12",
    "@storybook/builder-vite": "^0.2.4",
    "@storybook/react": "^6.5.12",
    "@storybook/testing-library": "^0.0.13",
    "@types/react": "^18.0.17",
    "@types/react-dom": "^18.0.6",
    "@vitejs/plugin-react": "^2.1.0",
    "autoprefixer": "^10.4.12",
    "babel-loader": "^8.2.5",
    "postcss": "^8.4.17",
    "tailwindcss": "^3.1.8",
    "typescript": "^4.6.4",
    "vite": "^3.1.0"
  }
}
```

## Publicando os componentes criados no StoryBook

- Heading.stories.tsx
- Text.stories.tsx
- Button.stories.tsx
- TextInput.stories.tsx
- Checkbox.stories.tsx

## Deploy do Storybook no Github Pages

Veja aqui a publicação do StoryBook no GitHub Pages

- [https://alissonif.github.io/ignite-lab-design-system](https://alissonif.github.io/ignite-lab-design-system/?path=/story/components-button--default)

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/113787415/196235010-b0e3a241-a0fb-4977-ad70-612fd876933f.PNG">

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/113787415/196235041-73d81f6b-d02e-4a97-a023-d712d2fb1997.PNG">

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/113787415/196235055-8e7b8332-3bd6-42ad-9f06-97bb41931e5c.PNG">

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/113787415/196235070-95a64ea3-48a8-4513-8935-c9cf193fd63c.PNG">

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/113787415/196235080-c4971f43-1f8b-4bdc-a70d-df3570747704.PNG">

## Instalação e uso

Clone o projeto e acesse a pasta

```bash
git clone https://github.com/alissonif/ignite-lab-design-system
```

Siga os passos abaixo:

```bash
# Instalar as Dependências
$ npm i

# Iniciar o Servidor em Modo de Desenvolvimento
$ npm run dev

# Iniciar o StoryBook
$ npm run storybook
```

## Ferramentas Utilizadas

<div>

<table border="0">
  <tr>
    <td align="center" width="96">
      <a href="#VisualStudioCode-tech">
        <img align="center" alt="devcss-Js" height="65" width="65" src="https://raw.githubusercontent.com/alissonif/ignite-lab-design-system/113787415/196241841-a94ae043-8e52-42bb-94e2-8153e192a294/figma-1.svg?raw=true">
      </a>
    </td>
    <td align="center" width="96">
      <a href="#VisualStudioCode-tech">
        <img align="center" alt="devcss-Js" height="65" width="65" src="https://raw.githubusercontent.com/alissonif/ignite-lab-design-system/196242175-e3333c8a-b7b0-4571-b1c1-9dc4ba00a08a/react-2.svg?raw=true">
      </a>
    </td>
    <td align="center" width="96">
      <a href="#VisualStudioCode-tech">
        <img align="center" alt="devcss-Js" height="65" width="65" src="https://github.com/alissonif/alissonif/blob/main/images/language_icons/https://user-images.githubusercontent.com/113787415/196242190-9b48a872-f3dd-4ae4-ab5f-07f51d7703f5.png?raw=true">
      </a>
    </td>
    <td align="center" width="96">
      <a href="#VisualStudioCode-tech">
        <img align="center" alt="devcss-Js" height="65" width="65" src="https://raw.githubusercontent.com/alissonif/ignite-lab-design-system/113787415/196242201-2d2aaf54-bd10-4a10-b1e7-fbc773250831/github-icon-1.svg?raw=true">
      </a>
    </td>
    <td align="center" width="96">
      <a href="#VisualStudioCode-tech">
        <img align="center" alt="devcss-Js" height="65" width="65" src="https://raw.githubusercontent.com/alissonif/ignite-lab-design-system/113787415/196242211-2af0466d-fdae-40df-9731-6573c425e2e9/storybook-1.svg?raw=true">
      </a>
    </td>
    <td align="center" width="96">
      <a href="#VisualStudioCode-tech">
        <img align="center" alt="devcss-Js" height="65" width="65" src="https://raw.githubusercontent.com/alissonif/ignite-lab-design-system/113787415/196242229-f4925676-d36e-4315-a3da-2026d3b27543/tailwindcss.svg?raw=true">
      </a>
    </td>
  </tr>
</table>

</div>

## Onde me encontrar

<div>

    <a href="https://instagram.com/josealisson97" target="_blank">
      <img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank">
    </a>
    <a href = "mailto:josealissonif@gmail.com">
      <img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank">
    </a>
    <a href="https://www.linkedin.com/in/josealissonif/" target="_blank">
      <img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank">

</div>

## Veja o meu Perfil no Github

https://github.com/alissonif

## Contact
 - Instagram: [https://www.instagram.com/josealisson97/](https://www.instagram.com/josealisson97/)
 - Linkedin: [https://www.linkedin.com/in/josealissonif/](https://www.linkedin.com/in/josealissonif/)
