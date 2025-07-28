# **Plan Maestro de Desarrollo: AppFlutter \- Gestión de Torneos y Eventos Deportivos**

Este documento integra todas las fases del ciclo de vida de desarrollo de software (SDLC) para la "AppFlutter \- Gestión de Torneos y Eventos Deportivos", desde la concepción inicial hasta el lanzamiento y el mantenimiento continuo.

## **1\. Fase de Ideación**

**Objetivo:** Clarificar la visión, definir el problema a resolver y validar la necesidad del mercado, con un enfoque en su atractivo para la inversión y su propuesta de valor social.

### **Visión General Ampliada**

Crear una **red social deportiva integral** que revolucione la forma en que los torneos y eventos deportivos se organizan, gestionan y participan en el área metropolitana. La meta es conectar a atletas, organizadores y aficionados en un ecosistema digital dinámico y vibrante. La aplicación buscará ser el **"Facebook de los deportes"**, un punto de encuentro fundamental para la comunidad deportiva, donde la interacción, el seguimiento de logros y la formación de comunidades serán pilares.

### **Público Objetivo**

Atletas (amateurs y semi-profesionales), organizadores de eventos deportivos (ligas, clubes, gimnasios), y aficionados al deporte en el área metropolitana.

### **Funcionalidades Clave**

* **Gestión Centralizada de Torneos y Eventos:** Permitirá a organizadores crear, programar y gestionar eventos eficientemente, simplificando la burocracia y mejorando la visibilidad de los torneos.  
* **Red Social Deportiva: El Corazón de la Conexión:** Funcionará como una plataforma robusta para que los usuarios se conecten, sigan a otros deportistas, compartan resultados, celebren logros, publiquen actualizaciones y se mantengan al tanto de la actividad deportiva de su interés. Fomentará la interacción y la formación de comunidades en torno a deportes y eventos específicos.  
* **Diversidad de Disciplinas:** Abordará deportes tradicionales (fútbol, baloncesto, ciclismo), deportes de mesa (ajedrez, billar) y otras actividades recreativas, promoviendo una inclusión amplia y atrayendo a una base de usuarios diversa.  
* **Sistema de Ranking de Usuarios:** Implementará un sistema de clasificación y ranking basado en la participación, resultados y habilidades. Esto no solo añade un componente competitivo y de reconocimiento, sino que también fomenta la participación continua y la interacción entre usuarios.  
* **Perfiles de Usuario Completos y Atractivos:** Los perfiles mostrarán estadísticas, historial de participación, logros y preferencias deportivas, sirviendo como una "identidad deportiva" digital para cada usuario.  
* **Notificaciones y Recordatorios Inteligentes:** Mantendrá a los usuarios informados sobre sus próximos eventos, resultados relevantes y actualizaciones de su red, impulsando el compromiso y la retención.

### **Propuesta de Valor para Inversores**

* **Gran Potencial de Mercado:** El mercado de los deportes amateurs y eventos locales es vasto y fragmentado, ofreciendo una oportunidad significativa para una plataforma centralizada.  
* **Alto Compromiso de Usuario:** El enfoque en la red social y la gamificación (rankings, logros) promete altos niveles de interacción y tiempo en la aplicación.  
* **Modelo de Negocio Escalable:** Potencial para monetización futura a través de inscripciones a eventos, publicidad dirigida, funcionalidades premium para organizadores, etc.  
* **Tecnología Robusta y Multiplataforma:** Flutter y Firebase aseguran un desarrollo ágil, escalabilidad y una base tecnológica moderna y eficiente.

### **Tecnologías Principales Seleccionadas y Consumo de APIs**

* **Frontend:** Flutter (Dart) \- para desarrollo móvil multiplataforma (iOS y Android), ofreciendo una única base de código para ambas plataformas, lo que agiliza el desarrollo y reduce costos de mantenimiento.  
* **Backend:** Firebase \- un conjunto de servicios de Google Cloud que ofrece soluciones robustas, escalables y con una integración nativa y optimizada con Flutter.  
  * **Firestore (Base de Datos NoSQL):** Almacenamiento y sincronización de datos en tiempo real (perfiles, eventos, posts, grupos, resultados). Su modelo de precios se basa en el número de lecturas, escrituras y eliminaciones de documentos, así como el almacenamiento de datos. Un diseño de datos eficiente (como la desnormalización estratégica) será clave para optimizar estos costos.  
  * **Firebase Authentication:** Gestión robusta de usuarios, incluyendo registro, inicio de sesión (con correo/contraseña, y extensible a proveedores de terceros como Google, Facebook), y recuperación de contraseña. El consumo se basa en el número de autenticaciones y usuarios activos mensuales.  
  * **Firebase Cloud Storage:** Almacenamiento seguro de archivos binarios de gran tamaño, como fotos de perfil, imágenes y videos de publicaciones, logos de eventos. El consumo se basa en el almacenamiento utilizado y la transferencia de datos.  
  * **Firebase Cloud Functions:** Permite ejecutar código de backend sin servidor en respuesta a eventos de Firebase (ej., creación de un nuevo post) o llamadas HTTP desde la aplicación. Es ideal para lógica compleja y sensible que no debe ejecutarse en el cliente, como el cálculo y actualización de rankings, validación segura de contraseñas de eventos privados, procesamiento de inscripciones, o la activación de notificaciones masivas. El consumo se basa en el número de invocaciones, el tiempo de ejecución y la memoria utilizada.  
  * **Firebase Cloud Messaging (FCM):** Envío confiable de notificaciones push a los usuarios, ya sean notificaciones dirigidas, segmentadas o basadas en eventos. El consumo es generalmente gratuito para la mayoría de los casos de uso básicos, con costos mínimos asociados a volúmenes extremadamente altos.  
