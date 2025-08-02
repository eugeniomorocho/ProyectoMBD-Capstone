# **Air Passengers Time Series API with FastAPI**

Este repositorio contiene una implementación de una API REST utilizando **FastAPI** para servir modelos o análisis relacionados con la serie temporal del dataset `air_passengers.csv`. El notebook `FastAPI setup.ipynb` explica paso a paso cómo levantar la API y procesar los datos.

## 🗃️ Contenido

- `FastAPI setup.ipynb`: Notebook con el código para configurar y ejecutar una API básica con FastAPI.
- `air_passengers.csv`: Dataset con registros mensuales de pasajeros aéreos entre 1949 y 1960.

## 🚀 Requerimientos

Es recomendable crear un entorno virtual antes de la instalación:

```bash
python -m venv venv
source venv/bin/activate  # En Windows usa: venv\Scripts\activate
```

Instala las dependencias necesarias:

```bash
pip install -r requirements.txt
```

Si no tienes un archivo `requirements.txt`, instala manualmente:

```bash
pip install fastapi uvicorn pandas jupyter
```

## ▶️ Cómo ejecutar el proyecto

### 1. Explora el notebook

Puedes abrir el notebook en Jupyter para estudiar el código:

```bash
jupyter notebook FastAPI\ setup.ipynb
```

Esto te permitirá visualizar y ejecutar el código paso a paso.

### 2. Crea el archivo principal de FastAPI (opcional si no usas solo el notebook)

Si decides extraer el código para ejecutar directamente desde un script `.py`, crea un archivo llamado `main.py` con contenido similar al que se encuentra en el notebook:

```python
from fastapi import FastAPI
import pandas as pd

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "API funcionando correctamente"}

@app.get("/data")
def get_data():
    df = pd.read_csv("air_passengers.csv")
    return df.to_dict()
```

### 3. Ejecuta la API localmente

Usa `uvicorn` para iniciar el servidor:

```bash
uvicorn main:app --reload
```

La API estará disponible en:

```
http://127.0.0.1:8000
```

Puedes probar los endpoints directamente en la documentación interactiva que genera FastAPI:

```
http://127.0.0.1:8000/docs
```

## 📊 Resultado esperado

Al consumir el endpoint `/data`, obtendrás una respuesta JSON con los datos del archivo `air_passengers.csv`.

## 📌 Notas adicionales

- Asegúrate de que `air_passengers.csv` esté en el mismo directorio desde el que ejecutas la API.
- Para análisis más complejos de la serie temporal (ej. predicciones), puedes integrar librerías como `statsmodels`, `prophet` o `scikit-learn`.