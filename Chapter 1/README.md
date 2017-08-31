##  ¿No se parecen a SOA los microservicios?

La arquitectura de microservicio está inspirada en SOA. Su arquitectura parece SOA, pero hay diferencias que hacen microservice una versión más depurada y organizada de SOA. En SOA también, los problemas se dividen en servicios y, por lo general, todos utilizan SOAP como protocolo de mensajería para la comunicación.

Hay muchos consumidores conectados con muchos servicios a través del bus de servicio. Los consumidores pueden invocar cualquier servicio enviando un mensaje a través del ESB (Enterprise Service Bus). Al igual que en microservicio en SOA estos servicios pueden estar en el mismo lenguaje o en un lenguage diferente.

En SOA  la base de datos normalmente se comparte entre los servicios, mientras que en microservicios, cada servicio debe tener su propia base de datos y ningún otro servicio puede hacer frente a eso directamente.

SOA cree en el principio de compartir tanto como sea posible, por lo que SOA promueve compartir recursos como bases de datos entre diferentes servicios, lo que en realidad aumenta el acoplamiento entre servicios. Esto contradice la arquitectura del microservicio.

Los Microservicios cree en el principio de compartir lo menos posible. Esto cambia el enfoque fundamental del diseño de cualquier servicio en arquitectura.


La capa de comunicación ESB que es el middleware en SOA, se convierte en el único punto de fallo. En caso de fallo en ESB, ninguno de los servicios puede funcionar, consumir datos o hablar entre sí.

Los Microservicios se ocupa de este problema con el principio de falla en el aislamiento. Normalmente, los microservices hablan sobre RESTful, y elimina la necesidad de cualquier canal de comunicación de middleware pesado.

Otra implicación de SOA son los contratos de servicios. Como no hay noción de  contextos unificado en SOA el mismo servicio puede realizar cambios en un modelo de datos diferente lo que lleva a un modelo de datos compartido. Este modelo de datos puede tener jerarquía o tipos de datos complejos. Los cambios en cualquiera de este modelo de datos, incluso con un solo campo, pueden resultar en el cambio de la interfaz en todos los servicios y en el despliegue de toda la aplicación.

La siguiente figura muestra la arquitectura típica de SOA Application:

![](../images/bus.png)


SOA es un término muy amplio y los microservicios puede ser un subconjunto de SOA que tiene una granularidad más fina en torno al diseño orientado al servicio. Hay una famosa cita sobre Microservicios.


>"Los Microservicios son SOA pero bien hechos".


## Asignación del dominio de negocios a componentes de microservicio

El diseño de una sólida arquitectura de microservicios comienza identificando el dominio del negocio, definiendo la capacidad alrededor de ese dominio y luego definiendo los microservicios a su alrededor.

La descomposición de un dominio de negocio se puede lograr con el concepto de diseño dirigido por el dominio (DDD), es un enfoque del desarrollo de software para necesidades complejas que conecta la implementación a un modelo en evolución.

La filosofía de DDD es tratar de entender el dominio de un problema que estamos intentando  resolver y modelarlo alrededor de este dominio. Sugiere el modelado sobre la base de casos de uso reales del negocio. Este modelado incluye definir un conjunto de conceptos para el dominio, la capacidad del dominio y el contexto asociado alrededor de él. Hay algunos conceptos básicos en DDD, que son los siguientes:

* Lenguaje ubicuo: Esto significa que todos los interesados (negocio, operación, desarrollador) deben compartir el lenguaje común (terminología) que no debe ser demasiado técnico, sino que debe estar más centrado en el modelo de negocio. Este lenguaje estará relacionado con el contexto acotado del dominio.

* Contexto acotado: La idea principal es definir el alcance de un modelo, definir los límites claros de su contexto, y luego hacer lo máximo posible para mantener el modelo unificado. El modelo definido debe mantenerse consistente y restringido dentro de límites definidos. Cada contexto acotado debe ser independiente de otro contexto. Define la separación de funciones entre los dominios. Cualquier negocio en particular puede tener varios dominios en él, como el envío, inventario, ventas, marketing, y así sucesivamente. Cada dominio tiene sus propias capacidades. Cada entidad o componente de un negocio permanece en su propio contexto limitado.