* **APIs Nativas de Plataforma (Google/iOS):** La aplicación se apoyará en gran medida en las APIs nativas de la plataforma (Android y iOS) para habilitar funcionalidades clave que requieren acceso a recursos del sistema o servicios de terceros. Esto asegura el mejor rendimiento y la integración más fluida con el ecosistema del dispositivo.  
  * **Servicios de Ubicación (Google Maps Platform / Core Location):** Para obtener la ubicación precisa del usuario (con su permiso), calcular distancias a los eventos, ordenar listados por proximidad y habilitar la función "Gente que Quizás Conozca". El consumo puede estar ligado al uso de la API de Mapas (si se integra un mapa interactivo) y a las solicitudes frecuentes de ubicación.  
  * **Servicios de Calendario (Google Calendar API / EventKit):** Para que los usuarios puedan añadir eventos de la aplicación directamente a sus calendarios personales del dispositivo, facilitando la gestión de su agenda deportiva.  
  * **Acceso a Galería/Cámara:** APIs nativas para permitir a los usuarios seleccionar imágenes de su galería o tomar fotos directamente con la cámara para subir a sus perfiles, publicaciones o eventos.  
  * **Otros servicios del sistema operativo:** Como acceso a contactos (para invitaciones), notificaciones locales (para recordatorios en la app), etc.  
* **Optimización de Consumo:** El diseño y desarrollo de la aplicación se enfocarán en optimizar el consumo de todas estas APIs y servicios. Esto incluirá estrategias como el uso eficiente de escuchas en tiempo real de Firestore, la compresión de imágenes antes de subirlas a Storage, la lógica de backend en Cloud Functions para minimizar operaciones del lado del cliente, y la gestión inteligente de las solicitudes de ubicación para preservar la batería del dispositivo y reducir costos de API.

### **Requisitos de la Aplicación de Gestión de Torneos (AppFlutter)**

#### **1\. Requisitos Funcionales (RF)**

Describen las funciones o servicios que el sistema debe proporcionar al usuario.

* **RF1: Autenticación de Usuarios:**  
  * RF1.1: Permitir el registro de nuevos usuarios (correo electrónico/contraseña, Google).  
  * RF1.2: Permitir el inicio de sesión de usuarios existentes (correo electrónico/contraseña, Google).  
  * RF1.3: Permitir la recuperación de contraseña.  
  * RF1.4: Permitir cerrar sesión.  
* **RF2: Gestión de Perfil de Usuario:**  
  * RF2.1: Permitir a los usuarios crear y editar su perfil (nombre, foto de perfil, información de contacto).  
  * RF2.2: Permitir a los usuarios ver su historial de torneos (organizados y participados).  
* **RF3: Gestión de Torneos (Organizadores):**  
  * RF3.1: Permitir a los usuarios con rol de "organizador" crear nuevos torneos (nombre, descripción, reglas, fecha/hora, ubicación, tipo de deporte, número máximo de participantes, premio).  
  * RF3.2: Permitir a los organizadores editar los detalles de sus propios torneos.  
  * RF3.3: Permitir a los organizadores eliminar sus propios torneos (con confirmación).  
  * RF3.4: Permitir a los organizadores gestionar las inscripciones a sus torneos (aceptar/rechazar participantes).  
  * RF3.5: Permitir a los organizadores registrar y actualizar resultados de los partidos/encuentros dentro de su torneo.  
  * RF3.6: Permitir a los organizadores asignar roles específicos a otros usuarios (ej. co-organizador, arbitro) dentro de un torneo específico.  
* **RF4: Exploración y Participación en Torneos (Participantes):**  
  * RF4.1: Mostrar una lista de torneos disponibles (filtrados por deporte, fecha, ubicación, popularidad, etc.).  
  * RF4.2: Permitir a los usuarios ver los detalles completos de un torneo.  
  * RF4.3: Permitir a los usuarios inscribirse en un torneo.  
  * RF4.4: Mostrar el estado de la inscripción (pendiente, aceptado, rechazado).  
  * RF4.5: Mostrar los resultados y el progreso de los torneos en los que participa.  
  * RF4.6: Mostrar la ubicación de los eventos del torneo en un mapa.  
  * RF4.7: Mostrar la distancia entre la ubicación actual del usuario y la ubicación del torneo.  
* **RF5: Comunicación/Notificaciones:**  
  * RF5.1: Enviar notificaciones a los participantes sobre el estado de su inscripción.  
  * RF5.2: Enviar notificaciones a los participantes sobre actualizaciones de partidos/horarios del torneo.  
  * RF5.3: Enviar notificaciones a los organizadores sobre nuevas inscripciones.  
  * RF5.4: Implementar un sistema de chat básico para organizadores/participantes dentro de un torneo (opcional en una fase posterior).  
* **RF6: Calificación/Feedback:**  
  * RF6.1: Permitir a los participantes calificar al organizador/torneo después de finalizado.  
  * RF6.2: Permitir a los organizadores calificar a los participantes.  
* **RF7: Búsqueda y Filtro:**  
  * RF7.1: Implementar funcionalidad de búsqueda por nombre de torneo, deporte, ubicación.  
  * RF7.2: Permitir filtrar torneos por estado (próximos, activos, finalizados), deporte, rango de fechas.

#### **2\. Requisitos No Funcionales (RNF)**

Describen cómo debe funcionar el sistema (calidad, rendimiento, seguridad, usabilidad, etc.).

* **RNF1: Rendimiento:**  
  * RNF1.1: La aplicación debe cargar la lista de torneos en menos de 3 segundos con una conexión de red estable.  
  * RNF1.2: El registro/inicio de sesión debe completarse en menos de 2 segundos.  
  * RNF1.3: La actualización de resultados de partidos debe ser casi instantánea (menos de 1 segundo).  
* **RNF2: Seguridad:**  
  * RNF2.1: Toda la comunicación entre la app y el backend (Firebase) debe estar cifrada (HTTPS).  
  * RNF2.2: Los datos sensibles del usuario deben almacenarse de forma segura.  
  * RNF2.3: Solo los usuarios autenticados deben poder acceder a ciertas funcionalidades.  
  * RNF2.4: Las reglas de seguridad de Firestore deben aplicar correctamente los permisos de lectura/escritura (ej. solo el organizador puede editar su torneo).  
* **RNF3: Usabilidad (UX/UI):**  
  * RNF3.1: La interfaz de usuario debe ser intuitiva y fácil de navegar.  
  * RNF3.2: La aplicación debe proporcionar retroalimentación visual clara para las acciones del usuario (cargas, errores, confirmaciones).  
  * RNF3.3: Diseño responsivo para diferentes tamaños de pantalla de dispositivos móviles.  
  * RNF3.4: La aplicación debe seguir las directrices de diseño de Material Design (Android) y/o Human Interface Guidelines (iOS) según corresponda.  
