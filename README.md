# Evaluación tercer trimestre.
# Aprender haciendo. 

**El rol del técnico: De la pasividad del consumidor a la autonomía del creador**

Un técnico en electrónica no es un usuario final; es un profesional que diseña, diagnostica e interactúa con la infraestructura crítica de los sistemas. En este nivel, debe resolver tareas operativas básicas, como descargar un instalador de internet, leer un manual o documentación. El conocimiento técnico actual no se memoriza: se investiga y se ejecuta de forma proactiva. Romper con el modo "consumidor de aplicaciones" y adoptar el rol de estudiante ACTIVO implica que el alumno debe ser capaz de autogestionar su entorno informático, experimentar sin miedo al error, buscar soluciones de forma independiente en la documentación y entender que configurar sus herramientas de software es el primer paso para dominar su propio hardware.

---

La llegada de la banda ancha, la fibra óptica, las redes móviles (4G/5G) y los protocolos descentralizados permitieron que miles de desarrolladores en diferentes continentes colaboren en tiempo real. **GitHub existe gracias a la velocidad y estabilidad de las telecomunicaciones actuales.** Sin redes globales de baja latencia, compartir repositorios masivos, clonar dependencias en segundos o coordinar *pull requests* globales sería imposible. Al mismo tiempo, toda la infraestructura moderna de telecomunicaciones corre sobre código libre. El núcleo de internet (servidores DNS, routers de borde, servidores en la nube) funciona bajo **Linux**. Los protocolos de red, la virtualización de funciones de red (NFV) y las redes definidas por software (SDN) se desarrollan bajo licencias abiertas porque la industria necesita estándares interoperables, seguros y transparentes que ninguna empresa de software cerrado puede garantizar de forma aislada. Para profundizar en estos conceptos claves, se propone como actividad practica la realización de diversas consignas a traves del acompañamiento del docente. 

---
La necesidad técnica de un sistema de control de versiones en **Bell** se volvió crítica con la introducción del **No. 1 ESS (Electronic Switching System) en la decada del '60**, la primera central telefónica a gran escala controlada por un programa informático (software almacenado). Hasta ese momento, el mantenimiento se realizaba de manera mecánica sobre el hardware, pero la llegada del _Stored Program Control_ (SPC) trasladó la inteligencia de conmutación de la red a millones de líneas de código. El estándar de calidad exigido para la red telefónica era el estricto criterio de alta disponibilidad conocido como **'Five Nines' (99.999 % de disponibilidad)**, el cual dictaba que el servicio no podía interrumpirse por más de **5 minutos acumulados en todo un año**. Durante la crisis del software de principios de los 70, la inexistencia de herramientas de control obligaba a los programadores a aplicar parches (_patches_) y modificaciones directamente en caliente sobre el código de producción de las centrales. La falta de trazabilidad provocaba que una modificación manual errónea para corregir un fallo local corrompiera de forma invisible la memoria de conmutación global de la central, desencadenando efectos dominó que **tumbaban por completo el servicio telefónico de distritos enteros**. Ante la imposibilidad humana de aislar qué línea de código exacta había roto la continuidad de la red o cómo retornar al estado estable anterior sin prolongar el apagón de las comunicaciones, **Marc Rochkind diseñó SCCS en Bell Labs en 1970**. El control de versiones nació, fundamentalmente, como un protocolo de contingencia de ingeniería eléctrica para auditar cambios y garantizar la reversibilidad inmediata del software antes de violar las tolerancias de tiempo de caída (_downtime_) de la infraestructura estatal de telecomunicaciones.

- **1972-1975 - SCCS (Source Code Control System):** Desarrollado por **Marc Rochkind** en los Laboratorios Bell para computadoras IBM. Fue el primer sistema formal de control de versiones. Funcionaba de forma local y permitía registrar un historial de cambios para recuperar versiones anteriores.
- **1982 - RCS (Revision Control System):** Una alternativa de código abierto que mejoró la velocidad al guardar solo las diferencias (deltas) entre una versión y otra, en lugar de duplicar todo el archivo.
- **1990 en adelante - Sistemas Centralizados (CVS y SVN):** Permitieron que los desarrolladores compartieran código a través de un servidor central, sentando las bases del trabajo en equipo moderno.
- **2005 - Git (Sistemas Distribuidos):** Creado por **Linus Torvalds** para el desarrollo del kernel de Linux. Cambió el paradigma al permitir que cada desarrollador tuviera una copia completa de todo el historial en su propia máquina, eliminando la dependencia absoluta de un servidor central.

