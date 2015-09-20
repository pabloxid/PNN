# PNN
Diseño, exploración, entrenamiento y visualización de Redes Neuronales Artificiales (ANN)

**Introducción:**

Más allá de la estética, este programa puede servir para probar en la práctica si determinado problema puede resolverse con este tipo de red neuronal (es posible que el modelo no resuelva cierto problema concreto, pero lo que sí es seguro es que el algoritmo de optimización de pesos es aceptable, sobre todo en relación al tiempo que se tarda en hallar una solución). 

Hay que encontrar un conjunto de no más de 20 datos que puedan ser representados por números enteros, elaborar una lista de ejemplos (que es bien fácil, son archivos de texto que en cada línea contienen los valores para cada entrada separados por comas), y probar. Al dimensionar la red, el número de entradas tiene que coincidir con el número de valores que hay en cada línea de los ejemplos, y el número de salidas depende del significado que se le dé, pero nótese que los ejemplos sólo pueden producir "1" en una de las salidas y "0" en todas las otras. El número de nodos de la capa oculta debe ser tan grande como el problema a resolver lo necesite, pero en el programa está limitado a 25.

**MANUAL**

*Dimensionar la red*

El primer paso para usar PNN es dimensionar la red. Los campos Entradas, Nodos ocultos y Salidas permiten especificar el número de neuronas de cada capa, y el botón Dimensionar confirma la acción. El máximo de neuronas es 20 para las capas de entrada y salida, y 25 para la capa oculta.

Al cambiar el número de neuronas en las capas de entrada o de salida, se borran todos los ejemplos y los pesos, y por consiguiente, el aprendizaje realizado. Al re-dimensionar la capa oculta, se borran los pesos pero no los ejemplos.

*Opciones de entrenamiento*

*Factor de aprendizaje:* es la variable que determina qué tanto son modificados los pesos en cada iteración de aprendizaje. Al aumentar este número, el error decrece a pasos más grandes pero en forma más inestable, pudiendo en ocasiones oscilar o incluso aumentar; al disminuir el valor, el aprendizaje se vuelve lento pero seguro. En el Modo automático este parámetro está desactivado.

*Aprendizaje extra:* la idea de este parámetro es darle más importancia, en el aprendizaje, a los ejemplos "positivos" o a los "negativos" (un ejemplo destinado a la salida 2 es un ejemplo "negativo" para la salida 1).

*Cantidad de iteraciones:* es la cantidad de bucles de backpropagation que ocurren al apretar el botón Iniciar aprendizaje en el Modo manual. En los modos semi-automático y automático este control está desactivado.

*Lista de ejemplos / Ingresar valores de entrada*

Son la parte central del programa. La lista de ejemplos cargados muestra en cada línea un conjunto de valores para las entradas y su correspondiente salida asociada. Los ejemplos están "asociados" a una salida, esto quiere decir que se asume que producen "1" en dicha salida y "0" en todas las demás salidas. En la lista podemos ver además el archivo desde donde se cargó cada ejemplo.

Los ejemplos se pueden borrar, seleccionándolos y apretando la tecla "Suprimir". Si apretamos "Enter" sobre un ejemplo, éste se carga en el campo Ingresar valores de entrada, y desde allí se puede testear el comportamiento de la red apretando Procesar salida. También es posible ingresar valores manualmente en ese campo y probarlos, y una vez ingresados se pueden agregar a la lista con el botón Agregar ejemplo. Los valores ingresados pueden ser enteros de cualquier tamaño.

Los ejemplos de la lista se pueden activar y desactivar con las teclas "+" y "-", respectivamente. Los ejemplos activados son los que se usan para el entrenamiento, los otros pueden permanecer en la lista a efectos de testear el desempeño de la red.

*Monitor de salida y error*

El dato mostrado a la derecha como Error se calcula en cada iteración del entrenamiento, como la media cuadrática de la diferencia entre el valor que debería producir cada ejemplo en cada salida y el que realmente produce. Las salidas se muestran como barras cuyo máximo valor es "1" y el mínimo "0", y se computan durante el entrenamiento o al apretar Procesar salida.