* **RNF4: Disponibilidad/Fiabilidad:**  
  * RNF4.1: La aplicación debe tener un tiempo de actividad del 99.9% (dependiendo de la infraestructura de Firebase).  
  * RNF4.2: La aplicación debe manejar gracefully las interrupciones de red.  
* **RNF5: Escalabilidad:**  
  * RNF5.1: La arquitectura de la aplicación (Firebase Firestore, Functions) debe ser capaz de soportar miles de usuarios concurrentes y millones de torneos/eventos sin degradación significativa del rendimiento.  
* **RNF6: Mantenibilidad:**  
  * RNF6.1: El código base debe ser limpio, modular y bien documentado para facilitar futuras modificaciones y expansiones.  
  * RNF6.2: Utilizar un sistema de control de versiones (Git).  
* **RNF7: Compatibilidad:**  
  * RNF7.1: La aplicación debe ser compatible con las últimas dos versiones principales de Android e iOS.

#### **3\. Requisitos de Negocio (RN)**

Describen los objetivos de alto nivel del negocio que la aplicación debe cumplir.

* **RN1: Aumentar la participación en torneos:** Proporcionar una plataforma fácil para encontrar y unirse a torneos.  
* **RN2: Simplificar la organización de torneos:** Reducir la carga administrativa para los organizadores de eventos deportivos locales.  
* **RN3: Crear una comunidad:** Fomentar la interacción entre jugadores y organizadores.  
* **RN4: Monetización (futura):** Abrir la posibilidad de modelos de negocio futuros (ej. inscripciones pagas, promoción de torneos).  
* **RN5: Recopilación de datos:** Recopilar datos sobre la popularidad de deportes, ubicaciones de torneos, etc., para futuras decisiones de negocio.

#### **4\. Requisitos de Información (RI)**

Detallan la información que el sistema debe almacenar, procesar y presentar.

* **RI1: Información del Usuario:**  
  * ID de Usuario (UID de Firebase Auth).  
  * Nombre de usuario.  
  * Correo electrónico.  
  * Foto de perfil (URL de Firebase Storage).  
  * Lista de torneos organizados (referencias).  
  * Lista de torneos participados (referencias, con estado de inscripción).  
  * Roles específicos dentro de torneos.  
* **RI2: Información del Torneo:**  
  * ID del Torneo.  
  * Nombre del Torneo.  
  * Descripción detallada.  
  * Reglas del Torneo.  
  * Fecha y Hora (inicio/fin).  
  * Ubicación (dirección, coordenadas geográficas).  
  * Tipo de Deporte (fútbol, baloncesto, tenis, etc.).  
  * Número máximo de participantes.  
  * Premio.  
  * ID del Organizador (referencia al usuario).  
  * Lista de participantes inscritos (con estado: pendiente, aceptado, rechazado).  
  * Resultados de los partidos/encuentros (estructura de datos para el bracket/liga).  
  * Estado del Torneo (próximo, activo, finalizado, cancelado).  
  * Calificaciones promedio.  
* **RI3: Información de Partidos/Resultados:**  
  * ID del Partido.  
  * Equipos/Jugadores participantes.  
  * Resultados (puntuación, ganador).  
  * Fecha y hora del partido.  
  * Estado del partido (programado, en juego, finalizado).  
  * Referencia al torneo al que pertenece.  
* **RI4: Información de Inscripción:**  
  * ID de Inscripción.  
  * ID de Usuario (participante).  
  * ID de Torneo.  
  * Estado de la inscripción (pendiente, aceptado, rechazado).  
  * Fecha de inscripción.  
* **RI5: Información de Calificaciones:**  
  * ID de Calificación.  
  * ID del calificador (usuario).  
  * ID del calificado (organizador/participante/torneo).  
  * Puntuación (ej. 1-5 estrellas).  
  * Comentario.  
  * Fecha de calificación.

## **2\. Fase de Planificación**

**Objetivo:** Establecer un roadmap claro, definir requisitos exhaustivos y estimar recursos.

### **Requisitos Funcionales Detallados (User Stories)**

* **Autenticación:**  
  * "Como usuario, quiero registrarme e iniciar sesión con correo/contraseña."  
  * "Como usuario, quiero restablecer mi contraseña."  
  * "Como usuario, quiero que la app valide si mi cuenta existe al intentar iniciar sesión."  
  * "Como usuario, quiero que la app valide si mi contraseña es correcta al iniciar sesión."  
  * "Como usuario, quiero ver mensajes de error claros si el login falla (ej. credenciales incorrectas, cuenta no existe)."  
* **Perfiles de Usuario:**  
  * "Como usuario, quiero crear y editar mi perfil (nombre completo, apodo/nombre de usuario, fecha de nacimiento, deportes favoritos, género, ubicación predeterminada, foto de perfil, mini-biografía)."  
  * "Como usuario, quiero ver el perfil de otros usuarios con sus estadísticas, logros e historial de eventos."  
  * "Como usuario, quiero tener un ID único fácil de compartir (ej. @miusuario\_id) para que otros me encuentren."  
* **Gestión de Eventos (Organizador):**  
  * "Como organizador, quiero crear un nuevo torneo/evento (nombre, deporte, fechas, ubicación, reglas, descripción)."  
  * "Como organizador, quiero definir si un torneo es público o privado."  
  * "Como organizador, si el torneo es privado, quiero establecer una contraseña de acceso."  
  * "Como organizador, quiero establecer el número máximo de cupos para un evento."  
  * "Como organizador, quiero gestionar las inscripciones de los participantes y ver cuántos cupos quedan."  
  * "Como organizador, quiero actualizar los resultados de los partidos/rondas en tiempo real."  
  * "Como organizador, quiero organizar los equipos/participantes en franjas horarias, manual o automáticamente."  
* **Participación en Eventos (Usuario):**  
  * "Como usuario, quiero buscar eventos deportivos por deporte, fecha o ubicación."  
  * "Como usuario, quiero que los eventos se ordenen por proximidad a mi ubicación actual."  
  * "Como usuario, quiero ver los detalles de un evento e inscribirme."  
  * "Como usuario, si un evento es privado, quiero ingresar la contraseña correcta para inscribirme."  
  * "Como usuario, quiero recibir notificaciones sobre mis próximos eventos y cambios en los mismos."  
  * "Como usuario, quiero ver mis eventos inscritos en un formato de calendario."  
  * "Como usuario, si soy invitado explícitamente a un evento, quiero que aparezca destacado."  
