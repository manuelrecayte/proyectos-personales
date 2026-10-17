# Proyecto Final PCD
## Introduccion
En este trabajo buscamos hacer la continucacion o segunda parte de un trabajo anterior, en el cual se busco predecir la edad de cangrejos con un modelo lineal, a partir de informacion morfologica. Se busca proponer una solucion alternativa para lograr predecir con mayor eficiencia la edad de los cangrejos.

Se llevaran a cabo tecnicas de aprendizaje automatico implementando algoritmos de  *Random Forest* como metodologia.


## Motivacion
Como motivacion, decidimos tomar un trabajo anterior realizado en R, al cual habiamos llegado a una conclusión abierta con un problema en ella.  Dicho incoveniente fue que el modelo final al que llegamos, no lograba predecir correctamente la edad de los cangrejos que tuvieron mas de aproximadamente 10 años de edad, subestimandola. Es decir, a partir de la edad en la que empieza a estimar incorrectamente no logra captar diferencias en atributos fisicos dandole a dos cangrejos adultos (uno mayor que el otro) misma edad.   
Dentro de las recomendaciones a posibles soluciones de dicho problema, fue que seleccionamos una para llevar adelante en este proyecto.

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

