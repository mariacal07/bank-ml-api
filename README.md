# Bank ML API

Proyecto de aprendizaje para entrenar un modelo de machine learning con
`scikit-learn` y exponerlo mediante una API. El caso de uso consiste en predecir
si un cliente contratara un producto o servicio bancario a partir de datos de una
campana de marketing.

El proyecto tambien sirve para practicar un flujo de trabajo con Git y GitHub
basado en ramas, commits y pull requests.

## Objetivos

- Explorar un dataset real de marketing bancario.
- Preparar datos categoricos y numericos con pipelines de `scikit-learn`.
- Entrenar y comparar varios modelos de clasificacion.
- Seleccionar un modelo final y guardarlo para reutilizarlo.
- Crear una API que cargue el modelo entrenado y devuelva predicciones.
- Practicar un flujo de trabajo con ramas de tipo `feature`.

## Dataset

El dataset utilizado es Bank Marketing, disponible en Kaggle:

https://www.kaggle.com/datasets/henriqueyamahata/bank-marketing

Los datos originales no se versionan en Git. Deben colocarse localmente en:

```text
data/raw/bank.csv
```

### Descargar con kagglehub

Instala `kagglehub` si no lo tienes:

```bash
pip install kagglehub
```

Descarga el dataset:

```python
import kagglehub

path = kagglehub.dataset_download("henriqueyamahata/bank-marketing")

print("Path to dataset files:", path)
```

Despues, copia el archivo `bank.csv` descargado a:

```text
data/raw/bank.csv
```

## Estructura del proyecto

```text
bank-ml-api/
  app/              # Codigo de la API
  data/
    raw/            # Dataset original, no versionado
  notebooks/        # Exploracion, EDA y experimentos
  scripts/          # Scripts reproducibles, como entrenamiento
  requirements.txt      # Dependencias base del proyecto
  requirements-dev.txt  # Dependencias para desarrollo y notebooks
```

## Uso de notebooks

Los notebooks se usan como laboratorio de trabajo:

- cargar y entender el dataset;
- hacer EDA;
- probar transformaciones;
- comparar modelos;
- analizar metricas;
- elegir una estrategia inicial.

Cuando una parte del notebook deja de ser exploratoria y pasa a formar parte del
flujo del proyecto, se mueve a archivos `.py`. Por ejemplo, el entrenamiento final
del modelo deberia vivir en un script reproducible, y la prediccion deberia vivir
en la API.

## Instalacion

Crea y activa un entorno virtual:

```bash
python -m venv venv
```

En Windows PowerShell:

```bash
venv\Scripts\Activate.ps1
```

Instala las dependencias base del proyecto:

```bash
pip install -r requirements.txt
```

Si vas a trabajar con notebooks, visualizaciones o descarga desde Kaggle, instala
tambien las dependencias de desarrollo:

```bash
pip install -r requirements-dev.txt
```

## Flujo de trabajo con Git

La rama `main` se reserva para versiones estables. Para cada cambio se crea una
rama nueva:

```bash
git switch -c feature/nombre-tarea
```

Ejemplos:

```text
feature/add-readme
feature/training-pipeline
feature/prediction-api
docs/update-dataset-instructions
fix/model-selection-loop
```

El flujo recomendado es:

```text
feature/... -> pull request -> main
```

Si el proyecto incorpora una rama de integracion, el flujo puede ser:

```text
feature/... -> pull request -> development -> pull request -> main
```

## Estado actual

El proyecto esta en una fase inicial. Actualmente contiene:

- dataset local ignorado por Git;
- notebook de exploracion;
- dependencias iniciales;
- estructura base de carpetas.

Los siguientes pasos previstos son convertir los experimentos del notebook en un
script de entrenamiento reproducible y despues crear una API para servir
predicciones.
