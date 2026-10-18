# Proyecto Final PCD
## Introduccion
En este trabajo buscamos hacer la continucacion o segunda parte de un trabajo anterior, en el cual se busco predecir la edad de cangrejos con un modelo lineal, a partir de informacion morfologica. Se busca proponer una solucion alternativa para lograr predecir con mayor eficiencia la edad de los cangrejos.

Se llevaran a cabo tecnicas de aprendizaje automatico implementando algoritmos de  *Random Forest* como metodologia.


## Motivacion
Como motivacion, decidimos tomar un trabajo anterior realizado en R, al cual habiamos llegado a una conclusión abierta con un problema en ella.  Dicho incoveniente fue que el modelo final al que llegamos, no lograba predecir correctamente la edad de los cangrejos que tuvieron mas de aproximadamente 10 años de edad, subestimandola. Es decir, a partir de la edad en la que empieza a estimar incorrectamente no logra captar diferencias en atributos fisicos dandole a dos cangrejos adultos (uno mayor que el otro) misma edad.   
Por lo que estaremos buscando en este caso buscar aplicar metodologías relacionadas al curso para intentar solucionar el problema, viendo a que conclusiones llegamos en este caso.

## Contexto 
Los datos utilizados contienen informacion morfologica acerca de cangrejos.     Fueron obtenidos de *Kaggle* (https://www.kaggle.com/datasets/sidhus/crab-age-prediction). El por qué de de la recoleccion de estos datos fue el siguiente:

El mercado de los cangrejos es un sector grande e importante dentro de la industria pesquera, y por lo tanto
conocer y poder estimar una característica tan importante de los mismos, como lo es su edad es considerado
un pilar fundamental para garantizar una gestión sostenible del recurso.
Determinar la edad de los cangrejos es muy importante por dos motivos principales:

Pescadería: Cuando se realiza la pesca de este animal, es de gran importancia saber la edad de los
individuos pescados ya que su precio de venta puede variar según la edad de los cangrejos debido a la
calidad de su carne. Asimismo, no interesa pescar cangrejos en étapas prematuras en demasía ya que
eso puede resultar en una disminución en la poblacion del animal.

Criaderos: En la actualidad existen criaderos de cangrejos, a los cuales les interesa saber cuando
realizar la cosecha para maximizar ganancias sin poner en riesgo la sostenibilidad del negocio.


## Descripción de los datos

<img width="523" height="319" alt="image" src="https://github.com/user-attachments/assets/3461679c-b948-475c-9781-58c792f699fe" />

Este es el primer análisis descriptivo de los datos. El segundo es luego de haber filtrado los datos por observaciones con valor indeterminado en el sexo. 
En el trabajo anterior, vimos que los cangrejos con sexo indeterminado son cangrejo, a los que debido a su corta edad no se les puede asignar un sexo. Para este nuevo analisis, ya no nos interesa modelar bien los cangrejos jovenes, asi que estos datos son removidos.

<img width="523" height="315" alt="image" src="https://github.com/user-attachments/assets/02694b14-f09a-4772-84f0-7d4809f1369a" />

Continuando con el análisis descriptivo, gráficos cada variable contra la edad.
<img width="941" height="437" alt="image" src="https://github.com/user-attachments/assets/4795bea2-4ea2-40ee-9463-70637b762e8d" />
<img width="338" height="217" alt="image" src="https://github.com/user-attachments/assets/38bfe7f9-f2f4-4688-90a8-569e71350da1" />

Para obtener un analisis descriptivo completo de las variables, observamos la correlacion entre las variables.

<img width="602" height="497" alt="image" src="https://github.com/user-attachments/assets/40bc0fd6-ba12-4bd8-8e02-8d6f22a9d13b" />

Como se puedo observar en los graficos de cada variable contra la edad, claramente hay dos datos atipicos de Height, probablemente provocados por un error en la medición, para no alterar los resultados por solo dos datos, se decidió removerlos. Tambien es apreciable la alta correlación entre muchas de las variables.

<img width="460" height="315" alt="image" src="https://github.com/user-attachments/assets/1cb18dd9-5b22-405d-b7e1-baaa549359e4" /> Height vs Age (sin outliers)

## Aplicamos *Random Forest*
Lo que buscamos es tomar solamente los datos de los cangrejos que dejaron de crecer fisicamente de manera abrupta. Para ello implementamos Random Forest buscando determinar que variable mejor explica el cambio en la edad, para asi, junto con su grafico determinar un umbral arbitrario, que permita discriminar del total de los datos unicamente aquellos que buscamos.
Luego de aplicar el algoritmo, grafico la importancia de las variables llegando a los siguientes resultados:
<img width="1041" height="452" alt="image" src="https://github.com/user-attachments/assets/5c2a1fdd-dc14-4f8c-84ff-b55b3dc8dc4c" />
Este gráfico muestra la importancia relativa de las variables, donde las variables de peso resultan ser las más determinantes para las predicciones: Shell_Weight lidera la capacidad predictiva con aproximadamente un 37% de relevancia, seguida por Shucked_Weight (peso desviscerado/carne) con un 25%, mientras que el peso total y el peso de las vísceras tienen un impacto moderado (~ 10%), las dimensiones físicas como diámetro, altura y longitud aportan de manera menor (5%-7%), y el sexo (Sex_M) resulta prácticamente irrelevante (<1%).   

Bajo los resultados obtenidos, continuamos mirando el grafico Shell_Weight vs Age para determinar donde es que se da el cambio abrupto en los datos. Tomando la decision arbitraria que se da a partir de los cangrejos con un peso de 5 onzas (140g) o mas.

<img width="696" height="438" alt="image" src="https://github.com/user-attachments/assets/47f1aace-05e0-4e56-82d9-2fc766ea5955" />

Tomando ese umbral particionamos los datos, y ajustamos un modelo para los datos seleccionados.
<img width="280" height="36" alt="image" src="https://github.com/user-attachments/assets/10c2cb73-4031-48b1-92e8-20dc70d1b6e9" />

## Selección de variables
A partir de nuestros nuevos datos, procedemos a una nueva selección de variables para nuestro modelo lineal. AL seguir teniendo el problema de alta correlación entre variables, decidimos usar Lasso para seleccionar las variables porque el algoritmo fuerza los coeficientes de las variables redundantes o altamente colineales exactamente a cero, evitando así la peligrosa inflación de la varianza y la inestabilidad de los coeficientes. Usamos Lasso para distintos alfa.
<img width="260" height="299" alt="image" src="https://github.com/user-attachments/assets/c8a3589a-6479-4754-8656-a7c5daeb29eb" />
## Selección de modelos y validación del rendimiento predictivo
Para la selección y comparación final de los modelos regularizados con distintos valores del hiperparámetro de mezcla ($\alpha$), se descartó el uso del coeficiente de determinación ($R^2$) calculado sobre el conjunto de entrenamiento. Dado que los modelos penalizados ajustan su complejidad en función de los datos observados, el $R^2$ de entrenamiento exhibe un sesgo optimista y favorece sistemáticamente a aquellos modelos con menor penalización o mayor número de variables retenidas, lo que puede inducir a un problema de sobreajuste.En su lugar, se implementó una estrategia de validación cruzada de K particiones (K-fold cross-validation). Este enfoque evalúa el rendimiento predictivo fuera de muestra de manera rigurosa, simulando cómo se comportaría el modelo ante nuevas observaciones independientes. La selección del modelo definitivo se basó en la maximización del $R^2$ de validación cruzada (equivalente a la minimización del error cuadrático medio de predicción), garantizando así que el modelo elegido posea una óptima capacidad de generalización y refleje una estructura explicativa robusta en lugar de una mera memorización del ruido muestral.

