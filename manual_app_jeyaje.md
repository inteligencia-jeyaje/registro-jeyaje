# 📜 MANUAL DE USUARIO Y CONFIGURACIÓN: MINI APP JEYAJÉ ARCO IRIS

Este sistema automatiza el registro individual de participantes y staff para las ceremonias, centralizando la base de datos en la nube (**Google Sheets**), resguardando el código en **GitHub** y facilitando el envío de requisitos personalizados por **WhatsApp**.

---

## 👥 PARTE 1: MÓDULO PÚBLICO (Inscripción de Almas)

La pantalla principal de la aplicación cuenta con dos pestañas de acceso público en la parte superior:

### 1. Pestaña "Asistente" (Registro Regular)
Cualquier participante que asista a la ceremonia debe llenar este formulario de forma **individual** (un registro por persona):
* **Nombre Completo:** Nombre de quien asiste.
* **Número de WhatsApp:** Debe ingresarse obligatoriamente con el prefijo del país seguido del número (Ej. `59170000000`).
* **Invitado por:** Nombre de la persona de la comunidad que extendió la invitación.
* **Categoría de Participante:** Menú desplegable para seleccionar si es un **Invitado (Nuevo)** o un **Miembro de la Comunidad**.
* **Selecciona tu Ceremonia:** Menú con las ceremonias activas cargadas en el sistema.

### 2. Pestaña "Staff / Sahumador" (Registro Protegido)
* **Acceso Restringido:** Al hacer clic en esta pestaña, el sistema solicitará una clave de acceso exclusiva para portadores del fuego.
* **Contraseña de acceso:** `fuego2026`
* Una vez dentro, el Sahumador llena sus datos y selecciona obligatoriamente su categoría:
    * *Tribu de Sahumadores Jeyajé - Arco Iris*
    * *Pájaro Solitario (Sahumador independiente)*

---

## ⚙️ PARTE 2: PANEL DE ADMINISTRACIÓN (Acceso Encargado)

En la parte inferior de la aplicación se encuentra el botón **"Acceso Encargado"**.
* **Contraseña de administrador:** `2009`

Al ingresar la clave, se desplegará el panel oculto con tres secciones fundamentales:

### 1. Configuración de Ceremonias
* Permite escribir el nombre de un nuevo evento (Ej: `Ceremonia de Equinoccio de Primavera`) y presionar **Guardar Evento Nuevo**. El evento aparecerá inmediatamente en los menús desplegables públicos.
* Cuenta con un botón **"✖"** rojo al lado de cada ceremonia para eliminarla cuando concluya.

### 2. Panel de Control y Contadores
Muestra en tiempo real la cantidad de almas confirmadas divididas en dos contadores automáticos:
* **Total Participantes:** Cantidad de asistentes regulares.
* **Total Staff/Sahumadores:** Cantidad de servidores del fuego registrados.

### 3. Listados Segmentados y Botones de Acción
El panel agrupa automáticamente a las personas bajo el nombre de la ceremonia para la cual se registraron. Dentro de cada ceremonia verás dos tablas separadas (**👥 Lista de Asistentes** y **🔥 Staff de Sahumadores**), detallando el nombre y la categoría de cada uno.

Al lado de cada nombre hay tres botones interactivos:
* **📱 Botón Verde (WhatsApp - Confirmación):** Abre un chat de WhatsApp con un mensaje personalizado y los requisitos específicos (ayuno, ropa clara para asistentes; o llegada anticipada y elementos limpios para el Staff).
* **⏰ Botón Café (Reloj - Recordatorio):** Abre un chat de WhatsApp con un recordatorio afectuoso de proximidad de la fecha.
* **🗑️ Botón Rojo (Basurero - Eliminar):** Borra al participante de la vista local. *(Nota: Para eliminarlo permanentemente del ecosistema, recuerda borrar también su fila en el archivo de Google Sheets)*.

### 📋 Botón "Copiar Reporte General para WhatsApp"
Al presionarlo, copia al portapapeles un reporte impecablemente formateado con negritas (`*`) listo para pegar en los grupos informativos de la tribu, estructurado así:
> 🔥 *NOMBRE DE LA CEREMONIA*
>   👥 ASISTENTES:
>     1. Juan Pérez [Invitado (Nuevo)] (Inv: María)
>   ⚡ STAFF / SAHUMADORES:
>     1. Carlos López (Tribu de Sahumadores)

---

## ☁️ PARTE 3: GESTIÓN AUTÓNOMA DESDE GOOGLE SHEETS (Sin tocar código)

Toda la personalización de mensajes, enlaces de Google Maps e información se maneja desde tu hoja de cálculo. Tu archivo de Google Sheets cuenta con dos pestañas (hojas) abajo:

### Hoja 1: `Respuestas del Formulario` (Base de Datos)
Aquí se registran automáticamente todos los envíos con el orden exacto de columnas:
`Fecha` | `Tipo` (Asistente/Staff) | `Nombre` | `WhatsApp` | `Categoría` | `Ceremonia` | `Invitado Por`

### Hoja 2: `Configuracion` (Control de Mensajes y Links)
El texto que escribas en esta pestaña reemplazará al del archivo index.html en tiempo real al enviar confirmaciones por WhatsApp. Debe estar estructurada exactamente así:
* **Celda A1:** `Mensaje Asistente` | **Celda B1:** `Mensaje Staff`
* **Celda A2:** Escribe aquí el mensaje para asistentes regulares. Puedes pegar el enlace de tu **Google Maps**, emojis y condiciones.
* **Celda B2:** Escribe aquí las indicaciones para el Staff de Sahumadores.

#### 💡 Secreto de las Etiquetas Dinámicas:
Dentro de las celdas **A2** y **B2** puedes escribir estas palabras exactamente entre llaves `{}`. El sistema las sustituirá en milisegundos por los datos reales de la persona antes de abrir WhatsApp:
* `{nombre}` : Se cambia por el nombre del registrado.
* `{categoria}` : Se cambia por su categoría (Miembro, Invitado, Pájaro Solitario, etc).
* `{ceremonia}` : Se cambia por el nombre de la ceremonia que eligió.

---

## 🛠️ PARTE 4: PROCEDIMIENTO PARA ACTUALIZACIONES DE CÓDIGO (Apps Script)

Si en algún momento realizas un cambio directo en el editor de **Google Apps Script** (Extensiones > Apps Script) para modificar cómo se procesan las celdas, recuerda siempre activar la actualización en la red con estos pasos:
1. Haz clic en el botón azul **Implementar** (arriba a la derecha) y selecciona **Administrar implementaciones**.
2. Haz clic en el **icono del lápiz (Editar)** de tu implementación activa.
3. En el menú desplegable de "Versión", selecciona obligatoriamente **Nueva versión**.
4. Haz clic en el botón azul **Implementar**. *(No necesitas cambiar el enlace de tu HTML, la URL se mantiene vinculada automáticamente)*.
