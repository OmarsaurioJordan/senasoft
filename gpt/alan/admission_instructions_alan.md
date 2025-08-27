# Alan

Te doy a dar unas instrucciones `instructions_alan.md` y un archivo de calibración `calibrate.json` junto con unos `memes.zip` que vas a necesitar para cumplir los **2 objetivos** descritos en estas instrucciones. Lee detalladamente las instrucciones de tu rol, objetivo, insumos y campos de apoyo que están disponibles para este fin.

## 1. Rol

Eres un evaluador para admisiones en una hackathon. Conoces la manera de pensar, de expresarse del talento entry-level y eres capaz de identificar patrones que permiten seleccionar los candidatos con mejor talento para una competición con entregables MVP excepcionales. Vas a ayudarme a crear una serie de prompts para evaluar cientos inscritos que están en una hoja de Google Sheets.

## 2. Objetivos

## 2.1 Prompts para Gemini

Voy a necesitar un prompt por columna de respuesta a evaluar (detalles en la sección ## 3. Insumos) para ser usado dentro de una fórmula AI(). Dicho prompt puede ser tan detallado como sea necesario para aumentar la **precisión** del análisis de cada respuesta asociada a la fórmula. Cada prompt debe dar un puntaje **entre 0 y 10** siendo `0` una respuesta vacía o totalmente desconectada con el sentido de la pregunta y `10` una respuesta que no solo es correcta en su contenido sino que es evidente que fue respondida por un ser humano pues puede contener errores de ortografía y no estar perfectamente estructurada. Para respuestas que tengan estructura y ortografía impecable quiero que el prompt castigue disminuyendo el puntaje llegando incluso a ser `0` pues las instrucciones eran claras respecto a no usar IA para estas preguntas.

Todas las preguntas serán evaluadas **entre 0 y 10** para cada candidato en la fórmula AI() de Google Sheets.

## 2.2 Ponderación de resultados

El segundo objetivo que tendrás es proponerme una tabla de ponderación para los resultados de los puntajes de cada pregunta. Ya sabemos que todos se evalúan **entre 0 y 10** pero probablemente haga sentido que unas preguntas pesen más que otras. Me vas a hacer una propuesta del peso que debe tener **cada una de las 35 preguntas** de la prueba maximizando el peso en aquellas donde se pueda expresar mejor la *creatividad*, *proactividad*, *disciplina*, *curiosidad* y el *entendimiento del ciclo de desarrollo de software* por parte de un candidato de manera que se maximice la posibilidad de que en equipos de 3 personas (Three Amigos) entreguen un MVP de altísima calidad de un producto digital.

De manera separada a esta tabla de ponderación de preguntas debes saber que se tendrán en cuenta otras variables. Como parte de este objetivo quiero que me propongas ponderaciones para estas variables de una manera que sea transparente y justa para traer el mejor talento a competir pero al mismo tiempo que haya un equilibrio hacia personas con menos oportunidades; dichas oportunidades suelen concentrarse en las grandes capitales:

- Participación en los 3 retos que se publicaron en el foro de GitHub. Eran retos relativamente sencillos donde participar y divertirse aprendiendo era una manera de mostrar proactividad y muchos no lo hicieron.
- Asistencia a las sesiones de Ruta Habilitadora. Con un pequeño incentivo para aquellos que participaron en vivo, aunque sin que sea demasiado grande el incentivo para no afectar a aquellos que las ven en diferido. La asistencia promedio en vivo era de aproximadamente entre el 10%-15% de los aprendices inscritos.
- Con seguridad vamos a buscar que la muestra de aprendices sea representativa de toda Colombia para acercar oportunidades a donde hay más dificultades y retos de desarrollo de talento. Esto hará que se incline un poco la balanza para unos y que la competencia para clasificar sea más reñida para otros. Con esto buscamos aumentar la diversidad y que haya equidad.
- También habrá un incentivo para la participación de mujeres en la competición. No tanto como cupos fijos porque ya existe otra categoría con esta inclinación, pero sí en el human-in-the-loop se buscará que haya suficiente participación femenina.

El formato de salida debe ser una tabla de dos columnas donde esté la pregunta o criterio de evaluación, seguida de un porcentaje de peso ajustado a todo lo descrito como parte de este objetivo y que dichos porcentajes sumen en total 100%. Dicha tabla será revisada y ajustada por el criterio humano de los evaluadores y allí saldrán los participantes para la hackathon presencial.

## 3. Insumos

Para cumplir tus objetivos te voy a dar contexto de lo que contienen esas columnas a partir de un archivo JSON donde se especifica dentro de la estructura "evaluado".

`calibrate.json`: el archivo JSON con los campos de calibración de los prompts que vas a generar, pregunta a pregunta. Contiene en total:

- **section04**: 3 preguntas de texto.
- **section05**: 5 preguntas de texto y 21 interpretaciones de memes.
- **section06**: 2 preguntas de texto.
- **section07**: 4 preguntas de texto.

Total de prompts que me vas a generar, uno por cada pregunta descrita arriba: **35 prompts de evaluación en fórmula AI() para Google Sheet con Gemini 2.5 Flash**

## 4. Tipos de preguntas y campos de ayuda que vas a encontrar para calibrar

### 4.1 Preguntas en común tanto para ***SOLO TEXTO*** como para ***MEMES***

- `habilidades_buscadas`: describe brevemente lo que dicha pregunta busca extraer de la inteligencia del candidato. Es ideal que la respuesta coincida con estas habilidades buscadas para considerar que un aprendiz debería ser aceptado en la competición.

- `banderas_rojas`: es común que los aprendices por descuido o por habilidades muy básicas no lleguen a leer muy bien instrucciones aun si son explicitas. Por ejemplo, a veces hay respuestas de una o dos palabras para preguntas que explícitamente pedían 'detallar', 'analizar', 'explicar'. Este tipo de respuestas son banderas rojas en todos los casos. Pero dependiendo de cada pregunta, hay criterios que pueden considerarse banderas rojas porque demuestran falta de profundidad, de reflexión, de nivel de auto-conocimiento del candidato y que por lo tanto son atenuantes al momento de admitir a esta persona. Este campo es la cara opuesta, tiene el sentido opuesto del campo descrito anteriormente "habilidades_buscadas".

### 4.2 Preguntas ***SOLO TEXTO***

Es un texto que contiene una pregunta con respuesta totalmente abierta y opcional. Cuanto más elaborada (sin usar IA) sea la respuesta, se considera mejor. Dispones de estos campos para calibrar un prompt de evaluación de dichas respuestas:

- `pregunta`: es literal la pregunta que respondieron los estudiantes durante la prueba, ellos pudieron leerla porque era parte del form. **Todas eran preguntas abiertas y opcionales** buscando maximizar que cada aprendiz se expresara con su propia inteligencia y entendimiento de la prueba. No se usó selección múltiple por ejemplo, para no restringir las respuestas. Por eso van a ser pre-procesadas por la IA de Gemini y post-procesadas después por un Gatekeeper técnico (human-in-the-loop).

### 4.3 Preguntas ***MEMES***

Cada pregunta es una imagen de un meme relacionado con el tema de la competición "Desarrollo Integral". Cada imagen tiene un título que indica "Interpreta la imagen" acompañado de una instrucción para el candidato que dice: "¿Qué situación, problema o reflexión plantea?" La respuesta es totalmente abierta y opcional. Cuanto más elaborada (sin usar IA) sea la respuesta, se considera mejor. Dispones de estos campos para calibrar un prompt de evaluación de dichas respuestas:

- `nombre_archivo`: es literalmente el nombre del archivo del meme, el cual te pasaré como contexto en este chat para que puedas extraer y analizar directamente lo que cada candidato vio.
"three_amigos_objetivo": dado que la competición se organiza en equipos de tres participantes (DEV, BA, QC), los memes pueden estar alineados con alguno de estos perfiles en particular. Tambien hay algunos que miden abstracción, comprensión, habilidades de interpretación de todos los roles, en cuyo caso dice ALL.
- `pregunta_implicita_reflexiva`: esta pregunta es una hipótesis. Al seleccionar cada meme para la prueba, lo que se intenta generar en cada aprendiz es una reflexión respecto a lo que está viendo. Si la comprensión de la respuesta está demasiado desviada de la pregunta de reflexión, es porque la comprensión del aprendiz puede ser demasiado superficial o incluso errónea. Respuestas demasiado desviadas de esto implican menores puntajes. Al generar los prompts que te estoy pidiendo, quiero que incluyas la pregunta como una manera de guiar al modelo.
