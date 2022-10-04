# c# y .net

*   caracteristicas de . net :

    * MUltiplataforma
    * open source
    *   Multi lenguaje

    ** LENGUAJE COMPILADO** como C

*   Componentedes de c# .net

    * Entorno de ejecucicon CTS encargado de ejecutar el codigo intermedio.
    * compiladores y lenguajes de programacion /f#,visual basic
    * frameworks de aplicaciones
    * IDES y editores de codigo
    * Common Languague Runtime (CLR)

        *   entorno de ejecucion / es el motor encargado de gestionar la ejecucion de los programas
        asignacion y administracion de la memoria /genera y compila codigo.//**traduce de codigo intermedo a codigo binario especifico para un sotfware**/No es el compilador de c#

    * Base Class Library (BLC)/libreia que se usa en .net / clase consol,math
    * Frameworks
    * Herramientas de desarrollo
    * componentes de insfracturuta comun 
    * orientados a componentes
    * El garbage collector libera la memoria almacenada en el segmento Heap, no en el Stack. El segmento Stack es liberado automáticamente.


* Procesos de compilacion
    * proceso de compilar codigo c# a lenguaje intermedio = tiempo de compilacion
    * proceso en que es codigo intermedio se convierte a codigo maquina es tiempo de ejecucion
    * tiempo de diseño = codear codigo
    
* Fue diseñado por el ingeniero de Microsoft Anders Hejlsberg, quien también está involucrado en el desarrollo de Typescript desde 2012.
* **Características de C#**

 **C# se compila primero a un lenguaje intermedio y posteriormente al ejecutarse es recompilado a lenguaje nativo/máquina.**

*  Es un lenguaje principalmente de tipado estático o fuertemente tipado.Decimos que un lenguaje es de tipado estático cuando los tipos de las variables tienen que definirse antes de compilar el programa.

* Garbage Collection

programa especial que se encarga de la liberación de memoria no utilizada en el segmento heap

* Método Main

El método Main es el punto de entrada (entry point) de todos los programas en C#, es decir, el primer método en ejecutarse.

* **Common Type System**

El Common Type System (CTS) define un conjunto de tipos de datos común a todos los lenguajes soportados por .NET.

Establece un marco de herramientas que habilita la ejecución de los distintos lenguajes de la plataforma.

Provee un modelo orientado a objetos.

Define un conjunto de reglas que todos los lenguajes deben seguir en lo que refiere a tipos.

Provee una biblioteca que contiene los tipos primitivos básicos (Boolean, Int32, Byte, Char, etc).

Define tipos de dato en dos categorías: de valor y de referencia.

**Existen dos segmentos o categorías de memoria: la pila (stack memory) y el montón (heap memory). La memoria stack es más rápiida pero limitada en tamaño. La memoria heap es más lenta pero más abundante.**
 
  Todos los tipos de valor se almacenan en la pila.

  Todos los tipos de referencia se almacenan en el montón."stack"
# Clases y metodos estaticos Constructores

