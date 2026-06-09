# Speech sugerido para la presentación

Este archivo está pensado como guía de defensa oral. No hace falta leerlo textual: la idea es usarlo para saber qué remarcar, cuánto peso darle a cada diapositiva y cómo conectar una con la siguiente.

## 1. Portada

**Foco:** presentar el tema como un proyecto de integración de ingeniería, no solamente como una aplicación de IA.

**Speech sugerido:**

Buenos días. Mi nombre es Uriel Sansoni y voy a presentar mi Proyecto II, titulado "Sistema de Gestión de Inventario con IA para Kits de Robótica".

El objetivo general del trabajo fue desarrollar un prototipo automatizado capaz de reconocer, clasificar, manipular e inventariar piezas de kits de robótica educativa. Para eso integré visión artificial, electrónica de control, sistemas embebidos, una cinta transportadora, un sensor óptico, una Raspberry Pi y un manipulador Dobot Magician Lite.

Me interesa remarcar desde el inicio que el proyecto no se limita a entrenar un modelo de inteligencia artificial. El trabajo principal fue construir un sistema físico completo, hacer que cada bloque funcione por separado y después lograr que todos esos bloques trabajen coordinados en un ciclo automático.

**Transición:** primero voy a explicar cuál es el problema concreto que motiva el proyecto.

## 2. Problema de partida

**Foco:** cuantificar el problema manual y mostrar que no es una molestia menor, sino una tarea repetitiva, extensa y de bajo valor agregado.

**Speech sugerido:**

El punto de partida es una situación bastante común en instituciones que usan kits de robótica educativa. El kit puede estar perfectamente ordenado al inicio, pero después de una clase o de una práctica vuelve mezclado. A partir de ahí aparece una tarea manual: reordenar, contar, verificar faltantes y dejar el kit listo para volver a usarlo.

El problema se vuelve más claro cuando lo llevamos a números. Cada kit tiene alrededor de 100 componentes distintos y, en total, debe contener 810 piezas. Además, en una institución puede haber entre 10 y 15 kits. Eso significa que una persona, o un grupo de personas, puede tener que controlar aproximadamente entre 8.000 y 12.000 piezas si se quiere revisar el inventario completo.

Ese trabajo normalmente requiere entre una y dos jornadas, dependiendo de cuántas personas participen. En general se hace de a dos personas, aunque puede sumarse más gente si hay urgencia o si los kits tienen que estar disponibles rápidamente para una clase.

Desde mi punto de vista, ahí hay un despropósito operativo: una persona capacitada termina dedicando muchas horas a una tarea repetitiva de conteo y ordenamiento, cuando ese tiempo podría usarse en actividades de mayor valor para la institución, como preparar mejores clases, capacitar docentes, mantener el equipamiento o planificar nuevas prácticas.

Entonces el problema no es solamente que las piezas estén mezcladas. El problema es la pérdida de trazabilidad, el tiempo requerido para recuperarla y el bajo valor agregado de hacer ese control completamente a mano.

**Transición:** frente a este tipo de problema, no partimos de una idea aislada; existen sistemas automáticos que resuelven tareas parecidas en otros contextos.

## 3. Contexto tecnológico

**Foco:** mostrar que transportar, detectar, decidir y separar objetos es una lógica real en automatización.

**Speech sugerido:**

La clasificación automática de objetos ya se usa en muchos sistemas reales. En general, aunque cambie la escala o el producto, la lógica de fondo es parecida: primero se transporta un objeto, luego se lo detecta o inspecciona, después se toma una decisión y finalmente se lo separa o deposita según algún criterio.

Los ejemplos que muestro acá sirven para ubicar el proyecto dentro de esa familia de soluciones. No busqué copiar una máquina industrial, porque el entorno educativo tiene otras restricciones: piezas pequeñas, presupuesto limitado, espacio reducido y necesidad de trabajar con hardware disponible en el laboratorio.

Lo importante es rescatar la lógica general: si se puede automatizar la identificación y separación de objetos en otros entornos, también se puede adaptar esa idea a una problemática educativa concreta, como el inventario de kits de robótica.

