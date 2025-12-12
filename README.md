# Proyecto_EDA


Conclusiones del análisis bivariante (medianas)

El análisis comparativo de las medianas de las variables numéricas entre los grupos y = "no" y y = "si" permite identificar qué factores muestran diferencias relevantes entre los clientes que contratan y los que no. En general, los resultados indican que solo algunas variables presentan variaciones sustanciales entre ambas clases, mientras que la mayoría mantiene valores centrales muy similares.

La variable con mayor capacidad discriminativa es duration, cuya mediana aumenta de 163 a 453 segundos en los casos de contratación. Esta diferencia notable confirma que las llamadas más largas se relacionan con una mayor probabilidad de éxito. Por el contrario, variables como age, campaign, income, kidhome, teenhome y numwebvisitsmonth muestran medianas idénticas o prácticamente iguales entre grupos, lo que sugiere una influencia muy limitada en el resultado de la campaña.

Las variables macroeconómicas presentan un patrón común: entre los clientes que contratan se observa una tendencia hacia valores más bajos en indicadores como emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m y nr.employed. Aunque la magnitud de las diferencias varía, el desplazamiento es consistente y apunta a que las contrataciones se concentran en momentos con un contexto económico menos favorable, especialmente en relación con los tipos de interés (euribor3m) y la variación del empleo (emp.var.rate).

En conjunto, las medianas indican que la duración de la llamada y ciertos factores macroeconómicos aportan señales diferenciales entre clases, mientras que el resto de variables numéricas no muestra variaciones relevantes. Estas observaciones ayudan a identificar cuáles pueden ser más útiles en etapas posteriores de modelización y selección de características.