El versionamiento de software nació para resolver problemas operativos concretos de la ingeniería:

- **Trazabilidad e Historial:** Permite auditar el código. Si un sistema falla, el control de versiones permite identificar con precisión exacta qué línea de código se modificó, qué día, a qué hora y qué desarrollador la escribió.
- **Desarrollo en Paralelo (Ramificación):** En proyectos grandes, un equipo puede estar corrigiendo un fallo urgente en el sistema de producción mientras otro equipo desarrolla una función completamente nueva. Las "ramas" (*branches*) permiten que ambos trabajen sobre el mismo código base sin interferir ni pisar el trabajo del otro.
- **Reversibilidad (Puntos de Restauración):** Funciona como una red de seguridad. Si una nueva actualización rompe el firmware o la comunicación de un sistema, el control de versiones permite revertir el estado del código al último punto estable en cuestión de segundos.
- **Gestión de Dependencias y Integración:** El software moderno no es una pieza única; interactúa con librerías, protocolos y sistemas externos de software libre. El versionamiento permite asegurar que los componentes sean compatibles entre sí mediante nomenclaturas claras (como el versionamiento semántico).

En las telecomunicaciones actuales, el hardware tradicional (routers, switches, antenas fijas) esta siendo desplazado gracias a las codificaciones-decodificaciones por el software.

- **SDR (Radio Definida por Software):** Hoy las frecuencias, filtros y protocolos de radio se programan (por ejemplo, con GNU Radio). Los algoritmos y herramientas para procesar señales satelitales o redes celulares están alojados en GitHub.
- **Redes basadas en Software (SDN) e Infraestructura como Código:** Los ingenieros de telecomunicaciones ya no configuran equipos consola por consola; escriben scripts de automatización. Esos scripts se guardan, prueban y despliegan usando **Git**. Y se comparten por diversos repositorios. 

El actual desarrollo de software se hace en grupos de trabajo numerosos que la mas usual de las veces no se encuentra compartiendo tiempo y espacio físicos. La versionamiento y el control de versiones nos permite, como ya mencionamos **Evitar el caos del "Código_Final_v2_este_sí.ino":** y **Trazabilidad:** Si el circuito o el código falla tras un cambio en la configuración de los pines de comunicación, Git les permite "volver en el tiempo" al punto exacto donde el sistema funcionaba.

El software libre no es "software gratis hecho por aficionados", sinó:

- **Firmwares Industriales:** Proyectos masivos de hardware abierto como *Marlin* (para impresoras 3D) o *GRBL*, para máquinas CNC como la que usa bCNC, o Universal-GCode-Sender nacen y se mantienen en GitHub gracias a miles de colaboradores del mundo.
- **El portafolio del técnico:** GitHub funciona actualmente como portafolio. Un profesional técnico que comparte sus proyectos, sus esquemas de PCB (de KiCad, por ejemplo) y sus códigos de comunicación a un repositorio público, le demuestra al mercado laboral o a la universidad que sabe trabajar con estándares profesionales.


---


En telecomunicaciones, un error de software o una vulnerabilidad oculta no significa simplemente que se cierre una aplicación; significa la caída de una red eléctrica, el hackeo de una central de telemetría industrial o la interrupción de las comunicaciones de una ciudad entera.
Cuando una empresa o un estado compra un software cerrado (propietario) para gestionar sus routers o servidores, está comprando una **"caja negra"**. Nadie, excepto los programadores de esa corporación, sabe exactamente qué hace ese código por dentro.