**Transición:** a partir de esa lógica general, el proyecto propone una adaptación compacta para piezas de kits educativos.

## 4. Oportunidad del proyecto

**Foco:** presentar la idea central: piezas mezcladas entran, piezas clasificadas e inventariadas salen.

**Speech sugerido:**

La oportunidad del proyecto fue llevar esa lógica de clasificación automática a una escala de laboratorio. La idea básica es simple: las piezas mezcladas ingresan al sistema, el prototipo las transporta, las observa con una cámara, reconoce a qué clase pertenecen, las manipula con el robot y actualiza un registro digital.

En otras palabras, el sistema no solo ordena físicamente. También genera información. Eso es importante porque el inventario no queda dependiendo únicamente de mirar una bandeja, sino que se registra la cantidad de piezas clasificadas por tipo.

El objetivo no fue construir una solución industrial cerrada para todos los componentes del kit desde el primer intento, sino validar una arquitectura funcional: demostrar que se puede integrar transporte, sensado, visión artificial, manipulación robótica e inventario digital en un único flujo de operación.

**Transición:** antes de entrar en cada bloque, muestro la solución final construida.

## 5. Solución construida

**Foco:** mostrar el prototipo completo y orientar visualmente al jurado.

**Speech sugerido:**

Esta es la vista general del prototipo final. Se puede ver la cinta transportadora, la zona de inspección, el sistema de sensado, la Raspberry Pi como unidad de procesamiento, la electrónica de control, el Dobot Magician Lite y las bandejas o depósitos donde se ubican las piezas clasificadas.

Decidí mostrar primero el sistema completo porque ayuda a entender que cada parte que voy a explicar después tiene una función dentro de un conjunto. La cinta no es solo una cinta: posiciona la pieza. El sensor no es solo un detector: sincroniza el ciclo. La cámara no es solo una cámara: genera la entrada para el modelo. Y el robot no trabaja aislado: ejecuta una decisión tomada por el software.

El resultado final es un prototipo capaz de ejecutar ciclos automáticos de clasificación, manipulación e inventariado. A partir de ahora voy a descomponerlo en bloques para explicar qué se hizo en cada parte.

**Transición:** primero, veamos la arquitectura global del sistema.

## 6. Diagrama global del sistema

**Foco:** explicar el flujo completo de información y acción.

**Speech sugerido:**

Este diagrama resume cómo se organiza el sistema. El flujo comienza con la alimentación de piezas y el transporte sobre la cinta. Cuando una pieza llega a la zona de inspección, el sensor óptico detecta su presencia y permite detener la cinta. Luego la Raspberry Pi captura una imagen, ejecuta la inferencia del modelo de visión artificial y determina qué pieza fue detectada.

Después aparece otro paso clave: convertir una detección en imagen, que está en píxeles, en una posición física que el robot pueda alcanzar. Para eso se utiliza una calibración entre cámara y robot. Con esa información, el Dobot realiza la toma y el depósito. Finalmente, el software actualiza el inventario digital.

Entonces hay dos tipos de flujo trabajando juntos. Por un lado, el flujo físico de la pieza: tolva, cinta, zona de inspección, toma y depósito. Por otro lado, el flujo de información: sensor, imagen, predicción, coordenadas, comando al robot e inventario.

**Transición:** empiezo por el bloque que hace posible mover y presentar las piezas: la parte mecánica.

## 7. Bloque mecánico: alimentación y transporte

**Foco:** remarcar diseño, construcción e iteración mecánica.

**Speech sugerido:**

El bloque mecánico tiene la función de recibir piezas, ordenar parcialmente el flujo y llevarlas hasta la zona de inspección. Para eso construí una cinta transportadora compacta, una tolva de alimentación, guías o paletas separadoras, rodillos, poleas, una banda y una estructura de soporte.

Esta parte fue importante porque la visión artificial y el robot dependen mucho de cómo llega la pieza. Si las piezas llegan amontonadas, fuera de lugar o con una orientación muy desfavorable, todo el resto del sistema se vuelve más difícil. Por eso el diseño mecánico no fue solamente montar una cinta, sino ajustar el ingreso de piezas para lograr una presentación suficientemente estable.

