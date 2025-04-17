# Torneo-eSport-UML
# Sistema Gestor de Torneos de eSports

Este proyecto consiste en un sistema de gestión de torneos de eSports. Permite la administración completa de equipos, jugadores y partidos, ofreciendo una plataforma centralizada para organizar torneos de manera efectiva.

## 📌 Análisis del Problema y Requisitos del Sistema

El sistema está diseñado para gestionar torneos en línea a través de una plataforma llamada **ESports**. En ella, distintos actores interactúan con funcionalidades específicas.

### 🎭 Actores del Sistema

- **Administrador**
- **Equipos**
- **Jugadores**
- **Sistema (ESports)** – Interfaz principal

### 🔧 Acciones por Actor

#### 🧑‍💼 Administrador
- Registrar, Modificar, Buscar, Eliminar → Equipos
- Añadir, Modificar, Buscar, Eliminar → Jugadores
- Crear, Modificar, Buscar, Eliminar → Torneos y Partidos
- Consultar listas de equipos y jugadores
- Gestionar el sistema completo (único actor con acceso total)

#### 🛡 Equipos
- Registrarse, buscar, darse de baja de torneos
- Alta, modificación o eliminación de jugadores en su equipo
- Buscar partidos
- Modificar la información del equipo

#### 🧍 Jugadores
- Comprobar si existe un equipo
- Darse de alta o baja de un equipo

#### 🖥 Sistema (ESports)
- Interfaz padre que gestiona métodos para equipos, jugadores, torneos, partidos y administradores

---

## 📌 Modelado del Sistema

### 📚 Identificación de Clases y Relaciones

- **Administrador**
  - Se relaciona con **Sistema (ESports)** por **composición**
  - Asociación estructural con **Equipo** y **Jugador**

- **Equipo**
  - Relación de **dependencia** con los **Jugadores**
  - Asociación estructural con el **Administrador**

- **Jugador**
  - Relación estructural con **Equipo**

- **Sistema (ESports)**
  - Relación de composición con **Administrador**
  - Relaciones funcionales indirectas con **Equipos** y **Jugadores**

---

## 📈 Casos de Uso y Relaciones

### Principales pasos:

#### 1. Registrar Equipo
- Incluye: `Comprobar requisitos del equipo` (`<include>`)
- Extiende: `Actualizar estado del equipo` (`<extends>`)
- Actor principal: Administrador

#### 2. Añadir Jugador a Equipo
- Incluye: `Comprobar existencia del equipo` (`<include>`)
- Extiende: `Actualizar jugador` (`<extends>`)
- Actor principal: Administrador

#### 3. Consultar lista de Equipos y Jugadores
- Incluye: `Comprobar existencia de la lista`
- Extiende: `Crear lista` (`<extends>`)
- Actor principal: Administrador

### 🔄 Relaciones generales
- Predominancia de relaciones de **dependencia**
- Relaciones de **asociación** estructural entre actores y sus funcionalidades
- Uso de `<include>` y `<extends>` para expresar relaciones obligatorias y extensiones

---

## 🧠 Conclusiones

EXPLICACIÓN DEL DIAGRAMA: 
ESports es el padre del proyecto, porque sin sistema no habría torneos, ya que son torneos que se celebran de manera online a través de esta plataforma. Por ese motivo lo he declarado como una Interface de la que el resto de las clases cogen sus métodos. 
He relacionado ESports con Administrador, porque es el único gestor del sistema. Ninguna otra clase tiene acceso al sistema (ESports), por lo que la relación entre ambos es de COMPOSICIÓN. No habría administrador si no hay sistema que administrar.  
Por ese motivo, todas las relaciones que se dan entre el administrador y las acciones son ASOCIACIÓN, ya que entre ellas se da una relación estructural. 
Con respecto al paso 1 Registrar Equipo, he relacionado las acciones con DEPENDENCIA, porque para que se dé situación de que un Equipo o un Jugador se puedan Registrar en el Torneo, tiene que cumplir los requisitos, por lo que lo uno no se puede dar sin lo otro.  De hecho, el vínculo entre el acto de “Comprobar si un equipo cumple con el requisito” para “Registrar Equipo” es <include>, al igual que ocurre con “Comprobar si un jugador cumple con el requisito”, ya que son acciones que se deben de realizar obligatoriamente para que se dé la primera, por lo que este acto va encapsulado en él. Nunca se podrían registrar un equipo o un jugador al torneo si no cumplen con los requisitos.
 Las acciones de “Comprobar equipo/jugador cumple requisitos” también las tienen que realizar los actores Equipo y Jugador para que se cercioren de la aptitud del otro, es decir de Equipo en caso del Jugador y de Jugador en caso de Equipo. En este caso, la relación es de ASOCIACIÓN, porque se da una relación estructural. 
