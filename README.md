# Practica4

Olivia Troitiño, Claudia Gascó, Alberto Martin

El objetivo de esta práctica es *demostrar la capacidad de aplicar modelos de tipo Large Language Models (LLMs) para extraer conocimiento*. Los estudiantes deberán utilizar un LLM, ya sea descargado o a través de una API pública, y *diseñar un prompt adecuado utilizando técnicas de prompt engineering*. Este proceso permitirá la automatización del procesamiento de información, la generación de un reporte y la evaluación de la calidad del resultado.

La práctica puede realizarse en grupos de hasta 4 personas, cuyos nombres deben estar claramente indicados en un documento README.md. Durante la realización de la práctica, será necesario explorar el funcionamiento de al menos tantos modelos de tipo LLM como participantes en el grupo. Estos modelos pueden ser del repositorio de Hugging Face o de una API pública. Además, se deben probar al menos tres tipos de prompts, cada uno utilizando una técnica de prompt engineering: zero-shot (solo explicación), few-shots (explicación con ejemplos) y chain of thoughts (razonamiento del resultado).

Librerías:
- datasets
- pandas
- os
- transformers
- tf-keras


LLMs seleccionados:
1. `distilbert-base-uncased-finetuned-sst-2-english`
- 

Teoría prompt engineering:
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


El *problema a resolver* es libre, pero debe ser validable como correctamente resuelto o no, o tener algún tipo de métrica numérica. Algunas ideas incluyen la detección de copia en prácticas, la corrección automática de exámenes de programación, la detección de spam, la extracción de contactos de una página web ... Es importante que el sistema se pueda aplicar a más de una fuente de datos o documentos (al menos 10), permitiendo el conteo del número de aciertos o una nota media de calidad si la evaluación es numérica.

    El problema a resolver es un análisis de reseñas de Amazon, las estrellas que el usuario le da al producto (1-5) y el sentimiento (negativo, neutro, positivo).

La práctica se entregará en forma de Jupyter Notebook, que debe ser aplicable en Google Colab. En el Jupyter Notebook deben aparecer los modelos a descargar, los prompts explicados, ejecutados y evaluados. Además, se debe preparar una presentación para exponer el último día de clase, explicando el problema, los prompts y modelos que mejor funcionaron, y un resumen de los resultados obtenidos con conclusiones finales.

Instrucciones:

    Objetivo: Aplicar modelos de tipo Large Language Models (LLMs) para extraer conocimiento.
    Formación de grupos: Trabajar en grupos de hasta 4 personas y documentar los nombres en un README.md.
    Exploración de modelos:

    Utilizar al menos tantos modelos de LLM como participantes en el grupo.
    Los modelos pueden ser del repositorio de Hugging Face o de una API pública.

    Pruebas de prompts:

    Probar al menos tres tipos de prompts:
    Zero-shot (solo explicación).
    Few-shots (explicación con ejemplos).
    Chain of thoughts (razonamiento del resultado).

    Selección del problema: Elegir un problema validable o con métrica numérica (ejemplos: detección de copia, corrección automática de exámenes, detección de spam, extracción de contactos, …).
    Aplicación del sistema: Aplicar el sistema a más de una fuente de datos o documentos (al menos 10).
    Entrega:

    Crear un Jupyter Notebook aplicable en Google Colab, incluyendo modelos, prompts explicados, ejecutados y evaluados.
    Preparar una presentación para exponer el último día de clase, explicando el problema, los mejores prompts y modelos, y un resumen de los resultados con conclusiones.

Evaluación:

    Exploración de modelos de tipo LLM y técnicas de prompt engineering justificadas. (3 puntos)
    Evaluación y justificación de los resultados del prompt engineering. (2 puntos)
    Presentación. (4 puntos)
    Limpieza y calidad general. (1 punto)

Entregables:

    Jupyter Notebook extractor de datos inicial (OPCIONAL).
    Carpeta con los datos de entrada INPUT.
    Jupyter Notebook principal con modelos, prompts y evaluación.
    Presentación que se expone en clase

Notas:

    La práctica se puede realizar en grupos de máximo 4 personas. Los nombres y apellidos de los integrantes del grupo han de aparecer en la primera línea de un fichero llamado “README.md” entregado con la práctica. Si no aparece dicha línea, se considera que la práctica fue realizada de manera individual por la persona que entregó la práctica (con las implicaciones correspondientes de control de copia).
    Los compañeros de la práctica que no se presenten el día de la presentación, obtienen un cero en la parte correspondiente de la presentación. Es decir, la nota de su práctica estará acotada por un 6.
    Los alumnos que entreguen una práctica que dé un error no controlado o no documentado (en un fichero llamado “README.md”), estará automáticamente suspensa con un cero. Entre estos errores se consideran los siguientes:
    Excepciones que no se atrapan ni se documentan.
    Errores de codificación.
    Errores de importación del código como librería.
    Las entregas fuera de la fecha final de la práctica se consideran suspensas y su valoración será un cero.
    Las entregas que empleen librerías no vistas en clase, han de documentar las librerías que hay que instalar y el comando con el que se instalan en un fichero aparte llamado “README.md”. Si aparecen librerías no vistas en clase sin ser documentadas en este fichero, el valor de la práctica será de cero.