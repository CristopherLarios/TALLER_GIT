# 🚀 Guía de Git: De Cero a Intermedio

Bienvenido a esta guía práctica de Git. Aquí aprenderás desde cómo inicializar tu primer repositorio hasta comandos intermedios para gestionar tu código como un profesional.

## 👶 Nivel 0: Configuración Inicial y Creación

Antes de empezar a guardar versiones de tu código, necesitas inicializar Git en tu proyecto.

### 1. `git init`
Este es el primer comando que debes ejecutar en la carpeta de tu proyecto. 
Convierte un directorio normal en un repositorio de Git, creando una carpeta oculta `.git` donde se guardará todo el historial de cambios.

```bash
# Navega a la carpeta de tu proyecto
cd mi-proyecto

# Inicializa el repositorio
git init
```

### 2. `git status`
Tu mejor amigo en Git. Te muestra el estado actual de tu repositorio: qué archivos han cambiado, cuáles están listos para guardarse y en qué rama estás.

```bash
git status
```

---

## 🟢 Nivel Básico: Guardando Cambios

El ciclo básico de Git consiste en modificar archivos, añadirlos al "área de preparación" (staging) y luego guardar un "historial" (commit).

### 3. `git add`
Añade los archivos modificados al "área de preparación" (staging area). Es como decir: *"Quiero que estos cambios se incluyan en mi próxima foto del proyecto"*.

```bash
# Añadir un archivo específico
git add index.html

# Añadir TODOS los archivos modificados y nuevos en la carpeta actual
git add .
```

### 4. `git commit`
Toma una "foto" (snapshot) de los archivos que están en el área de preparación. Cada commit debe tener un mensaje descriptivo para saber qué se hizo.

```bash
git commit -m "feat: añadir la página de inicio"
```

### 5. `git log`
Muestra el historial de todos los commits que has hecho en el proyecto.

```bash
git log

# Para ver una versión más resumida y visual del historial:
git log --oneline --graph
```

---

## 🟡 Nivel Intermedio: Ramas y Viajes en el Tiempo

Las ramas (branches) te permiten trabajar en nuevas características sin afectar el código principal o en producción.

### 6. `git branch`
Te permite ver, crear o eliminar ramas.

```bash
# Ver todas las ramas locales (la rama actual tiene un asterisco *)
git branch

# Crear una nueva rama llamada "nueva-funcionalidad"
git branch nueva-funcionalidad

# Eliminar una rama (que ya haya sido fusionada)
git branch -d nueva-funcionalidad
```

### 7. `git switch` (o `git checkout`)
Te permite cambiarte de una rama a otra. (`git switch` es la versión más moderna y recomendada específicamente para cambiar de ramas).

```bash
# Cambiar a una rama existente
git switch nueva-funcionalidad

# Crear una rama y cambiarte a ella en un solo paso
git switch -c mi-nueva-rama
```

### 8. `git merge`
Une los cambios de una rama a otra. Por ejemplo, si terminaste tu trabajo en `nueva-funcionalidad` y quieres integrarlo a la rama principal (generalmente `main` o `master`).

```bash
# 1. Primero te cambias a la rama que va a RECIBIR los cambios (ej. main)
git switch main

# 2. Luego fusionas la otra rama hacia donde estás parado
git merge nueva-funcionalidad
```

### 9. `git restore`
Si modificaste un archivo pero te arrepientes y quieres devolverlo a su estado original (el del último commit).

```bash
# Deshacer cambios no guardados en un archivo
git restore index.html

# Sacar un archivo del "staging area" (deshacer el git add, pero conservar los cambios en el archivo)
git restore --staged index.html
```

---

## 🌐 Nivel Intermedio: Trabajando con Repositorios Remotos (GitHub, GitLab)

Cuando quieres colaborar con otros, trabajar desde otra computadora o tener un respaldo en la nube.

### 10. `git remote add`
Conecta tu repositorio local con uno remoto (en la nube).

```bash
# Conectar tu repo local con un repositorio en GitHub
git remote add origin https://github.com/tu-usuario/tu-repo.git
```

### 11. `git push`
Sube tus commits locales al repositorio remoto.

```bash
# Subir la rama actual por primera vez (enlaza la rama local con la remota)
git push -u origin main

# Para las siguientes veces, solo necesitas:
git push
```

### 12. `git pull`
Descarga los últimos cambios del repositorio remoto y los fusiona (merge) automáticamente con tu código local actual.

```bash
git pull origin main
```

### 13. `git clone`
Descarga un repositorio completo de internet a tu computadora. Al hacer esto, **no necesitas hacer `git init`** después, porque el proyecto ya viene con toda su configuración de Git.

```bash
git clone https://github.com/usuario/proyecto.git
```

---

## 💡 Consejos de Oro
- **¡Haz commits pequeños y frecuentes!** Es mucho más fácil arreglar un error en un cambio pequeño que en uno de 5,000 líneas.
- **Escribe buenos mensajes de commit.** "Arreglo cosas" no te ayudará a entender qué hiciste 3 meses después. Usa verbos en imperativo o infinitivo: "Añadir botón de login", "Corregir bug visual en el footer".
- **Nunca hagas commits directamente en `main` si trabajas en equipo.** Crea siempre una rama para tus cambios y luego haz un `merge` (o Pull Request en GitHub).
- **`git status` es gratis.** Úsalo siempre que tengas dudas sobre en qué estado está tu proyecto antes de hacer un commit o un push.