*   **Principio dry**

    *   El principio Don't repeat yourself (DRY) ("No te repitas", en español) fue introducido por primera vez en el libro "The Pragmatic Programmer" escrito por Andy Hunt y Dave Thomas 
    "Toda pieza de conocimiento debe tener una representación única, inequívoca y fidedigna dentro de un sistema."
    *   Sus metodos no se asocian a un obejto en particular sino a la clase
    * La conversion explicita si nesecita intervencion del programador,se necesita casteo
    * una conversion implicita no nesecita casteo no deveria implicar perdida de datos
    * Refactorizar es mejorar la calidad del codigo sin cambiar su funcionalidad
    * Las clases estaticas no pueden heredar de otra clases no pudeden ser bases ni derivadas
    * Los contructores estaticos Inicializan los atributos estaticos de la clase , Se pueden declarar en clases no estaticos , Solo son llamados una unica vez en el ciclo de vida del programa, No tienen parametros de entrada, no tiene modificador de acceso.
    *  Los constructores estaticos no se pueden invocar poque se invocan solos la primera vez q inicializamos la clase
    * Los métodos no se instancian.
    * Los métodos estáticos son de la clase y no se invocan desde una instancia específica. Por lo tanto, no requieren ninguna instancia.
    * Si no se declara de forma explícita un constructor, existirá un constructor por defecto. El constructor por defecto es público y no tiene parámetros de entrada.
    * Los constructores inicializan los atributos del objeto. No reservan memoria, esa tarea es del operador new.
    * Los constructores estáticos no pueden ser invocados. La invocación la realiza el runtime en la primera interacción con la clase.
    * Los constructores estáticos son de la clase, no de una instancia específica. Por lo tanto, sólo pueden inicializar atributos de clase (estáticos).
    * Una clase es un tipo de clasificador que representa un conjunto de atributos y operaciones en común para un conjunto de objetos o entidades.
    Funciona como plantilla o molde para la creación de instancias de objetos.
    * Las clases definen los atributos y el comportamiento que tendrán los objetos, los cuales se crean a partir de ellas.
    * Lo que se almacena en un bloque de memoria es una instancia de la clase u objeto.
    * Un conjunto de objetos es una colección o array.
    * Los constructores estáticos no tienen parámetros de entrada, por lo tanto no se pueden sobrecargar.

    * No se puede invocar constructores estáticos con el operador :this().
    * Los constructores privados SÍ se pueden sobrecargar.
    * Los constructores de la clase base se invocan con el operador :base(), no con el :this().
    * Las sobrecargas no se resuelven por el nombre o identificador de los parámetros entrada. Lo que analiza el compilador es el número y orden de los TIPOS de los parámetros.


# POO

 *  Los objetos se crean en tiempo de ejecucion,viven en memoria
 *  Los objetos se almacena en el segemento de memoria heap porque son tipos de referencia
 *  Es un bloque de memoria que se ha asignado y configurado de acuerdo a las especificaciones de un clase
 *  Destuccion no determinista : Se conoce el punto de creacion con certeza, pero no el de destruccion 
 *  Los constructores inicializan el estado de un objeto osea los valores que toman sus atributos en determinado momento.La palabra new reserva memoria.
 *  Si no declaramos un constructor  se podra instanciar pero sin la posibilidad de pasarle argumentos al constructor, es de instancia y publico,constructor por defecto.
 *  Las constantes se asignan en tiempo de compilacion
 *  Dos objetos del mismo tipo no pueden tener distintos valores en un mismo atributo constante
 *  Un namespace es una agrupación lógica con fines de organizar nuestras clases y otros elementos. No tiene relación con el proyecto, el cual sí representa una unidad de compilación.
 * NAMESPACE : ES  una agrupacion logica de clases y otros elementos , proporciona un marco de trabajo jerarquico sobre el cual se construye y organiza todo el codigo.
 * El estado de un objeto son sus datos (atributos). El comportamiento se representa por implementaciones concretas de sus operaciones conocidas como métodos.
 * Es el objeto quien está almacenado en memoria, no la clase. La clase es un molde o plantilla a partir de la cual se instancian objetos. La referencia al objeto en memoria puede  estar almacenada en una variable.
 * Los objetos de las clases que implemen IEnumerable podrán ser recorridos con un foreach.

 **Sobrecarga**  

 *  Las sobrecarga se resuelve en tiempo de compilacion
 *  Los metodos staticos se pueden sobrecargar
 *  Los contructores staticos no se pueden sobrecargar
 *  No se pueden sobrecargar las clases
 *  Sobrecarga de operadores pide si o si un parametro de la clase donde sobrecargo el operador
 *  Sobrecarga de metodos : el compilador distingue los metodos que estan sobrecargados comparando la lista de parametros
 * Un metodo se sobrecarga para agregar funcionalidad
 *  El operador suma y asignación se sobrecarga automáticamente al sobrecargar el operador suma.
