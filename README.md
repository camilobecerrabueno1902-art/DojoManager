# DojoManager
Sistema de Control de Alumnos, Asistencias y Grados para Academia de Artes Marciales.

## Integrantes del Grupo
- J. Thomas Becerra Lozano
- Sara Nikolle Bueno Vera
- Juan Camilo Becerra Bueno


---

## Descripción del Proyecto
**DojoManager** es una aplicación web orientada a escuelas deportivas para optimizar la gestión administrativa y académica. Permite llevar el registro detallado de los estudiantes, el control de asistencias en tiempo real a los entrenamientos y el seguimiento de los exámenes de cambio de cinturón.

## Objetivo
Desarrollar una aplicación web robusta y segura para la administración integral de una academia de artes marciales, optimizando el control de asistencia en tiempo real, la gestión de alumnos y el seguimiento de exámenes de grado mediante tecnologías modernas de desarrollo backend y seguridad.

---

## Perfiles de Usuario y Roles
1. **Alumno:** 
   - Consulta su historial de asistencia.
   - Visualiza próximos exámenes de grado.
   - Revisa el estado de sus pagos de mensualidad pendientes.
2. **Instructor / Entrenador:** 
   - Pasa asistencia en tiempo real durante las clases.
   - Registra calificaciones técnicas de los alumnos.
   - Programa y gestiona los exámenes de grado.

---

## Requisitos Funcionales
1. **Gestión de Asistencia:** El sistema debe permitir al instructor seleccionar una clase específica y registrar la asistencia (Presente/Ausente) de los alumnos inscritos en tiempo real.
2. **Gestión de Exámenes de Grado:** El sistema debe permitir al instructor programar fechas de exámenes, asignar los alumnos candidatos y registrar el resultado (Aprobado/Reprobado) y el nuevo cinturón alcanzado.
3. **Consulta de Historial:** El sistema debe permitir al perfil "Alumno" visualizar su propio porcentaje de asistencia mensual y su historial de cinturones.
4. **Autenticación y Autorización:** El sistema debe validar las credenciales de ingreso (usuario y contraseña) y redirigir a una interfaz diferente dependiendo del rol (Instructor o Alumno).
5. **Control de Pagos:** El sistema debe mostrar al alumno el estado actual de su mensualidad (Al día, Pendiente, Vencida) basándose en los registros administrativos.

## Requisitos No Funcionales
1. **Seguridad (JWT):** Todas las peticiones a endpoints protegidos del backend deben requerir un token JWT válido enviado en la cabecera HTTP (`Authorization: Bearer <token>`). Las contraseñas deben estar encriptadas en la base de datos.
2. **Rendimiento:** El proceso de registro masivo de asistencia para una clase no debe tardar más de 2 segundos en reflejarse en la base de datos.
3. **Usabilidad:** La interfaz web debe ser "Responsive" (adaptable) para que los instructores puedan pasar asistencia cómodamente desde un teléfono móvil o tablet durante el entrenamiento.
4. **Mantenibilidad:** El código backend debe seguir el patrón de arquitectura multicapa (Controlador, Servicio, Repositorio) propio de Spring Boot para facilitar futuras actualizaciones.
5. **Disponibilidad:** El sistema debe garantizar una disponibilidad del 99% durante los horarios operativos habituales de la academia (ej. 8:00 AM a 10:00 PM).

---

## Tecnologías Previstas
- **Backend:** Java (Spring Boot)
- **Seguridad:** Spring Security con **JWT (JSON Web Token)** para la autenticación y gestión de sesiones sin estado.
- **Base de Datos:** MySQL / Relacional.
- **Control de Versiones:** Git y GitHub.

---

## Modelo de Base de Datos (DER Sugerido)
- **Instructors:** (`id`, `nombre`, `especialidad`, `contacto`)
- **Alumnos:** (`id`, `nombre`, `fecha_nacimiento`, `cinturon_actual`, `instructor_id`)
- **Clases:** (`id`, `fecha`, `hora`, `tema_entrenamiento`)
- **Asistencias:** (`id`, `alumno_id`, `clase_id`, `estado`) *(Presente / Ausente)*
- **Examenes_Grado:** (`id`, `alumno_id`, `cinturon_aspirado`, `fecha_examen`, `resultado`)

---

## Seguridad y Autenticación (JWT)
El sistema implementará un flujo de autenticación basado en tokens:
1. El usuario envía sus credenciales (`username` y `password`) al endpoint de Login.
2. Si son correctas, el servidor genera un **JWT** que se almacena en el navegador (por ejemplo, en `localStorage` o cookies seguras).
3. Para cada petición posterior a endpoints protegidos, el cliente enviará el token en la cabecera HTTP (`Authorization: Bearer <token>`), permitiendo validar la sesión de forma segura.