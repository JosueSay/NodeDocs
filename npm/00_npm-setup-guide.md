# Guía de instalación de npm (Windows y WSL)

## 1. Windows

### Opción A (recomendada): Instalador oficial de Node.js

1. Descarga el **MSI** desde: [https://nodejs.org/en/download](https://nodejs.org/en/download)
2. Durante la instalación, deja marcada la opción de **añadir al PATH**.
3. Verifica:

   ```bash
   node -v
   npm -v
   ```

   (npm se instala junto con Node.js). ([nodejs.org][1])

### Opción B: Gestor de versiones para Windows (nvm-windows)

1. Instala **nvm-windows** y usa nvm para instalar Node.js (trae npm).
2. Pasos y recomendaciones (quitar instalaciones previas, etc.) en la guía de Microsoft. ([Microsoft Learn][2])

### Opción C: npm/Node según guía de npm

* npm recomienda usar **un gestor de versiones** o el **instalador de Node** para obtener npm. Pasos y verificación en la guía oficial. ([docs.npmjs.com][3])

### Actualizar npm en Windows

```bash
npm -v
npm install -g npm@latest
npm -v
```

(Proceso descrito en la documentación de npm). ([docs.npmjs.com][3])

## 2. WSL (Ubuntu u otra distro Linux en Windows)

### Método recomendado: NVM dentro de WSL

1. Abre la terminal de tu distro WSL.
2. Instala NVM y luego Node LTS (incluye npm):

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
   # cierra y reabre la terminal
   nvm install --lts
   node -v
   npm -v
   ```

   Guía paso a paso y notas (evitar sudo, cambiar versiones con `nvm use`, etc.) en Microsoft Learn. ([Microsoft Learn][4])

> Alternativa: instalar Node.js por paquetes de la distro o scripts de Node.js, pero se recomienda NVM para evitar conflictos y facilitar cambios de versión. ([Microsoft Learn][4])

### Actualizar npm en WSL

```bash
npm -v
npm install -g npm@latest
npm -v
```

[1]: https://nodejs.org/en/download?utm_source=chatgpt.com "Download Node.js"
[2]: https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-windows?utm_source=chatgpt.com "Set up Node.js on native Windows"
[3]: https://docs.npmjs.com/downloading-and-installing-node-js-and-npm/?utm_source=chatgpt.com "Downloading and installing Node.js and npm"
[4]: https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl?utm_source=chatgpt.com "Install Node.js on Windows Subsystem for Linux (WSL2)"