- **El peligro de las "puertas traseras" (Backdoors):** En el software cerrado es imposible verificar si existen líneas de código diseñadas para espiar datos, enviar telemetría no autorizada o permitir accesos remotos vulnerables.
- **La ventaja de la Auditoría Abierta:** Con el software libre, el código fuente de los protocolos de red (como el kernel de **Linux**, los servidores DNS **BIND**, o los sistemas de enrutamiento) está expuesto públicamente en repositorios a la vista de millones de ingenieros y especialistas en ciberseguridad del mundo. Cualquier error de desbordamiento de memoria, falla en la encriptación o vulnerabilidad se detecta, se reporta y se parchea de forma comunitaria en cuestión de horas. La seguridad no se basa en el "secreto" (ocultar cómo funciona el programa), sino en la **transparencia absoluta** (demostrar matemáticamente que el programa es seguro).

Las telecomunicaciones exigen que dispositivos fabricados por distintas empresas, en distintas partes del mundo y con arquitecturas de hardware completamente diferentes, hablen **exactamente el mismo idioma** y se entiendan sin la menor falla.
Si el núcleo de internet dependiera de software cerrado, cada corporación intentaría imponer su propio estándar para monopolizar el mercado (creando ecosistemas incompatibles entre sí). El código libre resolvió esto mediante los **estándares interoperables**:

- **Consorcios abiertos:** Protocolos esenciales como **MQTT** (para vincular sensores e IoT), los protocolos de enrutamiento de internet, o la virtualización de redes (NFV/SDN) se discuten y desarrollan bajo licencias abiertas (como la Fundación Linux o el IETF).
- **Garantía de compatibilidad:** Al ser un código libre y compartido en repositorios, cualquier fabricante de hardware (desde una multinacional que hace routers de borde hasta los estudiantes programando un Arduino) puede clonar e implementar la **misma pila de protocolos exacta** en sus equipos. Esto garantiza que una placa electrónica diseñada en el taller de la escuela técnica se pueda conectar, comunicar e interoperar perfectamente con la infraestructura en la nube de cualquier servidor del planeta, sin tener que pagar regalías ni depender de un puente de software propietario.

---

El técnico en electrónica debe entender que **configurar codigo e interfaces maquina-computador es parte de su rol profesional**. Al aprender a usar repositorios, el estudiante adquiere la capacidad de:

1. **Inspeccionar el código** de las librerías de comunicación que compilará en un microcontrolador o de una interfaz. A fin de lograr su minima configuración operativa. 
2. **Verificar la procedencia y la estabilidad** de un protocolo antes de implementarlo en un sistema real.
3. **Asegurar la interoperabilidad** de sus diseños, garantizando que sus circuitos usen estándares abiertos que no dejen al cliente (o a la fábrica donde trabaje) atado de pies y manos a un único proveedor de software.

Los estudiantes manejan el hardware (Arduino), pero son "inquilinos" de sus interfaces. Se presenta el concepto de **soberanía digital** como un principio de autonomía profesional:

- **De consumidores pasivos a administradores reales:** Saber instalar herramientas desde la terminal, compilar un software de control numérico o configurar una comunicación serial en la PC los transforma en **dueños reales de su máquina**. 
- **Seguridad y auditoría en electrónica industrial:** En entornos industriales o de telecomunicaciones, no se puede meter una "caja negra" de software cerrado a controlar una red o una máquina CNC. Entender los repositorios y el código abierto les da la capacidad de auditar, modificar y adaptar el software a las necesidades físicas del hardware que están diseñando, garantizando que ellos (y no una corporación externa) tienen el control total del sistema.

Con la llegada de los **Agentes de IA (LLMs agénticos)** —sistemas que no solo chatean, sino que ejecutan acciones autónomas en la PC, crean ramas de Git, despliegan servidores y conectan APIs— la necesidad de entender cómo se comparte y estructura el código se vuelve **urgente**:

- **El Agente como un "empleado" de software:** En el corto plazo, los estudiantes no escribirán cada línea de código; interactuarán con agentes autónomos que resolverán problemas de programación y configuración de redes. Pero para dirigir a estos agentes, el técnico debe actuar como un **arquitecto o supervisor**. Si el estudiante no entiende la estructura de un repositorio, qué es un *commit*, cómo se gestionan las dependencias o cómo se conecta el código con los puertos de la PC, será incapaz de auditar lo que el agente propone o ejecuta.
- **Git como el idioma para auditar a la IA:** Cuando un agente de IA realice cambios automáticos en el firmware de un sistema de telecomunicaciones o de un Arduino, el canal profesional para revisar, aprobar o revertir esas acciones será **Git**. Los repositorios se convierten en la "caja negra" o el registro de vuelo donde los humanos controlamos la trazabilidad de lo que hacen los agentes de IA.
- **La paradoja de compartir:** Los LLMs se entrenan y mejoran gracias al código abierto compartido en plataformas como GitHub. Asi como redes P2P con contenido pirata. Si las nuevas generaciones no entienden el valor de documentar, estructurar y compartir código de calidad en repositorios, la fuente de conocimiento que alimenta a las propias IA se estancará. https://annas-archive.gl/blog/llms-txt.html