Durante el desarrollo hubo iteraciones: se modificaron elementos de la cinta, se ajustaron guías, se revisó el comportamiento de la banda y se buscó reducir agrupamientos. El sistema no elimina completamente todos los problemas de individualización, pero permitió obtener un flujo suficiente para validar el ciclo automático completo.

**Transición:** una vez resuelto el transporte físico, hacía falta controlar el movimiento y sincronizarlo con el resto del sistema.

## 8. Bloque electrónico: accionamiento y control local

**Foco:** explicar el rol del ESP32 y de la electrónica como subsistema local.

**Speech sugerido:**

Este bloque convierte la cinta en un subsistema controlado. El hardware principal incluye un motor paso a paso NEMA 17, un driver A4988, una fuente de alimentación, un regulador LM2596, un ESP32, la placa de conexiones y pulsadores de control.

El ESP32 cumple un rol local: mantiene el avance de la cinta, lee el estado del sensor y decide cuándo detener el transporte. Esto permite separar responsabilidades. La Raspberry Pi se concentra en la visión, la decisión de alto nivel, el robot y el inventario; el ESP32 se ocupa del control inmediato de la cinta y del evento de detección.

Esta separación es útil porque el control de transporte necesita reaccionar de manera simple y confiable. Cuando el sensor detecta una pieza, el ESP32 detiene la cinta y habilita que el resto del sistema continúe con captura e inferencia. Así, la cinta deja de ser un elemento mecánico suelto y pasa a formar parte de una secuencia sincronizada.

**Transición:** el evento que permite esa sincronización lo genera la barrera óptica.

## 9. Sensado: barrera láser-LDR

**Foco:** explicar por qué el sensor es clave para pausar el sistema justo cuando hay una pieza.

**Speech sugerido:**

Para detectar la presencia de una pieza utilicé una barrera óptica formada por un módulo láser KY-008 y una LDR. La idea es que, mientras el haz llega a la LDR, la cinta puede seguir avanzando. Cuando una pieza interrumpe el haz, el sistema interpreta que hay un objeto en la zona de inspección.

Este sensor cumple una función de sincronización. No clasifica la pieza, no mide su geometría ni decide el destino, pero determina el momento en que conviene detener la cinta y capturar la imagen. Es decir, convierte el paso de una pieza en un evento útil para el ciclo automático.

También fue necesario resolver el montaje físico del sensor, con soportes impresos que mantuvieran alineados emisor y receptor. En un prototipo de este tipo, una pequeña desalineación o una ubicación poco conveniente puede generar falsas detecciones o pérdida de repetitividad.

**Transición:** con la pieza detenida y detectada, entra en juego la Raspberry Pi como coordinadora del sistema.

## 10. Coordinación central: Raspberry Pi

**Foco:** presentar la Raspberry Pi como nodo de integración.

**Speech sugerido:**

La Raspberry Pi 4 funciona como el nodo central del prototipo. No acciona directamente la cinta, sino que concentra la lógica de alto nivel: recibe el estado del sistema, captura la imagen, ejecuta la inferencia, interpreta el resultado, aplica la calibración, comanda el Dobot y actualiza el inventario.

Me gusta pensar esta parte como el punto donde se unen los mundos del proyecto. Por un lado está el hardware físico: sensor, cinta, cámara y robot. Por otro lado está el software: detección, selección de pieza, coordenadas, secuencia de movimiento y registro digital.

Las entradas principales son el estado del sensado, la imagen de la zona de inspección y los parámetros de calibración. El proceso interno incluye preparar la imagen, consultar o ejecutar el modelo, seleccionar la detección válida y calcular la posición de toma. Las salidas son el comando al robot, el destino de depósito y la actualización del inventario.

**Transición:** el primer procesamiento importante que realiza esta lógica central es la visión artificial.

## 11. Visión artificial: dataset y modelo

