# pokedex

# Instrucciones de Instalación y Despliegue

## Instalación de Herramientas

### Node.js
1. **Instalar Node.js:**
   - Descarga e instala Node.js desde el [sitio oficial](https://nodejs.org/).

### Angular CLI
2. **Instalar Angular CLI:**
   - Ejecuta el siguiente comando en tu terminal:
     ```bash
     npm install -g @angular/cli
     ```

### Azure CLI (Opcional)
3. **Instalar Azure CLI:**
   - Descarga e instala Azure CLI desde el [sitio oficial](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).
   - Opcionalmente, puedes instalar Azure CLI usando npm:
     ```bash
     npm install -g azure-cli
     ```

## Construcción del Proyecto

4. **Construir la Aplicación Angular:**
   - Navega a la carpeta del proyecto y ejecuta los siguientes comandos:
     ```bash
     ng build --prod
     ng build --configuration production
     ```
   - Esto creará una carpeta llamada `dist` que contiene los archivos optimizados para producción.

### Optimización en Modo Producción
- **Minificación:** Reduce el tamaño de los archivos eliminando espacios en blanco y comentarios.
- **Ofuscación:** Cambia los nombres de variables y funciones para que ocupen menos espacio y sean más difíciles de entender, lo que también protege tu código.
- **Tree Shaking:** Elimina el código que no se utiliza para reducir el tamaño del bundle final.

### Contenido de la Carpeta `dist`
- **index.html:** Punto de entrada de la aplicación Angular.
- **main.[hash].js:** Código principal de la aplicación.
- **polyfills.[hash].js:** Compatibilidad con navegadores antiguos.
- **runtime.[hash].js:** Gestiona el orden de carga de los módulos.
- **vendor.[hash].js:** Dependencias externas (bibliotecas de terceros).
- **styles.[hash].css:** Estilos CSS globales y de componentes.
- **assets/:** Archivos estáticos como imágenes y fuentes.
- **.map files:** Ayudan en el proceso de depuración.

## Configuración de Seguridad

5. **Crear el Archivo `web.config`:**
   - Crea un archivo llamado `web.config` en la raíz del proyecto y agrega las siguientes líneas de código para configurar la seguridad de la web:
     ```xml
     <add name="Strict-Transport-Security" value="max-age=31536000"/>
     <add name="X-Frame-Options" value="DENY"/>
     <add name="X-Content-Type-Options" value="nosniff"/>
     <add name="Referrer-Policy" value="no-referrer"/>
     <add name="Permissions-Policy" value="geolocation=(), microphone=(), camera=()"/>
     ```
   - Copia este archivo tanto en la raíz del proyecto como en la carpeta `dist`.

## Despliegue en Azure

6. **Comprimir los Archivos:**
   - Comprime los elementos dentro de la carpeta `dist` en un archivo `.zip`.

7. **Acceder a Kudu en Azure:**
   - En la página de Azure, ve al sidebar y accede a **Development Tools > Advanced Tools > Go**.
   - Esto te llevará a la página de **Kudu**.

8. **Subir el Archivo `.zip`:**
   - En el navbar de Kudu, ve a **Debug console > CMD**.
   - Navega al explorador de archivos virtual en `site > wwwroot` y sube el archivo `.zip`.

9. **Verificar el Despliegue:**
   - Regresa a la página de Azure y en el sidebar, ve al apartado **Overview**.
   - Haz clic en el enlace que Azure te brinda para verificar que la aplicación esté desplegada correctamente.

¡Listo! Ahora tu aplicación Angular está desplegada y lista para ser utilizada.