Para la mayoría de los usuarios, internet es una pantalla de consumo masivo (redes sociales, streaming, búsquedas en Google). Para un técnico, internet es una **red de infraestructura y transferencia de datos**.
El estudiante debe desarrollar la capacidad de investigar, consumir y explotar los servicios profundos de la red:

- **Uso de Repositorios:** Dejar de depender del "instalador comercial" o de páginas web de descargas dudosas. El técnico debe ser capaz de ir directamente a la fuente del código, entender la estructura de un repositorio, clonarlo mediante la terminal y ejecutar o compilar el software (como configurar las dependencias en Python para correr herramientas especificas).
- **Interconexión mediante APIs:** En el contexto de las telecomunicaciones y el IoT (Internet de las Cosas), los dispositivos no operan aislados. Los estudiantes deben aprender a conectar un hardware (un microcontrolador) con servicios externos mediante **APIs** (Interfaces de Programación de Aplicaciones). Esto significa pasar de prender un LED local a consumir datos de una API meteorológica para automatizar un sistema de riego, o enviar datos de telemetría de un sensor a un servidor en la nube mediante protocolos abiertos como MQTT o HTTP.

En electrónica no existe una "única solución correcta"; existen soluciones adecuadas para contextos específicos. El estudiante no debe replicar tutoriales de forma automática, sino aprender a auditar sus propias decisiones tecnológicas:

- **Análisis de restricciones:** Ante una necesidad (por ejemplo, procesar las imágenes de una línea de ensamblaje o mover un simulador 2DOF), el estudiante debe investigar y decidir: *¿Este algoritmo lo puede procesar el microcontrolador en tiempo real o necesito derivar el cálculo pesado a una PC mediante visión artificial (OpenCV)? ¿Qué protocolo de comunicación me conviene usar según la distancia y el ruido electromagnético?*
- **Evaluación de viabilidad y licencias:** Aprender a leer la documentación técnica de un repositorio para verificar si el software es compatible con su hardware, si la comunidad lo sigue actualizando (revisando los últimos *commits* en GitHub) y si la licencia permite su modificación para la solución que necesitan implementar.

El trabajo en equipo en el ámbito técnico consiste en **coordinar la lógica y el diseño de un sistema complejo** sin que el trabajo de uno rompa el del otro.

- **Coordinación real sobre el código:** Al utilizar Git, los grupos de trabajo (de 3 o 4 estudiantes) deben aprender a operar bajo un flujo profesional. Cada estudiante trabaja en su propia rama (*branch*) desarrollando un módulo específico del proyecto (por ejemplo: uno la interfaz en la PC, otro el código de control del motor en Arduino y otro la comunicación serie).
- **Integración periódica:** Se elimina la práctica de juntar todo a último momento. Los estudiantes adquieren el hábito de realizar entregas parciales y periódicas (*commits* y *pull requests*), lo que les permite fusionar sus avances semanalmente en el repositorio central del grupo. Esto no solo simula el entorno laboral real de la ingeniería, sino que les enseña a resolver conflictos de código de manera lógica y ordenada.

---

	Objetivo: Que el estudiante tecnico logre comprender la diversidad el campo actual de las telecomunicaciones digitales. Para esto es necesario forzosamente familiarizar al estudiante a interactuar desde la linea de comandos de sus dispositivos digitales, a fin de exponerlo de forma practica a un sin fin de alternativas a la web, asi como sus decenas de protocolos menos amigables al usuario final. Utilizando la web como recurso de visualizacion y comprendiendo su lugar en el modelo teorico actual de servicios. 


