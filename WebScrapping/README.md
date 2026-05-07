# Web Scrapping de la Jornada

En este proyecto se consultaron las noticias del 01/01/2013 al 31/12/2015 del periódico La Jornada, las noticias fueron consultadas el 06/05/2026.

## Objetivo:
El objetivo del proyecto fue crear un indicador sobre masacres o multihomicidios en México (>3 muertes) para posteriormente utilizar a la variable como predictora en un análisis de regresión, que ya no se muestra en este repositorio.

## Explicación del flujo:
Si bien cada Notebook tiene una explicación, se describen a continuación las generalidades del repositorio

### 1. Creación del modelo ML
1. Primero, se debe correr el código de `LaJornada_TEST.ipynb`, en este código se extraen solo 60 días de noticias
2. Se extrae su texto y mediante una **Expresión Regular** se filtran la mayoría de noticias extraidas
3. Luego, se etiquetaron las noticias que fueron utilizadas para entrenar al modelo de clasificación de ML; el etiquetado fue mediante la expresión regular anterior.
4. El entrenamiento se realizó con una técnica parecida a Montecarlo, y a Random Forest: se generaron 100 modelos, cada uno con los mismos parámetros pero con una muestra aleatoria de los datos etiquetados, se puede ver un histograma de los parámetros de cada modelo invidual.
<img width="538" height="407" alt="image" src="https://github.com/user-attachments/assets/5a0df57c-0bf7-4722-905f-a6db8f3ae43a" />
5. Tras esto, se utilizaron estos modelos para "entrenar" a un único modelo óptimo, que obtuvo increíbles valores en cuanto a *precisión* y *recall*

### 2. Web Scrapping Fuerte y uso del modelo ML
1. Ya en el notebook `LaJornada_FINAL.ipynb`, primero se envían request a la ***portada y contraportada*** de cada periódico publicado diario por La Jornada, una vez adquirida la respuesta, se buscan todos los *links* y *href* dentro del html (y dentro de un *xml*) y se guardan según se encuentren en un archivo tipo JSON Lines(`.jsonl`)
2. Luego, para cada link en el archivo, se envía un request y se extrae su información (texto). **En total se extrae el texto de casi 80,000 noticias**. También se guarda el progreso según se extrae el texto en un JSON Lines
3. Tras obtener el texto, se utiliza una *expresión regular* para filtrar solo aquellas noticias que contienen ciertas palabras clave, y se guardan en otro archivo JSON Lines (`noticias_con_match.jsonl`)
4. Usando el motor de lenguaje en español de la librería `spacy`, se buscan las localizaciones de cada noticia, para intentar cruzarlas con el catálogo de municipios del INEGI, y así obtener un registro espacial
5. Por último, se utiliza el modelo entrenado en el otro notebook para clasificar estas noticias, y se mantiene no solo el resultado sino también la confianza del resultado (Distancia al hiperplano). Todo esto se guarda en el archivo `predicciones_ML.csv`
