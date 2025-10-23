# Guía de Instalación de pnpm

## 1. Requisitos previos

* **Node.js** versión **18.12 o superior** (si no se usa el instalador independiente o `@pnpm/exe`).
* Acceso a línea de comandos (PowerShell en Windows o Bash en Linux/WSL).
* Permisos de administrador para agregar variables de entorno si se solicita.

## 2. Instalación en Windows

### 2.1 Opción recomendada: instalación con npm o Corepack

#### Usando npm

Si ya tienes Node.js y npm instalados:

```bash
npm install -g pnpm@latest-10
```

Verificar instalación:

```bash
pnpm -v
```

#### Usando Corepack (integrado en Node.js ≥16.13)

Actualizar Corepack y habilitar pnpm:

```bash
npm install -g corepack@latest
corepack enable pnpm
```

Verificar versión:

```bash
pnpm -v
```

Para fijar la versión usada en un proyecto:

```bash
corepack use pnpm@latest-10
```

Esto agregará el campo `"packageManager"` al archivo `package.json`, garantizando consistencia de versión entre entornos.

### 2.2 Opción alternativa: script autónomo (standalone script)

Si no tienes Node.js instalado, puedes usar el siguiente comando en PowerShell:

```powershell
Invoke-WebRequest https://get.pnpm.io/install.ps1 -UseBasicParsing | Invoke-Expression
```

**Nota:** Windows Defender puede bloquear el ejecutable al usar este método. Por esta razón, se recomienda preferir la instalación mediante **npm** o **Corepack**.

Si el antivirus ralentiza las instalaciones, puedes excluir la ruta del almacén de pnpm:

```powershell
Add-MpPreference -ExclusionPath $(pnpm store path)
```

### 2.3 Otras opciones en Windows

| Método                 | Comando                            |
| ---------------------- | ---------------------------------- |
| **Winget**             | `winget install -e --id pnpm.pnpm` |
| **Scoop**              | `scoop install nodejs-lts pnpm`    |
| **Chocolatey (Choco)** | `choco install pnpm`               |
| **Volta**              | `volta install pnpm`               |

Verificar la instalación después de cualquiera de estos métodos:

```bash
pnpm -v
```

## 3. Instalación en WSL (Linux)

Referencia oficial: [https://pnpm.io/installation](https://pnpm.io/installation)

### 3.1 Requisitos previos

Asegurarse de tener instalado **Node.js ≥ 18.12**. Si no lo tienes, puede instalarse con NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
nvm install --lts
```

Verificar:

```bash
node -v
npm -v
```

### 3.2 Instalación mediante script

Ejecutar en terminal Bash dentro de WSL:

```bash
curl -fsSL https://get.pnpm.io/install.sh | sh -
```

Si no tienes `curl`, puedes usar `wget`:

```bash
wget -qO- https://get.pnpm.io/install.sh | sh -
```

Verificar la instalación:

```bash
pnpm -v
```

Instalar una versión específica:

```bash
curl -fsSL https://get.pnpm.io/install.sh | env PNPM_VERSION=<version> sh -
```

Ejemplo:

```bash
curl -fsSL https://get.pnpm.io/install.sh | env PNPM_VERSION=10.2.0 sh -
```

### 3.3 Instalación dentro de un contenedor Docker

Dependiendo del shell utilizado:

```bash
# bash
wget -qO- https://get.pnpm.io/install.sh | ENV="$HOME/.bashrc" SHELL="$(which bash)" bash -

# sh
wget -qO- https://get.pnpm.io/install.sh | ENV="$HOME/.shrc" SHELL="$(which sh)" sh -
```

### 3.4 Usando alias corto

Para facilitar el uso, se puede crear un alias permanente.

En sistemas POSIX (Linux/WSL):

```bash
echo "alias pn=pnpm" >> ~/.bashrc
source ~/.bashrc
```

En PowerShell (Windows):

```powershell
notepad $profile.AllUsersAllHosts
```

Agregar dentro del archivo abierto:

```powershell
set-alias -name pn -value pnpm
```

Guardar y cerrar.

## 4. Compatibilidad entre versiones

| Node.js | pnpm 8        | pnpm 9        | pnpm 10       |
| ------- | ------------- | ------------- | ------------- |
| 14      | No compatible | No compatible | No compatible |
| 16      | Compatible    | No            | No            |
| 18      | Compatible    | Compatible    | Compatible    |
| 20      | Compatible    | Compatible    | Compatible    |
| 22      | Compatible    | Compatible    | Compatible    |
| 24      | Compatible    | Compatible    | Compatible    |

## 5. Verificación y mantenimiento

### Verificar versión instalada

```bash
pnpm -v
```

### Actualizar pnpm

```bash
pnpm self-update
```

### Desinstalar pnpm

Si es necesario eliminarlo por completo, borrar las rutas donde se encuentre el binario:

En Linux:

```bash
which pnpm
```

En Windows:

```powershell
where.exe pnpm.*
```

Eliminar manualmente los archivos `pnpm`, `pnpm.cmd` o `pnpx.cmd` y reinstalar si es necesario.
