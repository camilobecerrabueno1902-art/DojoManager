# DojoManager
Sistema de Control de Alumnos, Asistencias y Grados para Academia de Artes Marciales.

##  Descripción del Proyecto
**DojoManager** es una aplicación web orientada a escuelas deportivas para optimizar la gestión administrativa y académica. Permite llevar el registro detallado de los estudiantes, el control de asistencias en tiempo real a los entrenamientos y el seguimiento de los exámenes de cambio de cinturón.

## Objetivo
Desarrollar una aplicación web robusta y segura para la administración integral de una academia de artes marciales, optimizando el control de asistencia en tiempo real, la gestión de alumnos y el seguimiento de exámenes de grado mediante tecnologías modernas de desarrollo backend y seguridad.

---

##  Perfiles de Usuario y Roles
1. **Alumno:** 
   - Consulta su historial de asistencia.
   - Visualiza próximos exámenes de grado.
   - Revisa el estado de sus pagos de mensualidad pendientes.
2. **Instructor / Entrenador:** 
   - Pasa asistencia en tiempo real durante las clases.
   - Registra calificaciones técnicas de los alumnos.
   - Programa y gestiona los exámenes de grado.

---

##  Tecnologías Previstas
- **Backend:** Java (Spring Boot)
- **Seguridad:** Spring Security con **JWT (JSON Web Token)** para la autenticación y gestión de sesiones sin estado.
- **Base de Datos:** MySQL / Relacional.
- **Control de Versiones:** Git y GitHub.

---

##  Modelo de Base de Datos (DER Sugerido)
- **Instructors:** (`id`, `nombre`, `especialidad`, `contacto`)
- **Alumnos:** (`id`, `nombre`, `fecha_nacimiento`, `cinturon_actual`, `instructor_id`)
- **Clases:** (`id`, `fecha`, `hora`, `tema_entrenamiento`)
- **Asistencias:** (`id`, `alumno_id`, `clase_id`, `estado`) *(Presente / Ausente)*
- **Examenes_Grado:** (`id`, `alumno_id`, `cinturon_aspirado`, `fecha_examen`, `resultado`)

---

##  Seguridad y Autenticación (JWT)
El sistema implementará un flujo de autenticación basado en tokens:
1. El usuario envía sus credenciales (`username` y `password`) al endpoint de Login.
2. Si son correctas, el servidor genera un **JWT** que se almacena en el navegador (por ejemplo, en `localStorage` o cookies seguras).
3. Para cada petición posterior a endpoints protegidos, el cliente enviará el token en la cabecera HTTP (`Authorization: Bearer <token>`), permitiendo validar la sesión de forma segura.