Se propone como herramienta didactica una serie de trabajos practicos que se realizaran en colaboración con el docente. Se otorgan libertades al estudiante sobre la intencion de su exploración. Siendo evaluados criterios alternativos al resultado final. Al dia de la fecha, las ultimas dos semanas estuvimos instalando y utilizando las siguientes herramientas informaticas:
- Git 
- Python3.x
- Opencode

Creamos una cuenta en www.Github.com, alli dentro creamos un repositorio y lo vinculamos con una carpeta/proyecto de nuestra computadora personal. Luego hacemos "push" sobre un archivo "ejemplo.py" que creamos, para que de esta forma realicemos nuestro primer-commit.

Luego, exploramos diferentes repositorios y su configuración interna, el primero de ellos será grbl, la libreria que permite a un Arduino328 funcionar como interface-USB para manejar mediante codigo G, a traves de un puerto serie, un Control Numerico Computalizado, como una impresora 3D, fresadora, grabadora laser, o brazo robot. Ahi dentro, será ocación de conversar sobre la tasa de baudios asignada para que funcionen correctamente la conexion, y cual es la diferencia con la tasa de bits. Así como las diferentes interfaces de usuario y sus propiedades y limitaciones. 
Nos serviremos de que estos programas GCodeSender, suelen ofrecer un servicio de API, y servidor web a modo de "Pendant" o control rapido. Para configurar, y evaluar su impacto en el usuario, con ayuda de una ia-agentica (Opencode, aider, claude-code; en reemplazo de los viejos buscadores indexados de la web), exploraremos que sucede si intantamos acceder a esta interface fuera de su red interna, y luego de su red local. 


Opciones ejemplo: Usar un software de control como **bCNC** e instalar el firmware articulado en el Arduino./ Utilizar el Arduino como plataforma MIDI y configurar la conexion con DAW / Descargar sofware de reconocimiento de vision en python articulando la comunicacion con un Arduino o plataforma similar para aplicaciones por ejemplo de asistencia, seguimiento de objetivos, contadores de estacionamiento etc. 




### Criterios de evaluación

