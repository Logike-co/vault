## ¿Por qué molestarse?

_"Los negocios se componen de dos cosas: personas y sistemas". Josh Kaufman._

Es difícil implementar o realizar el desarrollo de 1C. No se trata sólo de cuestiones de programación. En primer lugar, estamos hablando de vincular los procesos de oficina (en adelante, procesos de negocio) a la lógica del programa (o viceversa). Y también sobre formación de usuarios y soporte del sistema.

Aquí hay una lista de preguntas básicas:

1. ¿Qué quiere el usuario?
    
2. ¿Es posible hacer realidad los deseos del usuario comprando una "caja" 1C?
    
3. Si una solución en caja requiere mejoras, ¿qué se debe mejorar exactamente? ¿Y cuánto será?
    
4. ¿Qué “caja” debería comprar para hacer menos modificaciones?
    
5. ¿Nuestros “ajustes” satisfarán completamente al cliente?
    
6. ¿Está escrito correctamente "retrabajo"? ¿Podría ser este un código "malo"?
    
7. Si se ha mejorado ¿cuánto costará la actualización?
    
8. ¿Cómo formar personas para que trabajen de forma rápida y clara en el nuevo sistema?
    
9. Si la gente renuncia y es contratada, ¿cuánto tiempo tendrá que estudiar un nuevo recluta?
    
10. ¿Aprenderá el principiante por sí solo? ¿O tendrá instrucciones?
    
11. ¿Quién puede ayudar a un novato a aprender a utilizar el sistema?
    
12. ¿Un empleado despedido no puede transmitir información a un recién llegado?
    
13. El programador/desarrollador puede salir. ¿Será fácil para un nuevo programador mantener el sistema?

¿Cómo se pueden “superar” estos problemas durante el desarrollo y la implementación?

El lenguaje DRAGON: resuelve la mayoría de los problemas anteriores o los resuelve parcialmente.

También existen algunas desventajas en comparación con el enfoque de programación tradicional 1C:

1. Dedicamos más tiempo a describir la tarea.
    
2. El código generado por el traductor del programa IS Dragon (en adelante consideraremos este producto en particular como la principal herramienta de desarrollo) parece inusual y difícil de entender en comparación con el código "tradicional".
    

Mi opinión personal es que todas estas desventajas son subjetivas, pero tú decides.

