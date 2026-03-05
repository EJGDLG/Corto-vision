# Corto-vision
## Reporte — Transfer Learning (VGG16) para Clasificación de Enfermedades en Hojas de Mango

### Accuracy Global
El modelo alcanzó una **precisión global de 0.9650 (96.5%)** en el conjunto de validación.  
Este resultado indica que el modelo logra clasificar correctamente la gran mayoría de las imágenes de hojas de mango en sus respectivas categorías de enfermedad o estado saludable.

### Análisis de la Matriz de Confusión
La matriz de confusión muestra que la mayoría de las predicciones correctas se concentran en la **diagonal principal**, lo cual es un comportamiento esperado en un modelo bien entrenado. Esto indica que el modelo identifica correctamente cada clase en la mayoría de los casos.

Al analizar las clases individualmente, se observa que:

- Las clases como **Bacterial Canker, Healthy y Gall Midge** presentan tasas de clasificación muy altas, con muy pocas confusiones con otras categorías.
- Algunas pequeñas confusiones ocurren entre clases visualmente similares, por ejemplo entre **Anthracnose y Powdery Mildew**, lo cual es comprensible debido a que ciertas enfermedades presentan patrones de textura o color similares en las hojas.
- En general, el número de errores es bajo, lo que sugiere que el modelo logró aprender características discriminativas relevantes para diferenciar las enfermedades.

### Interpretación del Entrenamiento
Durante el entrenamiento, el modelo utilizó **Transfer Learning con VGG16 preentrenada en ImageNet**, lo que permite aprovechar filtros ya entrenados para detectar patrones básicos como bordes, texturas y formas. Al congelar las capas convolucionales y entrenar únicamente el clasificador final, el modelo pudo adaptarse eficientemente al nuevo problema de clasificación de enfermedades en hojas.

Además, el uso de **Data Augmentation (rotaciones, recortes y flips)** ayudó a mejorar la capacidad de generalización del modelo frente a variaciones de orientación o posición de las hojas.

### Evaluación de Overfitting
La diferencia entre la precisión de entrenamiento y la de validación es relativamente pequeña, lo cual sugiere que **no existe un sobreajuste significativo**. El modelo mantiene un desempeño consistente al evaluar datos no vistos.

Sin embargo, en las últimas épocas se observa cierta variabilidad en la función de pérdida, lo cual podría indicar que el modelo comienza a sobreajustarse ligeramente si se entrena durante demasiadas iteraciones.

### Conclusión
1. El modelo basado en **Transfer Learning con VGG16** logra aprender representaciones relevantes de las hojas de mango y clasificar correctamente las enfermedades con alta precisión.  
2. La matriz de confusión confirma que el modelo distingue adecuadamente entre las distintas clases, con pocos errores entre enfermedades visualmente similares.  
3. Para mejorar aún más la robustez del modelo se podrían aplicar técnicas adicionales como **Dropout, mayor Data Augmentation o ajuste del learning rate**, lo que ayudaría a reducir posibles efectos de sobreajuste y mejorar la generalización.
