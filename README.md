# Practica4
## Olivia Troitiño, Claudia Gascó, Alberto Martin
README separado en dos secciones.
1. Dev (comentarios durante el development de la práctica)
2. Entrega (información README estándar)

## Dev
### 👥 Organización del trabajo (3 personas)
```
🔹 Persona A: Obtención y preprocesamiento de datos
    Extraer al menos 10 reseñas reales (pueden ser más).
    Etiquetarlas manualmente o tomar reseñas con calificación (1 estrella = negativa, 5 estrellas = positiva).
    Guardarlas en un archivo .csv o .json.
    Opcional: crear un pequeño notebook para dejar documentado el paso (cuenta como “Notebook extractor de datos inicial”).
🔹 Persona B: Diseño de prompts y ejecución
    Crear 3 prompts por técnica.
    Ejecutar los prompts en al menos 3 modelos distintos de Hugging Face.
🔹 Persona C: Evaluación y presentación
    Comparar resultados entre modelos y entre tipos de prompts.
    Medir: precisión, coherencia, errores frecuentes, etc.
    Redactar el análisis de resultados, incluyendo:
        Qué prompts funcionaron mejor
        Qué modelo fue más acertado o rápido
        Qué dificultades tuvieron
    Armar la presentación (PowerPoint o PDF).
```
**Persona B (Olivia): Prompts y Ejecución**
- Tengo un prompt por cada técnica, todas corren pero la última (CoT) da todo negativo en los primeros dos modelos.
#TODO armar dos prompts más por cada técnica
#TODO reevaluar el prompt de CoT para ver si no lo estoy guiando a lo negativo O ALTERNATIVAMENTE reevaluar si son los modelos correctos para la práctica.

### Teoría Prompt Engineering
- **Zero-shot** prompting means that the prompt used to interact with the model won't contain examples or demonstrations. The zero-shot prompt directly instructs the model to perform a task without any additional examples to steer it.
    Example: 
    ``` Prompt:
            Classify the text into neutral, negative or positive. 
            Text: I think the vacation is okay.
            Sentiment:
        Output:
            Neutral```
- **Few-shot** prompting can be used as a technique to enable in-context learning where we provide demonstrations in the prompt to steer the model to better performance.
    Example:
    ``` Prompt: 
            A "whatpu" is a small, furry animal native to Tanzania. An example of a sentence that uses the word whatpu is:
            We were traveling in Africa and we saw these very cute whatpus.
            To do a "farduddle" means to jump up and down really fast. An example of a sentence that uses the word farduddle is:
        Output:
            When we won the game, we all started to farduddle in celebration.```
    We can observe that the model has somehow learned how to perform the task by providing it with just one example (i.e., 1-shot). For more difficult tasks, we can experiment with increasing the demonstrations (e.g., 3-shot, 5-shot, 10-shot, etc.).
- **Chain-of-thought** (CoT) prompting enables complex reasoning capabilities through intermediate reasoning steps. You can combine it with few-shot prompting to get better results on more complex tasks that require reasoning before responding.
    Example:
    ``` Prompt:
            The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
            A: Adding all the odd numbers (9, 15, 1) gives 25. The answer is False.

            The odd numbers in this group add up to an even number: 17,  10, 19, 4, 8, 12, 24.
            A: Adding all the odd numbers (17, 19) gives 36. The answer is True.

            The odd numbers in this group add up to an even number: 16,  11, 14, 4, 8, 13, 24.
            A: 
        Output:
            Adding all the odd numbers (15, 5, 13, 7, 1) gives 41. The answer is False.```



## Entrega
### Librerías
```
%pip install datasets
%pip install transformers
%pip install pandas
%pip install tensorflow
%pip install torch
%pip install tf-keras
%pip install os
```
### LLMs Testeados
1. `siebert/sentiment-roberta-large-english`
- Clasifica reseñas en positivo y negativo. Solo funciona para "raw text", hay que darle solamente la reseña. Por lo tanto, no aplica a ninguno de los tipos de prompt engineering.
2. `nlptown/bert-base-multilingual-uncased-sentiment`
- Clasifica reseñas de 1 a 5 estrellas.
3. `google/flan-t5-base`
- 

### Instrucciones:

Objetivo: Aplicar modelos de tipo Large Language Models (LLMs) para extraer conocimiento.
Formación de grupos: Trabajar en grupos de hasta 4 personas y documentar los nombres en un README.md.
Exploración de modelos:

Utilizar al menos tantos modelos de LLM como participantes en el grupo.
Los modelos pueden ser del repositorio de Hugging Face o de una API pública.

### Pruebas de prompts:

Probar al menos tres tipos de prompts:
- Zero-shot (solo explicación).
- Few-shots (explicación con ejemplos).
- Chain of thoughts (razonamiento del resultado).

Selección del problema: Elegir un problema validable o con métrica numérica (ejemplos: detección de copia, corrección automática de exámenes, detección de spam, extracción de contactos, …).
Aplicación del sistema: Aplicar el sistema a más de una fuente de datos o documentos (al menos 10).

### Entrega:

Crear un Jupyter Notebook aplicable en Google Colab, incluyendo modelos, prompts explicados, ejecutados y evaluados.
Preparar una presentación para exponer el último día de clase, explicando el problema, los mejores prompts y modelos, y un resumen de los resultados con conclusiones.

### Evaluación:

- Exploración de modelos de tipo LLM y técnicas de prompt engineering justificadas. (3 puntos)
- Evaluación y justificación de los resultados del prompt engineering. (2 puntos)
- Presentación. (4 puntos)
- Limpieza y calidad general. (1 punto)

### Entregables:

- Jupyter Notebook extractor de datos inicial (OPCIONAL).
- Carpeta con los datos de entrada INPUT.
- Jupyter Notebook principal con modelos, prompts y evaluación.
- Presentación que se expone en clase

### Notas:

- La práctica se puede realizar en grupos de máximo 4 personas. Los nombres y apellidos de los integrantes del grupo han de aparecer en la primera línea de un fichero llamado “README.md” entregado con la práctica. Si no aparece dicha línea, se considera que la práctica fue realizada de manera individual por la persona que entregó la práctica (con las implicaciones correspondientes de control de copia).
- Los compañeros de la práctica que no se presenten el día de la presentación, obtienen un cero en la parte correspondiente de la presentación. Es decir, la nota de su práctica estará acotada por un 6.
- Los alumnos que entreguen una práctica que dé un error no controlado o no documentado (en un fichero llamado “README.md”), estará automáticamente suspensa con un cero. Entre estos errores se consideran los siguientes:
- Excepciones que no se atrapan ni se documentan.
- Errores de codificación.
- Errores de importación del código como librería.
- Las entregas fuera de la fecha final de la práctica se consideran suspensas y su valoración será un cero.
- Las entregas que empleen librerías no vistas en clase, han de documentar las librerías que hay que instalar y el comando con el que se instalan en un fichero aparte llamado “README.md”. Si aparecen librerías no vistas en clase sin ser documentadas en este fichero, el valor de la práctica será de cero.