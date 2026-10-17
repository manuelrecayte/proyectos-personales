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
