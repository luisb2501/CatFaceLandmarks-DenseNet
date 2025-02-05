# Detección de Puntos de Referencia con DenseNet121

Este repositorio contiene código para detectar puntos de referencia faciales utilizando DenseNet121. El proyecto está dividido en varios módulos, cada uno responsable de diferentes aspectos del proceso de detección.

## Tabla de Contenidos
- [Uso](#uso)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Detalles del Modelo](#detalles-del-modelo)
- [Funciones Auxiliares](#funciones-auxiliares)
- [Evaluación](#evaluación)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

## Uso

Para ejecutar la detección de puntos de referencia, necesitas tener los modelos preentrenados y el conjunto de datos. Sigue estos pasos:

1. **Prepara el conjunto de datos**: Coloca tus imágenes en un directorio y asegúrate de tener archivos JSON correspondientes con las anotaciones de los puntos de referencia.

2. **Carga los Modelos Preentrenados**: Utiliza los scripts proporcionados para cargar los modelos preentrenados. Asegúrate de que las rutas a los modelos sean correctas. Puedes descargar los modelos desde [este enlace](https://drive.google.com/drive/folders/1eQW7rFMoDueqHhy4II3tgzoYmRCm481e?usp=sharing).

3. **Ejecuta los Jupyter Notebooks**: Abre los Jupyter Notebooks en el directorio `EnsamblajeModelos` para entrenar y evaluar los modelos.

4. **Predicción y Visualización**: Utiliza las funciones de predicción y visualización para obtener y mostrar los puntos de referencia en las imágenes.

## Estructura del Proyecto

```
DenseNet121-Landmark-Detection/
├── EnsamblajeModelos/
│   ├── LandmarkDetectorV2.ipynb
│   ├── LandmarkDetectorV3.ipynb
│   ├── LandmarkDetectorV4.ipynb
│   ├── Ensamblaje_Modelo_1.pth
│   ├── Ensamblaje_Modelo_2.pth
│   ├── Ensamblaje_Modelo_3.pth
├── FaceDetector/
│   ├── FaceDetector.ipynb
│   ├── FaceDetector_V3.pth
├── Landmarks_Optimizadores/
│   ├── ADAM/
│   │   ├── ADAM.ipynb
│   │   ├── EarLeftLandmarks_V2.pth
│   │   ├── EarRightLandmarks_V2.pth
│   │   ├── NoseAreaLandmarks_V2.pth
│   │   ├── EyeLeftLandmarks_V2.pth
│   │   ├── EyeRightLandmarks_V2.pth
│   ├── ADAMax/
│   │   ├── ADAMax.ipynb
│   │   ├── EarLeftLandmarks_V3.pth
│   │   ├── EarRightLandmarks_V3.pth
│   │   ├── NoseAreaLandmarks_V3.pth
│   │   ├── EyeLeftLandmarks_V3.pth
│   │   ├── EyeRightLandmarks_V3.pth
│   ├── ADAMW/
│   │   ├── ADAMW.ipynb
│   │   ├── EarLeftLandmarks_V4.pth
│   │   ├── EarRightLandmarks_V4.pth
│   │   ├── NoseAreaLandmarks_V4.pth
│   │   ├── EyeLeftLandmarks_V4.pth
│   │   ├── EyeRightLandmarks_V4.pth
├── RegionDetector/
│   ├── RegionDetector.ipynb
│   ├── RegionDetector_V2.pth
└── README.md

```

## Detalles del Modelo

### DenseNet121BoundingBox
Este modelo predice el cuadro delimitador de la cara en la imagen.

### DenseNet121Regions
Este modelo predice las regiones de interés dentro de la cara, como los ojos, orejas y nariz.

### DenseNet121EarLeft y DenseNet121EarRight
Estos modelos predicen los puntos de referencia para las orejas izquierda y derecha respectivamente.

### DenseNet121Nose
Este modelo predice los puntos de referencia para la nariz.

### DenseNet121EyeLeft y DenseNet121EyeRight
Estos modelos predicen los puntos de referencia para los ojos izquierdo y derecho respectivamente.

### AssembledModel
Este modelo combina todos los modelos anteriores para proporcionar un sistema integral de detección de puntos de referencia.

## Descripción de los Archivos

### EnsamblajeModelos/LandmarkDetectorV2.ipynb
Este notebook contiene la implementación de los modelos individuales para la detección de puntos de referencia. Se definen las clases de los modelos para el cuadro delimitador, las regiones, las orejas, la nariz y los ojos utilizando DenseNet121. Además, se carga el modelo ensamblado y se definen funciones auxiliares para ajustar cuadros delimitadores, recortar y redimensionar imágenes, dibujar puntos, reescalar puntos y revertir transformaciones.

### EnsamblajeModelos/LandmarkDetectorV3.ipynb
Este notebook es una versión mejorada del anterior, con optimizaciones en la definición de los modelos y las funciones auxiliares. Se incluyen ejemplos de uso y visualización de los puntos de referencia en las imágenes. También se implementa la función `predict_and_visualize` para predecir y visualizar cada paso del proceso de detección.

### EnsamblajeModelos/LandmarkDetectorV4.ipynb
Este notebook contiene mejoras adicionales en la precisión y eficiencia de los modelos. Se ajustan los hiperparámetros y se optimizan las funciones auxiliares para un mejor rendimiento. Además, se incluyen más ejemplos de uso y visualización.

### FaceDetector/FaceDetector.ipynb
Este notebook se centra en la detección de caras utilizando DenseNet121. Se define el modelo para predecir el cuadro delimitador de la cara en la imagen y se incluyen ejemplos de uso y visualización de los cuadros delimitadores.

### Landmarks_Optimizadores/ADAM/ADAM.ipynb
Este notebook utiliza el optimizador ADAM para entrenar los modelos de puntos de referencia. Se definen las configuraciones del optimizador y se entrenan los modelos utilizando este método. También se incluyen ejemplos de evaluación y visualización de los resultados.

### Landmarks_Optimizadores/ADAMW/ADAMW.ipynb
Este notebook es similar al anterior, pero utiliza el optimizador ADAMW. Se definen las configuraciones del optimizador y se entrenan los modelos utilizando este método. También se incluyen ejemplos de evaluación y visualización de los resultados.

### Landmarks_Optimizadores/ADAMax/ADAMax.ipynb
Este notebook utiliza el optimizador ADAMax para entrenar los modelos de puntos de referencia. Se definen las configuraciones del optimizador y se entrenan los modelos utilizando este método. También se incluyen ejemplos de evaluación y visualización de los resultados.

### RegionDetector/RegionDetector.ipynb
Este notebook se centra en la detección de regiones de interés dentro de la cara, como los ojos, orejas y nariz. Se define el modelo para predecir estas regiones utilizando DenseNet121 y se incluyen ejemplos de uso y visualización de las regiones detectadas.

## Funciones Auxiliares

Las funciones auxiliares están definidas para asistir con varias tareas como ajustar cuadros delimitadores, recortar y redimensionar imágenes, dibujar puntos, reescalar puntos y revertir transformaciones.

## Evaluación

Para evaluar el modelo, utiliza las funciones `evaluate_model` y `calculate_mse` proporcionadas en el notebook `LandmarkDetectorV2.ipynb`. Estas funciones calculan el Error Medio Normalizado (NME) y el Error Cuadrático Medio (MSE) en el conjunto de datos de validación.

## Contribuciones

¡Las contribuciones son bienvenidas! Por favor, abre un issue o envía un pull request para cualquier mejora o corrección de errores.

## Licencia

Este proyecto está licenciado bajo la Licencia Creative Commons Attribution 4.0 International. Consulta el archivo [LICENSE](LICENSE) para más detalles.