* **Red Social:**  
  * "Como usuario, quiero seguir a otros deportistas para ver sus actualizaciones."  
  * "Como usuario, quiero ver un feed de actividad que muestre publicaciones de los usuarios que sigo y eventos relevantes."  
  * "Como usuario, quiero compartir mis resultados y logros con publicaciones (texto, imágenes)."  
  * "Como usuario, quiero crear grupos temáticos o de equipo."  
  * "Como usuario, quiero invitar a otros usuarios a unirse a grupos o eventos."  
  * "Como usuario, quiero recibir recomendaciones de otros usuarios y eventos basados en mis deportes favoritos y ubicación."  
  * "Como usuario, quiero encontrar gente que quizás conozca basada en ubicación, intereses y conexiones."  
* **Sistema de Ranking:**  
  * "Como usuario, quiero ver mi posición en el ranking global y por deporte."  
  * "Como usuario, quiero ver los rankings de otros deportistas."

### **Requisitos No Funcionales**

* **Rendimiento:** Tiempos de carga rápidos, respuesta fluida de la UI, mínima latencia en actualizaciones en tiempo real.  
* **Seguridad:** Protección de datos de usuario (contraseñas encriptadas, datos personales), autenticación robusta, reglas de seguridad de Firestore para control de acceso, validación de contraseñas de eventos privados en el backend.  
* **Usabilidad:** Interfaz intuitiva y fácil de usar, navegación clara, feedback visual al usuario.  
* **Disponibilidad:** Alta disponibilidad del backend (Firebase) y la app.  
* **Escalabilidad:** Capacidad para soportar un número creciente de usuarios y datos.  
* **Localización:** Inicialmente español, con posibilidad de expansión futura a otros idiomas.  
* **Offline Support:** Considerar caching para ciertas funcionalidades (ej. ver eventos previamente cargados sin conexión).

### **Definición de MVP (Producto Mínimo Viable)**

Identificar las funcionalidades *absolutamente esenciales* para la primera versión lanzable. Un posible MVP podría incluir:

* Registro/Login, Creación de Perfiles básicos.  
* Creación de Eventos públicos y privados (sin gestión avanzada de cupos inicial).  
* Inscripción a Eventos, Visualización de Eventos por lista y detalle (con acceso condicional a privados).  
* Función de Seguir/Dejar de Seguir.  
  Las funciones de ranking avanzado, grupos, invitaciones, organización automática de horarios y recomendaciones detalladas podrían ser para iteraciones futuras.

### **Cronograma y Hitos**

Establecer plazos realistas para cada fase y definir hitos clave (ej. "MVP funcional para X fecha").

### **Roles y Responsabilidades**

Si trabajas solo, eres desarrollador, diseñador, etc. Si es en equipo, asignar roles.

### **Diagrama de Clases (Código)**

Este diagrama de clases UML (Unified Modeling Language) representa las principales entidades y sus relaciones, sirviendo como un blueprint técnico para la implementación en Flutter/Dart y la estructura de datos en Firebase.

classDiagram  
    direction LR

    class AuthManager {  
        \- FirebaseAuth \_auth  
        \+ Future\<UserCredential\> signIn(String email, String password)  
        \+ Future\<UserCredential\> signUp(String email, String password)  
        \+ Future\<void\> resetPassword(String email)  
        \+ Future\<void\> signOut()  
        \+ Stream\<User?\> authStateChanges()  
    }

    class UserService {  
        \- FirebaseFirestore \_firestore  
        \- FirebaseStorage \_storage  
        \+ Future\<AppUser\> getUser(String userId)  
        \+ Future\<void\> createUser(AppUser user)  
        \+ Future\<void\> updateUser(AppUser user)  
        \+ Future\<String\> uploadProfileImage(File imageFile, String userId)  
        \+ Future\<void\> followUser(String currentUserId, String targetUserId)  
        \+ Future\<void\> unfollowUser(String currentUserId, String targetUserId)  
        \+ Stream\<List\<AppUser\>\> searchUsers(String query)  
        \+ Future\<List\<AppUser\>\> getRecommendedUsers(AppUser currentUser)  
    }

    class EventService {  
        \- FirebaseFirestore \_firestore  
        \- Geolocator \_geolocator  
        \+ Future\<void\> createEvent(Event event)  
        \+ Future\<void\> updateEvent(Event event)  
        \+ Stream\<List\<Event\>\> getEventsNearMe(double latitude, double longitude)  
        \+ Stream\<List\<Event\>\> getEventsBySport(String sportId)  
        \+ Stream\<List\<Event\>\> getEventsForDate(DateTime date)  
        \+ Future\<bool\> joinEvent(String userId, String eventId, String? password)  
        \+ Future\<bool\> leaveEvent(String userId, String eventId)  
        \+ Future\<void\> updateMatchResult(String eventId, String matchId, Map\<String, dynamic\> result)  
    }

    class PostService {  
        \- FirebaseFirestore \_firestore  
        \- FirebaseStorage \_storage  
        \+ Future\<void\> createPost(Post post)  
        \+ Stream\<List\<Post\>\> getFeedPosts(List\<String\> followedUserIds)  
        \+ Future\<String\> uploadPostImage(File imageFile)  
        \+ Future\<void\> addComment(String postId, Comment comment)  
        \+ Future\<void\> addLike(String postId, String userId)  
        \+ Future\<void\> removeLike(String postId, String userId)  
    }

    class GroupService {  
        \- FirebaseFirestore \_firestore  
        \+ Future\<void\> createGroup(Group group)  
        \+ Future\<void\> inviteUserToGroup(String groupId, String userId)  
        \+ Stream\<List\<Group\>\> getUserGroups(String userId)  
        \+ Future\<bool\> joinGroup(String groupId, String userId)  
        \+ Future\<bool\> leaveGroup(String groupId, String userId)  
    }

    class RankingService {  
        \- FirebaseFirestore \_firestore  
        \+ Stream\<List\<AppUser\>\> getGlobalRanking(String sportId)  
        \+ Stream\<AppUser\> getUserRanking(String userId, String sportId)  
        \+ Future\<void\> updateRanking(String userId, String sportId, int points)  
    }

    class AppUser {  
        \- String id  
        \- String name  
        \- String email  
        \- String? profileImageUrl  
        \- String? bio  
        \- List\<String\> favoriteSports  
        \- List\<String\> followingIds  
        \- List\<String\> followerIds  
        \- String? uniqueAppId // For easy search  
        \- Map\<String, UserSportStats\> stats  
        \+ AppUser fromFirestore(DocumentSnapshot doc)  
        \+ Map\<String, dynamic\> toFirestore()  
    }

    class UserSportStats {  
        \- int wins  
        \- int losses  
        \- int draws  
        \- int participations  
        \- int rankingScore  
        \+ UserSportStats fromMap(Map\<String, dynamic\> data)  
        \+ Map\<String, dynamic\> toMap()  
    }

    class Event {  
        \- String id  
        \- String name  
        \- String sportId  
        \- String description  
        \- DateTime startDate  
        \- DateTime endDate  
        \- String location  
        \- double latitude  
        \- double longitude  
        \- String organizerId  
        \- String status  
        \- int? maxParticipants  
        \- int currentParticipants  
        \- bool isPrivate  
        \- String? privatePassword // Will be validated in backend for security  
        \- String rules  
        \+ Event fromFirestore(DocumentSnapshot doc)  
        \+ Map\<String, dynamic\> toFirestore()  
    }

    class Post {  
        \- String id  
        \- String userId  
        \- String content  
        \- String? imageUrl  
        \- DateTime timestamp  
        \- List\<String\> likedBy  
        \+ Post fromFirestore(DocumentSnapshot doc)  
        \+ Map\<String, dynamic\> toFirestore()  
    }

    class Comment {  
        \- String id  
        \- String userId  
        \- String content  
        \- DateTime timestamp  
        \+ Comment fromFirestore(Map\<String, dynamic\> data)  
        \+ Map\<String, dynamic\> toMap()  
    }

    class Group {  
        \- String id  
        \- String name  
        \- String description  
        \- String adminId  
        \- List\<String\> memberIds  
        \- bool isPublic  
        \+ Group fromFirestore(DocumentSnapshot doc)  
        \+ Map\<String, dynamic\> toFirestore()  
    }

    AuthManager \--\> UserService : uses  
    UserService \--\> AppUser : manages  
    EventService \--\> Event : manages  
    EventService \--\> AppUser : participants  
    EventService \--\> Geolocator : uses  
    Event \--\> UserSportStats : impacts  
    PostService \--\> Post : manages  
    PostService \--\> AppUser : author, likes  
    Post \--\> Comment : has  
    GroupService \--\> Group : manages  
    GroupService \--\> AppUser : members  
    RankingService \--\> AppUser : updates and queries stats  
    RankingService \--\> UserSportStats : uses

