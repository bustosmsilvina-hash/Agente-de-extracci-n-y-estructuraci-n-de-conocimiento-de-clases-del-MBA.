# Agente-de-extracci-n-y-estructuraci-n-de-conocimiento-de-clases-del-MBA.
# Agente de estructuración de clases MBA

## Qué construí

Construí un agente de IA que recibe como fuente una transcripción de una clase del MBA y extrae de ella el contenido académico más relevante.

El resultado principal es un archivo Excel estructurado, que organiza conceptos, definiciones, modelos, ejemplos, relaciones, aplicaciones, preguntas de estudio y tareas.

El objetivo es convertir una transcripción extensa en un material de estudio más ordenado, práctico y fácil de consultar.

## Cómo se lo pedí

### Primera versión del System Prompt

Primero creé un agente con el rol de analista académico. Le indiqué que debía utilizar únicamente la información de la transcripción y organizarla en diferentes categorías.

El primer contrato incluía secciones separadas para "Conceptos clave" y "Definiciones", además de una sección de "Ambigüedades o información faltante".

También le indiqué que generara un archivo Excel con la misma información.

El User Prompt utilizado fue:

"Procesá la transcripción adjunta siguiendo las instrucciones del proyecto. Generá la ficha de conocimiento estructurada y el archivo Excel correspondiente. Utilizá exclusivamente la información de la transcripción."

### Primera corrida - V0

Utilicé una transcripción real de una clase del MBA.

El agente generó la información tanto en el chat como en un archivo Excel.

Al revisar el resultado observé que era demasiado extenso y que algunos conceptos aparecían repetidos en diferentes secciones. Por ejemplo, un concepto podía aparecer primero como concepto clave, después nuevamente como definición y luego volver a aparecer al explicar una relación o aplicación.

También observé que la sección de "Ambigüedades o información faltante" no me resultaba útil para el objetivo que buscaba.

### Primera iteración - V1

Modifiqué el System Prompt para solucionar principalmente el problema de repetición.

Los cambios fueron:

- Unifiqué "Conceptos clave" y "Definiciones" en una sola sección llamada "Conceptos y definiciones".
- Agregué una regla explícita para que cada concepto aparezca una sola vez.
- Indiqué que, si un concepto aparece varias veces durante la clase, el agente debe consolidar la información en un único registro.
- Indiqué que las demás secciones deben aportar información nueva y no repetir las definiciones.
- Eliminé la sección de "Ambigüedades o información faltante".
- Modifiqué el Excel para que tampoco tenga una hoja separada para definiciones ni para ambigüedades.
- Agregué una instrucción para priorizar síntesis sobre exhaustividad.

Volví a procesar la misma transcripción utilizando el mismo User Prompt para poder comparar el resultado.

### Segunda iteración - V2

Después de revisar la V1 detecté otro problema: el agente generaba el contenido estructurado en el chat y luego volvía a colocar prácticamente la misma información en el Excel.

Esto no me resultaba práctico porque mi objetivo final es utilizar el Excel como material de estudio y consulta.

Por eso modifiqué el formato de salida del System Prompt.

Indiqué que:

- el Excel sea el único producto final del agente;
- toda la información extraída se coloque dentro del Excel;
- no se reproduzcan en el chat las tablas ni el contenido de la ficha;
- el chat solamente indique que el archivo está listo.

El objetivo de este cambio fue evitar información duplicada y hacer más simple el uso del agente.

## Qué funciona

El agente puede recibir una transcripción real de una clase del MBA y analizarla utilizando únicamente esa fuente.

Genera un archivo Excel organizado en diferentes hojas para facilitar la consulta del contenido.

La estructura del Excel incluye:

- Resumen
- Conceptos y definiciones
- Modelos y frameworks
- Ejemplos y casos
- Relaciones entre conceptos
- Énfasis del profesor
- Aplicaciones prácticas
- Preguntas de estudio
- Entregas y tareas
- Información adicional / nuevos atributos, cuando corresponde

También se definió un formato visual minimalista para el Excel, utilizando tonos terracota, siena, beige y colores neutros.

La primera y segunda versión permitieron comprobar que las instrucciones del agente tienen un efecto directo sobre la cantidad, organización y utilidad de la información obtenida.

## Qué falta o qué falló

La primera versión generaba una salida demasiado extensa y repetía conceptos en diferentes secciones.

La separación entre "Conceptos clave" y "Definiciones" generaba duplicación de información.

También se comprobó que algunas secciones no aportaban suficiente valor para el objetivo de estudio, especialmente "Ambigüedades o información faltante".

En la V1 se solucionó gran parte de la repetición, pero todavía se generaba en el chat el mismo contenido que posteriormente aparecía en el Excel.

Por este motivo se realizó una segunda modificación del contrato para que el Excel sea el único resultado final.

**No hay un archivo de salida correspondiente a la versión V2 porque, en esta versión, se modificó el comportamiento del agente para que deje de reproducir la salida estructurada en el chat y entregue únicamente el archivo Excel.**

## Qué aprendí

Aprendí que crear un agente no consiste solamente en pedirle a la IA que realice una tarea, sino en definir con precisión cómo debe realizarla y cómo debe entregar el resultado.

También aprendí que las instrucciones iniciales pueden parecer correctas, pero al probar el agente aparecen problemas que solamente se detectan viendo una corrida real.

En este caso, las pruebas permitieron identificar dos problemas diferentes: primero la repetición de información y después la duplicación entre el chat y el Excel.

Finalmente, entendí que modificar una parte concreta del prompt y volver a probar permite mejorar el comportamiento del agente de forma más controlada.