Espero que tenga experiencia en implementación o haya desarrollado algo en 1C. Si planea contratar a un programador, instale “algo” en su oficina para comprender a dónde va el dinero en su negocio. Entonces será mejor que leas otro artículo (lo escribiré cuando tenga tiempo ![:-)](https://drakon.su/lib/images/smileys/icon_smile.gif)y publicaré el enlace aquí). En general, hay mucha literatura de este tipo en Internet.

Entonces, ¿has decidido probarlo? Sigue leyendo.![:-)](https://drakon.su/lib/images/smileys/icon_smile.gif)

## ¿Dónde empezar?

Ir. Sobre el lenguaje en sí (qué tipo de diagramas son, cómo leerlos y en general) consulte aquí: [http://drakon.su/jazyk/start](http://drakon.su/jazyk/start "http://drakon.su/jazyk/start")

El lenguaje DRAGON seguiría siendo un lenguaje con un ámbito de aplicación incomprensible si no existieran "herramientas de dibujo" convenientes para los simples mortales, para mí y para usted. No revisaré ni compararé estos productos en este artículo (tal vez más adelante ![:-)](https://drakon.su/lib/images/smileys/icon_smile.gif)).

Dibujaremos diagramas y generaremos código 1C para módulos utilizando el programa IS Dragon, que respeto profundamente, Gennady Tyshov. Me gustaría agradecer una vez más a este hombre excepcional por su trabajo. Puedes leer más aquí: [http://drakon.su/programma_is_drakon](http://drakon.su/programma_is_drakon "http://drakon.su/programma_is_drakon")

Encontrar este producto es bastante fácil:

- siga este enlace [http://forum.oberoncore.ru/viewtopic.php?f=79&t=4239&sid=d1b4ea48141eb55fd798da283d692a71&start=140](http://forum.oberoncore.ru/viewtopic.php?f=79&t=4239&sid=d1b4ea48141eb55fd798da283d692a71&start=140 "http://forum.oberoncore.ru/viewtopic.php?f=79&t=4239&sid=d1b4ea48141eb55fd798da283d692a71&start=140")
    
- ir a la última página del foro
    
- descargue la versión actual del producto, generalmente se encuentra en la última página del foro
    
- instalar
    
- listo
    

Diré de inmediato que el producto está pagado y tiene un período de "prueba": 15 días.

Espero que tengas 1C?

## 1C "rápido"

Si no le importan todos los detalles de cómo "hacerse amigos" de los usuarios con 1C. Y usted simplemente desea comenzar a “codificar” rápidamente en Dragon... Aquí están sus instrucciones, leídas de izquierda a derecha:

![[Pasted image 20240517105557.png]]

A continuación se explica cómo insertar un vínculo a un archivo en un diagrama de flujo:

![[Pasted image 20240517105627.png]]

Aquí se explica cómo "mover" objetos en un diagrama:

![[Pasted image 20240517105642.png]]

## Cómo "hacer amigos" entre usuarios y 1C

_"¿Negocio? ¿Departamentos? ¿Marketing? ¡Muéstrame el dinero! ¡Muéstrame la carne! De una entrevista con algún oligarca._

¿Es esta una imagen familiar? Reunión con el cliente (no así, así: Cliente):

- "¿Estás haciendo 1C?" - Cliente
    
- "Sí" - Programador 1C
    
- “Compramos 1C, un amigo programador lo instaló y transfirió datos del antiguo 1C. Bueno, empezaron a hacerle preguntas sobre su trabajo, y él respondió de alguna manera “lentamente” y luego desapareció. No contesta el teléfono en absoluto... ¿Puede usted ayudar?" - Cliente
    
- “Necesitamos echar un vistazo…. ¿Que compraste? - programador 1C
    
- “Aquí está la caja... . 1C "Gestión de una pequeña empresa". Aquí... El contador le mostrará todo. Hacemos muebles. Necesitamos informes sobre el almacén y la caja registradora. Empecemos desde aquí por ahora. Entonces necesitas calcular tu salario. Quiero saber el beneficio. De lo contrario, estoy completamente confundido: ¿somos rentables o no?” - Cliente
    
- “Necesitamos echar un vistazo...” - Programador 1C
    
- "¿Cuánto va a costar?" - Cliente
    
- “X” rublos por hora” - Programador 1C
    
- "¿Cuánto tiempo tardará?" - Cliente
    
- “Necesitamos calcular...” - Programador 1C
    

No consideraré en detalle la cuestión de la evaluación del trabajo: cada uno tiene el suyo. Esto es lo que hay que hacer, según tengo entendido. Ya hay una "conf" comprada. ¿Porqué ella? ¿Quién eligió? Preguntas sin respuesta… . La pregunta principal es: ¿cómo puede ser “amiga” de esta empresa y cuánto le costará al Cliente? A partir de aquí habrá una respuesta a la pregunta: ¿cuánto ganaré = cuánto tiempo dedicaré y cuántas horas me pagarán? Hay que entender: el cliente lo quiere barato, yo lo quiero tanto como lo necesito. Necesitamos llegar a un acuerdo. Es necesario negociar con argumentos en la mano, preferiblemente “con números”. Para obtenerlos "+/- kilómetro", es necesario comprender la esencia del trabajo de la empresa: describir los procesos de negocio. Ir.

Hablamos y dibujamos el siguiente diagrama:

![[Pasted image 20240517105706.png]]

Sí, cualquier analista de negocios dirá: “¡Creatividad infantil!” Pero el "programador Yazh" para mí es "violeta", lo principal es que ahora puedo tomar este diagrama e iniciar una conversación sustantiva y la gente me entenderá (lo entenderán, lo entenderán, ha sido probado en personas ![:-)](https://drakon.su/lib/images/smileys/icon_smile.gif)).

Más. Sería necesario entender aproximadamente qué tipo de “conf” compró el Cliente (ya lo compró). Tomamos el diagrama, buscamos las instrucciones para el “conf” e intentamos, leyendo el diagrama y las instrucciones, entender cómo encaja el “conf” en el esquema de trabajo. Si compró ZUP e intentó implementar este esquema en él, ya sabe, nada funcionará. Luego vamos al Cliente y le decimos que o el “conf” necesita otro (este por ejemplo...) o buscamos otro “programador tyzh”.

En nuestra historia, "conf" es más o menos apropiado. Adiós… . Vamos a tomarlo. Acudimos al Cliente, informamos y, lo más importante, averiguamos qué haremos primero. En nuestra historia, el Cliente solicitó implementar primero la contabilidad de almacén. Después de hablar con el tendero, nuestro esquema básico adopta esta forma:

![[Pasted image 20240517105728.png]]

Como puede ver, el elemento número 9 ahora se ha convertido en un "Inserto", un enlace a otro diagrama. Descifremos el diagrama de trabajo del Almacenista para el módulo inserto No. 9 del diagrama anterior:

[![](https://drakon.su/_media/1s_araptanov/kartinki/sxema_33.png)](https://drakon.su/_detail/1s_araptanov/kartinki/sxema_33.png?id=drakon-sxemy_aleksandra_araptanova "1s_araptanov:kartinki:sxema_33.png")

Recibimos instrucciones para la recepción de mercancías por parte del Almacenista:

[![](https://drakon.su/_media/1s_araptanov/kartinki/sxema_133_0.png)](https://drakon.su/_detail/1s_araptanov/kartinki/sxema_133_0.png?id=drakon-sxemy_aleksandra_araptanova "1s_araptanov:kartinki:sxema_133_0.png")

[![](https://drakon.su/_media/1s_araptanov/kartinki/sxema_195.png)](https://drakon.su/_detail/1s_araptanov/kartinki/sxema_195.png?id=drakon-sxemy_aleksandra_araptanova "1s_araptanov:kartinki:sxema_195.png")

Dibujó. Ahora nos sentamos junto al tendero e intentamos implementar este esquema. Y entonces “aparece”. Resulta que la configuración de impresión debe cambiarse manualmente cada vez. Trastorno. Realizaremos mejoras para que los parámetros de impresión se puedan configurar de forma independiente. Y reflejemos esto en el diagrama:

[![](https://drakon.su/_media/1s_araptanov/kartinki/sxema_189_0.png)](https://drakon.su/_detail/1s_araptanov/kartinki/sxema_189_0.png?id=drakon-sxemy_aleksandra_araptanova "1s_araptanov:kartinki:sxema_189_0.png")

Atención al elemento del circuito No. 197. Así reflejo los cambios en la configuración. Este elemento se incluye en “Acciones Paralelas” con el elemento N° 193. Esto significa que mi modificación se "activa" cuando el usuario hace clic en este botón. El título “Revisión de MFK-0002” significa que esta modificación se llama así en mis catálogos (conservo un pequeño fichero de mis trabajos, Dragon me ayuda con esto...). Esta modificación: sólo un par de líneas en el código ya escrito. Consideraremos el diseño de mejoras más serias más adelante.

El nombre del módulo contiene un breve significado de la modificación y la dirección de las líneas ingresadas en el configurador. El texto de revisión se encuentra en el tercer punto de entrada (puedes ver que es negro). Aquí está el texto que puede ver allí:

```
''TabDoc = Elemento.Valor;
		//+AAA Establece parámetros al imprimir etiquetas
		Si Buscar(TabularDocuments[0].Ver, "Etiqueta") > 0 Entonces
			TabDoc.FieldTop = 0;
			TabDoc.FieldBottom = 0;
			TabDoc.FieldLeft = 0;
			TabDoc.FieldRight = 0;
			TabDoc.HeaderFooterSizeTop = 0;
			TabDoc.HeaderFooterSizeBottom = 0;
			TabDoc.AutoScale = Verdadero;
		terminara si;
		//-AAA Establece parámetros al imprimir etiquetas
		TabDoc.Print(PrintDialogUseMode.NotUse);''
```

Nada complicado, como puedes ver.

Resumamos en base a las preguntas formuladas anteriormente:

1. ¿Qué quiere el usuario?

- Lo entendimos (aproximadamente ![;-)](https://drakon.su/lib/images/smileys/icon_wink.gif)) elaborando un diagrama de dragón del algoritmo principal de la empresa.
    

2. ¿Es posible hacer realidad los deseos del usuario comprando una "caja" 1C?

- Comparamos el diagrama del dragón y las instrucciones para el “confe”; serán necesarias algunas modificaciones menores.
    

3. Si una solución en caja requiere mejoras, ¿qué se debe mejorar exactamente? ¿Y cuánto será?

- Aún no está claro, pero lo más probable es que haya “pequeñas” mejoras. Nada particularmente caro.
    

4. ¿Qué “caja” debo comprar para tener menos modificaciones?

- La configuración comprada inicialmente es adecuada. Nuevamente, basado en la comparación anterior del esquema del dragón y las Instrucciones de la Confederación.
    

5. ¿Nuestros “ajustes” satisfarán completamente al cliente?

- Nuestra modificación es “pequeña” y está plenamente justificada.
    

6. ¿Se escribe correctamente “retrabajo”? ¿Podría ser este un código "malo"?

- Creo que sí.
    

7. Si se modifica, ¿cuánto costará la actualización?

- Hay una descripción clara de qué, por qué y cómo cambiaron; será fácil de actualizar.
    

8. ¿Cómo capacitar a las personas para que trabajen de forma rápida y clara en el nuevo sistema?

- Las instrucciones del diagrama del dragón para los usuarios son detalladas y completas. La gente aprende fácilmente.
    

9. Si la gente renuncia y es contratada, ¿cuánto tiempo tendrá que estudiar el nuevo recluta?

- Hay instrucciones: aprenderá rápidamente.
    

10. ¿El principiante estudiará solo? ¿O tendrá instrucciones?

- Hay instrucciones: será fácil de aprender.
    

11. ¿Quién ayudará a un principiante a aprender a trabajar en el sistema?

- Hay instrucciones, completas y detalladas. Ella ayudará. Como último recurso, mi sucesor o jefe lo ayudará.
    

12. ¿Un empleado despedido no puede transmitir información a un recién llegado?

- Todas las instrucciones, en forma de diagramas de dragón, en formato electrónico y/o impreso, son almacenadas por la dirección de la empresa. Y se emiten fácilmente según sea necesario.
    

13. El programador/desarrollador puede salir. ¿Será fácil para un nuevo programador mantener el sistema?

- Todos los diagramas de dragones se guardan con una descripción detallada de las mejoras y su lógica. Sí, será fácil de mantener. Por supuesto, el código es específico, pero puedes “codificar” directamente desde “IS Dragon”. Parece que cuando hay una descripción de la lógica de las mejoras, el código “específico” es un “pequeño” mal comparado con cuando simplemente no hay más que comentarios “incomprensibles” (y sucede que no los hay).
    

Nada mal para empezar. Vamonos.

* [Diagramas de dragones en una fábrica de muebles.](https://drakon.su/drakon-sxemy_na_mebelnoj_fabrike/start "drakon-sxemy_na_mebelnoj_fabrike:empezar")

[Diagramas de dragones en una fábrica de muebles.](https://drakon.su/_media/biblioteka_1/01._2012_uchis_chitat_new_end_podlinnik.pdf "biblioteka_1:01._2012_uchis_chitat_new_end_podlinnik.pdf")