![][image1]  
**CRUD de Usuarios (AppUser):**

* **C**rear Usuario (Registro)  
* **R**eer Usuario (Ver Perfil, Ver Usuarios en Torneo)  
* **U**pdate Usuario (Editar Perfil)  
* **D**elete Usuario (Eliminar Cuenta \- aunque rara vez se implementa directamente en apps públicas, a menudo es una "desactivación")

**CRUD de Torneos (Event):**

* **C**rear Torneo  
* **R**eer Torneo (Ver detalles del torneo, listar torneos)  
* **U**pdate Torneo (Editar detalles del torneo)  
* **D**elete Torneo (Eliminar torneo \- por el organizador)

**CRUD de Inscripciones a Torneos (UserEventStats / EventService \- Participación):**

* **C**rear Inscripción (Usuario se inscribe en un torneo)  
* **R**eer Inscripción (Ver estado de la inscripción, lista de participantes para organizador)  
* **U**pdate Inscripción (Organizador acepta/rechaza inscripción)  
* **D**elete Inscripción (Usuario cancela su inscripción o es eliminado por organizador)

**CRUD de Resultados de Partidos/Encuentros (parte de Event o como entidad separada como "MatchResult"):**

* **C**rear Resultado (Registrar un nuevo resultado de partido)  
* **R**eer Resultado (Ver resultados de partidos)  
* **U**pdate Resultado (Actualizar un resultado existente)  
* **D**elete Resultado (Eliminar un resultado \- si hay un error)

**CRUD de Posts/Anuncios (Post):**

* **C**rear Post (Por el organizador o admin de la app)  
* **R**eer Post (Ver posts en un torneo o feed)  
* **U**pdate Post (Editar un post existente)  
* **D**elete Post (Eliminar un post)

**CRUD de Comentarios (Comment):**

* **C**rear Comentario  
* **R**eer Comentarios  
* **U**pdate Comentario (Editar comentario propio)  
* **D**elete Comentario (Eliminar comentario propio o por moderador)

**CRUD de Calificaciones/Reviews (Rating):**

* **C**rear Calificación  
* **R**eer Calificaciones  
* **U**pdate Calificación (Editar calificación propia)  
* **D**elete Calificación (Eliminar calificación propia)

**CRUD de Grupos (Group \- si se implementa un sistema de grupos dentro de la app):**

* **C**rear Grupo  
* **R**eer Grupo  
* **U**pdate Grupo  
* **D**elete Grupo

**CRUD de Notificaciones (Notifications \- si se gestionan persistencia de notificaciones en la DB):**

* **C**rear Notificación (Cuando ocurre un evento)  
* **R**eer Notificación (Usuario ve sus notificaciones)  
* **U**pdate Notificación (Marcar como leída)  
* **D**elete Notificación (Eliminar notificaciones antiguas)

**CRUD de Roles de Usuario en Torneos (User roles within a specific Event):**

* **C**rear Rol (Asignar rol de co-organizador/arbitro a alguien)  
* **R**eer Rol (Ver roles asignados en un torneo)  
* **U**pdate Rol (Cambiar rol de un usuario en un torneo)  
* **D**elete Rol (Remover rol de un usuario en un torneo)

## ---

**3\. Fase de Diseño**

**Objetivo:** Crear el diseño visual y técnico detallado de la aplicación, traduciendo los requisitos en una experiencia de usuario intuitiva, atractiva para inversores y usuarios, y una estructura técnica clara para el desarrollo.

### **Filosofía de Diseño: Inspiración Deportiva y Conexión Social**