* Los operadores se dicen binarios cuando operan con dos operandos.
* En la declaración de la sobrecarga de un operador unario hay un solo parámetro de entrada (operando), mientras que los binarios tienen dos.
* Si bien se recomienda sobrescribir el comportamiento del método Equals al sobrecargar el operador de igualdad, no hacerlo no resultará en un error en tiempo de compilación.

 # Formularios

 *  Los formularios son objetos,heredande form,object
 *  ShowDialog() muestra un formulario en forma modal NO permitiendo interactuar con otras ventas,devuelve un valor de tipo DialogResult.El medoto show tambien devuelve DialogResult.
 *  Los formularios se instancian
 *  El primer formulario se instancia en la clase program
 *  El modificador partial permite separar la declaracion/logica de una misma clase en dos o mas archivos
 *  Se puede agregar parametros de entrada al constructor de la clase del formulario
 *  Orden de los eventos del ciclo de vida de windows form del primero en lanzarse al ultimo
    New,load,paint,activate,formclosing,formclosed,disposed
 * Los formularios son instancias de clases que heredan de Form. Son objetos como cualquier otro.
 * No requieren tener un constructor sin parámetros.
 * El modificador partial permite que la declaración de una misma clase esté separada en dos o más archivos.
 * Efectivamente ShowDialog() es para mostrar el formulario de forma modal, pero las ventanas modales no permiten interactuar con otras ventanas.
 * El método Show() muestra un formulario de forma NO-MODAL, permitiendo interactuar con otras ventanas.
 # Encapsulamiento
 *  El encapsulamiento es AGRUPAR datos de un objeto junto a metodos que operan sobre esos datos, Exponer solo aquellos que sea relevante para responsibilidad de la clase,Proteger el acceso y manipular los datos de un objeto
 *  El encapsulamiento es AGRUPAR datos de un objeto junto a metodos que operan sobre esos datos, Exponer solo aquellos que sea relevante para responsibilidad de la clase,Proteger el acceso y manipular los datos de un objeto
 * El pilar del encapsulamiento consiste en agrupar en un contenedor los datos del objeto junto con los métodos que operan sobre esos datos (Clases). Al mismo tiempo que se ocultan los detalles de la implementación o internos y se protege el acceso a datos. Exponiendo únicamente lo esencial / importante.

* El modificador internal permite acceso desde clases dentro de un mismo ensamblado (unidad de compilación / proyecto).
* El modificador protected permite acceso desde la misma clase y derivadas.
* El encapsulamiento protege el acceso a datos y oculta los detalles de la implementación.

 # Colecciones y Indexadores

 *  Las colecciones genericas son fuertemente tipadas las no genericas no
 *  Los elementos de un array "jagged(escalonadas/irregulares) son  tipos de referencia
 *  La coleccion Genericas cuentan con seguridad de tipos,son dinamicas,no tienen tamaño fijo
 *  Las matrices son de tamaño fijo
 *  Las coleccion de tipo List Estan indexadas por numero de posicion de sus elementos, todos sus elementos son de un tipo especifico
 *  Las coleccion de tipo dictionary Estan indexadas Clave/key,Estan compuesta por pares clave-valor,Todos sus elemntos son de un tipo en especifico
 *  Las coleccion de tipo stack Se procesan en orden ultimo en entrar,primero salir LIFO
 *  Las coleccion de tipo Queue Se procesan en orden primero en entrar,primero en salir FIFO
 *  Tenemos que instanciar las colecciones para poder agregar elementos
 *  Las coleccion STACK Y QUEUE NO SON ORDENABLES
 *  Indexar implica Ordenar una serie de datos para facilitar su consulta a travez de su indice
 *  Los indexadores aceptan numeros string obejtos 
 *  Puede haber indexadore que trabajen con mas de un indice
 *  Los indexadores se pueden sobrecargar
 *  No se pueden declarar indexadores staticos
 *  Los enumarados pueden estar en un namespace y dentro de una clace
 *  Un indexador puede recibir mas de un parametro(Multidimensional)
 * Los elementos de un array "Jagged" son otros arrays. Los arrays son reference type, por lo tanto se por defecto con null.
 * Efectivamente, inmutable significa que los datos del objeto no podrán ser alterados una vez que fue instanciado. Es el caso de los strings.
