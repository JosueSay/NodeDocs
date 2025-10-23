# Documentación de Instalación y Entorno — Node.js

## 1. Instalación de Node.js en Windows

### Paso 1: Descargar e instalar

Descargar el instalador desde:
[https://nodejs.org/en/download](https://nodejs.org/en/download)

1. Selecciona el instalador `.msi` para Windows (x64 o ARM64 según tu sistema).
2. Ejecuta el instalador y sigue los pasos del asistente.
3. Marca la opción “Agregar Node.js a las variables de entorno PATH”.
4. Finaliza la instalación.

### Paso 2: Verificar instalación

Abrir PowerShell o CMD y ejecutar:

```bash
node -v
npm -v
```

### Paso 3: Instalación de manejadores de paquetes adicionales

Node incluye **npm**, pero también se puede instalar:

| Manejador | Instalación            | Comando de versión | Descripción breve                                            |
| --------- | ---------------------- | ------------------ | ------------------------------------------------------------ |
| **npm**   | Se instala con Node.js | `npm -v`           | Predeterminado, buena compatibilidad.                        |
| **yarn**  | `npm install -g yarn`  | `yarn -v`          | Más rápido con caché eficiente; útil para proyectos grandes. |
| **pnpm**  | `npm install -g pnpm`  | `pnpm -v`          | Optimiza espacio en disco y dependencias compartidas.        |

### Tabla comparativa de manejadores de paquetes

| Criterio                     | **npm**                                                    | **yarn**                                                      | **pnpm**                                                      |
| ---------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| Velocidad de instalación     | Media                                                      | Alta                                                          | Muy alta                                                      |
| Uso de espacio en disco      | Alto                                                       | Medio                                                         | Bajo                                                          |
| Compatibilidad               | Máxima (nativo)                                            | Alta                                                          | Alta                                                          |
| Soporte para monorepos       | Limitado                                                   | Bueno                                                         | Excelente                                                     |
| Determinismo en dependencias | Medio                                                      | Bueno                                                         | Excelente                                                     |
| Cuándo usar                  | Cuando necesitas compatibilidad total o proyectos simples. | Cuando buscas rapidez y mejor gestión de caché.               | Cuando trabajas en grandes proyectos o monorepos.             |
| Cuándo evitar                | En proyectos grandes con dependencias repetidas.           | Si dependes de herramientas que no soportan Yarn Plug’n’Play. | Si usas scripts que asumen estructura `node_modules` clásica. |

### Consultar guías oficiales

Para más detalle sobre instalación en Windows o WSL, consultar:

- [npm](https://docs.npmjs.com/)
- [yarn](https://yarnpkg.com/getting-started/install)
- [pnpm](https://pnpm.io/installation)

## 2. Instalación de Node.js en WSL (Windows Subsystem for Linux)

Referencia oficial:
[Instalar Node.js en WSL — Microsoft Learn](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl)

### Paso 1: Instalar y configurar WSL 2

1. Ejecutar en PowerShell como administrador:

    ```bash
    wsl --install
    ```

2. Reiniciar el sistema si se solicita.
3. Verificar la versión instalada:

    ```bash
    wsl --list --verbose
    ```

    (La versión recomendada es WSL 2).

4. Abrir la distribución Linux (por defecto: Ubuntu) y actualizar paquetes:

    ```bash
    sudo apt update && sudo apt upgrade
    lsb_release -dc
    ```

### Paso 2: Instalar NVM (Node Version Manager)

Instalar cURL (si no está presente):

```bash
sudo apt install curl
```

Instalar NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

Cerrar y reabrir la terminal, luego verificar:

```bash
command -v nvm
```

Si responde `nvm`, la instalación fue exitosa.

### Paso 3: Instalar Node.js y npm con NVM

Instalar versión LTS (recomendada para producción):

```bash
nvm install --lts
```

Instalar versión actual (para pruebas):

```bash
nvm install node
```

Verificar versiones instaladas:

```bash
nvm ls
```

Verificar Node y npm activos:

```bash
node -v
npm -v
```

Cambiar versión activa:

```bash
nvm use --lts
# o
nvm use node
```

Con NVM se pueden tener múltiples versiones de Node.js sin conflictos.

### Paso 4: Instalar VS Code con integración WSL

1. Instalar VS Code en Windows: [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Instalar la extensión **Remote - WSL** desde la marketplace de VS Code.
3. Abrir VS Code y seleccionar en la esquina inferior izquierda “Conectar con WSL”.
4. Abrir el proyecto dentro del entorno Linux.

Ventajas:

- Autocompletado e IntelliSense nativo en Linux.
- Ejecución y depuración directa en el entorno WSL.
- Integración completa con Git, Docker, ESLint, etc.

### Paso 5: Verificación final

Dentro de la terminal WSL o en VS Code conectado al entorno WSL:

```bash
node -v
npm -v
which node
which npm
```

Si las rutas apuntan a `/home/usuario/.nvm/...`, la instalación está correcta.