**Foco:** explicar las 7 clases como subconjunto representativo y volver a la escala real del kit.

**Speech sugerido:**

Para la visión artificial construí un dataset propio con imágenes tomadas sobre el montaje real. Esto es importante porque el modelo no se entrenó con imágenes genéricas de internet, sino con piezas reales, sobre la cinta real y bajo condiciones similares a las que aparecen durante el ciclo automático.

En esta versión se trabajó con 7 clases de piezas y 356 imágenes. Roboflow se usó para organizar el dataset, anotar las imágenes con cajas, generar versiones del conjunto de datos y entrenar el modelo de detección.

Acá vale la pena volver al dato inicial del problema. El kit completo tiene cerca de 100 componentes distintos y 810 piezas totales. Entonces estas 7 clases no representan todavía la totalidad del kit, sino un subconjunto elegido para validar la arquitectura. La pregunta que intenta responder esta etapa no es "ya clasifiqué las 100 clases", sino "¿el sistema completo puede detectar piezas reales, manipularlas y registrar el inventario de manera automática?".

Una vez validada esta base, ampliar la cantidad de clases sería una continuación natural: implicaría capturar más imágenes, etiquetar más piezas, entrenar nuevas versiones del modelo y adaptar eventualmente el agarre para piezas más difíciles.

**Transición:** una vez entrenado el modelo, el sistema necesita convertir una imagen nueva en una decisión operativa.

## 12. Inferencia: de imagen a decisión

**Foco:** explicar cómo una predicción se transforma en acción.

**Speech sugerido:**

En la etapa de inferencia, el sistema captura una imagen de la zona de inspección y el modelo devuelve una o más predicciones. Cada predicción incluye la clase detectada, una región de la imagen marcada con una caja y un nivel de confianza.

El software no se queda solo con la etiqueta. Tiene que seleccionar una detección válida, conservar la posición de la pieza en la imagen y asociar esa clase con un destino físico. Por ejemplo: si el modelo detecta cierto tipo de pieza, esa clase se vincula con un depósito determinado.

Este paso es el puente entre inteligencia artificial y automatización. La red neuronal entrega información visual, pero el sistema necesita traducir esa información en una decisión concreta: qué pieza tomar y hacia dónde llevarla.

**Transición:** para que el robot pueda tomar la pieza, todavía falta convertir la posición en imagen a coordenadas físicas.

## 13. Calibración cámara-robot

**Foco:** explicar la homografía de manera clara y aplicada.

**Speech sugerido:**

La predicción del modelo está expresada en píxeles. El Dobot, en cambio, necesita coordenadas físicas dentro de su espacio de trabajo. Por eso fue necesario calibrar la relación entre el plano de la imagen y el plano real donde se ubican las piezas.

Para resolverlo utilicé una homografía, que permite transformar puntos de la imagen en puntos del plano físico. En términos prácticos, tomo el centro de la caja detectada en la imagen y lo convierto en una coordenada que el robot puede usar como punto de toma.

La calibración se hizo usando pares de puntos imagen-robot sobre la zona visible de la cinta. En el informe se documenta el uso de 15 puntos y el cálculo con OpenCV mediante `cv2.findHomography()` usando RANSAC. Además, se definió una pose fija de cámara y una zona válida para evitar enviar al robot a posiciones fuera de alcance o poco confiables.

Este paso es fundamental porque una buena detección visual no alcanza si después el robot no puede ubicar físicamente la pieza.

**Transición:** con la clase y la posición física definidas, el siguiente bloque es la manipulación robótica.

## 14. Manipulación robótica: Dobot y depósitos

**Foco:** mostrar que el Dobot ejecuta una decisión calculada por el sistema.

**Speech sugerido:**

En esta etapa el Dobot Magician Lite realiza la maniobra de pick and place. Recibe una posición de toma, se desplaza hacia la pieza, la toma con el gripper y la deposita en el sector correspondiente según la clase detectada.

El robot no actúa de forma aislada ni con una secuencia fija independiente de la pieza. La posición de toma viene de la calibración cámara-robot, y el destino depende de la clase predicha por el modelo. Por eso esta etapa integra la salida de visión artificial con el movimiento físico.

