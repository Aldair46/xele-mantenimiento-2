# Sistema de mantenimiento · Xele Fitness

Aplicación web para el mantenimiento preventivo de las 8 máquinas de la sala de musculación del Gimnasio Xele Fitness: estado de la sala, fichas técnicas, plan preventivo por frecuencia, reporte de fallas con foto e indicadores (Disponibilidad, MTBF, MTTR y cumplimiento del plan).

Publicada con GitHub Pages. Los datos se comparten entre todos los dispositivos mediante Firebase (Authentication + Firestore, plan gratuito).

## Archivos

- `index.html`, `css/`, `js/`, `img/`: la aplicación.
- `js/datos.js`: fichas técnicas y plan de las 8 máquinas.
- `js/firebase-config.js`: datos de conexión al proyecto de Firebase.
- `reglas-firestore.txt`: reglas de seguridad para pegar en Firebase > Firestore > Reglas.

## Configuración en Firebase (una sola vez)

1. Crear proyecto en https://console.firebase.google.com
2. Authentication > Método de acceso > activar Correo electrónico/contraseña.
3. Authentication > Usuarios > crear una cuenta por persona.
4. Authentication > Configuración > Dominios autorizados > agregar `aldair46.github.io`.
5. Firestore Database > Crear base de datos (modo producción, southamerica-east1).
6. Firestore > Reglas > pegar el contenido de `reglas-firestore.txt` > Publicar.
7. Firestore > Datos > colección `ajustes`, documento `roles`, campo `duenos` (array) con los correos de los dueños en minúsculas.
8. Configuración del proyecto > Tus apps > Web (</>) > copiar `firebaseConfig` en `js/firebase-config.js`.

Mientras `js/firebase-config.js` tenga los valores de ejemplo, la app guarda los datos solo en cada dispositivo.

## Roles

- **Dueño** (correo en `ajustes/roles`): gestiona fallas (estado, costo, horas de parada, cierre) y ajusta las horas de operación.
- **Personal de sala**: reporta fallas con foto y marca las tareas del plan.