| Criterio                                      | 4 — Logrado con solidez                                                                                                               | 3 — Logrado                                                                  | 2 — En proceso                                                          | 1 — Inicial                                                                                |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Uso del tiempo de trabajo**                 | Aprovecha el tiempo de clase para investigar, consultar y avanzar autónomamente.                                                      | Utiliza adecuadamente el tiempo y realiza consultas cuando las necesita.     | Necesita recordatorios frecuentes para aprovechar el tiempo.            | No utiliza el tiempo disponible para avanzar en el proyecto.                               |
| **Investigación y formulación de hipótesis**  | Investiga alternativas, formula hipótesis y fundamenta sus decisiones considerando uso, accesibilidad, estabilidad y aspectos éticos. | Investiga alternativas y fundamenta las principales decisiones.              | Investiga de manera parcial y fundamenta pocas decisiones.              | Adopta soluciones sin investigación ni fundamentación.                                     |
| **Uso del repositorio y commits**             | Realiza commits periódicos y significativos que permiten reconstruir claramente el proceso de desarrollo.                             | Mantiene el repositorio actualizado y realiza commits durante el desarrollo. | Los commits son escasos, irregulares o poco significativos.             | El repositorio presenta únicamente una entrega final o evidencia insuficiente del proceso. |
| **Trazabilidad del aporte individual**        | El historial permite identificar claramente el aporte y la evolución del trabajo de cada integrante.                                  | El aporte individual puede reconocerse en el repositorio.                    | El aporte individual resulta parcialmente identificable.                | No existe evidencia suficiente del aporte individual.                                      |
| **Integración del trabajo grupal**            | Integra correctamente los distintos aportes en una solución común y funcional.                                                        | Los aportes individuales se integran adecuadamente.                          | La integración presenta dificultades o requiere intervención frecuente. | Los aportes permanecen aislados o no conforman una solución común.                         |
| **Resolución de problemas**                   | Detecta problemas, plantea alternativas, prueba soluciones y fundamenta la opción adoptada.                                           | Identifica problemas y encuentra soluciones adecuadas.                       | Requiere asistencia frecuente para resolver problemas.                  | No logra avanzar ante dificultades sin intervención externa.                               |
| **Autonomía operativa y rol activo**           | Resuelve de forma independiente la instalación, actualización y configuración de sus herramientas informáticas. Lee documentación técnica (ReadMe) antes de consultar al docente. | Configura y prepara sus herramientas con mínima asistencia. Logra destrabarse solo buscando información en la red o en los repositorios. | Muestra una actitud pasiva o de queja ante errores de entorno informático. Depende frecuentemente de que el docente o un compañero le solucionen la instalación. | Se paraliza ante la falta de un instalador guiado. Demuestra desinterés o incapacidad para gestionar de manera autónoma el software básico de su computadora. |
| **Comprensión del código y las herramientas** | Puede explicar y justificar el funcionamiento de las principales partes del proyecto y las herramientas utilizadas.                   | Comprende y puede explicar los elementos principales.                        | Comprende parcialmente el código o depende de explicaciones externas.   | No puede explicar de manera suficiente aquello que desarrolló o incorporó.                 |
| **Uso crítico de IA**                         | Utiliza IA como herramienta de apoyo, verifica sus resultados, comprende los cambios y puede justificarlos técnicamente.              | Utiliza IA como apoyo y verifica sus resultados principales.                 | Utiliza resultados de IA con una verificación limitada.                 | Incorpora resultados de IA sin comprenderlos ni verificarlos.                              |
| **Documentación del proceso**                 | Documenta con claridad decisiones, procedimientos, problemas y soluciones.                                                            | Registra adecuadamente los aspectos principales del proyecto.                | La documentación es parcial o poco clara.                               | La documentación es inexistente o insuficiente.                                            |
| **Pruebas y estabilidad**                     | Realiza pruebas sistemáticas, detecta errores y verifica el funcionamiento antes de cada entrega.                                     | Realiza pruebas y corrige los errores principales.                           | Realiza pruebas limitadas o deja problemas sin resolver.                | No verifica adecuadamente el funcionamiento.                                               |
| **Consideración del usuario y contexto**      | Relaciona la solución con un usuario concreto, su contexto de uso y sus posibles limitaciones.                                        | Identifica adecuadamente el usuario y el contexto de uso.                    | Considera parcialmente al usuario o el contexto.                        | No puede establecer claramente para quién o para qué se desarrolla la solución.            |
| **Licencias y software libre**                | Identifica y respeta las licencias de las herramientas y recursos utilizados y puede explicar sus implicancias.                       | Reconoce y respeta las principales condiciones de uso.                       | Presenta dificultades para identificar las condiciones de uso.          | Utiliza recursos sin verificar su procedencia o condiciones de uso.                        |
| **Defensa del proceso de desarrollo**         | Puede explicar y fundamentar las decisiones tomadas y demostrar mediante el repositorio cuál fue su participación efectiva.           | Puede explicar las principales decisiones y su participación.                | Puede explicar parcialmente el proceso o necesita asistencia.           | No puede explicar adecuadamente el proceso ni demostrar su participación.                  |

**Puntaje máximo: 56 puntos.**


### 2. Presentación de antenas — 20 %

[**Aquí va la consigna y/o rúbrica correspondiente a la presentación de antenas.**]

### 3. Trabajo y comportamiento en clase — 20 %

[**Aquí va la grilla específica de comportamiento y desempeño en clase.**]


### Ejemplo: el embudo de consulta

Antes de que el docente revise un problema de entorno informático (el famoso *"Profe, no me anda Windows"*), el alumno debe acreditar tres pasos previos obligatorios:

1. **Leer la documentación oficial:** haber revisado/investigado la documentacióon en la pagina web oficial, o su archivo de instalación (ReadMe) del repositorio en GitHub. Y/o haber consultado a su modelo LLM-IA, haberle preguntado a Opencode/Aider/freebuff/Gemini... sobre el proceso para lograr el objetivo, o la forma de continual luego de un error de terminal que apareció e intentado aplicar la solución propuesta.
2. **Mostrar el error exacto:** presentar en pantalla el código de error o el log real, no un "no anda/no sé".

Si no se completaron los tres pasos, el problema no se revisa. El objetivo es que la consulta sea técnica y fundamentada, no una delegación de la responsabilidad de configuración.