Durante el desarrollo también aparecieron limitaciones propias del efector final. El gripper estándar funciona mejor con algunas geometrías que con otras, especialmente en piezas medianas o con zonas de agarre claras. Algunas piezas pequeñas, muy finas o con orientaciones desfavorables son más difíciles de tomar. Eso aparece después en los resultados y en las mejoras futuras.

**Transición:** una vez que la pieza se deposita, el sistema debe cerrar el ciclo registrando lo que ocurrió.

## 15. Inventario digital

**Foco:** remarcar que el sistema produce trazabilidad, no solo movimiento físico.

**Speech sugerido:**

El inventario digital es el cierre lógico del ciclo. Después de depositar una pieza, el software incrementa el contador asociado a la clase reconocida y guarda esa información en un archivo.

Esto es importante porque uno de los problemas iniciales era la pérdida de trazabilidad. Si el sistema solo moviera piezas de un lugar a otro, resolvería parcialmente el orden físico, pero no generaría un registro verificable. En cambio, con el inventario digital, cada ciclo exitoso queda asociado a una clase y a un conteo.

En esta versión el inventario se resolvió de forma simple, mediante archivo persistente. Aun así, valida la idea central: el resultado del ciclo físico queda vinculado con un dato digital. En una evolución futura, esto podría crecer hacia una interfaz gráfica, una base de datos, historial por sesión o gestión de múltiples kits.

**Transición:** juntando todos estos bloques, se obtiene el ciclo automático integrado.

## 16. Ciclo automático integrado

**Foco:** narrar la secuencia completa mientras se muestra el video.

**Speech sugerido:**

En esta diapositiva se ve el ciclo automático integrado. La secuencia completa es la siguiente: primero la pieza avanza por la cinta; luego la barrera óptica detecta su presencia y detiene el transporte; después la Raspberry Pi captura la imagen y realiza la inferencia; con la clase y la posición obtenidas, se calcula el punto de toma; el Dobot toma la pieza y la deposita en el sector correspondiente; finalmente, el inventario digital se actualiza.

Lo que busqué validar acá es que los bloques no funcionen solo como demostraciones separadas. La cinta, el sensor, la cámara, el modelo, la calibración, el robot y el inventario tienen que encadenarse en una única operación.

Este punto es central para la defensa del proyecto: el aporte no está en que exista una cinta, o un modelo, o un robot por separado. El aporte está en haber logrado que todos esos elementos formen una plataforma funcional.

**Transición:** antes de mostrar resultados, explico cómo se validó el sistema.

## 17. Ensayos realizados

**Foco:** ordenar la validación: primero por bloque, después integración, finalmente corrida de 35 ciclos.

**Speech sugerido:**

La validación se hizo de forma progresiva. Primero se probaron los bloques por separado: transporte, sensor, cámara, inferencia, Dobot e inventario. Esto permitió detectar problemas locales antes de integrarlos.

Después se avanzó hacia pruebas de integración. Por ejemplo, que el ESP32 detenga la cinta ante una detección, que la Raspberry capture la imagen en el momento correcto, que el modelo devuelva una predicción útil, que esa predicción se transforme en coordenadas y que el Dobot ejecute la toma y el depósito.

Finalmente se realizó una corrida integral de 35 ciclos automáticos consecutivos. Ese número no busca representar una campaña estadística definitiva sobre todo el universo del kit, sino una validación funcional del sistema completo trabajando de manera repetida.

**Transición:** con esa corrida y con las métricas del modelo, se obtuvieron los resultados medibles.

## 18. Resultados medibles

**Foco:** separar desempeño del modelo y desempeño del sistema físico completo.

**Speech sugerido:**

Los resultados se pueden leer en dos niveles. Primero está el desempeño del modelo de visión artificial. El modelo final alcanzó un mAP@50 de 99,5%, una precisión de 96,6%, un recall de 98,6% y un F1-score de 97,6%. Estos valores indican que, dentro del conjunto de clases entrenadas y las condiciones de validación, el modelo tuvo un desempeño muy bueno.

