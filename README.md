<div align="center">
    <img alt="nestjs-commons" width="250" height="auto" src="https://camo.githubusercontent.com/c704e8013883cc3a04c7657e656fe30be5b188145d759a6aaff441658c5ffae0/68747470733a2f2f6e6573746a732e636f6d2f696d672f6c6f676f5f746578742e737667" />
    <h3>NestJS - Commons</h3>
</div>

<p align="center">
    <img src="https://img.shields.io/static/v1.svg?style=flat&label=Node&message=v14.15.4&labelColor=339933&color=757575&logoColor=FFFFFF&logo=Node.js" alt="Node.js"/>
    <img src="https://img.shields.io/static/v1.svg?style=flat&label=Npm&message=v6.14.10&labelColor=CB3837&logoColor=FFFFFF&color=757575&logo=npm" alt="Npm"/>
    <img src="https://img.shields.io/static/v1.svg?style=flat&label=NestJs&message=v8.2.6&labelColor=E0234E&logoColor=FFFFFF&color=757575&logo=Nestjs" alt="NestJs"/>
    <img alt="GitHub license" src="https://img.shields.io/github/license/rudemex/nestjs-commons?style=flat">
    <br/>
    <img alt="GitHub Workflow Status" src="https://github.com/rudemex/nestjs-commons/actions/workflows/master.yml/badge.svg?branch=master">
    <img alt="Codecov" src="https://img.shields.io/codecov/c/github/rudemex/nestjs-commons?logoColor=FFFFFF&logo=Codecov&labelColor=#F01F7A">
    <img src="https://sonarcloud.io/api/project_badges/measure?project=rudemex_nestjs-commons&metric=alert_status" alt="sonarcloud">
    <img alt="GitHub package.json version" src="https://img.shields.io/github/package-json/v/rudemex/nestjs-commons">
    <br/> 
</p>

Esta dependencia está pensada para ser utilizada en [NestJs Starter](https://github.com/rudemex/nestjs-starter), o
cualquier proyecto que utilice una configuración centralizada, siguiendo la misma arquitectura del starter.

## Glosario

- [🥳 Demo](https://rudemex-nestjs-starter.herokuapp.com/docs)
- [📝 Requerimientos básicos](#basic-requirements)
- [🛠️ Instalar dependencia](#install-dependencie)
- [⚙️ Configuración](#configurations)
- [📤 Commits](#commits)
- [📄 Changelog](./CHANGELOG.md)
- [📜 License MIT](license.md)

---

<a name="basic-requirements"></a>

## 📝 Requerimientos básicos

- [NestJs Starter](https://github.com/rudemex/nestjs-starter)
- Node.js v14.15.4 or higher ([Download](https://nodejs.org/es/download/))
- NPM v6.14.10 or higher
- NestJS v8.2.0 or higher ([Documentación](https://nestjs.com/))

<a name="install-dependencie"></a>

## 🛠️ Instalar dependencia

```
npm install @tresdoce/nestjs-commons
```

<a name="configurations"></a>

## ⚙️ Configuración

### Eslint

```javascript
// .eslintrc.js

const config = require('@tresdoce/nestjs-commons');
module.exports = config.eslintConfig();
```

### Jest

```javascript
// jest.config.ts

import { jestConfig } from '@tresdoce/nestjs-commons';
import * as dotenv from 'dotenv';

process.env.NODE_ENV = 'test';

dotenv.config({
  path: '.env.test',
});

module.exports = jestConfig;
```

### Webpack

```javascript
// webpack.config.js

const config = require('@tresdoce/nestjs-commons');
module.exports = (options) => config.buildConfig(options);
```

### HTTPS

Se requiere crear el `certificado` y la `privkey` (llave privada), Podés encontrar más info [acá](https://leiva.io/2020/06/13/implementar-https-en-nestjs/).

```typescript
// ./src/main.ts

import * as path from 'path';
import { readHttpsCertificate } from '@tresdoce/nestjs-commons'

const crtPath = path.resolve(__dirname, './ssl/fullchain.crt');
const keyPath = path.resolve(__dirname, './ssl/privkey.key');

async function bootstrap() {
    const app = await NestFactory.create(AppModule, {
        httpsOptions: readHttpsCertificate(crtPath, keyPath),
        logger: new Logger(),
    });

    ...

    await app.listen(port, () => {
        console.log(`App running on: http://localhost:${port}`);
    });
}

bootstrap();
```

<a name="commits"></a>

## 📤 Commits

Para los mensajes de commits se toma como
referencia [`conventional commits`](https://www.conventionalcommits.org/en/v1.0.0-beta.4/#summary).

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

- **type:** chore, docs, feat, fix, refactor (más comunes)
- **scope:** indica la página, componente, funcionalidad
- **description:** comienza en minúsculas y no debe superar los 72 caracteres.

## 📄 Changelog

All notable changes to this package will be documented in [Changelog](./CHANGELOG.md) file.

---

<div align="center">
    <a href="mailto:mdelgado@tresdoce.com.ar" target="_blank" alt="Send an email">
        <img src="./.readme-static/logo-mex-red.svg" width="120" alt="Mex" />
    </a><br/>
    <p>Made with ❤</p>
</div>