* Las colecciones genéricas se caracterizan por ser fuertemente tipadas, se componen de elementos de un tipo concreto.
* La diferencia entre colecciones y matrices es que las primeras son de tamaño dinámico mientras que las segundas son de tamaño fijo.
* Darle al objeto un espacio en memoria es parte del proceso de instanciar, no tiene que ver con indexar.
* Las clases se pueden indexar por múltiples parámetros de cualquier tipo. Depende de la necesidad y del criterio de indexación diseñado para la clase.
* No es un requisito que la clase tenga una colección o array como atributo para poder ser indexada. De nuevo, depende de la necesidad y del criterio de indexación diseñado.

# Conversiones
* Las conversiones explícitas exigen el uso del operador de casteo ya que se suelen utilizar cuando la conversión podría implicar pérdida de información.
* Las conversiones implícitas no exigen el uso del operador de casteo, se resuelven automáticamente. Esto es porque se suelen utilizar cuando la conversión no podría implicar pérdida de información.


 # Herencia y Polimorfismo

 *  Permite crear clases nas especificas a trave de otras mas generales, Permite agrupar atributos y comportamiento en comun de un conjunto de clases,Permite reutilizar  y organizar mejor el codio
 *  Todos los objetos heredan de object  incluso aquellos qe ya tienen una clase base,Es posible ya que la herencia es transitiva
 *  Los constructores no se heredan por eso se usa el :base()
 *  Los mienbros privados de la clase base se heredan pero no pueden acceder
 *  Las clases derivadas deben ser igual de accesibles o menos que la clase base
 *  Las clases SELLADAS no pueden ser bases de otras clases pero si pueden se clases derivadas/hijas
 *  Principio de sustitucion de liskov Indica que las instancias de clases derivadas deberian poder sustituir a una instacia de su clase base sin cambios en el funcionamiento del programa
 *  Las clases abstract pueden heredar de otras clases (ser derivadas),pueden contener metodos de implementacion ,no pueden instanciarse
 *  La palabra reservada override se usa para implementar un metodo abstracto y para invalidar un metodo virtual
 *  El polimorfismo se resulve en base a el tipo de la instancia en tiempo de ejecucion
 * La herencia nos permite crear nuevas clases reutilizando, extendiendo o modificando la estructura y el comportamiento de la clase padre. De esta manera podemos crear clases más específicas a partir de otras más generales.
 Su propósito es agrupar atributos y comportamiento en común de un conjunto de clases que componen una determinada realidad, reutilizando y organizando mejor el código.

* El mecanismo de herencia por si mismo no impide el acceso a los detalles de la implementación. Eso tiene más que ver con encapsulamiento.
* A través de la herencia se pueden crear clases más específicas a partir de otras más generales. Y no al revés.
* La herencia nos permite crear nuevas clases reutilizando, extendiendo o modificando la estructura y el comportamiento de la clase padre. De esta manera podemos crear clases más específicas a partir de otras más generales.

Su propósito es agrupar atributos y comportamiento en común de un conjunto de clases que componen una determinada realidad, reutilizando y organizando mejor el código.

* El mecanismo de herencia por si mismo no impide el acceso a los detalles de la implementación. Eso tiene más que ver con encapsulamiento.
* A través de la herencia se pueden crear clases más específicas a partir de otras más generales. Y no al revés.
* Las clases abstractas no pueden ser instanciadas, pero sí pueden ser heredadas. Están pensadas para ser la base de una jerarquía de herencia.
* Las clases selladas no pueden ser heredadas (ser base), pero sí pueden heredar (ser derivadas).
* Las clases estáticas no pueden heredar, ni ser heredadas, ni instanciarse.
* Los métodos virtuales ya tienen una implementación por defecto, por lo tanto no es obligatoria su invalidación en la clase derivada. Los abstractos, por otro lado, no tienen implementación por defecto y deben ser sobrescritos por las clases derivadas.


 