La AppFlutter buscará una estética moderna, limpia y dinámica, que resuene con el espíritu deportivo. Nos inspiraremos en la eficiencia de la navegación y la claridad de los feeds de redes sociales populares como **X (Twitter) y Facebook**, pero adaptando y redefiniendo estos patrones para crear una experiencia **únicamente centrada en el deporte y la organización de eventos**. No será una copia, sino una evolución que integra lo mejor de estas plataformas con las necesidades específicas de la comunidad deportiva.  
El diseño hará énfasis en:

* **Contenido Primero:** Destacar eventos, logros, estadísticas y publicaciones.  
* **Interacción Fluida:** Facilitar la conexión entre usuarios, la participación en eventos y la gestión de torneos.  
* **Legibilidad y Accesibilidad:** Asegurar que la información sea fácil de consumir y la app usable para todos.  
* **Identidad Vibrante:** Utilizar colores y tipografías que transmitan energía y pasión por el deporte.

### **Identidad Visual: Colores y Tipografía**

#### **Paleta de Colores**

1. **Color Primario (Dominante):** **Azul Deportivo Vibrante (\#1E90FF \- Dodger Blue)**  
   * **Justificación:** Transmite confianza, profesionalismo, energía y el dinamismo asociado a los deportes.  
   * **Modo Claro:** Se usará para elementos clave como barras de navegación, botones principales, titulares y acentos.  
   * **Modo Oscuro:** Mantendrá su vibración, pero podría usarse en un tono ligeramente más claro o desaturado si es necesario para el contraste sobre fondos muy oscuros, o como un acento brillante en elementos importantes.  
2. **Color Secundario / Acento:** **Naranja Energético (\#FF6F00 \- Orange Peel)**  
   * **Justificación:** Aporta contraste, vitalidad y se usará para llamadas a la acción (CTAs), elementos interactivos destacados, iconos de notificación y barras de progreso.  
   * **Modo Claro/Oscuro:** Mantendrá su uso como elemento de acento para captar la atención, con ajustes mínimos para asegurar la legibilidad en ambos temas.  
* **Neutros:** Una gama de grises para fondos, texto secundario y elementos de interfaz que no necesiten destacar, junto con blanco y negro puro para fondos y texto principal en los respectivos modos.  
  * **Modo Claro:** Fondos claros, con el color principal del fondo en **\#E9ECEF**. Texto oscuro (\#212529).  
  * **Modo Oscuro (Opciones de Usuario):** El usuario podrá elegir entre dos variantes de modo oscuro, ambas optimizadas para diferentes preferencias visuales:  
    * **Oscuro (Gris Profundo \- \#212121):** Fondos en un tono de gris muy oscuro que ofrece un contraste suave y reduce la fatiga visual sin ser un negro absoluto. Ideal para quienes prefieren un modo oscuro menos "duro". Texto claro (\#FFFFFF, \#E0E0E0).  
    * **Oscuro Absoluto (Negro Puro \- \#000000):** Fondos totalmente negros, ideal para dispositivos con pantallas OLED o para usuarios que prefieren la máxima reducción de luz y un contraste extremo. Texto claro (\#FFFFFF, \#E0E0E0).

#### **Tipografía (Máximo 2 para coherencia)**

1. **Para Titulares y Elementos Destacados:** **Oswald**  
   * **Justificación:** Es una fuente sans-serif audaz, condensada y moderna que transmite fuerza y dinamismo, ideal para nombres de eventos, titulares de sección y elementos que requieren impacto visual.  
2. **Para Cuerpo de Texto y Componentes Generales:** **Inter**  
   * **Justificación:** Una fuente sans-serif altamente legible, optimizada para pantallas y que ofrece una gran versatilidad para diferentes pesos y tamaños, asegurando una lectura cómoda en todo tipo de contenido (descripciones, publicaciones, datos de perfil).

### **Estructura de Navegación y UI General**

#### **Barras de Navegación**

* **Móvil (Barra Inferior):** Similar a Facebook/Instagram, una **barra de navegación inferior (Bottom Navigation Bar)** con iconos claros para las secciones principales:  
  * Home/Feed (Ícono de casa o feed)  
  * Eventos (Ícono de calendario o trofeo)  
  * Perfil (Ícono de usuario)  
  * Grupos/Comunidad (Ícono de personas)  
  * Notificaciones (Ícono de campana, con badge numérico)  
* **Web/Tablet (Barra Lateral Izquierda):** Inspirada en **X (Twitter)**, una **barra lateral de navegación fija a la izquierda** con enlaces a las mismas secciones principales, utilizando iconos y etiquetas de texto para mayor claridad en pantallas más grandes. Esto optimiza el espacio horizontal y mantiene la consistencia con la versión móvil.

#### **Sistema de Notificaciones**

* **Similar a Facebook:** Un icono de campana en la barra superior (o en la barra de navegación inferior/lateral) que muestra un **badge numérico** con el recuento de notificaciones no leídas.  
* Al hacer clic, se abre una **pantalla dedicada de notificaciones** con un listado cronológico, categorizadas visualmente (ej. "Nueva invitación a evento", "Nuevo seguidor", "Publicación con likes", "Cambio de resultado en torneo").

#### **Diseño de la Función "Gente que Quizás Conozcas"**

* **Ubicación:** Un bloque o sección discreta en el feed social o en una pestaña dedicada de "Explorar/Descubrir".  
* **Criterios:** Utilizará una combinación de:  
  * **Ubicación Cercana:** Usuarios en la misma área geográfica.  
  * **Intereses en Común:** Deportes favoritos, eventos a los que han asistido o planean asistir.  
  * **Conexiones de Segundo Grado:** Amigos de tus amigos.  
  * **Datos de Perfil:** Otros datos que el usuario elija compartir.  
* **UI:** Mostrará tarjetas de perfil pequeñas con foto, nombre y un botón directo para "Seguir" o "Añadir Amigo".

### **Diseño de Flujos y Pantallas Clave (Especificaciones Detalladas)**

#### **Pantalla Principal / Feed Social**

* **Diseño:** La pestaña principal será un **feed scrollable** donde se mezclan publicaciones de usuarios seguidos, actualizaciones de eventos (ej. "¡El equipo X ganó el torneo Y\!"), logros de la comunidad y recomendaciones.  
* **Prioridad:** El contenido más relevante y reciente aparecerá primero. Las imágenes y videos de publicaciones y eventos serán prominentes.

#### **Pantalla de Explorar Eventos**

* **Listado Principal:** Los torneos y eventos se mostrarán en una lista (ListView en Flutter) ordenada **de más cerca a más lejos** de la ubicación actual del usuario.  
* **Filtros y Preferencias:**  
  * Filtros claros por deporte/actividad (basado en las preferencias del usuario o seleccionables).  
  * Opciones para filtrar por fecha, tipo (público/privado).  
  * **Eventos de Interés:** El sistema priorizará mostrar eventos que coincidan con los deportes favoritos del usuario.  
* **Indicación Público/Privado:** Cada tarjeta de evento en la lista tendrá un **pequeño icono visual** (ej. un candado para privados) y/o una etiqueta discreta para indicar su tipo.  
* **Invitaciones Explícitas:** Si un usuario es **invitado explícitamente por el creador/organizador** a un evento (público o privado), este evento aparecerá **siempre en la parte superior de la lista**, destacado con una **banda de color o una insignia de "Invitación"**, y una pequeña **alerta visual** para asegurar que no se pase por alto.

#### **Privacidad en el Listado y Detalles de Eventos**

* **Vista en Lista (Información Limitada):** Para la privacidad y la limpieza de la interfaz, en la lista principal de eventos solo se mostrará:  
  * Nombre del Evento  
  * Ubicación (con la distancia calculada al usuario)  
  * Descripción Corta  
  * Puestos Libres / Cupos disponibles  
* **Vista de Detalles (Acceso Condicional):** Para ver más detalles del evento (participantes, reglas completas, resultados, etc.), el usuario debe **seleccionar el evento**.  
  * **Eventos Públicos:** Acceso inmediato a todos los detalles.  
  * **Eventos Privados:** Al intentar ver los detalles, se presentará un **modal o pantalla de solicitud de contraseña**. Sin la contraseña correcta, el usuario no podrá ver ninguna información adicional ni interactuar con el evento (ej. unirse).  
* **Creador/Organizador Siempre Visible:** En la vista de detalles de cualquier evento (público o privado), la información del Creador o Director del Evento siempre será visible.

#### **Flujo de Creación de Evento**

Este será un flujo guiado y claro:

1. **Nombre del Evento:** Campo de texto obligatorio.  
2. **Deporte o Actividad:** Un selector que muestre la lista de deportes disponibles.  
3. **Cantidad de Integrantes / Equipos:**  
   * El campo se adaptará al deporte elegido (ej. para fútbol, puede ser número de equipos; para ajedrez, número de jugadores).  
   * Habrá un límite lógico basado en el deporte (ej. máximo 20 equipos de fútbol, 2 jugadores de ajedrez).  
   * El usuario especificará cuántos equipos/jugadores participarán.  
4. **Público vs. Privado:** Un toggle switch o botones de radio claros para elegir.  
   * **Si es Privado:** Se habilitarán dos campos de texto adicionales: Contraseña del Evento y Repetir Contraseña. Estos campos tendrán validación de coincidencia y fortaleza.  
5. **Fechas y Horarios:** Selectores intuitivos para Fecha de Inicio, Fecha de Fin, Hora de Inicio y Hora de Fin.  
6. **Ubicación:** Campo de texto para la dirección y/o integración con un mapa para seleccionar un punto exacto.  
7. **Descripción Detallada y Reglas:** Campos de texto multilinea.  
8. **Organización de Equipos y Horarios (Nueva Pestaña/Paso):** Después de la información básica del evento, se abrirá una **nueva pestaña o sección dedicada** donde el organizador podrá:  
   * **Asignar Participantes/Equipos a Franjas Horarias:** Visualizar las franjas horarias disponibles y arrastrar/soltar (o seleccionar) equipos/participantes en ellas.  
   * **Organización Automática:** Un botón para "Generar Horarios Automáticamente" que, basado en el número de participantes/equipos y la duración total del evento, proponga una distribución de partidos/rondas en las franjas horarias disponibles.  
   * **Organización Manual:** Permitir al organizador arrastrar y soltar participantes/equipos y asignar horarios individualmente, con validación para evitar solapamientos.

#### **Perfiles de Usuario**

* El ID Único de App (@miusuario\_id) para buscar personas será prominente en el perfil del usuario, junto a un botón para copiarlo o compartirlo fácilmente.  
* **Información en Creación de Usuario:** Al momento del registro (o como parte del onboarding inicial), se solicitará al usuario la siguiente información:  
  * Nombre Completo  
  * Apodo / Nombre de Usuario (que podría ser el @uniqueAppId o un campo separado)  
  * Fecha de Nacimiento  
  * Deportes Favoritos (selección múltiple de una lista predefinida)  
  * Género (opcional)  
  * Ubicación Predeterminada (ciudad/municipio)  
  * Foto de Perfil (opcional, con opción de subir o tomar foto)  
  * Mini-biografía (opcional)

### **Límites Sociales y Escalabilidad (Contextualización)**

Los límites propuestos para las conexiones sociales (máximo 500 amigos, máximo 50 grupos, máximo 1000 seguidos) son estándar para las redes sociales y se consideran generosos para fomentar la interacción sin sobrecargar la experiencia del usuario o el rendimiento inicial del sistema.  
Contexto con la población de Antioquia:  
El departamento de Antioquia, Colombia, tiene una población estimada de aproximadamente 6.8 millones de habitantes. Si incluso una fracción de esta población adopta AppFlutter (por ejemplo, el 1%), estaríamos hablando de 68,000 usuarios potenciales. Con los límites definidos, cada uno de estos usuarios puede establecer un número significativo de conexiones y participar en comunidades, lo que demuestra la gran escalabilidad de la red social de la aplicación. Estos límites garantizan que la base de datos pueda manejar eficientemente la red de conexiones sin comprometer el rendimiento, y que cada usuario pueda tener una experiencia social rica y personalizada.

### **Próximos Pasos en Diseño**

Con estos detalles definidos, el siguiente paso práctico sería la creación de los **Mockups de Alta Fidelidad** en una herramienta de diseño. Estos mockups servirán como el blueprint visual para la fase de desarrollo. Además, comenzaremos a bosquejar las **Reglas de Seguridad de Firebase Firestore** basándose en los flujos de privacidad y acceso definidos.

## ---

**4\. Fase de Desarrollo**

**Objetivo:** Implementar las funcionalidades definidas en las fases anteriores.

### **Actividades**

* **Configuración del Proyecto:** Inicializar el proyecto Flutter, configurar Firebase (añadir firebase\_core, firebase\_auth, cloud\_firestore, firebase\_storage, geolocator, table\_calendar a pubspec.yaml, configurar archivos de plataforma google-services.json, GoogleService-Info.plist).  
* **Autenticación:** Implementar registro, inicio de sesión, y restablecimiento de contraseña con Firebase Authentication, incluyendo validación y mensajes de error.  
* **CRUD de Perfiles:** Crear interfaces para crear, leer, actualizar y eliminar perfiles de usuario, incluyendo la carga de imágenes a Firebase Cloud Storage y la generación/manejo de IDs de usuario únicos.  
* **CRUD de Eventos:** Desarrollar la lógica y las pantallas para que los organizadores creen y gestionen eventos (públicos/privados, cupos, contraseña, organización de equipos/horarios), y los usuarios busquen, filtren (por ubicación/calendario/preferencias) y se inscriban (con validación de contraseña para privados).  
* **Funcionalidades Sociales:** Implementar seguir/dejar de seguir, feed de publicaciones, y la capacidad de crear posts (texto, imágenes). Desarrollar la creación y gestión de grupos, y la funcionalidad de invitación. Implementar la sección "Gente que Quizás Conozcas".  
* **Sistema de Ranking:** Desarrollar la lógica para calcular y mostrar rankings (posiblemente usando Cloud Functions para el cálculo).  
* **Notificaciones:** Integrar Firebase Cloud Messaging (FCM) para notificaciones push de eventos, nuevas publicaciones, invitaciones. Implementar la pantalla de listado de notificaciones.  
* **Refactorización y Optimización de Código:** Mejorar la calidad, legibilidad y rendimiento del código de forma continua.  
* **Control de Versiones:** Uso constante de Git para la gestión de código y colaboración.

## ---

**5\. Fase de Pruebas**

**Objetivo:** Identificar y corregir errores, asegurar que la aplicación cumple con los requisitos.

### **Actividades**

* **Pruebas Unitarias:** Probar funciones y clases individuales (ej. métodos de los modelos de Dart, lógica de servicios, validadores de formulario).  
* **Pruebas de Widgets:** Probar componentes individuales de la UI de Flutter de forma aislada, incluyendo diferentes estados (carga, error, vacío), y los modos claro/oscuro.  
* **Pruebas de Integración:** Probar cómo interactúan diferentes partes de la aplicación juntas (ej. registro de usuario y la posterior lectura de su perfil desde Firestore, creación de evento y su aparición en la lista, el flujo completo de creación de eventos con organización de horarios).  
* **Pruebas de Funcionalidad:** Verificar que todas las características funcionan según lo especificado en los requisitos, incluyendo flujos complejos (ej. inscripción a evento privado con contraseña correcta/incorrecta, búsqueda y filtrado de eventos por ubicación y preferencias).  
* **Pruebas de Rendimiento:** Evaluar la velocidad y la capacidad de respuesta de la aplicación bajo diferentes cargas, especialmente en el feed social y las listas de eventos con muchos datos.  
* **Pruebas de Usabilidad:** Evaluar la facilidad de uso de la aplicación con usuarios reales o simulados, prestando atención a la claridad de los mensajes y la intuición de la navegación.  
* **Pruebas de Seguridad:** Evaluar vulnerabilidades de la aplicación y de las reglas de seguridad de Firebase (ej. acceso no autorizado a datos privados, inyección de datos maliciosos, validación de contraseñas de eventos).  
* **Pruebas de Compatibilidad:** Asegurar que la aplicación funciona correctamente en diferentes dispositivos, tamaños de pantalla y versiones de SO (iOS y Android), y en los diferentes modos de tema (claro/oscuro).  
* **Pruebas de Aceptación de Usuario (UAT):** Usuarios beta o interesados prueban la aplicación para asegurar que cumple con sus expectativas y necesidades.

## ---

**6\. Fase de Lanzamiento**

**Objetivo:** Poner la aplicación a disposición de los usuarios finales.

### **Actividades**

* **Preparación para el Lanzamiento:**  
  * Finalizar el branding (nombre, logo).  
  * Crear capturas de pantalla y videos promocionales atractivos para las tiendas, destacando las funcionalidades sociales y de organización.  
  * Redactar la descripción de la aplicación para Google Play Store y Apple App Store, enfatizando el "Facebook de los deportes" y la capacidad de conectar y organizar.  
  * Configurar la política de privacidad y los términos de servicio.  
* **Compilación y Firma de la Aplicación:** Generar los paquetes de lanzamiento (APK/App Bundle para Android, IPA para iOS).  
* **Envío a las Tiendas de Aplicaciones:**  
  * Subir la aplicación a Google Play Console.  
  * Subir la aplicación a Apple App Store Connect.  
  * Pasar el proceso de revisión de ambas tiendas.  
* **Marketing y Promoción:** Dar a conocer la aplicación a tu público objetivo (redes sociales, comunidades deportivas, clubes, gimnasios, etc.), enfatizando su propuesta de valor.

## ---

**7\. Fase de Mantenimiento y Mejora Continua (Post-Lanzamiento)**

**Objetivo:** Mantener la aplicación funcional, segura y relevante.

### **Actividades**

* **Monitoreo:** Vigilar el rendimiento de la aplicación, errores (Firebase Crashlytics), uso de funcionalidades y satisfacción del usuario.  
* **Recopilación de Feedback:** Escuchar activamente a los usuarios, recopilar sugerencias y reportes de errores a través de canales dedicados (ej. encuestas en la app, soporte al cliente).  
* **Actualizaciones y Corrección de Errores:** Lanzar nuevas versiones con correcciones de errores, mejoras de rendimiento y parches de seguridad.  
* **Nuevas Funcionalidades:** Planificar e implementar nuevas características basadas en el feedback del usuario y la visión a largo plazo (ej. chat dentro de grupos, integración de resultados más complejos, streaming de eventos, monetización avanzada).  
* **Optimización de Costos:** Monitorear y optimizar los costos de Firebase de forma continua para asegurar la rentabilidad.

[image1]: <data:image/png;base64,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>