Una vez que se ha registrado el Equipo es obligatorio “Actualizar el estado del Equipo” en el sistema, por lo que la relación entre “Registrar Equipo” y “Actualizar Equipo” es de DEPENDENCIA con un vínculo de <extends> ya que es una extensión de Registrar Equipo, que es una acción que completaría la acción para finalizar el registro. El único actor que puede realizar esa operación es el Administrador, por lo que lo he relacionado con una relación de Asociación. 
Con respecto al paso 2 Añadir jugador equipo, lo he relacionado con “Registrar un Equipo” como DEPENDENCIA porque para poder añadir un equipo, el equipo tiene que estar registrado previamente. Por este motivo el vínculo existente entre ambos es de <include>, ya que el uno no se da sin el otro. 
El único actor que puede realizar esa acción es el Administrador, por lo que la relación que tiene es de ASOCIACIÓN, es estructural. 
A “Añadir Equipo” en incluido “Comprobar existe equipo” por parte del actor Jugador, porque un jugador no podría solicitar unirse a un equipo, si previamente no se ha cerciorado de la existencia de este. Este tipo de relación entre las acciones es de DEPENDENCIA y lo he vinculado como <include> por este mismo motivo, ya que el uno depende del otro, y la relación del actor con la acción es de ASOCIACIÓN, ya que es una relación estructural.
Una vez que se ha realizado “Añadir jugador equipo” se tiene que “Actualizar jugador” por lo que también se da una relación de DEPENDENCIA entre las acciones con un vínculo de <extends> porque la acción de “añadir jugador equipo” finalizaría al “Actualizar jugador”, la última complementa a la primera, amplia su funcionalidad al ser una extensión, una consecución. El único actor que puede realizar esta acción es el administrador, por lo que la relación entre el actor Administrador y la acción “Actualizar jugador” es de ASOCIACIÓN. 
Por último, el paso 3 Consultar lista equipos y jugadores lo he relacionado con “Añadir jugador equipo” con DEPENDENCIA porque para que se puedan consultar las listas de ambos, los equipos tienen que estar registrados y los equipos deben tener añadidos los jugadores, porque lo que lo uno no se puede das sin los pasos previos. Por este motivo, el vínculo entre ambos es <include> ya que uno va encapsulado en el otro. El único actor que puede realizar la acción es el Administrador, por lo que lo he relacionado con ASOCIACIÓN.  
Para poder consultar las listas de equipos y jugadores, previamente, tenemos que asegurarnos de la existencia de estos, por lo que hay que “Comprobar existe lista”. La relación entre ambas acciones es de DEPENDECIA y lo he vinculado como <include> porque para consultarlos, tenemos que cerciorarnos de su existencia. Para poder consultar las listas del sistema, previamente, tenemos que “Crear la lista de equipos y jugadores, por lo que la relación es de DEPENDENCIA, pero en este caso tiene un vínculo <extends>, ya que la creación completa la acción de consulta. El único actor que puede crear la lista es el Administrador, por lo que la relación entre actor y acción es de ASOCIACIÓN. 

> 💬 *Comentario personal:*
> La relación general que tiene el proyecto es de DEPEDENCIA, ya que un paso no se puede generar sin el anterior. 
El Administrador un el actor primordial para que el sistema gestor funcione, aunque el actor principal es el Sistema Gestor o ESports, ya que es eje sobre el que se sustenta el torneo al ser la herramienta base. 
Los actores secundarios son Equipos y Jugadores. Obviamente, son necesarios para que se puedan realizar los torneos, pero no son los decisivos. 
Y como conclusión personal, creo que bastante he podido desarrollar con tan poca formación e información. He tenido que buscar información en post y videos para entender qué tenía que presentar, porque en ninguna de las clases se ha realizado un ejercicio completo de estas características. De hecho, hubiera sido de gran ayuda contar con el documento tipo que pedí en la clase del 31 de marzo para que nos sirviera como referencia.  
Me ha resultado bastante complejo tratar de ver los métodos de cada clase, porque, aunque hemos realizado muchos ejercicios de programación con Tomás, nunca hemos tenido que pensar en los métodos de cada clase, por lo que me he basado en el ejemplo que hiciste en la última clase, a pesar de considerar que hay demasiados métodos y no me parece una propuesta adecuada. 
Por el contrario, no me ha resultado tan complejo definir los atributos que tienen las clases, porque es un ejercicio que sí que hemos hecho en varias ocasiones en BBDD.
Me encantará tener una corrección del ejercicio para entender en qué he fallado y en qué tengo que mejorar. 

---

## 📋 Autor

Trabajo realizado por: Arantza Alcazar Romero 
Materia: *Análisis y Diseño de Sistemas (AD-3)  
Fecha de entrega: 17-04-25




 

