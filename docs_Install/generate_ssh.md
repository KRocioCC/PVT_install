# GENERAR CLAVES SSH


## ¿Qué es SSH?

SSH es un protocolo seguro que te permite conectarte a servidores (como GitHub) sin escribir tu contraseña cada vez. Usa un par de claves: una **privada** (confidencial) y otra **pública** (que compartes).

## Pasos para generar claves SSH

### 1) Generar el par de claves

En tu terminal, ejecuta:

```sh
ssh-keygen -t ed25519 -C "tu_correo@gmail.com"
```

Reemplaza `tu_correo@gmail.com` con tu correo real. Presiona **Enter** en todas las preguntas para usar los valores por defecto.

### 2) Verificar que se generaron

```sh
ls ~/.ssh/
```

Deberías ver dos archivos:
- `id_ed25519` (clave privada - NUNCA la compartas)
- `id_ed25519.pub` (clave pública - esto sí lo usarás)

### 3) Copiar tu clave pública

```sh
cat ~/.ssh/id_ed25519.pub
```

**Copia TODA la salida** (desde `ssh-ed25519` hasta tu correo).

## Agregar la clave pública a GitHub

### 1) Ve a GitHub

- Abre https://github.com/settings/ssh/new

### 2) Agrega la clave SSH

- **Title**: Dale un nombre (ej: "Mi SSH")
- **Key**: Pega lo que copiaste en el paso anterior
- Haz clic en **"Add SSH key"**

### 3) Verifica que funciona

En tu terminal:

```sh
ssh -T git@github.com
```

Si sale algo como "Hi! You've successfully authenticated...", ¡está listo!