DDD nos ayuda a identificar estos dominios y su punto de segregación. Todo este concepto de DDD coincide con los principios de microservicios. Piensa en un modelo, encapsula el modelo alrededor del contexto acotado y estos contextos definen los límites.


Como los microservicios deben aislarse, se hace necesario que un microservicio tenga una clara responsabilidad o frontera. Cuando se adopta DDD, el dominio del problema más grande se puede descomponer en los más pequeños con el contexto limitado, lo que llevará a una mejor comprensión de la definición de microservicios a su alrededor. 

Si no hacemos esta clara separación de límites, tendremos una fuga de responsabilidad entre los microservicios, y entonces tendremos una gran bola de barro sin tener ningún límite claro. DDD ayuda a entender y definir el contexto de límites. Una muy buena lectura en DDD es la implementación de diseño impulsado por el dominio de Vaughn Vernon, que le da una profunda comprensión del diseño impulsado por el dominio.
___

### Organización de componentes de microservicio alrededor de las oportunidades de negocio

Los microservicios dan poder a la organización con rapidez. Permiten que la organización responda al mercado de una manera más rápida. Mejoran la productividad, la entrega y por supuesto la velocidad en la implantacion del entregable del proyecto.

El desafío en este paradigma es alinear su equipo dentro de la organización alrededor de esta arquitectura de manera eficiente. Los microservicios no se adaptan a todas las organizaciones. La implementación de la arquitectura de microservicios puede modificar condiciones mismas de la organización.

La oportunidad de negocio se puede definir como un servicio de operación independiente para un propósito particular en los negocios. La oportunidades de negocio en la organización se puede definir en cada nivel/dominio. El nivel superior de gestión puede tener diferentes definiciones de negocio, las operaciones pueden tener otras, ventas pueden tener diferentes, la tecnología puede tener diferentes, y así sucesivamente. Por lo tanto, identificar la capacidad de negocios de forma fina para organizar el microservicio en esa direccion.

La oportunidad de negocio y el microservicio parecen ser los mismos por definición, pero no lo son. La ejecución de una campaña promocional es una capacidad comercial para el departamento de marketing. Después de identificar esta capacidad, comience a organizar el componente de microservicio a su alrededor, quiza un servicio de remitente de correo electrónico, un servicio de generador de links con promociones, el servicio de recopilación de datos, etc. Es un proceso de dos pasos:

Identificar la capacidad comercial correcta.
Definición del componente de microservicio que le de soporte.


Ambos pasos tienen que ser hechos con  granularidad fina tanto como sea posible. Esto ayudará a diseñar la arquitectura de manera eficiente.

Otro factor importante es la comunicación. La comunicación es un cable vivo en cualquier sistema. Puede haber comunicación entre los equipos, entre la organización y el usuario final para obtener retroalimentación constante, la comunicación entre los diferentes niveles de gestión (superior, medio, inferior), e incluso la comunicación entre los componentes del sistema de software de esa organización. 


Hay una ley que relaciona la comunicación entre los componentes de software y cómo la comunicación ocurre dentro de la organización. La ley es la ley de Conway.

***Cualquier organización que diseña un sistema (definido ampliamente) producirá un diseño cuya estructura es una copia de la estructura de comunicación de la organización.***


Según esta ley, la arquitectura de la aplicación será una copia de su estructura organizativa, pero existe una alta probabilidad de que su estructura organizativa también pueda tener un impacto en la arquitectura de su aplicación. Las ubicaciones de los equipos y la comunicación del equipo afectan la arquitectura de la aplicación, lo que puede resultar en una estructura de organización alineada.

Si una organización tiene cinco equipos con cuatro miembros de equipo en cada equipo nos encontramos con una situación en la que no es fácil desglosar un servicio que debe manejar un equipo. La unión de dos equipos podría ser una solución aquí. Esto básicamente cambia la estructura organizativa alrededor de la arquitectura de la aplicación.


## Ir o no por el camino de microservicios


Hay muchos factores que una organización debe considerar antes de migrar a la arquitectura de microservicios. Antes de dar un gran paso, cualquier organización debe considerar los siguientes factores.

### Adquisición de la organización

Asegúrese de que las personas que van a trabajar en este entorno se educan al respecto. No se limita solamente al conjunto de habilidades técnicas, sino que también necesitan el conocimiento del concepto en el cual están trabajando. En su mayoría, personas o equipos deben adoptar la filosofía de desarrollador de full stack.