*Aleatorizar pesos*

Este botón modifica aleatoriamente los valores de los pesos, de acuerdo al modo de aleatorización seleccionado en el menú Configuración.

*Iniciar aprendizaje*

Inicia el proceso de entrenamiento de la red, de acuerdo al modo de operación seleccionado en el menú Configuración.

*Menú Archivo*

*Cargar set de ejemplos:* permite ingresar un conjunto de ejemplos desde un archivo de texto. Dicho archivo deberá tener en cada línea un grupo de valores separados por comas, uno para cada entrada. Al cargar un archivo, todos los ejemplos que éste contenga se asociarán a la salida seleccionada en el cuadro de diálogo que aparece a continuación.

*Cargar y Guardar pesos:* permiten salvar los pesos en un archivo, una vez concluido el entrenamiento y volverlos a cargar luego para usarlos como punto de partida de una siguiente sesión de aprendizaje. Los pesos se guardan en un archivo de texto conteniendo un conjunto de valores separados por comas en cada línea, correspondientes al conjunto de pesos de cada nodo, empezando por los de la capa de salida y siguiendo por los de la capa oculta, en orden ascendente. El número de valores en cada línea de pesos de salida es igual a Nº de nodos ocultos + 1 y en cada línea de pesos de la capa oculta es igual a Nº de entradas + 1; ello se debe a la presencia de las neuronas "bias".

*Menú Configuración*

*Modos de operación:* en el modo "manual", el usuario puede especificar el número de iteraciones que se producirán al pulsar Iniciar aprendizaje y ajustar el factor de aprendizaje y el aprendizaje extra en cada oportunidad. En el modo "semi-automático" el programa seguirá repitiendo el bucle de entrenamiento mientras el error se mantenga decreciente. En el modo "automático" el programa toma el control de todos los parámetros, y repite 10 veces la rutina de entrenamiento partiendo de distintos valores aleatorios, ajustando automáticamente el factor de aprendizaje y devuelve el mejor de los 10 resultados.

*Modos de aleatorización:* afectan al comportamiento del botón Aleatorizar pesos. Cuando la aleatorización es "relativa" se le suma a cada peso un valor aleatorio, de lo contrario se sustituye su valor actual por el nuevo. "extrema" y "moderada" se refieren a la magnitud de los números aleatorios utilizados.

*Menú Ayuda*

*Demo:* esta opción tiene el efecto de dimensionar una red con 7 entradas y 3 salidas, y cargar 3 sets de aproximadamente 20 ejemplos cada uno, uno para cada salida.

*Ventana de visualización*

Esta ventana muestra una representación gráfica tridimensional de la red, en la cual las neuronas de cada capa están representadas por esferas de un color. El tamaño de estas esferas representa el valor de salida de la neurona, y los diámetros de las conexiones representan los pesos. Las conexiones de color verde son positivas y las de color azul son negativas. Las neuronas "bias" son de color blanco y su tamaño es constante.

Al hacer foco en la ventana de visualización, quedan disponibles las siguientes opciones:

- haciendo click con el botón derecho del mouse, detenemos o reanudamos la rotación automática del modelo. Cuando la rotación automática está detenida, podemos rotarlo libremente con el botón izquierdo del mouse.

- con las teclas de dirección seleccionamos un parámetro, que va a aparecer detallado en el ángulo inferior izquierdo de la ventana, y con las teclas "+" y "-" modificamos su valor.

Los parámetros que se pueden modificar son:

- la disposición espacial de las neuronas en cada capa;

- el espaciado de las mismas;

- la rotación de todo el plano de la capa;

- la distancia entre las capas;

- la cantidad de caras de la sección de los "caños" que interconectan a las neuronas (que por defecto es 20, pero puede ir de 2 a 50, generando la sensación cilíndrica).

En caso de haber cerrado la ventana de control, podemos invocarla nuevamente apretando cualquier tecla que no tenga otra función.

