#Gestión de sesiones
Se define una arquitectura de microservicios y escalabilidad horizontal, utilizando JWT (stateless).

#Cookies
Se almacenan con HttpOnly, de manera que no sean accesibles para javascript del navegador.

#Contraseñas
Se encriptan con Bcrypt.

#Autenticación
Se limita los intentos de login por IP origen para evitar ataques de fuerza bruta.

#Log
Se define un log para el registro de los eventos exitosos y fallidos.

##Componentes
#Sesión
Almacena el JWT token en memoria y limpia las credenciales al cerrar sesión.

#Login - Entrada de datos
Gestiona el formulario en sus distintos estados y captura el evento de envío.

#Login - Validación
Evalúa el formato del email y la complejidad de la contraseña ingresada.

#Auth
Componente encargado de crear el cuerpo POST hacia el backend con las cabeceras necesarias.

#Rutas
Se protege las rutas evitando el acceso a usuarios no autorizados.

##Arquitectura
#Capa de datos
Tabla de usuarios con (id, email, password_hash) indexando 'email'.

#Capa de servidor
Generados de tokens JWT.
Módulo de cifrado con Bcrypt.
Post endpoint /api/v1/auth/login.

#Capa de cliente
Visualización de errores y estados de la aplicación.
El token de sesión se almacena de forma segura.
Formulario para ingreso de email y contraseña.
