Aquí tienes la guía estilizada y corregida, lista para ser copiada y pegada en tu archivo de Word. 😊📄

---

### **Guía para levantar el servidor del Backend localmente** 🚀

1. **Instalar paquetes en la carpeta Backend** 📂  
   - Ejecuta `npm install` en la carpeta `backend`.  
   - Si la instalación de paquetes y dependencias es exitosa, pasa al **punto 6**. ✅  

2. **Error durante la instalación (específicamente "error code 7" relacionado con bcrypt)** ❌  
   - Es probable que se trate de una **incompatibilidad de tu versión de Node.js** con los paquetes.  
   - La versión de Node.js utilizada para el backend es **v22.12**.  

3. **Usar NVM (Node Version Manager) para gestionar versiones de Node.js** 🔄  
   - **3.1** Instala NVM para tu sistema operativo: [Documentación oficial](https://github.com/nvm-sh/nvm).  
   - **3.2** Desde la carpeta `backend`, ejecuta:  
     ```bash
     nvm install 22.12
     nvm use 22.12
     ```  
   - **3.3** Para asegurarte de que el backend siempre use esta versión, crea un archivo `.nvmrc` dentro de `backend`:  
     ```bash
     echo "22.12" > .nvmrc
     ```  
     Luego, cada vez que entres a la carpeta `backend`, solo ejecuta:  
     ```bash
     nvm use
     ```  

4. **Mantener la versión 20.18 en el Frontend** 🖥️  
   - **4.1** En la carpeta `frontend`, haz lo mismo pero con la versión **20.18**:  
     ```bash
     nvm install 20.18
     nvm use 20.18
     echo "20.18" > .nvmrc
     ```  
   - **4.2** Cada vez que entres a `frontend`, solo ejecuta:  
     ```bash
     nvm use
     ```  

5. **(Opcional) Cambiar automáticamente de versión al entrar en cada carpeta** 🤖  
   - Agrega esto a tu `.bashrc` o `.zshrc`:  
     ```bash
     autoload -U add-zsh-hook
     add-zsh-hook chpwd load-nvmrc
     load-nvmrc() {
       if [[ -f .nvmrc ]]; then
         nvm use
       fi
     }
     load-nvmrc
     ```  

6. **Configurar el archivo `.env`** ⚙️  
   - En la carpeta `backend`, cambia el nombre del archivo `.env.example` a `.env`.  

7. **Obtener credenciales de Google Client** 🔑  
   - Inicia sesión en **Google Cloud** para obtener las credenciales.  
   - Busca en Google o YouTube: **"¿Cómo obtener Google Client ID y Client Secret?"**  
     - **No preguntes a LLM's (ChatGPT, Deepseek, etc.)**, ya que la información puede estar desactualizada.  
   - **7.1** En Google Cloud, en el apartado **"Orígenes autorizados de JavaScript"**, agrega:  
     ```
     http://localhost:8082
     ```  
   - **7.2** En **"URIs de redirección autorizados"**, agrega:  
     ```
     http://localhost:8082/auth/google/callback
     ```  
   - **7.3** Haz clic en **"Crear"** y copia el **Client ID** y **Client Secret**.  

8. **Obtener credenciales de Facebook Client** 🔑  
   - Inicia sesión en **Facebook Developers**: [https://developers.facebook.com/](https://developers.facebook.com/).  
   - **8.1** Crea una nueva App y asígnale el nombre **Doggii**.  
   - **8.2** En el menú de la izquierda, ve a **"Productos" > "Configurar"** en **"Inicio de Sesión con Facebook"**.  
     - Elige **"Web"** y agrega `http://localhost:8082` como la URL del sitio.  
   - **8.3** Ve a **"Configuración" > "Básica"**.  
   - **8.4** El apartado **"Identificador de la app"** corresponde al `FACEBOOK_CLIENT_ID` del archivo `.env`.  
     - El apartado **"Clave secreta de la app"** corresponde al `FACEBOOK_CLIENT_SECRET`.  

9. **Obtener el MONGO_URI** 🗄️  
   - Inicia sesión en **MongoDB Atlas**: [https://www.mongodb.com/products/platform/atlas-database](https://www.mongodb.com/products/platform/atlas-database).  
   - **9.1** Haz clic en **"Create a New Project"** y nómbralo como **DoggiApp**.  
   - **9.2** Dentro de tu proyecto, haz clic en **"Build a Database"**.  
     - Selecciona **"Shared Cluster"** (Gratis).  
     - Elige **Amazon AWS** y una región cercana a ti (ejemplo: **North Virginia (us-east-1)**).  
     - En **"Cluster Name"**, pon de nombre **DoggiApp**.  
     - Presiona **"Create Cluster"** y espera unos minutos hasta que esté listo.  
   - **9.3** Ve a la pestaña **"Database Access"**.  
     - Crea un usuario con un nombre y contraseña segura (ejemplo: `doggi_user`).  
     - Guarda bien la contraseña porque la necesitarás en tu `.env`.  
   - **9.4** Cuando aparezca la siguiente pantalla:  
     [imagen]  
     Copia la URL desde el inicio hasta `...mongodb.net` como se indica en la imagen.  
   - **9.5** Pega esa URL en el apartado `MONGO_URI` de tu `.env`.  

10. **Instalar MongoDB globalmente** 📦  
    - Ejecuta:  
      ```bash
      npm install mongodb
      ```  

---

**Con estos pasos, deberías ser capaz de correr tu servidor localmente.** 🎉😅  

--- 