Pero el proyecto no termina en el modelo. Por eso también medí el desempeño del sistema completo. En la corrida de 35 ciclos, hubo 32 clasificaciones correctas, 29 tomas correctas, 28 depósitos correctos y 27 ciclos completados sin intervención. El tiempo de ciclo estuvo alrededor de 20 segundos.

La lectura importante es que, a medida que pasamos de visión a manipulación física, aparecen pérdidas. Eso es esperable en un prototipo integrado: el modelo puede detectar bien, pero después influyen la orientación de la pieza, el punto real de agarre, la precisión de la calibración y las limitaciones del gripper.

También vuelvo a relacionarlo con la escala del problema original. Frente a kits de 810 piezas y entre 10 y 15 unidades por institución, este prototipo todavía no reemplaza todo el proceso manual. Pero sí valida una base técnica para automatizarlo: reconoce piezas reales, toma decisiones, manipula objetos y genera inventario. La ampliación de clases y la mejora mecánica son pasos siguientes, no cambios de concepto.

**Transición:** con esos resultados, cierro con qué quedó validado y qué mejoras quedan abiertas.

## 19. Conclusión y continuidad

**Foco:** cerrar fuerte: se validó una arquitectura completa y queda una plataforma evolutiva.

**Speech sugerido:**

Como conclusión, se construyó una base funcional para automatizar el inventario de kits de robótica educativa. El sistema integró transporte, sensado, visión artificial, calibración cámara-robot, manipulación robótica e inventario digital en un prototipo operativo.

Quedó validado que es posible detectar piezas reales sobre la cinta, convertir esa detección en una decisión, ejecutar una acción robótica y registrar el resultado. También quedó claro qué aspectos limitan hoy el desempeño: la alimentación individual de piezas, la robustez del agarre, la ampliación del conjunto de clases y la dependencia de inferencia remota.

Las mejoras futuras más directas serían rediseñar la alimentación para garantizar una pieza por vez, optimizar o cambiar el efector final del robot, ampliar progresivamente el dataset hasta cubrir más piezas del kit, ejecutar inferencia local y desarrollar una interfaz gráfica con gestión avanzada del inventario.

El valor final del proyecto es haber demostrado la viabilidad técnica de una arquitectura completa. No es solo una maqueta ni solo un modelo de IA: es una plataforma integrada que puede evolucionar hacia una herramienta real para reducir tareas manuales repetitivas en instituciones educativas.

**Transición:** con esto doy por finalizada la presentación y quedo disponible para preguntas.

## 20. Muchas gracias

**Foco:** cierre breve y preparar respuestas.

**Speech sugerido:**

Muchas gracias por su atención.

Quedo disponible para preguntas sobre el diseño mecánico, la electrónica de control, la visión artificial, la calibración cámara-robot, la integración del software o los resultados obtenidos.

## Preguntas que conviene tener preparadas

**Por qué solo 7 clases si el kit tiene cerca de 100 componentes distintos:** porque el alcance del proyecto fue validar la arquitectura completa con un subconjunto representativo. Ampliar clases requiere más imágenes, más etiquetado, reentrenamiento y posiblemente mejoras de agarre.

**Por qué usar Raspberry Pi y ESP32:** la Raspberry Pi concentra procesamiento de alto nivel, visión, comunicación con el robot e inventario; el ESP32 se encarga del control local de la cinta y lectura del sensor.

**Qué parte fue más crítica:** la integración. Cada bloque podía funcionar por separado, pero el desafío fue sincronizar transporte, sensado, captura, predicción, calibración, robot e inventario.

**Qué limita más el desempeño actual:** la individualización de piezas y el agarre físico. Las métricas del modelo fueron altas, pero el ciclo completo depende también de mecánica, orientación de pieza y precisión de toma.

**Qué haría primero como mejora:** mejorar la alimentación para garantizar una pieza por vez y rediseñar el efector final o los puntos de agarre. Eso probablemente aumentaría el porcentaje de ciclos completos sin intervención.
