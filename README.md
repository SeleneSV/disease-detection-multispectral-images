# Disease Detection with Multispectral Images

Detección de Enfermedades en Plantas de Maíz y Frijol Usando Inteligencia Artificial e Imágenes Multiespectrales

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20.0-orange.svg)](https://www.tensorflow.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.7.2-green.svg)](https://scikit-learn.org/)

## 📋 Descripción

Este proyecto de investigación implementa técnicas de inteligencia artificial y aprendizaje automático para la detección de deficiencias nutricionales (específicamente de fósforo) en plantas de maíz y frijol común utilizando imágenes multiespectrales.

El sistema analiza imágenes capturadas en 10 bandas espectrales diferentes (444, 475, 531, 560, 650, 668, 705, 717, 740, 848 nm) para clasificar plantas en diferentes niveles de deficiencia de fósforo.

## 🎯 Objetivos

- Desarrollar modelos de clasificación para identificar niveles de deficiencia de fósforo en cultivos
- Comparar el rendimiento de diferentes arquitecturas de aprendizaje automático (ML, MLP, DNN, CNN)
- Extraer características espectrales relevantes para la detección temprana de estrés nutricional
- Proporcionar una herramienta no destructiva para el monitoreo del estado nutricional de los cultivos

## 📁 Estructura del Proyecto

```
disease-detection-multispectral-images/
│
├── data/                           # Datos fuente
│   ├── mat/                        # Archivos MATLAB (.mat)
│   │   ├── frijol/
│   │   └── maiz/
│   └── tiff/                       # Imágenes TIFF
│       ├── frijol/
│       └── maiz/
│
├── datasets/                       # Datasets procesados
│   ├── dataset_frijol.csv
│   ├── dataset_maiz.csv
│   └── new/                        # Versiones actualizadas
│
├── extracted_objects_frijol/       # Objetos segmentados de frijol
│   ├── T1/                         # Tratamiento 1 (control)
│   ├── T2/                         # Tratamiento 2
│   ├── T3/                         # Tratamiento 3
│   └── T4/                         # Tratamiento 4
│
├── extracted_objects_maiz/         # Objetos segmentados de maíz
│   ├── T1/                         # Por banda espectral
│   ├── T2/
│   ├── T3/
│   └── T4/
│
├── models/                         # Modelos entrenados
│   ├── frijol/
│   └── maiz/
│
├── results/                        # Resultados y métricas
│   ├── training_history_frijol.csv
│   ├── training_history_maiz.csv
│   ├── training_history_frijol_cnn.csv
│   ├── training_history_maiz_cnn.csv
│   ├── data/
│   └── predictions/
│
├── build_dataset.ipynb            # Construcción del dataset
├── dataset_images.ipynb           # Procesamiento de imágenes
├── train_ml_frijol.ipynb          # ML clásico - Frijol
├── train_ml_maiz.ipynb            # ML clásico - Maíz
├── dnn_frijol.ipynb               # Redes neuronales profundas - Frijol
├── dnn_maiz.ipynb                 # Redes neuronales profundas - Maíz
├── cnn_frijol.ipynb               # Redes convolucionales - Frijol
├── cnn_maiz.ipynb                 # Redes convolucionales - Maíz
├── requirements.txt               # Dependencias del proyecto
└── README.md                      # Este archivo
```

## 🚀 Instalación

### Prerrequisitos

- Python 3.8 o superior
- pip (gestor de paquetes de Python)
- Jupyter Notebook o JupyterLab

### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/SeleneSV/disease-detection-multispectral-images.git
cd disease-detection-multispectral-images
```

2. **Crear un entorno virtual (recomendado)**
```bash
python -m venv .venv
```

3. **Activar el entorno virtual**
   - Windows:
   ```bash
   .venv\Scripts\activate
   ```
   - Linux/Mac:
   ```bash
   source .venv/bin/activate
   ```

4. **Instalar dependencias**
```bash
pip install -r requirements.txt
```

## 💻 Uso

### 1. Procesamiento de Datos

**Construcción del dataset:**
```bash
jupyter notebook build_dataset.ipynb
```

Este notebook extrae características de las imágenes multiespectrales y genera los archivos CSV con los datos procesados.

**Procesamiento de imágenes:**
```bash
jupyter notebook dataset_images.ipynb
```

### 2. Entrenamiento de Modelos

#### Modelos de Machine Learning Clásico

Para entrenar modelos con algoritmos tradicionales (Random Forest, XGBoost, etc.):

```bash
# Para frijol
jupyter notebook train_ml_frijol.ipynb

# Para maíz
jupyter notebook train_ml_maiz.ipynb
```

#### Redes Neuronales Profundas (DNN)

```bash
# Para frijol
jupyter notebook dnn_frijol.ipynb

# Para maíz
jupyter notebook dnn_maiz.ipynb
```

#### Redes Neuronales Convolucionales (CNN)

```bash
# Para frijol
jupyter notebook cnn_frijol.ipynb

# Para maíz
jupyter notebook cnn_maiz.ipynb
```

### 3. Análisis de Resultados

Los resultados del entrenamiento se guardan automáticamente en la carpeta `results/`:
- Métricas de evaluación
- Predicciones del modelo
- Matrices de confusión y gráficos de rendimiento

## 🔬 Metodología

### Tratamientos

El proyecto evalúa 4 niveles de deficiencia de fósforo y nitrógeno:

- **T1**: Control (nivel óptimo)
- **T2**: Deficiencia leve
- **T3**: Deficiencia moderada
- **T4**: Deficiencia severa

### Bandas Espectrales

Las imágenes se capturan en 10 bandas espectrales (nm):
- **444, 475**: Azul
- **531, 560**: Verde
- **650, 668**: Rojo
- **705, 717, 740**: Red-edge
- **842**: Infrarrojo cercano (NIR)

### Modelos Implementados

1. **Machine Learning Clásico:**
   - Random Forest
   - XGBoost
   - K-Nearest Neighbors (KNN)
   - Multi-Layer Perceptron (MLP)

2. **Deep Neural Networks (DNN)**

3. **Convolutional Neural Networks (CNN)**

## 🛠️ Tecnologías Utilizadas

- **Python**: Lenguaje de programación principal
- **TensorFlow/Keras**: Deep Learning
- **scikit-learn**: Machine Learning tradicional
- **XGBoost**: Gradient Boosting
- **OpenCV**: Procesamiento de imágenes
- **NumPy/Pandas**: Manipulación de datos
- **Matplotlib/Seaborn**: Visualización
- **SciPy**: Cálculos científicos

## 📈 Resultados

Los modelos desarrollados son capaces de:

- Clasificar con alta precisión los diferentes niveles de deficiencia de fósforo y nitrógeno
- Identificar patrones espectrales específicos de cada tratamiento
- Proporcionar predicciones tempranas antes de que los síntomas sean visibles al ojo humano

*Para resultados detallados, consultar los notebooks individuales y la carpeta `results/`.*

## 🤝 Contribuciones

Este es un proyecto de investigación académica. Si deseas contribuir o usar este código para tu investigación:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Este proyecto es parte de una tesis de maestría en la Universidad Nacional de Colombia (UNAL).

## 👥 Autores

- **Selene Solano** - *Investigador Principal* - [SeleneSV](https://github.com/SeleneSV)

## 🙏 Agradecimientos

- Universidad Nacional de Colombia
- Facultad de Minas
- Programa de Maestría en Ingeniería Análitica

## 📧 Contacto

Para preguntas o colaboraciones, por favor abre un issue en este repositorio.

---

**Nota**: Este proyecto utiliza imágenes multiespectrales capturadas en condiciones controladas. Los modelos están entrenados específicamente para los cultivos y condiciones descritas.