Su mentalidad debe estar alineada en el conocimiento de trabajo de DevOps. El desarrollador trabaja en un entorno de microservicio, tiene una completa propiedad de su microservicio. Es muy necesario que no debe haber límites en su mente como desarrolladores como desarrollador de front-end, desarrollador de back-end, miembro de DevOps y así sucesivamente.

El equipo debe estar listo para hacer todas las cosas por sí mismo. Aunque tener DevOps siempre es una buena cosa, el equipo debe ser autosuficiente para manejar estas tareas.


### Experiencia de DevOps

Asegúrese de que las organizaciones cuenten con un equipo maduro de DevOps y que los procedimientos estén en su lugar para manejar múltiples lanzamientos que ocurren en un día. Al pasar de la arquitectura monolítica a microservicios, cada servicio debe monitorearse por separado. Será una responsabilidad adicional para el equipo de infraestructura y DevOps. Si usted tiene que enviar rápido e independiente, entonces su DevOps y el sistema de monitoreo debe ser lo suficientemente atento como para ir y revertir eficientemente si algo sale mal.

### Analizar el modelo de base de datos existente

La descomposición eficiente de las bases de datos es un problema. A veces, una base de datos está diseñada de tal manera que es difícil de descomponer o que requiere un gran cambio de diseño en las tablas de DB. ¿Está lista la organización para tomar ese reto? ¿Es factible dividir una gran DB en bases de datos mucho más pequeñas que son lógicamente y físicamente diferentes el uno del otro? Como los datos están en la forma descentralizada y residen en diferentes bases de datos, significa que no habrá conexión física en las tablas. Esto lleva a cambios profundos en las bases de datos. 

### Automatización y CI / CD

Las herramientas de pruebas de automatización y las herramientas de CI / CD, como Jenkins y Team City, deberían estar en el lugar para la entrega o liberación frecuente de microservicios. Cada microservicio tiene que tener su propia canalización de despliegue y gestión de configuración. Esto será de nuevo una sobrecarga para el equipo de DevOps. TDD es muy importante en este aspecto. Los casos de prueba de unidad y los casos de prueba de integración deben estar en su lugar para soportar pruebas de automatización y entrega continua.

### Integración

Para tener diferentes piezas de una aplicación que se ejecuta en diferentes lugares (microservicios), se necesita mucho trabajo de integración, para obtener la salida deseada. Trabajo de integración como la comunicación entre estos servicios y un montón de trabajo de mantenimiento será gastos generales, mientras que avanzar hacia microservices.

### Seguridad

Con tantos componentes hablando entre sí sobre las API o sobre la mensajería, la seguridad se convierte en un aspecto importante a tener en cuenta. Los microservicios basados en credenciales o basados en tokens ofrecen muchas soluciones para manejar los problemas, pero será una sobrecarga para los equipos de desarrollo y de infraestructura.

Cualquier organización que esté lista para dar sangre a la arquitectura de microservicios debe considerar dar pensamientos a los factores anteriores. La implementación exitosa de esto dará a cualquier organización la libertad de escala, alta disponibilidad, y cualquier despliegue de tiempo y puede lograr un tiempo de inactividad cero.


___

### Spring Boot

Spring Boot viene como una ventaja sobre Spring bootstrapping ya que facilidad el desarrollo, evitando las tediosas configuraciones. Spring Boot no es otro framework; Se acaba de hacer en la parte superior de spring para reducir el esfuerzo de desarrollo. Ahorra mucho esfuerzo para gran parte del código, la configuración XML y la anotación. Se integra con otros módulos Spring fácilmente. También tiene un servidor web HTTP embebido en la aplicación web. Tiene CLI. Spring Boot, que se ajusta a muchas herramientas de construcción como Maven y Gradle perfectamente.


___
### Correr tu primer spring boot

Para correr este ejemplo usamos maven

>$ mvn spring-boot:run

Todo esta parametrizado en el archivo src/main/resources/application.properties


```bash
server.port=8899
server.contextPath=/firstboot
```


http://localhost:8899/firstboot/greeting/{userName}

Podemos hacer la prueba usando [httpie](https://httpie.org/)

>$ http -f -b http://localhost:8899/firstboot/greeting/sidlors

Welcome, sidlors!


