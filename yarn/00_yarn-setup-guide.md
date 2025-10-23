# Guía de instalación de Yarn (Windows y WSL)

## 1. Requisitos previos

Antes de instalar Yarn asegúrate de tener:

* **Node.js** versión `>=8.0.0` (recomendado LTS o superior).
* **npm** ya instalado (se incluye con Node.js).

Verifica:

```bash
node -v
npm -v
```

## 2. Instalación de Yarn en Windows

Existen tres métodos oficiales para instalar Yarn en Windows.

### Opción A: Instalador (.msi)

1. Descarga el instalador desde la página oficial:
   [https://classic.yarnpkg.com/lang/en/docs/install/#windows-stable](https://classic.yarnpkg.com/lang/en/docs/install/#windows-stable)

2. Ejecuta el archivo `.msi` descargado.

3. Acepta los términos, deja la ruta por defecto y marca la opción **"Agregar Yarn al PATH"**.

4. Finaliza la instalación.

Verifica:

```bash
yarn -v
```

*

### Opción B: Instalación con Chocolatey

Si tienes **Chocolatey** instalado:

```bash
choco install yarn
```

Este comando también instalará **Node.js** si no está presente.

Verificar instalación:

```bash
yarn --version
```

### Opción C: Instalación con Scoop

Si usas **Scoop** (instalador de línea de comandos para Windows):

```bash
scoop install yarn
```

Si **Node.js** no está instalado, Scoop mostrará una sugerencia para hacerlo:

```bash
scoop install nodejs
```

Verificar:

```bash
yarn --version
```

### Opción D (recomendada y multiplataforma): Instalar mediante npm

Yarn puede instalarse directamente usando npm, que ya viene con Node.js:

```bash
npm install --global yarn
```

Verificar instalación:

```bash
yarn -v
```

Actualizar Yarn más adelante:

```bash
npm install --global yarn@latest
```

## 3. Instalación de Yarn en WSL (Ubuntu o similar)

Referencia: [dev.to/bonstine - Installing Yarn on WSL](https://dev.to/bonstine/installing-yarn-on-wsl-38p2)

### Paso 1: Abrir la terminal WSL

Inicia tu distribución (por ejemplo, Ubuntu) desde el menú de inicio o ejecutando:

```bash
wsl
```

### Paso 2: Ejecutar el script de instalación oficial

Ejecuta el siguiente comando:

```bash
curl -o- -L https://yarnpkg.com/install.sh | bash
```

Este comando descarga e instala Yarn directamente.

### Paso 3: Reiniciar la terminal WSL

Después de que el script finalice, **cierra y vuelve a abrir** la terminal WSL para actualizar las variables de entorno.

Verifica la instalación:

```bash
yarn --version
```

Si aparece un número de versión, la instalación fue exitosa.

## 4. Ejemplo de uso básico

Inicializar un nuevo proyecto y agregar dependencias:

```bash
mkdir mi_proyecto
cd mi_proyecto
yarn init -y
yarn add express
```

Ejecutar un script:

```bash
yarn run start
```

Actualizar dependencias:

```bash
yarn upgrade
```

Eliminar una dependencia:

```bash
yarn remove express
```

## 5. Comparación rápida con otros manejadores de paquetes

| Característica       | **npm**  | **yarn** | **pnpm**   |
| -------------------- | -------- | -------- | ---------- |
| Velocidad            | Media    | Alta     | Muy alta   |
| Caché de paquetes    | Básica   | Avanzada | Compartida |
| Uso de espacio       | Alto     | Medio    | Bajo       |
| Monorepos            | Limitado | Bueno    | Excelente  |
| Determinismo         | Medio    | Bueno    | Excelente  |
| Instalación paralela | No       | Sí       | Sí         |

## 6. Comprobación y actualización

Verificar Yarn:

```bash
yarn -v
```

Actualizar Yarn globalmente (si se instaló con npm):

```bash
npm install -g yarn@latest
```

Si se instaló con script (WSL):

```bash
curl -o- -L https://yarnpkg.com/install.sh | bash
```

**Fuentes oficiales:**

* [Yarn Classic Installation Docs](https://classic.yarnpkg.com/lang/en/docs/install/#windows-stable)
* [Yarn on WSL Guide (dev.to)](https://dev.to/bonstine/installing-yarn-on-wsl-38p2)
