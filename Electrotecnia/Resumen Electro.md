# Resumen Electro

[TOC]

## Metodo De Las Mallas

Consiste en aplicar ley de kirchoff de los voltajes a las mallas de manera que la ley de Kirchoff de las corrientes quede aplicada implícitamente.

Este metodo nos permite obtener el valor de las corrientes ficticias de malla, se consideran solo las mallas independientes, esto significa que sean un camino cerrado sin otro camino cerrado en su interior.

Para este metodo se aplicaran los siguientes pasos:
1. Determinar el numero de mallas independientes, y darles a las corrientes ficticias un sentido (todas iguales).
2. Aplicar ley de kirchoff de las tensiones a cada malla
3. Substituir por las características tensión corriente de los elementos
4. Resolver el sistema de ecuaciones.

Ejemplo:


![](ZImages/Pasted%20image%2020220628123523.png)

Paso 1: Determinamos que hay 2 mallas y le asignamos un sentido a sus corrientes ficticias.

Paso 2: Aplicamos ley de Kirchhoff de las tensiones a las mallas.
$$
\begin{align}
u_{s1}-u_{a}-u_{c}&=0\\
\ -u_{s2}-u_{b}+u_{c}&=0
\end{align}
$$

Paso 3: substituimos por las características tension corriente de los elementos:

$$
\begin{align}
u_{a}&=i_{1}Z_{1}\\
u_{b}&= i_{2}Z_2\\
u_{c}&= (i_{1}-i_{2})Z_{3}
\end{align}
$$
Remplazamos en la ecuación:

$$
\begin{align}
u_{s1}&=u_{a}+u_{c}= i_{1}Z_{1}+(i_{1}-i_{2})Z_{3}\\
-u_{s2}&= u_{b}-u_{c} = i_{2}Z_{2} -(i_{1}-i_{2})Z_{3}
\end{align}
$$
despejando nos queda el sistema de ecuaciones:
$$
\begin{align}
u_{s1}&= i_{1}(Z_{1}+Z_{3})-i_{2}Z_{3}\\
- u_{s2}&= -i_{1}Z_{3}+(Z_{2}+Z_{3})i_{2}
\end{align}
$$

### Fuentes De Corrientes Ideales En Una Sola Malla

En este caso esto nos disminuye el numero de ecuaciones ya que la corriente en la malla va a estar dada por la fuente:
$$
i_{2}=-is
$$
![](https://i.imgur.com/ttMdECg.png)


### Fuentes De Corriente Ideales Entre Dos Mallas

En este caso la fuente define la diferencia de corrientes entre las dos mallas, formando lo que se llama una supermalla, y se la trata como si fuese una sola.

![](https://i.imgur.com/OYfVDXS.png)

nos da la relacion $i_{s}=i_{3}-i_{2}$

### Fuentes De Corriente Con Resistencia Interna

Se pueden transformar fuentes de corriente con resistencia en fuentes de tension con resistencia interna para reducir el numero de mallas.

![](https://i.imgur.com/0gsVGff.png)


### Fuentes Dependientes De Tensión Y Corriente

Las fuentes dependientes se trabajan igual que las independientes con la salvedad que aparece una ecuación mas que es la de control de la fuente

## Método De Los Nodos

El método de los nodos determina la tension en los nodos independientes ($N-1$), aplicando a estos el primer lema de Kirchhoff.

Siempre que sea posible debemos substituir las fuentes de voltaje por fuentes de corriente.

Para realizar este metodo seguimos los siguientes pasos:
1. Se define el numero total de nodos $N$ y se toma uno como referencia ($v=0$ en ese nodo, generalmente se elige el con mas ramas conectadas), luego se asigna sentido a las corrientes.
2. Se aplica la ley de Kirchhoff de las corrientes a los $N-1$ nodos.
3. Se substituyen por las caracteristicas $V-I$ de cada componente usando la ley de ohm.
4.  Se resuelve el sistema de ecuaciones:

### Ejemplo Con Fuentes Independientes De Corriente:

![](https://i.imgur.com/lFCidvS.png)

Paso 1: se elije el nodo 3 como nodo de referencia $v_{3}=0$ y se le da sentido a las corrientes, podemos ver que $N=3$ entonces $N-1 = 2$.

$$
\begin{align*}
u_{1}&= v_{1}-0 = u_{1}\\
u_{2}&= v_{2}-0 = u_{2}\\
u_{12} &= v_{1}-v_{2}=u_{1}-u_{2}
\end{align*}
$$

Paso 2: se aplica la ley de kirchoff de las corrientes.
$$
\begin{align*}
i_{s1}- i_{12}-i_{13}=0\\
i_{12}- i_{s2}-i_{23}=0
\end{align*}
$$
por lo que reordenando nos queda:
$$
\begin{align*}
i_{s1}&= i_{12}+ i_{13}\\
i_{s2} &= i_{23}-i_{12} 
\end{align*}
$$

Paso 3: substituimos por las caracteristicas $V-I$ que por la ley de ohm serian:
$$
\begin{align*}
i_{12}&=u_{12}Y_{2}= (u_{1}-u_{2})Y_{2}\\
i_{13} &= u_{1}Y_{1}\\
i_{23}&= u_{2}Y_{3}
\end{align*}
$$
substituyendo:
$$
\begin{align*}
i_{s1}&= (u_{1}-u_{2})Y_{2}+u_{1}Y_{1}=u_{1}(Y_{1}+Y_{2})-u_{2}Y_{2}\\
i_{s2} &= u_{2}Y_{3} - (u_{1}-u_{2})Y_{2}=-u_{1}Y_{2}+ u_{2}(Y_{2}+Y_{3})
\end{align*}
$$


finalmente el ultimo paso es resolver el sistema de ecuaciones para encontrar $u_{1}$ y $u_{2}$.

### Fuente De Tension Ideal Entre Un Nodo Y El De Referencia

si tenemos una fuente de tension ideal entre un nodo y el de referencia esto nos va a dar directamente la tension en el nodo, por lo que esto reduce el numero de ecuaciones.

### Fuente De Tension Ideal Entre Dos Puntos No De Referencia

La tension entre ambos nodos va a estar dada por la fuente de voltaje ($V_{3}-V_{2}=V_{s}$), estos nodos forman lo que se llama un supernodo y se trabaja como si fuera un solo nodo. a su vez esto nos agrega la incógnita de la corriente.

### Fuentes De Tension Con Resistencia Interna

Se pude reducir el numero de nodos realizando transformación de fuentes.

### Fuentes Dependientes

En el caso de fuentes dependientes se trabaja igual con la diferencia que tendremos una ecuación mas en el sistema, siendo esta la ecuación del control de la fuente dependiente.

## Principio De Superposición

Este se aplica a redes lineales, tiene por objeto calcular la respuesta en un elemento del circuito cuando hay múltiples fuentes.

El teorema nos dice: *La respuesta de un circuito lineal, a varias fuentes de excitación actuando simultáneamente es igual a la suma de las respuestas que se obtendiran con cada fuente actuando por separado*.

Una variable cualquiera del circuito se puede calcular por la sumatoria de los efectos producidos por cada fuente independiente cancelando las otras fuentes.
Fuentes de voltaje se cancelan substituyendose por un cortocircuito $v=0$, y fuentes de corriente se cancelan con un circuito abierto $i=0$.

Fuentes dependientes no se cancelan.

Ejemplo: Obtener el voltaje $v_{3}$

![](ZImages/Pasted%20image%2020220628125536.png)

Al actuar solo la fuente de voltaje tendremos:

![](ZImages/Pasted%20image%2020220628125724.png)
$$
v_{3,vs}= \frac{R_{1}}{R_3+R_{1}}v_s
$$
si solo actúa la fuente de corriente tendremos:

![](ZImages/Pasted%20image%2020220628125812.png)
$$
v_{3,is}= \frac{R_{1}R_{3}}{R_{1}+R_3}i_{s}
$$
por lo tanto el voltaje $v_{3}$ sera:
$$
v_{3}=  \frac{R_{1}}{R_3+R_{1}}v_{s}+\frac{R_{1}R_{3}}{R_{1}+R_3}i_{s}
$$

## Teorema De Sustitución

Suponga una red activa, lineal y bilateral, en la que en una rama cualquiera de impedancia $Z$, se tiene una diferencia de potencial $v=Zi$. este teorema señala que se puede sustituir esta rama por un generador de tension ideal de tension $v_{s}$ que sea igual en cada instante a la diferencia de tensión $u=Zi$, o una fuente de corriente que produzca la misma corriente, sin afectar al resto del circuito.

![](ZImages/Pasted%20image%2020220629160724.png)

![](ZImages/Pasted%20image%2020220331105632.png)

En particular si los terminales $A$ y $B$ de la red están abiertos ($Z$ infinito), existe una diferencia de potencial $u_{0}$ entre $A$ y $B$, y no cambia el estado de la red al substituir la tension $u_{0}$ por un generador $u_{s}=u_{0}$ de la misma polaridad.

## Teorema De Reprocidad

Si se tiene una red pasiva (sin generadores) y se aplica en una rama $AB$ un generador $u_{s}$ y se mide la corriente $I$ en otra rama $CD$, el resultado es el mismo si se intercambia la excitacion y la respuesta, es decir, al aplicar un generador $u_{s}$ a la rama $CD$ se producira una corriente $I$ en la rama AB.

![](ZImages/Pasted%20image%2020220331110054.png)

esto se consecuencia natural de la simetria del determinante de impedancias de una red pasiva, lineal, invariante y bilateral.

si en la fugura se señalan las variables de $AB$ con el subindice 1, y las del lado $CB$ con subindice 2, tenemos entonces:
$$
\frac{u_{1}}{i_{2}} = \frac{u_{2}}{i_{1}}
$$
entonces al tener $u_{1}=u_{2}=u_{s}$ tendremos $i_{1}=i_{2}=I$.

## Thevenin

Un circuito lineal compuesto por elementos activos y pasivos que tenga un par de terminales $a$ y $b$ puede ser substituido entre dichos terminales por una fuente de tension con resistencia interna.

![](ZImages/Pasted%20image%2020220331085750.png)

De acuerdo al tipo de fuentes que contenga el circuito tendremos tres casos:

### Con Fuentes Independientes

El voltaje en equivalente de la fuente sera igual al voltaje de circuito abierto entre los terminales: $V_{th }= V_{ca}$.

Y el calculo de $R_{th }$ podrá realizarse de dos maneras:
1. Pasivando las fuentes y calculando la resistencia de Thevenin que se ve desde $a$ y $b$.
2. Cortocircuitando entre $a$ y $b$ y calculando la corriente de cortocircuito, luego calculando $R_{th }= V_{th} /I_{cc}$ .

Ejemplo:

![](ZImages/Pasted%20image%2020220628130908.png)

Primero calculamos la tension de circuito abierto:
![](ZImages/Pasted%20image%2020220628131000.png)
La cual sera:
$$
V_{th} = V_{s} \frac{R_{2}}{R_{1}+R_{2}}
$$
calculando $R_{th}$ pasivando las fuentes vemos que:
![](ZImages/Pasted%20image%2020220628131123.png)
$$
R_{th} = \frac{R_{1}R_{2}}{R_{1}+R_{2}}
$$
Y si calculamos $R_{th}$ utilizando la corriente de cortocircuito vemos que llegamos al mismo resultado:
$$
i_{cc}= \frac{V_{s}}{R_{1}}
$$
entonces:
$$
R_{th} = \frac{{V_{s}\frac{R_{2}}{R_{1}+R_{2}}}}{V_{s}/R_{1}}= \frac{R_{1}R_{2}}{R_1+R_{2}} 
$$

### Con Fuentes Independientes Y Dependientes

En este caso calculamos $V_{th}$ como la tension de circuito abierto y $R_{th}$ como el cociente $V_{th}/i_{cc}$.

### Con Fuentes Dependientes Solamente

Estos circuitos tendrán $V_{Th}=0$ , para el calculo de la $R_{th}$ se coloca entre $a$ y $b$ una fuente de tension o corriente de valor conocido, y se mide la corriente o tension respectivamente que pase por la misma. 
$$
R_{Th} = \frac{v_{ab}}{i_{ab}}
$$
al colocar ya sea una fuente de corriente o de voltaje.

## Teorema De Norton

Similar a Thevenin pero se remplaza el circuito por una fuente de corriente con resistencia interna.

Este teorema nos dice que podemos remplazar un circuito lineal compuesto por elementos activos y pasivos desde el punto de vista de un par de terminales $a$ y $b$, por una fuente de corriente $I_{N}$ con resistencia interna (paralela) $R_{N}$.

La resolucion es muy similar a thevenin con los tres mismos casos, pero ahora $i_{N}$ va a ser la corriente de corto entre a y b, y la $R_{N}$ sera calculada de la misma manera que $R_{th}$.

### Con Fuentes Independientes

En este caso la corriente de corto entre los terminales sera igual a la corriente de la fuente: $I_{N}=I_{cc}$

Y en este caso se podra calcular $R_N$ de dos maneras:

1. Pasivando todas las fuentes y calculando la resistencia de thevenin vista desde $a$ y $b$.
2. Midiendo la tension de circuito abierto entre $a$ y $b$, y usando la corriente de cortocircuito calcular $R_{N}= V_{ca}/I_{N}$.

> Resolver mismo ejemplo que en thevenin

### Con Fuentes Dependientes E Independientes

En este caso se calcula $I_{N}$ como la corriente de corto circuito y usando el voltaje de circuito abierto calculamos $R_{N}=V_{ca}/I_{cc}$

> Duda: Tambien se puede hacer agregando una fuente entre los terminales?

### Con Fuentes Dependientes

Estos circuitos tendran $I_{N}=0$, y para el calculo de la $R_{N}$ se colocara entre $a$ y $b$ una fuente de tension o corriente de valor conocido, y luego se medira la corriente o tension respectivamente que pase por esta fuente.
$$
R_{N} = \frac{V_{ab}}{i_{ab}}
$$

## Teorema De Kenelly

Este teorema nos permite encontrar la equivalencia entre un circuito "estrella" y un circuito "Triangulo".

![image-20220630093803983](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220630093803983.png)

Empezamos evaluando entre dos terminales en ambos circuitos:
$$
\begin{align}
1)&&Z_{1}+Z_{3} &= Z_{b}|| (Z_{a}+Z_{c})\\
2)&&Z_{2}+Z_{3} &= Z_{c}|| (Z_{a}+Z_{b})\\
3)&&Z_{1}+Z_{2} &= Z_{a}|| (Z_{b}+Z_{c})\\
\end{align}
$$
Sumando dos de estas ecuaciones llegamos a tener una de las impedancias de triangulo en términos de las impedancias de estrella ($(1)-(2)+(3)$):
$$
\begin{align}
Z_{1}+\cancel{Z_{3}}-\cancel {Z_{2}}-\cancel{Z_{3}}+Z_{1}+\cancel{Z_{2}}&= \frac{Z_{b}(Z_{c}+Z_{a})}{Z_{a}+Z_{b}+Z_{c}} - \frac{Z_{c}(Z_{a}+Z_b)}{Z_{a}+Z_{b}+Z_{c}} +\frac{Z_{a}(Z_{b}+Z_c)}{Z_{a}+Z_{b}+Z_{c}} \\
2 Z_{1}&= \frac{2Z_{a}Z_{b}+\cancel{Z_{a}Z_{c}}-\cancel{Z_{a}Z_{c}}+\cancel{Z_{c}Z_{b}}-\cancel{Z_{c}Z_{b}}}{Z_{T}} \\
Z_{1}&= \frac{2Z_{b}Z_{a}}{2 Z_{T}} = \frac{Z_{a}Z_{b}}{Z_{a}+Z_{b}+Z_{c}}
\end{align}
$$
respectivamente para las otras impedancias de triangulo tendremos:
$$
\begin{align}
Z_{2}&= \frac{Z_{a}Z_{c}}{Z_{a}+Z_{b}+Z_{c}}\\
Z_{3}&= \frac{Z_{b}Z_{c}}{Z_{a}+Z_{b}+Z_{c}}
\end{align}
$$
Para hacer el paso de estrella a triangulo vamos a necesitar las relaciones entre las impedancias de estrella para simplificar los pasos:
$$
\begin{align}
\frac{Z_{1}}{Z_{2}} &= \frac{Z_{b}\cancel{Z_{a}}}{\cancel{Z_{a}}Z_{c}} \frac{\cancel{Z_{a}+Z_{b}+Z_{c}}}{\cancel{Z_{a}+Z_{b}+Z_{c}}} = \frac{Z_{b}}{Z_{c}}\\
\frac{Z_{1}}{Z_{3}} &= \frac{Z_{a}\cancel{Z_{b}}}{\cancel{Z_{b}}Z_{c}} \frac{\cancel{Z_{a}+Z_{b}+Z_{c}}}{\cancel{Z_{a}+Z_{b}+Z_{c}}} = \frac{Z_{a}}{Z_{c}}\\
\frac{Z_{2}}{Z_{3}} &= \frac{Z_{a}\cancel{Z_{c}}}{\cancel{Z_{c}}Z_{b}} \frac{\cancel{Z_{a}+Z_{b}+Z_{c}}}{\cancel{Z_{a}+Z_{b}+Z_{c}}} = \frac{Z_{a}}{Z_{b}}
\end{align}
$$
Primero empezamos desde donde terminamos al pasar de triangulo a estrella, y dividimos todo por $Z_{a}$:
$$
\begin{align}
Z_{1}& = \frac{Z_{a}Z_{b}}{Z_{a}+Z_{b}+Z_{c}}\\
Z_{1}&= \frac{Z_{b}}{1+Z_{b}/Z_{a}+Z_{c}/Z_{a}}
\end{align}
$$
remplazando por las relaciones calculadas antes:
$$
\begin{align}
Z_{1}&= \frac{Z_{b}}{1 + Z_{3}/Z_{2}+ Z_{3}/Z_{1}}\\
Z_{1} \left(1 + \frac{Z_{3}}{Z_{2}}+ \frac{Z_{3}}{Z_{1}}\right) &= Z_{b}\\
Z_{b}&= \left(Z_{1}+Z_{3}+ \frac{Z_{3}Z_{1}}{Z_{2}}\right)\\
Z_{b}&= \frac{Z_{1}Z_{2}+Z_{3}Z_{2}+Z_{1}Z_{3}}{Z_{2}}
\end{align}
$$
para las otras 2 impedancias de estrella obtendremos:
$$
\begin{align}
Z_{a} = \frac{Z_{1}Z_{2}+Z_{3}Z_{2}+Z_{1}Z_{3}}{Z_{3}}\\
Z_{c} = \frac{Z_{1}Z_{2}+Z_{3}Z_{2}+Z_{1}Z_{3}}{Z_{1}}
\end{align}
$$

## Teorema De La Maxima Transferencia De Potencia

Si queremos saber la resistencia que ubicar en un circuito cualquiera para que por ella halla una maxima transferencia de potencia podemos pasar pasar este circuito a su equivalente de Thevenin, y de ahi calcular el valor de $R$.

Podemos observar que para $R \rightarrow\infty$ tendremos un circuito abierto, y el voltaje sera maximo pero la potencia sera $p=v\cdot i = 0$, y para $R=0$ la corriente sera maxima, pero la potencia sera $p=v\cdot i= 0$, por lo tanto $R$ debe tener algún valor intermedio de $R$ que no se obtiene maximizando ni $v$ ni $i$.

![](ZImages/Pasted%20image%2020220629154733.png)

En $R$ la potencia disipada es $p=vi$ pero $v$ por divisor de tensiones es:
$$
V = \frac{V_{Th}R}{R_{Th}+R}
$$
y la corriente por ley de ohm sera:
$$
I = \frac{V_{Th}}{R+R_{Th}}
$$
por lo tanto la potencia va a ser:
$$
p = \frac{V_{Th}R}{R_{Th}+R} \frac{V_{Th}}{R_{Th}+R} = \frac{V_{Th}^{2}R}{(R_{Th}+R)^{2}}
$$
y esta función llegara a un máximo cuando $dp/dR=0$, entonces:
$$
\begin{align*}
\frac{V_{Th}^{2}(R_{Th}+R)^2-2V_{Th}^{2}R(R_{Th}+R)}{(R_{Th}+R)^{4}} &= 0\\
(R_{Th}+R)^{2}-2R(R+R_{Th}) &=0\\
(R_{Th}+R)^{2} &= 2R(R+R_{Th})\\
(R_{Th}+\cancel{R}) &= \cancel2R\\
R_{Th} &= R
\end{align*}
$$
Por lo tanto la potencia maxima se alcanza cuando $R=R_{Th}$ y remplazando encontramos la potencia maxima transferida:
$$
P_{max} = \frac{V_{Th}^{2}R_{Th}}{(R_{Th}+R_{Th})^{2}} = \frac{V_{Th}^{2}}{4 R_{Th}}
$$
La curva de potencia se puede visualizar como:

![](ZImages/Pasted%20image%2020220629160404.png)

donde tanto en $R=0$ como en $R \rightarrow \infty$ la potencia es nula.

## Circuitos RL Y RC Sin Fuente

Estos se caracterizan por tener solo un elemento almacenador de energía.

### RL Sin Fuente

Dado un circuito RL en paralelo:
![](ZImages/Pasted%20image%2020220630103503.png)

Pasado el suficiente tiempo con la fuente conectada el inductor actua como un corto circuito y la corriente que circula por el inductor es igual a la de la fuente, $V_{L} = L\ di/dt$, luego al instante $t=0$, abrimos el circuito dejandolo sin fuente, toda la energia almacenada en el inductor se va a ir disipando en el resistor, siguiendo la respuesta dada por la ecuacion diferencial que estamos por formular.

Nos interesa saber la corriente para $t>0$, donde el circuito es basicamente:

![](ZImages/Pasted%20image%2020220630103534.png)

Para encontrar esto, aplicamos ley de Kirchhoff de los voltajes, y encontramos:
$$
\begin{align*}
v_{L}(t)+ v_{R}(t) &= 0\\
L \frac{di(t)}{dt}+Ri(t)&=0\\
 \frac{di(t)}{dt}+ \frac{R}{L}i(t) &=0
\end{align*}
$$
para resolver esta ecuacion diferencial despejamos y definimos $\tau = L/R$ :
$$
\begin{align*}
\int\frac{di(t)}{i(t)} &=\int -\frac{R}{L}dt\\\\
\ln|i(t)| &= - \frac{t}{\tau} + k\\
i(t) &= e^{k}e^{-\frac{t}{\tau}}=A e^{-t/\tau}
\end{align*}
$$
entonces vemos que la respuesta decrece exponencial-mente desde un valor $A$. Para encontrar este valor debemos ver el estado inicial de el elemento almacenador de energia, y usar la condicion de continuidad para el parametro correspondiente, en este caso para $t=0$ encontramos que para que se satisfaga la condicion de continuidad la malla debe tener:
$$
i(0^{+}) = i(0^{-}) =I_{0}
$$
y esta valor es la condicion inicial del circuito y substituyendo en la ecuacion para este valor inicial encontramos $A$:
$$
i(0^{+}) = Ae^{0}=A = I_{0}
$$
![](ZImages/Pasted%20image%2020220403092745.png)

El voltaje en los elementos del circuito puede ser calculado usando las referencias elegidas:

en el resistor:
$$
v_{R} = Ri(t) = RI_{0}e^{-t/\tau}
$$
Para encontrar el voltaje en el inductor podemos derivarlo desde $v_R+v_{L}=0$ o encontrarlo usando su relacion con la corriente:
$$
v_{L}(t)= L \frac{di}{dt} = LI_{0}\left(- \frac{R}{L}e^{t/\tau} \right)=-I_{0}Re^{-t/\tau}
$$
podemos ver el voltaje en cada elemento de la figura como:

![](ZImages/Pasted%20image%2020220403093125.png)

Se puede demostrar que la energia acumulada en el inductor es la misma que la disipada en la resistencia:
$$
\begin{align*}
W_{L}= \frac{1}{2}L i_{0}^{2}- \frac{1}{2}L i^{2} && W_{R}=\int_{0}^{t}Ri^{2}dt
\end{align*}
$$

#### Constante De Tiempo $\tau$

De esta depende la velocidad con la que disminuye la corriente, $\tau$ es el tiempo en el cual la corriente disminuye en un $63,2\%$.

![](ZImages/Pasted%20image%2020220630104532.png)

Si la corriente disminuyera continuamente con su rapidez inicial se haría cero en $t=\tau$, en $t=5\tau$ la corriente es igual a aproximadamente un 1% de su valor inicial y se pude considerar nula.

Dado que $\tau=L/R$ a mayor $L$ mayor $\tau$ ya que se almacena mas energia, y a menor $R$ aumenta $\tau$ ya que la corriente tarda mas tiempo en disiparse

### RC Sin Fuente

Ahora digamos que tenemos el capacitor cargado por suficiente tiempo en el circuito, esto significa que el capacitor esta actuando como circuito abierto:

![](ZImages/Pasted%20image%2020220403093249.png)

Entonces en $t=0$ apretamos el interruptor conectando el capacitor al resistor.

![](ZImages/Pasted%20image%2020220403093348.png)

Desde este momento en adelante la energia almacenada en el capacitor se empieza a disipar en el resistor, si queremos ver como evoluciona el voltaje en el tiempo entonces debemos aplicar ley de kirchhoff de los voltajes a la malla:
$$
\begin{align*}
v_{C}(t)+v_{R}(t)&=0\\
v_{C}(t) + Ri(t) &=0
\end{align*}
$$
 y como podemos expresar la corriente como:
$$
i(t)= C \frac{dv_{C}}{dt}
$$
entonces remplazando:
$$
v_{C}(t) + CR \frac{dv_{C}}{dt}=0
$$
resolviendo esta ecuacion diferencial y remplazando $\tau=1/RC$ llegamos a:
$$
v_{C}(t) = A e^{-t/\tau}
$$
y usando la condicion inicial encontramos $V_{C}(0^{+})=Ae^{0}=V_{0}$

entonces la respuesta es:
$$
v_{C}(t) = V_{0}e^{-t/\tau}
$$
y usando la relacion $v_{C}(t)+v_{R}(t)=0$ podemos ver el voltaje en los elementos en el tiempo:

![](ZImages/Pasted%20image%2020220403094321.png)

para encontrar la corriente remplazamos en la ecuacion:
$$
i(t) = C \frac{dv_{C }(t)}{dt} = \frac{C}{RC} V_{0}e^{-t/\tau}=
\frac{V_{0}}{R}e^{-t/\tau}
$$
![](ZImages/Pasted%20image%2020220630105255.png)

## Circuitos RL Y RC Con Fuente

### Solucion a Una ODE De 1er Orden No Homogenea

Sistemas del tipo:

$$
A \frac{dx(t)}{dt} + B x(t) = F
$$
$A$ y $B$ son constantes, y a $F$ se la conoce como una funcion impulsora.

En estos sistemas tendremos una solucion general formada por dos partes, la solucion a la ecuacion homogenea $x_{t}$, la cual llamamos respuesta natural, o transitoria la cual desaparecera con el tiempo, y calcularemos como:

$$
x_{n} = K e^\frac{-Bt}{A}
$$
y la respuesta permantente $x_p$, particular, o forzada, la cual sera la solucion que se mantenga en el tiempo, esta se calcula mediante a la integral particular como:

$$
x_{p}= \frac{1}{A} e^{-\frac{Bt}{A}} \int F\cdot e^{\frac{Bt}{A}} dt
$$
entonces la solucion general tendra la forma:

$$x(t) = x_{p}(t)+ x_{n}(t) = \frac{1}{A} e^{-\frac{Bt}{A}} \int F\cdot e^{\frac{Bt}{A}} dt + K e^\frac{-Bt}{A}$$

### RL Con Fuente

![](ZImages/Pasted%20image%2020220630111506.png)

Analizamos el circuito aplicando ley de Kirchhoff de los voltajes, para llegar a:
$$
\begin{align*}
V_{L}+V_{R}&= V_{s}\\
L \frac{di(t)}{dt}+ Ri(t) &= V_{s}
\end{align*}
$$
Cuya solucion tiene dos partes, una natural obtenida resolviendo la ecuación homogénea, la cual sera transitoria y se disipara en el tiempo, y otra forzada la cual esta dada por la respuesta en regimen permanente y sera estable en el tiempo. La respuesta natural sera:
$$
i_{n}(t) = K e^{-tR/L}=Ke^{-t/\tau}
$$
Donde $\tau = L/R$ y calcularemos la respuesta en regimen permanente como:
$$
i_{p}(t) = \frac{1}{L}e^{-t/\tau}
\int V_{s} e^{t/\tau}dt=
\frac{1}{L} e^{-t/\tau}V_{s}
\tau e^{t/\tau}=
\frac{1}{L}V_{s} \frac{L}{R} = \frac{V_{s}}{R} 
$$
por lo que nos queda una respuesta general:
$$
i(t) = K e^{-t/\tau}+ \frac{V_{s}}{R} 
$$
Y si tomamos la condicion inicial de que en $t=0$ tenemos $i=0$, nos queda:
$$
0 = Ke^{0}+ \frac{V_{s}}{R} \implies K=- \frac{V_{s}}{R}
$$
por lo tanto la solucion sera:
$$
i(t) = - \frac{V_{s}}{R} e^{-t/\tau}+ \frac{V_{s}}{R} =
\frac{V_{s}}{R} (1-e^{-t/\tau})
$$
Y el voltaje que pase por el inductor estara dado por:
$$
V_{L}(t) = L \frac{di(t)}{dt} = L\frac{V_{s}}{R} \frac{1}{\tau} e^{-t/\tau} =
L\frac{V_{s}}{R} \frac{R}{L} e^{-t/\tau}=
V_{s}e^{-t/\tau}
$$
![](ZImages/Pasted%20image%2020220630113346.png)

### RC Con Fuente

![](ZImages/Pasted%20image%2020220630113453.png)

Analizamos el circuito por ley de Kirchhoff de los voltajes y vemos que:
$$
\begin{align*}
V_{s} &= V_{R}+V_{C}\\
V_{s} &= Ri_{c}+ V_{c}\\
V_{s}&=  R C \frac{dV_{c}}{dt}+V_{c}
\end{align*}
$$
Cuya solucion tiene dos partes, una natural obtenida resolviendo la ecuación homogénea, la cual sera transitoria y se disipara en el tiempo, y otra forzada la cual esta dada por la respuesta en regimen permanente y sera estable en el tiempo. La respuesta natural sera:
$$
V_{c,n} = K e^{-t/RC}=
Ke^{-t/\tau}
$$
donde definimos $\tau = RC$.  Y la respuesta transitoria, forzada o de regimen permanente la encontramos utilizando la integral particular:
$$
V_{c,p} = \frac{1}{RC}e^{-t/RC} \int V_{s}e^{t/RC}dt
= \frac{1}{RC}e^{-t/RC} V_{s} RC e^{t/RC} = V_{s}
$$
por lo tanto la respuesta general sera:
$$
V_{c}(t)= V_{c,n}(t)+V_{c,p}(t) =Ke^{-t/RC}+V_{s}
$$
y si tomamos como condiciones iniciales que en $t=0$ tenemos $V_{c}(0)=0$, quedamos con:
$$
V_{c}(0)=0=K e^{0}+V_{s}\implies
K=-V_{s}
$$
por lo que el voltaje nos queda:
$$
V_{c} = -V_{s}e^{-t/RC}+V_{s}=
V_{s}(1-e^{-t/\tau})
$$
y podemos encontrar la corriente que pasa por el circuito utilizando la relacion:
$$
i(t) = C \frac{dV_{c}}{dt}=-C \left(- \frac{1}{\tau}\right)V_{s} e^{-t/\tau}= \frac{C}{RC}V_{s}e^{-t/\tau}=
\frac{V_{s}}{R}e^{-t/\tau}  
$$
![](ZImages/Pasted%20image%2020220630115054.png)

## Circuito RLC

Si consideramos un RLC en serie:

![](ZImages/Pasted%20image%2020220405110359.png)

podemos ver que por ley de voltajes de Kirchhoff:
$$
v_{f}=v_{R}+v_{L}+v_{C}
$$
y como la misma corriente circula por todos los elementos podemos ver esto en terminos de corriente:
$$
\begin{align*}
v_{f}&= R i(t)+ L \frac{di(t)}{dt} + \frac{1}{C}\int i(t) dt\\
\end{align*}
$$
derivando respecto a la corriente llegamos a la ecuacion difierencial homogenea de segundo orden:
$$
0 = L \frac{di^{2}}{dt^{2}}+ R \frac{di}{dt} + \frac{1}{C} i
$$
la cual tendra la ecuacion caracteristica.
$$
L s^{2}+ Rs+ \frac{1}{C}=0
$$

$$
A s^{2}+Bs+D
$$

La cual tendra raices de la forma:
$$
s_{1,2} = \frac{-R\pm\sqrt{R^{2}-4 \frac{L}{C}}}{2L}
$$
donde llamamos a $\alpha =B/2A= R/2L$ coeficiente de amortiguamiento, y a $\omega_{0}=\sqrt{D/A}=\sqrt{1/LC}$  la frecuencia natural de resonancia no amortiguada.

podemos entonces reescribir las raices como:
$$
s_{1,2}= -\alpha\pm \sqrt{\alpha^{2}-\omega_{0}^{2}}
$$
Y vamos a tener 4 tipos de respuesta.

### Respuesta Sobreamortiguada

donde:
$$\alpha^{2}>\omega_{0}^{2}$$ por lo tanto:
$$
\left(\frac{R}{2L}\right)^{2}> \frac{1}{LC}
$$
en este caso las raíces son negativas, reales y distintas, y la solucion tendra la forma:
$$
i(t) = K_{1}e^{s_{1}t}+K_{2}e^{s_{2}t}
$$

### Respuesta Con Amortiguamiento Critico

esto sucede cuando $\alpha^{2}=\omega_{0}^{2}$, por lo tanto:
$$
\left(\frac{R}{2L}\right)^{2} = \frac{1}{LC}
$$
en este caso las raices son reales, negativas e iguales, y tendremos la solucion de forma:
$$
i(t) = K_{1}e^{st} + tK_{2}e^{st}
$$

### Respuesta Subamortiguada

En este caso tendremos $\alpha^{2}<\omega_{0}^{2}$, por lo tanto:
$$
\left(\frac{R}{2L}\right)^{2}< \frac{1}{LC}
$$
y esto nos lleva a tener raices con componente imaginario conjugado de la forma:
$$
s_{1,2}=-\alpha \pm j \sqrt{w_{0}^{2}-\alpha ^{2}}
$$
donde $w_{n}^{2}=w_{0}^{2}-\alpha^{2}$ es la frecuencia natural de resonancia amortiguada, y con esto podemos reescribir las raices como:
$$
s_{1,2}= -\alpha \pm j w_{n}
$$
La solucion a estos sistemas tendra la forma:
$$
i(t) = e^{-\alpha t} (K_{1}\cos(\omega_{n}t)+ K_{2}\sin(\omega_{n}t))
$$
![](ZImages/Pasted%20image%2020220405112856.png)

### Respuesta Oscilatoria

Esta sucede en caso de que $B=0$, es decir $R=0$, por lo que no hay amortiguamiento ya que $\alpha=0$, y $\omega_{n}=\omega_{0}$. Esto nos da las raices:
$$
s_{1,2} = \pm j\sqrt{\omega_{0}^{2}}=\pm \omega_{0}
$$
son raices imaginarias conjugadas, y este sistema tendra la solucion:
$$
i = K_{1}\cos(\omega_{0}t)+K_{2}\sin(\omega_{0}t)
$$
![](ZImages/Pasted%20image%2020220630125411.png)

## Representaciones De Magnitud

Podemos representar una corriente alterna de 4 maneras:
- Trigonométrica
- Cartesiana
- Vectorial 
- Simbólica

### Representacion Trigonometrica

En esta se utilizan los valores instantaneos para describirla:
$$
i(t) = I_{max}\sin (\omega t)= I_{max}\sin(2\pi ft)= I_{max}\sin\left(\frac{2\pi}{T}t\right)
$$

### Representacion Cartesiana

![](ZImages/Pasted%20image%2020220630130524.png)
Donde $A$ va a ser la corriente maxima, y la longitud de onda sera $T$.

### Representacion Vectorial

En una onda senoidal podemos representar los valores instantaneos como la proyeccion de un vector que gira a velocidad $\omega$ sobre el eje de las ordenadas.

![](ZImages/Pasted%20image%2020220630130908.png)

Esta representacion nos sirve para prescindir del tiempo ya que si a estos vectores giratorios que rotan a la misma velocidad por tener la misma frecuencia los frisamos en un instante, podemos analizar los parametros electricos ya que la diferencia de angulos es la misma.

### Representacion Simbolica

En estas se pasan representaciones que son en funcion de tiempo a representaciones que no lo son, a esto se llama transformada.

Podemos representar al vector rotatorio en el plano complejo, esto se puede hacer de tres formas:

#### Coordenadas Rectangulares

Dado que tenemos el angulo y magnitud del vector podemos represntarlo en sus componentes real y compleja como $\vec Z = Z \cos\theta + j Z\sin\theta$.

![](ZImages/Pasted%20image%2020220630131611.png)

Para el paso contrario hariamos $Z = \sqrt{Z_{real}^2+Z_{compleja}^2}$ y $\theta = \tan^{-1}(Z_{compleja}/Z_{real})$.

Esta representacion nos permite sumar y restar vectores facilmente.

### Coordenadas Polares

Normalmente escrita de la forma $\vec Z = Z \angle \theta$

![](ZImages/Pasted%20image%2020220630131819.png)

esta representacion nos permite multiplicar y dividir vectores con facilidad.

#### Coordenadas Exponenciales

Estas surgen de el vector representado de la forma $\vec Z = Z e^{j\theta}$ o $\vec Z = Z (\cos\theta+j\sin\theta)$.

![](/home/bbruno/Pasted image 20220630132022.png)

## Valor Medio De Señal

El valor medio de una señal se calcula como:
$$
i_{m}= \frac{1}{T}\int_{0}^{T}i(t) dt
$$
pero en el caso de una señal sino o coseno sera nulo, por lo que lo calcularemos sobre un semiperiodo.
![](ZImages/Pasted%20image%2020220630135407.png)
Por lo tanto lo calculamos como:
$$
\begin{align*}
i_{m} &= \frac{2}{T} \int_{0}^{\frac{T}{2}} I_{max}\sin(\omega t) dt = \frac{2I_{max}}{T} \int_{0}^{\frac{T}{2}}\sin(\omega t) dt\\
&= \frac{2I_{max}}{T} \left|- \frac{1}{\omega} \cos(\omega t) \right|_{0}^{\frac{T}{2}}= \frac{2}{\pi} I_{max} \approx 0.6366\cdot I_{max}
\end{align*}
$$

## Valor Eficaz Y Factor De Forma

El valor eficaz, o valor RMS ( root means square), de una señal es:
$$
x_{eff}  = \sqrt{\frac{1}{T} \int_{0}^{T} x(t)^{2} dt}
$$
en el caso de una señal sinusoidal como por ejemplo una corriente alterna:
$$
\begin{align*}
i_{eff} &= \sqrt{\frac{1}{T} \int_{0}^{T}I_{max}^{2} \sin^{2}(\phi +\omega t)} \\
&= \sqrt{\frac{1}{2\pi}I_{max}^{2} \int_{0}^{2\pi} \sin^{2}(u)\  d(u)} & u&=\omega t\\
&=  \sqrt{\frac{1}{2\pi}I_{max}^{2} \left(\int_{0}^{2\pi} \frac{1}{2} du+ \int_{0}^{2\pi} \frac{1}{2}\cos(2u) \right) } & \sin^{2}u&= \frac{1-\cos(2u)}{2} \\
&=  \sqrt{\frac{1}{4\pi}I_{max}^{2} 2\pi}= \sqrt{\frac{I_{max}^{2}}{2}} \\
&= {\frac{I_{max}}{\sqrt{2}} }
\end{align*}
$$
es el valor en continuo en el cual el area bajo la curva es la misma que la de la función original, en esta aplicación significa que el valor eficaz de una corriente alterna es el valor de corriente continua que en la misma resistencia disipa la misma energía en igual periodo de tiempo.

El factor de forma es:
$$
F_{f}= \frac{I_{eff}}{I_{med}}
$$
en el caso de una corriente senoidal:
$$
F_{f}= \frac{I_{max}\pi}{\sqrt{2}2I_{max}} = \frac{\pi}{2\sqrt{2}}= 1.11
$$

## Receptor Resistivo Puro

![](ZImages/Pasted%20image%2020220405144453.png)

Suponiendo que sabemos que por el elemento circula un voltaje de la forma:
$$
v(t) = V_{max}\sin(\omega t+ \phi_{v})
$$
Determinaremos la corriente en el elemento mediante la ley de ohm:
$$
i(t) = \frac{v(t)}{{R}} = \frac{V_{max}}{R} \sin(\omega t + \phi_{v})
$$
que en dominio fasorial corresponde a:

$$I_{max}\angle \phi_{v} = \frac{V_{max}}{R} \angle \phi_{v}$$
Donde podemos ver que $I_{max}R= V_{max}$ y que $\phi_{i}=\phi_v$

por consiguiente los valores sinusoidales de la corriente y la tensión en una resistencia son:
$$
\begin{align*}
I = I_{max} \sin(\omega t+ \phi_{i})= \frac{V_{max}}{R}sin(\omega t +\phi_i)  && V = V_{max} \sin(wt+\phi_{i})
\end{align*}
$$
![](ZImages/Pasted%20image%2020220405145317.png)
misma fase, diferente amplitud.

visto tomando como referencia $\phi_{v}$:
![](ZImages/Pasted%20image%2020220630141027.png)

## Receptor Inductivo Puro

![](ZImages/Pasted%20image%2020220630141228.png)

Suponiendo que sabemos que por el elemento circula una corriente de la forma:
$$
i(t) = I_{max}\sin(\omega t+ \phi_{i})
$$
y queremos determinar la tension existente en el elemento, la cual tendrá la forma general:
$$
v(t) = V_{max} \sin(\omega t + \phi_{v})
$$
la solución del problema seria encontrar los valores de $V$, y $\phi_{v}$ en función de $I$ y $\phi_{i}$, ademas del parámetro $L$.

Para esto usamos la relacion:
$$
v(t) = L \frac{di(t)}{dt} =  \omega L I_{max}\cos(\omega t+\phi_i) = \omega L I_{max}\sin(\omega t+\phi_i +90)
$$
o en dominio de frecuencia esto se puede hacer como:
$$
\vec V = jL\omega \vec I \implies V_{max} \angle \phi_{v} = \omega LI_{max} \angle (\phi_{i}+90) 
$$
Por lo que $V_{max}=\omega L I_{max}$ y $\phi_{v}=\phi_{i}+90\implies \phi_i =\phi_v -90$, y esto se puede visualizar en el plano cartesiano tomando como referencia $\phi_{v}$ como:

![](ZImages/Pasted%20image%2020220630142430.png)

y en el plano complejo como:

![](ZImages/Pasted%20image%2020220630142447.png)

Donde $V= j X_{L}I_{max}$

## Receptor Capacitivo Puro

![](ZImages/Pasted%20image%2020220630165632.png)

Suponiendo que tenemos un elemento capacitivo puro el cual se somete a un voltaje $v(t) = V_{max}\sin(\omega t + \phi_{v})$.

Podemos calcular la corriente que va a circular a lo largo del elemento mediante la relacion:
$$
i(t) = C \frac{dv}{dt} = C\omega V_{max}\cos(\omega t+\phi_{v})=C\omega V_{max}\sin(\omega t+\phi_{v}+90) 
$$
visto en el dominio de frecuencia esto seria
$$
I_{max}\angle \phi_{i} = C\omega V_{max}\angle(\phi_{v}+90)
$$
Por lo tanto en este caso $\phi_{i}=\phi_{v}+90$ y $I_{max}=C\omega V_{max}$, al tomar $\phi_{v}$ como referencia como:

![](ZImages/Pasted%20image%2020220630170930.png)

y en el plano complejo como:

![](ZImages/Pasted%20image%2020220630170943.png)

donde $\vec V=-jX_{c}\vec I$

A su vez se puede pensar en la corriente por ley de ohm como en dominio de frecuencia donde:
$$
\begin{align*}
\vec I &= \frac{\vec V}{-jX_{c}}= \frac{V_{max}}{X_{c}}\angle\phi_{v}+90 \\
i(t) &= \frac{V_{max}}{X_{c}}\sin(\omega t+\phi_{v}+90)
\end{align*}
$$
y como $X_{c}=1/\omega C$ llegamos a lo mismo.

## Receptor RL Serie

![](ZImages/Pasted%20image%2020220630172205.png)

Dado que el circuito esta expuesto a un voltaje $v(t)= V_{max}\sin(\omega t+\phi_{v})$ podemos ver que por ley de kirchoff de los voltajes tendremos:
$$
v(t) = Ri(t)+L \frac{di}{dt}
$$
Lo que podemos pasar al dominio de frecuencia como:
$$
\vec V= R\vec I + j\omega L \vec I = \vec I(R+j\omega L)  
$$
desde donde deducimos:
$$
I = \frac{V_{max}}{R+j\omega L} \angle \phi_{v} = \frac{V_{max}}{\sqrt{R^{2}+\omega^{2} L^{2}}}\angle\phi_{v}-\phi 
$$
donde $\phi$ es el angulo del vector obtenido al sumar la resistencia y el elemento inductivo, $R+j\omega L$, este angulo se consigue como: $\phi = \tan^{-1}(\omega L/R)$ 

Corriente la cual en el dominio del tiempo sera:
$$
i(t) = \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\omega t+\phi_{v}-\phi)
$$
Podemos ver que la magnitud se modifica segun la ley de ohm como:
$$
I_{max} = \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}}= \frac{V_{max}}{Z_{RL}}
$$
graficando con $\phi_v=0$ veriamos el voltaje y corriente como:

![image-20220630175832866](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220630175832866.png)

Y en el plano complejo sin referencia podemos ver como:
![](ZImages/Pasted%20image%2020220406175922.png)

pero si tomamos $\phi_{i}$ como referencia tendremos:

![](ZImages/Pasted%20image%2020220406175934.png)

## Receptor RC Serie

![](ZImages/Pasted%20image%2020220311171359.png)
Empezamos analizando el circuito sabiendo que esta expuesto a una fuente de voltaje de $v(t)=V_{max}\sin(\omega t+\phi_{v})$, y aplicando la ley de Kirchhoff de los voltajes podemos ver que:
$$
\begin{align*}
v(t) &= v_{R}+v_{C}\\
V_{max}\sin(\omega t+\phi_{v}) &= R i(t)+ \frac{1}{C}\int i(t)dt 
\end{align*}
$$
si pasamos esto al dominio de frecuencia vemos que:
$$
V_{max}\angle \phi_{v} = R\vec I  -j\frac{\vec I}{C \omega} = \left(R- \frac{j}{C\omega}\right)I_{max}\angle\phi_{i}  
$$
por lo tanto podemos pasar dividiendo y quedamos con:
$$
I_{max}\angle\phi_{i}=  \frac{V_{max}}{R- \frac{j}{\omega C}}\angle \phi_{v} = \frac{V_{max}}{\sqrt{R^{2}+1/\omega^{2}C^{2}}}
\angle \phi_{v} +\phi
$$
donde $\phi= \tan^{-1}(X_{c}/R)=\tan^{-1}(1/R\omega C)$.

y podemos ver que la magnitud fue modificada por lo mismo que si hubieramos aplicado la ley de ohm:
$$
I_{max}= \frac{V_{max}}{\sqrt{R^{2}+1/\omega^{2}C^2}}
= \frac{V_{max}}{Z_{RC}}
$$
la corriente en dominio del tiempo sera:
$$
I_{max}\angle\phi_{i}=  \frac{V_{max}}{R- \frac{j}{\omega C}}\angle \phi_{v} = \frac{V_{max}}{\sqrt{R^{2}+1/\omega^{2}C^{2}}}
\sin(\omega t + \phi_{v} +\phi)
$$
Visualizando esto con $\phi_{v}=0$ tenemos:

![](ZImages/Pasted%20image%2020220630175953.png)

si tomamos la corriente como referencia podemos ver que los voltajes en cada componente seran:

![](ZImages/Pasted%20image%2020220630180138.png)

lo que podemos relacionar con el triangulo de impedancias ya que este sera el mismo pero dividiendo ambos lados por la corriente:

![](ZImages/Pasted%20image%2020220630180215.png)

## Receptor RLC Serie

![](ZImages/Pasted%20image%2020220630180704.png)

Vemos por ley de Kirchhoff de los voltajes que:
$$
\begin{align}
\vec V &= \vec V_{R}+\vec V_{L}+\vec V_{C}\\
&= \vec I R + jL\omega\vec I - \frac{j}{C\omega}\vec I \\
\vec V&= \vec I (R+ j(L\omega - 1/C\omega)) \\
&= \vec I (R+ j(\underbrace{X_{L} - X_{C}}_X))\\
&= \vec I \vec Z
\end{align}
$$
Entonces definimos la reactancia como $X=X_{L}-X_{C}$ y la impedancia como $\vec Z = R+jX$, dejando definida la ley de ohm para los circuitos de alterna como $\vec V = \vec Z\vec I$

la impedancia tendra modulo igual a:
$$
Z = \sqrt{R^{2}+(X_{L}-X_{C})^{2}}
$$
con un angulo dado por:
$$
\phi = \tan^{-1} \frac{X_{L}-X_{C}}{R}
$$
por lo tanto podemos ver esto en el triangulo de impedancias como:

![](ZImages/Pasted%20image%2020220630181426.png)

-  si es que $X_{L}>X_{C}$ este se va a comportar como un circuito $RL$, es decir $\phi>0$, el voltaje adelanta la corriente.
- si $X_{c}>X_{L}$ se va a comportar como un circuito $RC$, es decir $\phi<0$ , la corriente adelante el voltaje.
- si es que $X_{L}=X_{C}$ entonces se va a comportar como un circuito resistivo puro, $\phi=0$.

## Respuesta Transitoria RC En CA

![](ZImages/Pasted%20image%2020220630192022.png)

Dado que tenemos un voltaje $v(t)= V_{max}\sin(\omega t)$

por ley de Kirchhoff de los voltajes vamos a tener:
$$
iR + \frac{1}{C} \int i\ dt= V_{max}\sin(\omega t)
$$
derivando todo respecto a la corriente vamos a quedar con:
$$
R \frac{di}{dt}+ \frac{1}{C} i = \omega V_{max}\cos(\omega t)
$$
Por lo que conseguiremos la respuesta natural como la solucion del problema homogeneo:
$$
R \frac{di}{dt} + \frac{1}{C}i = 0
$$
que tendra la solucion:
$$
i_{n}= K e^{-t/\tau}
$$
Y utilizando la integral particular encontramos la respuesta forzada o de regimen permanente del sistema:
$$
i_{p} = \frac{V_{max}}{\sqrt{R^{2}+ \frac{1}{\omega^{2}C^{2}}}} \sin(\omega t+ \phi)
$$
donde  $\phi=\tan^{-1}(X_{c}/R)$.

lo que nos deja con una respuesta general de la forma:
$$
i_{p}= \frac{V_{max}}{\sqrt{R^{2}+ \frac{1}{\omega^{2}C^{2}}}} \sin(\omega t+\phi)+ K e^{-t/\tau}
$$
Y aplicando las condiciones iniciales vamos a encontrar $K$.

## Respuesta Transitoria RL En CA

dado un circuito RL con una fuente alterna de voltaje $v(t)= V_{max}\sin(\omega t+\phi_{v})$

![](ZImages/Pasted%20image%2020220630194153.png)

Aplicando la ley de Kirchhoff de los voltajes podemos ver que:
$$
L \frac{di}{dt}+ Ri = V_{max}\sin(\omega t+\phi_{v})
$$
Donde la respuesta natural va a ser obtenida de resolver el problema homogeneo:
$$
L \frac{di}{dt}+ Ri = 0
$$
y al resolver obtenemos:
$$
i_{n} = K e^{-t/\tau}
$$
con $\tau = L/R$.

Y al resolver para la respuesta forzada o de regimen permanente con la integral particular obtenemos:
$$
i_{p} = \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\omega t+\phi_{v}-\phi)
$$
donde $\phi = \tan^{-1}(X_{L}/R)=\tan^{-1}(\omega L/R)$, lo que nos deja con la solucion general:
$$
i(t) = i_{p}+i_{n}= \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\omega t+\phi_{v}-\phi) + K e^{-t/\tau}
$$
y encontramos soluciones particulares resolviendo para las condiciones iniciales, por ejemplo si en $t=0$ tenemos $i=0$, resolviendo nos queda:
$$
\begin{align*}
i(0^{+})=0&= \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\phi_{v}-\phi)+ K\\
K &= - \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\phi_{v}-\phi)
\end{align*}
$$
y remplazando en la ecuación nos queda:
$$
i(t) = \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\omega t+\phi_{v}-\phi) - \frac{V_{max}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \sin(\phi_{v}-\phi) e^{-t/\tau}
$$

## Potencia Activa, Instantanea Y Reactiva

suponiendo una red lineal con tension $v(t)=V_{m}\cos(\omega t)$ que excita un circuito generico de impedancia equivalente $Z = R+jX=Z\angle\phi$, produce una corriente:
$$
i(t) = I_{m}\cos(\omega t-\phi)
$$
y sabemos que la potencia instantanea se obtiene del producto entre el voltaje y la corriente:
$$
p(t) = I_{m}\cos(\omega t-\phi) V_{m}\cos(\omega t)
$$
y si hacemos uso de la identidad trigonometrica:
$$
\cos(a)\cos(b) = \frac{1}{2}[\cos(a-b)+\cos(a+b)]
$$
entonces quedamos con:
$$
p(t) = \frac{1}{2} I_{m}V_{m} [cos(2\omega t -\phi)+\cos(\phi)]
$$
y substituyendo por los valores eficaces nos queda:
$$
p(t) = IV\cos(\phi) +IV \cos(2\omega t-\phi)
$$
vemos que la potencia tiene un termino constante independiente del tiempo que solo depende del angulo de la impedancia, cuando $\phi=0$ el termino tomara su valor maximo, y si $\phi=90$ este factor sera nulo. Este valor es lo que definimos como **Potencia Activa**, y a su vez es lo que nos da la potencia media ya que el otro termino oscila en el tiempo.
$$
P = VI\cos(\phi)
$$
Y si volvemos a la ecuacion y expandimos el termino que oscila en el tiempo $VI \cos(2\omega t-\phi)$:
$$
VI\cos(2\omega t-\phi) = VI cos(\phi)\cos(2\omega t)+VI\sin(\phi)\sin(2\omega t)
$$
Vemos que tenemos un termino de potencia activa que oscila en el tiempo, y definimos   $Q=VI\sin(\phi)$ como la **potencia reactiva**, y con esto nos queda la expresion de potencia como:
$$
p(t) = P(1+\cos(2\omega t) ) + Q\sin(2\omega t)
$$
En resumen la potencia consta de dos terminos, $P$ es la potencia constante suministrada por la red de CA, mientras que $Q$ es la potencia reactiva con valor medio nulo y es oscilante.

Al producto $VI$ que es igual a la amplitud de la potencia fluctuante lo llamamos **Potencia Aparente** $S$, entre las potencias existen las siguientes relaciones:

$$
\begin{align*}
P &= VI \cos\varphi = S \cos\varphi \\
Q &= VI \sin\varphi = S \sin\varphi \\
S&= \sqrt{P^{2}+Q^{2}}\\
\end{align*}
$$
Otra forma de ver a la potencia aparente como termino fluctuante, entonces tomando el voltaje como referencia nos queda:
$$
S = VI \cos(2\omega t-\phi) = VI^{*} = (V\angle 0)(I\angle-\phi)
$$

### Potencia En Circuito Resistivo Puro

en el caso de un circuito puramente resistivo la impedancia es $Z=R$ y $\phi=0$, entonces la potencia instantanea es:

**Definiendo $v$ y $i$** con cosenos:
$$
p(t) = VI+VI \cos(2\omega t-\phi) = VI+VI \cos(2\omega t) = P(1+cos(2\omega t))
$$

entonces el valor medio de la potencia es $P=VI$ y esta potencia (es la potencia activa) oscila entre $0$ y $2VI$, con el doble de frecuencia que la de la corriente y la del voltaje.



![](ZImages/Pasted%20image%2020220715104537.png)

**Definiendo $v$ y $i$ ** con senos:
$$
p(t) = VI-VI \cos(2\omega t+\phi) = VI+VI \cos(2\omega t) = P(1-cos(2\omega t))
$$
![](ZImages/Pasted%20image%2020220306142319.png)

podemos ver que como no hay termino $VI\sin(2\omega t)$ no hay potencia reactiva

$$U = RI \implies I= \frac{U}{R}= \frac{U}{R }\angle0 $$

y esto corresponde a:

$$
\begin{align*}
u(t) = \sqrt 2 V\cos(\omega t)&& i(t)=\sqrt 2 I\cos\omega t&& U=RI&&\phi=0
\end{align*}
$$

![](ZImages/Pasted%20image%2020220407155129.png)

### Potencia En Circuito Inductivo Puro

En este caso $Z=j\omega L$ y $\phi=90$, en este caso la potencia instantanea se vuelve:

$$
p(t) =\cancel{VI \cos(90)}+ VI\cos(2\omega t-90)= VI \sin(2\omega t) = Q \sin(2\omega t)
$$
Vemos que como $cos(90)=0$, por el defasaje en el otro termino terminamos con una función seno, por lo que esta potencia es puramente reactiva, y oscila con media de 0.

en este caso la corriente se atraza 90° respecto a voltaje, ya que (tomando el voltaje como referencia):

$$V=j\omega LI \implies I = \frac{V}{j\omega L}\angle 0 = \frac{V}{\omega L}\angle-90° $$

![](ZImages/Pasted%20image%2020220306142618.png)

![](ZImages/Pasted%20image%2020220407160035.png)

la potencia tomando valores positivos y negativos se debe al intercambio energetico que se produce entre el elemento inductivo y el generador, en los semiciclos positivos acumula energía en forma de campos magnéticos mientras que en los semiciclos negativos devuelve esta energía al generador.

### Potencia En Circuito Capasitivo Puro

En este caso $Z=-j/\omega C$ y $\phi=-90$ por lo tanto la ecuacion nos queda:

$$
p(t) = VI\cos(2\omega t+90) = - VI \sin(2\omega t)
$$
por lo tanto el funcionamiento sera igual pero opuesto a la del circuito con solo el elemento inductivo, esta vez la transferencia de energia sera entre el elemento capacitivo y el generador.

![](ZImages/Pasted%20image%2020220407160104.png)

## Potencia Instantanea RL En Alterna

Hay dos maneras de llegar a lo mismo, con coseno y la del apunte del profe

### Planteo Con Coseno

Dado un circuito:
![](ZImages/Pasted%20image%2020220406174716.png)
con un voltaje $u(t) = \sqrt{2}U \cos(\omega t+\phi_{u})$ el cual podemos representar en el dominio de frecuencia siguiendo la segunda ley de Kirchhoff como: $U=U\angle \phi_{u}= RI+j\omega L I$

![](ZImages/Pasted%20image%2020220406174830.png)

De donde deducimos:
$$
I = \frac{U}{R+j\omega L} \angle \phi_{u} = \frac{U}{\sqrt{R^{2}+\omega^{2} L^{2}}}\angle\phi_{u}-\phi 
$$
donde $\phi = \arctan(L\omega/R)$ por lo tanto la intensidad instantánea es:

$$
I = \sqrt2 \frac{U}{\sqrt{R^{2}+\omega^{2} L^{2}}}\angle\phi_{u}-\phi
$$

De ahí sacamos el valor de corriente eficaz y el angulo de la corriente como:

$$
\begin{align*}
I &= \frac{U_{m}}{\sqrt{R^{2}+\omega^{2}L^{2}}} \\

\phi_{i}&=\phi_{v}-\phi 
\end{align*}
$$
con estos datos calculamos la potencia instantánea en el dominio de tiempo en el circuito como:

$$
p(t) = \sqrt 2 V\cos(\omega t+\phi_{v})\sqrt2 I\cos(\omega t+\phi_{v}-\phi)
$$
y si tomamos como referencia el voltaje entonces $\phi_{v}=0$ y nos queda:

$$
p(t) = 2V \cos(\omega t)I\cos(\omega t-\phi)
$$
y podemos desarrollar esto para esto usando la identidad trigonométrica que todos tanto queremos:

$$
\begin{align*}
p(t) &= 2VI \frac{cos(2\omega t-\phi )+\cos(\phi)}{2}\\
&= VI \cos\phi + VI \cos(2\omega t-\phi)\\

\end{align*}
$$
De donde podemos usar otra identidad trigonométrica para expandir el termino fluctuante $VI\cos(2\omega t-\phi)$:

$$
\begin{align*}
p(t) &= VI \cos(\phi) + VI(\cos(\phi)\cos(2\omega t)+\sin(\phi)\sin(2\omega t))\\
&= \underbrace{VI\cos(\phi)}_{P} (1+\cos(2\omega t))+ \underbrace{VI\sin(\phi)}_{Q} \sin(2\omega t)\\
&= P(1+\cos(2\omega t))+ Q\sin(2\omega t) 
\end{align*}
$$

Podemos ver que la potencia instantánea queda compuesta por dos partes una fluctuante (Potencia Aparente $S$)  con magnitud igual a $IV$ y una parte constante en el tiempo la cual es igual a la potencia activa $P$ con magnitud igual a $IV\cos(\phi)$, por lo tanto podemos ver la potencia en el tiempo como:

![](ZImages/Pasted%20image%2020220409154608.png)

Ademas podemos dibujar el triangulo de potencias escribiendo la potencia aparente con sus componente reactiva y activa:

![](ZImages/Pasted%20image%2020220409154725.png)

A partir de lo cual podemos ver que la potencia reactiva viene de la reactancia y que la parte activa viene de la resistencia, usando también el triangulo de impedancia:

![](ZImages/Pasted%20image%2020220409155038.png)
(cambiar $\theta$ por $\phi$)

utilizando estos dos diagramas vemos que:

$$
\begin{align*}
R &= |Z| \cos\phi & X&=|Z|\sin\phi\\
P &= |S| \cos\phi & Q&=|S|\sin\phi\\
 &= |V||I| \cos\phi & &= |V||I| \sin\phi\\
 &= |I^{2}||Z|\cos\phi & &= |I^{2}||Z| \sin\phi\\
 &= |I^{2}|R & &= |I^{2}| X
\end{align*}
$$

### Explicacion Del Apunte

Tenemos un circuito inductivo del tipo:

![](ZImages/Pasted%20image%2020220701111844.png)

donde circula una corriente $i(t)= I_{max}\sin(\omega t)$, con un voltaje respectivo $v(t)=V_{max}\sin(\omega t+\phi)$ (el defasaje se suma al voltaje ya que es inductivo), donde $\phi = \tan^{-1}(\omega L/R)$, y $I_{max}=V/Z$.

planteamos entonces la potencia instantanea en el circuito como:

$$
\begin{align*}
p(t)&= v(t)i(t) &&\\
&= V_{max}I_{max}\sin(\omega t)\sin(\omega t+\phi)
\end{align*}
$$
llegado a este punto utilizamos la propiedad trigonometrica:
$$
\sin(a+b) = (\sin a \cos b+ \sin b \cos a)
$$
para llegar a:
$$
\begin{align*}
p(t) &= I_{max}V_{max} \sin(\omega t)(\sin (\omega t)\cos(\phi)+\cos(\omega t)\sin (\phi))\\
&= I_{max}V_{max}\cos(\phi)\sin^{2}(\omega t)+I_{max}V_{max}\sin\phi\cos(\omega t)\sin(\omega t)
\end{align*}
$$
y volviendo a utilizar la misma propiedad trigonometrica:

$$
\begin{align*}
\sin(2a)&=\sin(a+a) = \sin(a)\cos(a)+\sin(a)\cos(a)\\
\sin(2a)&=2 \sin(a)\cos(a)\\
\frac{\sin(2a)}{2}&=\sin(a)\cos(a)
\end{align*}
$$
por lo tanto $\cos(\omega t)\sin (\omega t)= \sin(2\omega t)/2$, y con esto finalmente llegamos a:

$$
p(t) = {V_{max}I_{max}\cos(\phi)}\sin^{2}(\omega t)+
\frac{V_{max}I_{max}}{2} \sin\phi \sin(2\omega t)
$$
> para que termine de tener sentido por que es lo mismo de esta manera y trabajando con senos $\sin^{2}(\omega t)= (1-\cos(2\omega t))/2$ , por lo que lo unico que cambia es que esta un poco mas a la derecha con funciones coseno, pero la frecuencia es la misma, y en ambos hay un termino conformado solo por $VI\cos\phi$.
> La razon por la que estarian todos divididos por 2 en la notacion de seno y en la de coseno no es porque en la de coseno trabajamos con valores eficaces.

#### Primer Termino

Al graficar el primer termino de esta ecuacion vemos que vamos a tener una señal positiva con el doble de frecuencia que la corriente y el voltaje:
![](ZImages/Pasted%20image%2020220701113832.png)
Esta señal va a llegar a su valor pico en $V_{max}I_{max}\cos\phi$ y su valor medio en $V_{max}I_{max}\cos(\phi)/2$, si substituimos por valores eficaces el valor medio sera $VI\cos(\phi)$.

A la magnitud de este primer termino oscilante, la definimos como la potencia activa $P= \frac{1}{2} V_{max}I_{max}\cos(\phi)= VI\cos(\phi)$.

Tambien podemos encontrar esta potencia activa desde la impedancia como:
$$
P = \frac{V^{2}}{Z} \cos(\phi) = I^{2}Z\cos(\phi)
$$
ademas dado que sabemos que el factor potencia es $fp=\cos(\phi)$, y esto se puede encontrar en el triangulo de impedancias como la relacion entre los lados del triangulo:

![](ZImages/Pasted%20image%2020220701114834.png)

Entonces podemos decir que $\cos(\phi)= R/Z$, y por lo tanto substituyendo tenemos:
$$
\begin{align*}
P = VI\cos(\phi) &= I^{2}Z \frac{R}{Z}=I^{2}R\\
\end{align*} 
$$
y si pensamos en el voltaje que pasa por la resistencia este seria $V_{R}=RI= R\ V/Z$, por lo tanto si despejamos el voltaje desde aca vamos a tener: $V = V_{R}Z/R$, y remplazando en la formula para potencia activa:

$$
P = VI\cos(\phi) = \frac{V^{2}}{Z} \frac{R}{Z}= \frac{Z^{2}V_{R}^{2}}{R^{2}} \frac{R}{Z^{2}} = \frac{V_{R}^{2}}{R}
$$
Se puede pensar en la potencia activa como la potencia que se disipa en la resistencia.

#### Segundo Termino

El segundo termino de la formula de potencia:

$$
\frac{V_{max}I_{max}}{2} \sin\phi \sin(2\omega t)
$$
![](ZImages/Pasted%20image%2020220701115915.png)

Tendra un valor pico de $\frac{V_{max}I_{max}}{2} \sin\phi$, pero un valor medio de 0, definimos a la magnitud de este termino fluctuante como potencia reactiva $Q= \frac{V_{max}I_{max}}{2} \sin(\phi) = VI\sin(\phi)$.

![](ZImages/Pasted%20image%2020220701114834.png)

definimos a $f_{pr}=\sin(\phi)$ como el factor de potencia reactivo. Sabemos que por el triangulo de potencia $\cos(\phi)= X_{L}/Z$, por lo tanto podemos escribir la potencia reactiva en funcion a la reactancia.

$$
Q = VI \sin\phi = I^{2}Z \frac{X_{L}}{Z} = I^{2}X_{L}
$$
Tambien podemos escribirla en funcion del voltaje en la reactancia, dado que este es $V_{L}=X_{L}I= X_{L}V/Z$ , por lo tanto despejando para $V$ tenemos $V= ZV_{L}/X_{L}$, y substituyendo en la formula de la potencia reactiva:

$$
Q = VI \sin(\phi) = \frac{V^{2}}{Z} \frac{X_{L}}{Z} = \frac{Z^{2}V_{L}^{2}}{X_{L}^{2}} \frac{X_{L}}{Z^{2}} = \frac{V_{L}^{2}}{X_{L}}
$$

#### Finalizacion Del Planteo

Si seguimos el desarrollo de la ecuación:

$$
p(t) = {V_{max}I_{max}\cos(\phi)}\sin^{2}(\omega t)+
\frac{V_{max}I_{max}}{2} \sin\phi \sin(2\omega t)
$$
haciendo uso de la propiedad trigonometrica $\sin^{2}(a)= (1-\cos(2a))/2$:

$$
p(t) = \frac{V_{max}I_{max}}{2} \cos\phi- \frac{V_{max}I_{max}}{2} \cos(\phi)\cos(2\omega t)+\frac{V_{max}I_{max}}{2} \sin(\phi) \sin(\omega t)
$$

si tomamos los valores eficaces y aplicamos la propiedad asociativa en los terminos fluctuantes quedamos con:

$$
p(t)= VI\cos(\phi) - VI[\cos(2\omega t)\cos\phi - \sin(2\omega t)\sin(\phi)]
$$
y aplicando la propiedad trigonometrica $\cos(a+b)=\cos(a)\cos(b)-\sin(a)\sin(b)$ quedamos con:

$$
p(t) = VI\cos(\phi) - VI\cos(2\omega t+\phi)
$$
lo que podemos ver graficamente como:

![](ZImages/Pasted%20image%2020220701121439.png)

En las partes positiva de $p(t)$ el generador entrega energía a la resistencia que la disipa y al inductor que la almacena en forma de campos magnéticos y en las negativas el inductor le devuelve su energía al generador

## Potencia instantánea En RC En CA

### Planteo Con Frecuencia

Dado un circuito serie RL con una fuente alterna.

con un voltaje $u(t)= \sqrt2 U \sin(\omega t+\phi_{u})$ el cual pasamos al dominio de frecuencia, donde aplicamos la ley de kirchhoff de los voltajes para encontrar:

$$
\bar U = \bar U \angle \phi_{u}= R\bar I - j \frac{\bar{I}}{\omega C}
$$
de donde usando el triangulo de donde sacamos la corriente por el factor comun:

$$
U\angle \phi_{u} = \bar I \left(R- \frac{j}{\omega C} \right)
$$
y si representamos esta impedancia en el dominio fasorial, (usando el triangulo de impedancias, y definiendo el angulo como negativo y para abajo), quedamos con:

$$
\bar Z = \sqrt{R^{2}+ \frac{1}{\omega^{2}C^{2}}} \angle-\phi
$$
por lo tanto la ecuacion nos queda:

$$
\begin{align*}
 U \angle \phi_{u} &= \bar I |Z| \angle-\phi\\
\frac{U\angle\phi_{u}}{\sqrt{R^{2}+ \frac{1}{\omega^{2}C^{2}}}\angle-\phi} &=  \bar I\\
\bar I&= \sqrt 2  \frac{U}{\sqrt{R^{2}+ \frac{1}{\omega^{2}C^{2}}}}\angle\phi_{u}+\phi
\end{align*}
$$
desde donde sacamos el valor eficaz de corriente y el angulo de la corriente igualando la fase y el modulo de ambos lados de la ecuacion.

Con estos datos calculamos la potencia instantanea en el dominio del tiempo como:

$$
p(t) = \sqrt{2}V\cos(\omega t+\phi_{v})\sqrt{2}I \cos(\omega t+\phi_{v}+\phi)
$$
y si tomamos como referencia el voltaje entonces $\phi_{v}=0$, y quedamos con:

$$
p(t) = 2V\cos(\omega t)I\cos(\omega t+\phi)
$$
y desarrollando esto usando la identidad trigonometrica esa:

$$
\begin{align*}
p(t) &= 2VI \frac{\cos(2\omega t+\phi)+\cos\phi}{2}\\
&= 2VI \cos\phi +2 VI \cos(2\omega t+\phi)
\end{align*}
$$
donde este segundo podemos expandir el termino fluctuante usando
$\cos(a+b) = \cos(a)\cos(b)-\sin(a)\sin(b)$ y quedamos con:

$$
\begin{align*}
p(t)&= VI\cos(\phi)+ VI (\cos\phi \cos(2\omega t)-\sin\phi\sin(2\omega t))\\
&= \underbrace{VI\cos(\phi)}_{P} (1+\cos(2\omega t))- \underbrace{VI\sin(\phi)}_{Q} \sin(2\omega t)\\
&= P(1+\cos(2\omega t))- Q\sin(2\omega t)
\end{align*}
$$
Podemos ver que la potencia instantanea queda compuesta por dos partes, una fluctuante (la potencia aparente $S$) con magnitud igual a $VI$ y una parte constante en el tiempo la cual es la potencia media con el mismo valor que la potencia activa $P = IV\cos(\phi)$ por lo que podemos ver la potencia en el tiempo como:

![](ZImages/Pasted%20image%2020220715114012.png)

ademas podemos dibujar el triangulo de potencias escribiendo la potencia aparente con sus componente reactiva y activa:

a partir de donde podemos ver que la potencia reactiva viene de la reactancia y que la parte activa viene de la resistencia, usando el triangulo de impedancia vemos que:

$$
\begin{align*}
R &= |Z| \cos\phi & X&=|Z|\sin\phi\\
P &= |S| \cos\phi & Q&=|S|\sin\phi\\
 &= |V||I| \cos\phi & &= |V||I| \sin\phi\\
 &= |I^{2}||Z|\cos\phi & &= |I^{2}||Z| \sin\phi=|I^{2}|X\\
 &= |I^{2}|R & &= -|I^{2}| X_{C}
\end{align*}
$$

teniendo en cuenta que $X=X_{L}-X_{C}$ y en este caso $X_L =0$.

### Derivacion Del Apunte

Partiendo de un circuito inductivo del tipo:

![](ZImages/Pasted%20image%2020220705095407.png)

Donde circula una corriente de la forma $i(t)= I_{max}\sin(\omega t)$, y un voltaje de la forma $v(t)=V_{max}\sin(\omega t-\phi)$, donde podemos encontrar la magnitud de la corriente desde el voltaje y la impedancia como:

$$
I_{max} = \frac{V_{max}}{\sqrt{R^{2}+ \frac{1}{\omega^{2}R^{2}}}}
$$
y el angulo $\phi$ desde la relacion entre la resistencia y impedancia:

$$
\phi = \tan^{-1}\left(\frac{-X_{c}}{R}\right)
$$
por lo tanto la potencia sera:

$$
\begin{align*}
p(t) &= v(t)i(t)\\
&= V_{max}I_{max}\sin(\omega t)\sin(\omega t-\phi)\\
&= V_{max}I_{max}\sin(\omega t)(\sin \omega t \cos\phi - \cos\omega t \sin\phi)\\
&= V_{max}I_{max}(\sin^{2}\omega t\cos \phi - \sin\omega t\cos\omega t \sin \phi)\\
&= V_{max}I_{max}\left(\sin^{2}\omega t\cos\phi - \frac{\sin(2\omega t)}{2} \sin\phi\right)
\end{align*}
$$
Donde el primer termino: $V_{max}I_{max}\sin^{2}\omega t \cos\phi$ es igual al encontrado en el circuito $RL$, y representa la potencia activa que se disipa en la resisitencia.

El segundo termino es similar al que vimos en $RL$ pero cambiado de signo, por lo que este representa la potencia reactiva que maneja el capacitor.

Si seguimos desarrollando podemos ver que al usar la propiedad trigonometrica: $\sin^{2}(a)= (1-\cos(2a))/2$, nos queda:

$$
p(t) = \frac{V_{max}I_{max}}{2} \cos\phi (1-\cos(2\omega t))- \frac{V_{max}I_{max}}{2} \sin\phi \sin2\omega t
$$
y substituyendo por las deficiones de potencia activa y reactiva quedamos con:

$$
p(t) = P (1-\cos(2\omega t))- Q\sin2\omega t
$$
Si tomamos los valores eficaces $V = V_{max}/\sqrt2$ y $I=I_{max}/\sqrt{2}$ , entonces expandiendo y aplicando la propiedad trigonometrica de suma de cosenos $\cos(a+b)=\cos(a)\cos(b)-\sin(a)\sin(b)$ quedamos con:

$$
\begin{align*}
p(t) &= VI \cos\phi - VI[\cos(\phi)\cos(2\omega t)+\sin(\phi)\sin(2\omega t)]\\
&= VI\cos(\phi)- \cos(2\omega t-\phi)
\end{align*}
$$
lo que podemos representar graficamente como:

![](ZImages/Pasted%20image%2020220715113825.png)



En las partes positiva de $p(t)$ el generador entrega energía a la resistencia que la disipa y al capacitor que la almacena en forma de campos eléctricos y en las negativas el capacitor le devuelve su energía al generador

## Potencia instantánea En Circuito RLC En CA

En el caso de tener un circuito de la forma:
![](ZImages/Pasted%20image%2020220705102459.png)

Donde circulara una corriente de la forma $i(t) = I_{max}\sin(\omega t)$ con un voltaje $v(t)=V_{max}\sin(\omega t+\phi)$, Podremos encontrar la magnitud de esta corriente como la razon entre la magnitud del voltaje y la de la impedancia:

$$
I_{max} = \frac{V_{max}}{\sqrt{R^{2}+X^{2}}}
$$
donde $X = X_{L}-X_{C} = \omega L- 1/\omega C$ , y el angulo $\phi$ estara dado por:

$$
\phi = \tan^{-1} \left(\frac{X}{R}\right)
$$
Desde esto podemos deducir que cuando $\phi$ sea positivo, tendremos $\omega L > 1/\omega C$ y el circuito se comportara como un $RL$, mientras que si $\phi$ es negativo, tendremos $\omega L< 1/\omega C$ y el circuito se comportara como un $RC$.

Calcularemos la potencia una vez mas como:

$$
\begin{align*}
p(t) &= v(t)i(t)\\
&= V_{max}I_{max}\sin(\omega t)\sin(\omega t+\phi)\\
&= V_{max}I_{max}\sin(\omega t)(\sin \omega t \cos\phi + \cos\omega t \sin\phi)\\
&= V_{max}I_{max}(\sin^{2}\omega t\cos \phi + \sin\omega t\cos\omega t \sin \phi)\\
&= V_{max}I_{max}\left(\sin^{2}\omega t\cos\phi + \frac{\sin(2\omega t)}{2} \sin\phi\right)
\end{align*}
$$
Donde el primer termino: $V_{max}I_{max}\sin^{2}\omega t \cos\phi$ , tendra 
llegara a su valor maximo en $V_{max}I_{max}\cos(\phi)$, y tendra un valor medio de $V_{max}I_{max}\cos(\phi)/2$ , yrepresenta la potencia activa que se disipa en la resisitencia.

la magnitud de este primer termino oscilante, la definimos como la potencia activa $P= \frac{1}{2} V_{max}I_{max}\cos(\phi)= VI\cos(\phi)$.

Tambien podemos encontrar esta potencia activa desde la impedancia como:

$$
P = \frac{V^{2}}{Z} \cos(\phi) = I^{2}Z\cos(\phi)  
$$

  

ademas dado que sabemos que el factor potencia es $fp=\cos(\phi)$, y esto se puede encontrar en el triangulo de impedancias como la relacion entre los lados del triangulo:

![](file:///home/bbruno/Documents/NOtes/Notes/ZImages/Pasted%20image%2020220701114834.png?lastModify=1657025532)

Entonces podemos decir que $\cos(\phi)= R/Z$, y por lo tanto substituyendo tenemos:

$$
\begin{align*} P = VI\cos(\phi) &= I^{2}Z \frac{R}{Z}=I^{2}R\\ \end{align*}  
$$

y si pensamos en el voltaje que pasa por la resistencia este seria $V_{R}=RI= R\ V/Z$, por lo tanto si despejamos el voltaje desde aca vamos a tener: $V = V_{R}Z/R$, y remplazando en la formula para potencia activa:

$$
P = VI\cos(\phi) = \frac{V^{2}}{Z} \frac{R}{Z}= \frac{Z^{2}V_{R}^{2}}{R^{2}} \frac{R}{Z^{2}} = \frac{V_{R}^{2}}{R}  
$$


Se puede pensar en la potencia activa como la potencia que se disipa en la resistencia.

El segundo termino:

$$
\frac{V_{max}I_{max}}{2} \sin\phi \sin(2\omega t)
$$
tendra un valor pico de $\frac{V_{max}I_{max}}{2} \sin\phi$, y un valor medio de $0$, vamos a definir la magnitud de este termino fluctuante como la potencia reactiva:

$$
Q = \frac{V_{max}I_{max}}{2} \sin\phi =VI\sin\phi
$$
Como el seno de angulos entre $0$ y $-90°$ es negativo, podemos ver que en caso de circuitos capacitivos donde el angulo estara en ese rango vamos a tener potencia reactiva negativa.

definimos a $f_{pr}=\sin(\phi)$ como el factor de potencia reactivo. Sabemos que por el triangulo de potencia $\cos(\phi)= X/Z$, por lo tanto podemos escribir la potencia reactiva en funcion a la reactancia.

$$
Q = VI \sin\phi = I^{2}Z \frac{X_{L}}{Z} = I^{2}X_{L}  
$$

Tambien podemos escribirla en funcion del voltaje en la reactancia, dado que este es $V_{X}=XI= XV/Z$, por lo tanto despejando para $V$ tenemos $V= ZV_{X}/X$, y substituyendo en la formula de la potencia reactiva:

$$
Q = VI \sin(\phi) = \frac{V^{2}}{Z} \frac{X}{Z} = \frac{Z^{2}V_{X}^{2}}{X^{2}} \frac{X}{Z^{2}} = \frac{V_{X}^{2}}{X}
$$
por lo tanto podemos ver a la potencia reactiva como la potencia involucrada en el intercambio de energia almacenada por el capacitor en forma de campos electricos y por el inductor en forma de campos magneticos.

!![](ZImages/Pasted%20image%2020220715114740.png)

## Potencia Aparente

Partiendo de la ecuacion para potencia instantanea:

$$
p(t) = VI \cos(\phi)+ VI\cos(2\omega t-\phi)
$$

Desarrollando el termino fluctuante $VI\cos(\omega t -\phi)$ quedamos con:

$$
\begin{align*}
S =VI \cos(\omega t -\phi) &= VI (\cos(\phi)\cos(2\omega t)+\sin(\phi)\sin(2\omega t))\\
&= \underbrace{VI\cos(\phi)}_{P} \cos(2\omega t)+ \underbrace{VI\sin(\phi)}_{Q}\sin(2\omega t)
\end{align*}
$$

donde $P$ es la **Potencia Activa** y $Q$ es la **Potencia Reactiva**, descompusimos la potencia fluctuante en dos terminos, el de potencia activa con pulsacion $2\omega$ y el de potencia reactiva el cual esta retrasado $90°$ respecto al anterior y tambien es de pulsacion $2\omega$.

Al producto $VI$ resultante de la amplitud de la potencia fluctuante queda llamado como **Potencia Aparente**:

$$
\begin{align*}
S &= VI=\sqrt{P^{2}+Q^{2}}\\
P &= S\cos(\phi)\\
Q &= S\sin(\phi)
\end{align*}
$$

![](ZImages/Pasted%20image%2020220705104746.png)

La potencia aparente puede tambien ser encontrada como:

$$
\begin{align*}
S = VI && S=IZ I =I^{2}Z&& S=V \frac{V}{Z}= \frac{V^{2}}{Z}
\end{align*}
$$

Es importante destacar que las expresiones son modulares (no 
complejas). Por convenio, se consideran los ángulos r positivos para cargas inductivas y negativos para las capacitivas, esto no afecta la potencia activa ya que $\cos(x)=\cos(-x)$ pero es necesario dar signo a las potencias reactivas, las cuales seran positivas para cargas inductivas y negativas para cargas capacitivas.

## Triangulo De Potencia

Partiendo de la ecuacion para potencia instantanea:

$$
p(t) = VI \cos(\phi)+ VI\cos(2\omega t-\phi)  
$$

  

Desarrollando el termino fluctuante $VI\cos(\omega t -\phi)$ quedamos con:

$$
\begin{align*} S =VI \cos(\omega t -\phi) &= VI (\cos(\phi)\cos(2\omega t)+\sin(\phi)\sin(2\omega t))\\ &= \underbrace{VI\cos(\phi)}_{P} \cos(2\omega t)+ \underbrace{VI\sin(\phi)}_{Q}\sin(2\omega t) \end{align*}  
$$

donde P es la **Potencia Activa** y Q es la **Potencia Reactiva**, descompusimos la potencia fluctuante en dos terminos normales, el de potencia activa con pulsacion $2\omega$ y el de potencia reactiva el cual esta retrasado 90° respecto al anterior y tambien es de pulsacion $2\omega$, podemos representar 
esto en forma de un Triangulo de potencias:

![](ZImages/Pasted%20image%2020220705105738.png)
al cual tambien podemos llegar desde el triangulo de impedancia:

![](ZImages/Pasted%20image%2020220705105712.png)

Esto tambien se puede representar mediante un numero complejo al igual que $\vec Z$. $\vec S = P+jQ=P+j(Q_{L}-Q_{C})=I^{2}R+jI^{2}X= S\angle\phi$.

![](ZImages/Pasted%20image%2020220705105917.png)

donde:

$$
\begin{align*}
S = \sqrt{P^{2}+Q^{2}} &&\text{y}&& \phi = \tan^{-1}\left(\frac{Q}{P}\right)
\end{align*}
$$

### Potencia Compleja

Podremos tambien pensar en la deduccion de la potencia compleja de la siguiente manera:

Dado un voltaje $\vec V = Ve^{j(\theta+\phi)}$ y una corriente $\vec I = I e^{j\theta}$, enconces encontramos la potencia compleja como:

$$
\begin{align*}
\vec S &= \vec V\vec I^{*}\\
&= Ve^{j\phi+\theta} I e^{-j\theta}\\
&= VI e^{j\phi}\\
&= P +jQ\\
&= I^{2}R+j I^{2}X
\end{align*}
$$

## Corrección Del Factor De Potencia

### Con Fasores

Recordando la definicion de factor de potencia:

$$
fp = \cos(\phi) = \frac{P}{S }
$$
a mayor factor de potencia:
- menor intensidad de corriente en la linea de alimentacion
- menor potencia reactiva
- menores perdidas por efecto joule
- menores tensiones necesarias en la generacion

La mayoria de los consumidores requieren reactancia inductiva por lo que por lo general para corregir el factor de potencia se conecta una reactancia capacitiva en paralelo.

![](ZImages/Pasted%20image%2020220306102822.png)

Dibujamos el triangulo de potencias, teniendo en cuenta que la potencia reactiva actual es $Q$, pero queremos agregar $Q_{C}$ para reducir $Q$ a $Q_{T}$, y a su vez cambia el modulo $S$ a $S_{T}$.

![](ZImages/Pasted%20image%2020220306102926.png)

La potencia total va a estar compuesta por la parte inductiva y capacitiva, $Q_{T}= Q_{C}+Q$. la corriente de la carga estara atrazada un angulo $\phi$ respecto a la tension tomada como referencia ya que el circuito es inductivo.

Ese angulo sera reducido a  $\phi'$ cuando agreguemos el elemento capacitivo.

![](ZImages/Pasted%20image%2020220306103148.png)

$$
\begin{align*}
V = V\angle 0 && I_{L}=I_L \angle-\phi && I_{C}= \frac{V}{Z}= \frac{V\angle 0}{-j} C\omega = VC\omega\angle90 = I_{C}\angle 90°
\end{align*}
$$
por ley de Kirchhoff de las corrientes podemos ver que la corriente total es igual a la corriente de la carga inductiva mas la corriente del elemento capacitivo:

$$
I_{T}= I_{L}+ I_{C} \implies I_{T}\angle \phi' = I_{L}\angle-\phi +I_{C}\angle90° 
$$
pasando a coordenadas cartesianas:

$$
I_{T} (\cos\phi' - j\cos\phi') = I_{L}(\cos\phi-\sin\phi)+jI_{C}
$$
la razon por la que los signos de la parte imaginaria de la corriente total y carga inductiva son negativas es porque son inductivas.

Obtenemos entonces dos ecuaciones, una para la parte real y otra para la parte imaginaria.

$$
\begin{align*}
I_{T}\cos\phi' &= I_{L}\cos\phi\\
-I_{T}\sin\phi' &= -I_{L}\sin\phi + I_{C}
\end{align*}
$$
y como queremos encontrar la corriente capacitiva necesaria para modificar angulo $\phi$ a $\phi'$ despejamos para encontrar $I_{C}$:

$$
\begin{align*}
I_{T} &= I_{L} \frac{\cos\phi}{\cos\phi'}\\
I_{C} &= - I_{T} \sin\phi' + I_{L}\sin\phi\\
&= - I_{L}\cos\phi \tan\phi' + I_{L}\sin\phi\\
&= I_{L}\cos\phi(\tan\phi-\tan\phi')
\end{align*}
$$
por lo que teniendo en cuenta que $I_{C}=V\omega C$ podemos calcular la capacitancia necesaria como:

$$
C = \frac{I_{C}}{V\omega}= \frac{I_{L}\cos\phi}{V\omega}(\tan\phi-\tan\phi')
$$

y la potencia reactiva de esta capacitance es:

$$
\begin{align*}
Q_{C} &= Im\{V \cdot I^{*}_{C}\}= Im\{ V\angle 0 \cdot I\angle-90\}=-VI\\
|Q_C| &= V I_{C} = V I_{L} \cos(\tan \varphi-\tan\varphi')\implies P(\tan \varphi-\tan\varphi') = Q_C

\end{align*}
$$

### Metodo Del Apunte

Circuitos normalmente tienen caracteristicas inductivas por lo que por lo general colocaremos cargas capacitivas en paralelo para disminuir el factor de potencia.

![](ZImages/Pasted%20image%2020220705111254.png)

Hacemos esto ya que al corregir el factor de potencia disminuimos $S(S=VI)$ y por lo tanto $I$, entonces disminuimos las perdidas por efecto de Joule en los conductores ($I^{2}R$) y la caida de tension en la linea ($IZ_{L}$).

A partir del triangulo de potencias podemos observar que:

$$
\begin{align*}
Q_{i} =P \tan \phi_{i}&&\text{y que}&& Q_{f}=P\tan\phi_{f}
\end{align*}
$$
por lo tanto dado que $Q_{C}$ es la potencia reactiva que nos lleva de $Q_{i}$ a $Q_{f}$ podemos decir que:

$$
Q_{C}=Q_{i}-Q_{f} = P(\tan \phi_{i}-\tan \phi_f)
$$
Y despejamos la capacitancia necesaria para producir esta potencia reactiva como:

$$
Q_{C}= X_{C}I^{2}_{C}= VI_{C} = \frac{V^{2}}{X_{C}}= V^{2}\omega C
$$
por lo tanto:

$$
\begin{align*}
V^{2}\omega C &= P(\tan \phi_{i}-\tan \phi_{f})\\
C&= \frac{P(\tan \phi_{i}-\tan \phi_{f})}{V^{2}\omega}
\end{align*}
$$

## Calculo De Corriente De Neutro

Considerando un sistema:

![](ZImages/Pasted%20image%2020220412110504.png)

Para estudiar este circuito tomaremos el neutro de la alimentacion como tension de referencia, osea $V_{N}=0$. De este modo se determinara primeramente la tension $V_{N'N}$ que define la tension de neutro del receptor.

Las tensiones de cada carga son iguales respectivamente a:
$$
\begin{align*}
V_{RN'}&=V_{RN}-V_{N'N}\\
V_{SN'}&=V_{SN}-V_{N'N}\\
V_{TN'}&=V_{TN}-V_{N'N}
\end{align*}
$$
de este modo las corrientes de cada linea son el voltaje en la carga sobre la impedancia de la carga:

$$
\begin{align*}
I_{R}&= \frac{V_{RN}-V_{N'N}}{Z_{R}}\\
I_{S}&= \frac{V_{SN}-V_{N'N}}{Z_{T}}\\
I_{T}&= \frac{V_{TN}-V_{N'N}}{Z_{S}}\\
\end{align*}
$$
y en el neutro entonces tendremos la corriente: 

$$
I_{N}= \frac{V_{N'N}}{Z_{N}}
$$
ahora por ley de kirchoff de las corrientes:

$$
\begin{align*}
I_{R}+I_{S}+I_{T}&=I_{N}\\
\frac{V_{RN}-V_{N'N}}{Z_{R}}+\frac{V_{SN}-V_{N'N}}{Z_{S}}+\frac{V_{TN}-V_{N'N}}{Z_{T}} &= \frac{V_{N'N}}{Z_{N}}\\
\frac{V_{RN}}{Z_{R}}+\frac{V_{SN}}{Z_{S}}+\frac{V_{TN}}{Z_{T}} &= V_{N'N} \left(\frac{1}{Z_{N}}+ \frac{1}{Z_{R}}+ \frac{1}{Z_{S}}+ \frac{1}{Z_{T}}\right)\\
\frac{\frac{V_{RN}}{Z_{R}}+\frac{V_{SN}}{Z_{S}}+\frac{V_{TN}}{Z_{T}}}{Y_{R}+Y_{S}+Y_{T}+Y_{N}} &=V_{N'N}\\
\frac{U_{RN}Y_{R}+U_{SN}Y_{S}+U_{TN}Y_{T}}{Y_{R}+Y_{S}+Y_{T}+Y_{N}} &=V_{N'N}
\end{align*}
$$

La tension $V_{N'N}$ es denominada **Tension de desplazamiento del neutro**, y usando este dato podemos volver a las ecuaciones de corriente en cada linea para remplazar y luego sumando las corrientes de linea encontrar la corriente de neutro.

Se puede hacer una interpretacion gemoetrica de los voltajes como:

![](ZImages/Pasted%20image%2020220412111941.png)

se pueden deducir los siguientes casos particulares:

### Carga En Estrella Equilibrada

si las cargas estan equilibradas $Y_{R}=Y_{S}=Y_{T}=Y$, entones la tension en las cargas sera:

$$
V_{N'N} = \frac{Y(V_{RN}+V_{SN}+V_{TN})}{3Y+Y_{N}}=0
$$
ya que al ser la alimentacion simetrica se cumple que $V_{RN}+V_{SN}+V_{TN}=0$.
por lo que coincide el valor de voltaje en los puntos $N$ y $N'$.

### Carga En Estrella Desequilibrada 4 Hilos

en este caso es como vimos antes, determinamos las corrientes de linea y de rotorno por neutro una vez calculada la tension $V_{N'N}$. En el caso particular que se desprecie la impedancia de neutro, osea $Z_{N}=0$, entonces $V_{N'N}=0$, es decir los potenciales de los puntos neutros del generador y receptor seran iguales (unidos por un hilo de impedancia nula $Z_{N}$).

### Carga En Estrella Desequilibrada 3 Hilos

Este caso es cuando no hay conductor neutro en la instalacion, lo que equivale a $Z_{N}=\infty$ o a $Y_{N}=0$. se calcula la tension de neutro de las cargas con la ecuacion deducida para $V_{N'N}$ de desplazamiento de neutro, se determinan las tensiones de linea como $V_{RN'}=V_{RN}-V_{N'N}$ para cada una y se determinan las corrientes de linea, en este caso como no hay un hilo neutro, no habra corriente de retorno por ese hilo.

## Potencia Trifasica

### Con Fasores

Los conceptos de potencia activa, reactiva y aparente se pueden extender a sistemas trifasicos de modo simple:

la potencia instantánea total de una conexion en estrella o triangulo es:

$$
p(t) = p_{1}(t)+ p_{2}(t)+ p_{3}(t) = \sum\limits_{k=1}^{3} v_{k}(t)i_{k}(t)
$$
esta potencia es la misma sea que este en triangulo o estrella ya que en triangulo:

$$
\begin{align*}
V_{f}= \frac{V_{l}}{\sqrt3} && I_{f}=I_{l}\\
&P=3I_{f}V_{f}= \frac{3}{\sqrt 3}I_{l}V_{l}
\end{align*}
$$

Mientras que en estrella:

$$
\begin{align*}
V_{f}=V_{l} && I_{f}= \frac{I_{l}}{\sqrt3}\\
&P=3I_{f}V_{f}= \frac{3}{\sqrt3}I_{l}V_{l}
\end{align*}
$$

de modo análogo la potencia activa o media total es:

$$
P =\sum\limits_{k=1}^{3} V_{k}I_{k}\cos\phi_{k}
$$
donde $V$ y $I$ son los módulos de voltaje y corriente eficaces respectivamente.

de forma similar la potencia reactiva es:

$$
Q = \sum\limits_{k=1}^{3}V_{k}I_{k}\sin\phi_{k}
$$
y la potencia aparente estara dada por:

$$
S = \sqrt{P^{2}+Q^{2}}
$$

es mas facil de comprender usando potencia compleja, por ejemplo supone que los fasores de tension son dados por:

$$
\begin{align*}
V_{1}=V_{1}\angle \alpha && V_{2}=V_{2}\angle \beta && V_{3}=V_{3}\angle\gamma
\end{align*}
$$
con los fasores de corriente simples:

$$
\begin{align*}
I_{1}= I_{1}\angle(\alpha - \phi_{1}) &&
I_{2}= I_{2}\angle(\beta - \phi_{2}) &&
I_{3}= I_{3}\angle(\gamma - \phi_{3})
\end{align*}
$$
la potencia compleja de una fase viene dada por  $\bar S_{F}= \bar U_{F} \bar I_{F}^{*}$.

por lo tanto corresponde a una potencia compleja total:

$$
\bar S = \sum\limits_{k=1}^{3} V_{k}I_{k}^{*}
$$
y si se tiene en cuenta cada componente esto nos deja con:

$$
\begin{align*}
\bar S =& 
(V_{1}I_{1}\cos\phi_{1}+jV_{1}I_{1}\sin\phi_{1})+
(V_{2}I_{2}\cos\phi_{2}+jV_{2}I_{2}\sin\phi_{2})
\\&+
(V_{3}I_{3}\cos\phi_{3}+jV_{3}I_{3}\sin\phi_{3})

\end{align*}
$$
o como:

$$
\bar S = \sum\limits_{k=1}^{3} V_{k}I_{k}\cos\phi_{k}+j\sum\limits_{k=1}^{3}V_{k}I_{k}\sin\phi_{k}
$$
y usando la definicion de potencia activa y reactiva esto queda como:

$$
\bar S = P+jQ
$$

#### En Sistemas Trifasicos Equilibrados (y simetrico)

Considerando que tenemos las tensiones:

$$
\begin{align*}
u_{1}(t)&=\sqrt2 V_{F}\cos\omega t\\
u_{2}(t)&=\sqrt2 V_{F}\cos(\omega t-120°)\\
u_{3}(t)&=\sqrt2 V_{F}\cos(\omega t+120°)
\end{align*}
$$
y sean las corrientes de la forma:

$$
\begin{align*}
i_{1}(t) &= \sqrt2 I_{F}\cos(\omega t-\phi)\\
i_{2}(t) &= \sqrt2 I_{F}\cos(\omega t-120°-\phi)\\
i_{3}(t) &= \sqrt2 I_{F}\cos(\omega t+120°-\phi)
\end{align*}
$$
que corresponden a una carga equilibrada, en le que $\phi$ indica el argumento de la impedancia de cada fase, entonces la potencia total es:

$$
\begin{align*}
p(t) &= \sum\limits_{k=1}^{3}u_{k}(t)i_{k}(t)\\
&= 2V_{F}I_{F}[
\cos(\omega t)\cos(\omega t-\phi)+
\cos(\omega t-120°)\cos(\omega t-120°-\phi)\\
&\ \ \ +
\cos(\omega t+120°)\cos(\omega t+120°-\phi)
]
\end{align*}
$$
y haciendo uso de la propiedad trigonometrica $\cos x\cos y = \frac{1}{2}(\cos(x+y)+ \cos(x-y))$ quedamos con:

$$
p(t) = V_{F}I_{F} (3 \cos\phi+ \cos(2\omega t-\phi)+\cos(2\omega t+120°-\phi)+\cos(2\omega t-120°-\phi))
$$

Y la suma de los ultimos tres terminos representa un sistema equilibrado o simetrico con velocidad $2\omega$ por lo que sus componentes se cancelan en cualquier momento y la suma es 0, lo que nos deja con la potencia instantanea escrita como:

$$
p(t) = 3U_{F}I_{F}\cos\phi
$$
independiente del tiempo, en el caso trifasico equilibrado los terminos sinusoidales de pulsacion $2\omega$ se cancelan entre si, y nos dejan la potencia instantanea constante e igual a la potencia media o activa.

la potencia reactiva sera $Q= 3Q_{fase} = 3V_{F}I_{F}\sin\phi$ y la aparente $S=\sqrt{P^{2}+Q^{2}}=3V_{F}I_{F}$

![](ZImages/Pasted%20image%2020220412101947.png)
![](ZImages/Pasted%20image%2020220412102049.png)

### Deducción Del Apunte

Dada una carga equilibrada con 3 resistencias iguales conectadas en estrella
![](ZImages/Pasted%20image%2020220707095309.png)
donde tenemos:
$$
\begin{align*}
v_{ao}&= V_{max}\cos(\omega t)\\
i_{ao}&= I_{max}\cos(\omega t)\\
v_{bo}&= V_{max}\cos(\omega t- 120°)\\
i_{bo}&= I_{max}\cos(\omega t-120°)\\
v_{co}&= V_{max}\cos(\omega t+ 120°)\\
i_{co}&= I_{max}\cos(\omega t+ 120°)
\end{align*}
$$
sabemos que la potencia total sera 
$$
\begin{align*}
p(t)&= p_{1}(t)+p_{2}(t)+p_{3}(t)\\
&= V_{max}I_{max}\cos^{2}(\omega t)+V_{max}I_{max} \cos^{2}(\omega t-120°)+V_{max}I_{max} \cos^{2}(\omega t+120°)\\
&= V_{max}I_{max}\big(\cos^{2}(\omega t)+(\cos(\omega t)\cos(120°)+\sin(\omega t)\sin(120°))^{2}+ (\cos(\omega t)\cos(120°)-\sin(\omega t)\sin(120°))^{2} \big)
\end{align*}
$$
esto viene de la identidad trigonometrica: $\cos(a+b) = \cos(a)\cos(b)-\sin(a)\sin(b)$
Desarrollando los cuadrados de los binomios, y simplificando teniendo en cuenta que $\cos(120°)=\cos(-120) = -0.5$ y que $\sin(120°)= \sqrt3/2$
por lo tanto quedamos con:
$$
\begin{align*}
p(t) &= V_{max}I_{max}\left(\cos^{2}(\omega t)+ \frac{1}{2^{2}}\cos^{2}(\omega t))+2\cos(\omega t)\sin(\omega t) + \left(\frac{\sqrt3}
{2}\right)^{2}\sin^{2}(\omega t)\right)\\
&\ \ \ \ - V_{max}I_{max} \left(\frac{1}{2^{2}}\cos^{2}(\omega t))-2\cos(\omega t)\sin(\omega t) + \left(\frac{\sqrt3}
{2}\right)^{2}\sin^{2}(\omega t) \right) \\
&= V_{max}I_{max} \left(\cos^{2} \omega t+ \frac{2}{2^{2}} \cos^{2}\omega t+2 \left(\frac{\sqrt3}
{2}\right)^{2}\sin^{2}\omega t \right)\\
&= V_{max}I_{max}\left(\frac{3}{2} \cos^{2}\omega t 
 + \frac{3}{2}\sin^{2}\omega t \right)\\
&= \frac{3}{2} V_{max}I_{max} (\cos^{2}\omega t+\sin^{2}\omega t)= \frac{3}{2}V_{max}I_{max}
\end{align*}
$$
Con voltajes eficientes esto se vuelve $p(t)= 3VI$, esta resolución fue hecha con $\cos(\phi)=1$, es decir $\phi=0$, pero esto también se cumple para cualquier otro tipo de carga, por lo que podemos escribir:

$$
p(t)= 3V_{f}I_{f}\cos(\phi)
$$

En el caso de sistemas monofasicos la potencia instantánea sera pulsante por lo que su ecuación dependiente del tiempo era:
$$
p(t)= VI\cos(\phi)- VI\cos(2\omega t-\phi)
$$

pero en los sistemas trifasicos con cargas equilibradas esta sera constante $p(t)=3V_{f}I_{f}\cos(\phi)$ y esto representa una gran ventaja técnica.

#### Conexion Estrella Desequilibrada:

En este caso las potencias activas y reactivas se calculan sumando escalarmente fase a fase.

$$
\begin{align*}
P &= V_{1N}I_{1}\cos\phi_{1}+V_{2N}I_{2}\cos\phi_{2}+V_{3N}I_{3}\cos\phi_{3}\\
Q &=V_{1N}I_{1}\sin\phi_{1}+V_{2N}I_{2}\sin\phi_{2}+V_{3N}I_{3}\sin\phi_{3} \\
\vec S&= P+jQ= S\angle \phi
\end{align*}
$$

#### Conexion Estrella Equilibrada

$$
\begin{align*}
V_{1N'}&=V_{2N'}=V_{3N'}=V_{f}\\
I_{1}&=I_{2}=I_{3}=I_{f}\\
\cos(\phi_{1}) &= \cos(\phi_{2})=\cos(\phi_{3})=\cos(\phi)
\end{align*}
$$
Y la potencia sera:

$$
P=3V_{f}I_{f}\cos(\phi)
$$

con $I_{f}=I_{l}$ y $V_{f}=V_{l}/\sqrt3$  por lo tanto en términos de los voltajes y corrientes de linea tendremos:

$$
\begin{align*}
P &= \sqrt3 V_{l}I_{l}\cos\phi\\
Q &= \sqrt3 V_{l}I_{l}\sin\phi\\
S &= \sqrt3 V_{l}I_{L}
\end{align*}
$$

#### Triangulo Desequilibrado

$$
\begin{align*}
P &= V_{12}I_{12}\cos\phi_{12}+V_{23}I_{23}\cos\phi_{23}+V_{31}I_{31}\cos\phi_{31}\\
Q &=V_{12}I_{12}\sin\phi_{12}+V_{23}I_{23}\sin\phi_{3}+V_{31}I_{31}\sin\phi_{31} \\
\vec S&= P+jQ= S\angle \phi
\end{align*}
$$

#### Triangulo Equilibrado

$$
\begin{align*}
V_{12}&=V_{23}=V_{31}=V_{f}\\
I_{12}&=I_{23}=I_{31}=I_{f}\\
\cos(\phi_{12}) &= \cos(\phi_{23})=\cos(\phi_{31})=\cos(\phi)
\end{align*}
$$
donde la potencia sera:

$$
P = 3V_{f}I_{f}\cos(\phi)
$$

con $V_{f}=V_{l}$ y con $I_{f}= I_{L}/\sqrt3$ , por lo que las potencias respecto a los voltajes y tensiones de linea seran iguales que en el caso de estrella equilibrado.

## Factor Q

También se lo llama factor calidad, se lo define como $Q_0$ y es representativo de las características energéticas del circuito, este factor es el cociente entre la energía almacenada en el circuito y la disipada por ciclo, normalizado con una constante $2\pi$.
$$
Q_{0}= 2\pi \frac{\text{ Energia maxima almacenada}}{\text{Energia disipada por ciclo}}
$$
Dado que en resonancia la energía máxima almacenada en un inductor es igual a la energía máxima almacenada en un capacitor podemos usar cualquiera de estos para calcular $Q_0$.

### En Un RLC Serie

en este caso la energia instantanea en un inductor sera:
$$
\omega_L (t)= \frac{1}{2} L i_L^2 
$$
y esta sera maxima cuando $i_L$ toma su maximo valor:
$$
\omega_{L}(t) = \frac{1}{2}L I_{L_{max}}^{2}
$$
Conseguimos la energía instantánea dispada en la resistencia integrando sobre la potencia en el resistor:
$$
w_{R}(t) = R \int (i_{R})^{2}dt
$$
 Dado que suponemos una corriente de la forma $i_R = I_{R_max} \cos(\omega_0 t)$, nos queda la siguiente expresión para la corriente cuadrada:
$$
i_{R}^{2} = i_{R_{max}} cos(\omega_{0}t) \cdot i_{R_{max}} \cos(\omega_{0}t) = \frac{i_{R_{max}}}{2}[cos(\omega_{0}t -\omega_{0}t)+  cos(\omega_{0}t+\omega_{0}t)]
$$
Utilizando esto calculamos la energía instantánea disipada como:
$$
W_{R}= R\int_{0}^{T} \left(\frac{I_{R_{max}}^{2}}{2}+ \frac{I_{R_{max}}^{2}}{2} \cos(2\omega t)\right) dt = \frac{1}{2}R (I_{R_{max}})^{2} T
$$
con $T=2\pi/\omega_0$ siendo el periodo de la señal en resonancia.

Luego podemos calcular $Q_0$ desde su definicion como:
$$
Q_0 = \frac{2\pi}{T} \frac{ L (I_{L_{max}})^{2} 1/2}{R (I_{R_{max}})^{2}1/2} = \omega_{0}\frac{L (I_{L_{max}})^{2}}{R (I_{R_{max}})^{2}}
$$
Pero como este es un circuito en serie la corriente que pasa por el inductor va a ser la misma que la que pase por el capacitor, por lo tanto:
$$
Q_0 = \frac{\omega_0 L}{R}
$$
o dado que en resonancia $\omega_0 L = 1/\omega_0 C$ podemos usar esta relacion para escribir el factor de calidad como:
$$
Q_0 = \frac{1}{\omega_0 RC}
$$
En el caso paralelo sera:
$$
Q_0 = \omega_0 RC = \frac{R}{\omega_0 L}
$$

## Curva Universal De Admitancia De Resonancia En Serie

La admitancia de un circuito serie es la inversa de la impedancia:

$$
Y = \frac{1}{R+j\left(\omega L- \frac{1}{\omega C}\right)}
$$
Pero esta ecuacion puede ponerse en forma mas conveniente haciendo cambios en $Z$ antes de calcular $Y$.
Empezamos substituyendo a $C$ por su equivalente en resonancia ($1/L\omega_0^{2}$) .
$$
Z = R + j \left(\omega L - \frac{1}{\omega C}\right) = R + j \left(\omega L - L \frac{\omega_{0}^{2}}{\omega}\right)
$$
Luego se saca de factor comun $\omega_0 L$:
$$
Z = R + j \omega_{0}L \left( \frac{\omega}{\omega_{0}} - \frac{\omega_{0}}{\omega}\right)
$$
y introducimos la **Desintonizacion Fracional** la cual es:
$$
\delta = \frac{\omega-\omega_{0}}{\omega_{0}}
$$
podemos ver que:
$$
1+\delta = \frac{\omega_{0}+\omega-\omega_{0}}{\omega_{0}}= \frac{\omega}{\omega_{0}}
$$
por lo tanto, podemos introducir la en la ecuacion al substituir lo que esta entre parentesis:
$$
\begin{align*}
\frac{\omega}{\omega_{0}} - \frac{\omega_{0}}{\omega} &= \delta +1 - \frac{1}{\delta+1}  = \frac{(\delta+1)^{2}-1}{\delta+1} = \delta \frac{\delta+2}{\delta+1}
\end{align*}
$$
lo que nos deja con:
$$
Z = R + j \omega_{0}L \delta \frac{\delta+2}{\delta+1}
$$
y dado que el factor de calidad es:
$$
Q_0 = \frac{\omega_0L}{R_0} 
$$
Entonces multiplicamos y dividimos por $R_0$ para poder introducir $Q_0$ a la formula:
$$
Z = \left(R \frac{R_{0}}{R_{0}} + j\omega_{0}L 
\frac{R_{0}}{R_{0}} \delta \frac{\delta+2}{\delta+1}\right) = R_{0} \left( \frac{R}{R_{0}} + j Q \delta \frac{\delta+2}{\delta+1}\right)
$$
Y dado que para frecuencias cercanas a resonancia $\delta$ se vuelve pequeña en comparacion a $1$ , y la resistencia puede ser constante respecto a la frecuencia entonces$R \rightarrow R_0$, con esto podemos reducir la ecuacion a:
$$
Z = R_{0} \left( 1 + j 2Q \delta\right)
$$
En resonancia la desintonizacion factorial sera zero.

Podemos ahora calcular $Y$ como $1/Z$:
$$
Y = \frac{Y_{0}}{1+ j2Q\delta}
$$
donde $Y_{0}$ es la admitancia en resonancia, inversa de $R_{0}$, la forma mas util es:

$$
\frac{Y}{Y_{0}}= \frac{1}{1+j2Q_{0}\delta}
$$

la admitancia en resonancia $Y_{0}$ es una conductora pura, es la reciproca de la resistencia del circuito $R_{0}$. para frecuencias arriba o abajo de la resonancia la admitancia es menor.
La agudeza de la cresta depende de $Q_{0}$, a baja perdida alta cresta.

El angulo de admitancia se incrementa desde 0 en resonancia hasta cerca de 90 cuando se pierde la resonancia.

Usando esta formula se forma la curva universal de resonancia,  esta es la misma para todos los circuitos, solo cambia la altura y ancho, para diferentes frecuencias de resonancia y perdida , por lo tanto se puede usar para representar la resonancia en todos los circuitos modificando la escala apropiadamente.

![](ZImages/Pasted%20image%2020220308154725.png)

![](ZImages/Pasted%20image%2020220715101125.png)

Las componentes se encuentran racionalizando la formula:

$$
\frac{Y}{Y_{0}}= \frac{1}{1+j2Q_{0}\delta} = \frac{1-j2Q_{0}\delta}{1+(2Q_{0}\delta)^{2}}
$$

donde la compotente real sera:

$$
Re\left[\frac{Y}{Y_{0}}\right]= \frac{G}{Y_{0}} = \frac{1}{1+(2Q_{0}\delta)^{2}}
$$
La componte imaginaria sera:
$$
Im\left[\frac{Y}{Y_{0}}\right]= \frac{B}{Y_{0}}= \frac{-2Q_{0}\delta}{1+(2Q_{0}\delta)^{2}}
$$
y la magnitud de la admitancia total sera:

$$
\frac{|Y|}{Y_{0}} = \frac{\sqrt{1+(2Q_{0}\delta)^{2}}}{1+(2Q_{0}\delta)^{2}} = \frac{1}{\sqrt{1+(2Q_{0}\delta)^{2}}}
$$
es importante notar que:

- La total tiene maximo en 1
- La imaginaria cruza 0.5 en 0.5 y luego disminuye.
- a $1/\sqrt2$  tenemos la mitad de la potencia y coincide con 0.5 en frequencia.

## Curva Universal De Resonancia En Paralelo

Dado un circuito:
![](ZImages/Pasted%20image%2020220708100055.png)

Sabemos que la admitancia del circuito sera:

$$
Y =G+jB =   \frac{1}{R} + \frac{1}{jX} = \frac{1}{R} + j\left(\omega C- \frac{1}{L\omega}\right)
$$

Podemos expresar la impedancia de un circuito como:
$$
Z = \frac{1}{Y} = \frac{1}{G+jB}= \frac{1}{G+j(\omega C- 1/L\omega)}
$$
donde $G$ es la conductancia y $B$ es la susceptancia. 

pero queremos expresar esto en términos mas convenientes, por lo que vamos a hacer cambios en $Y$ antes de calcular $Z$.

Sabemos que en un circuito resonante RLC en paralelo vamos a tener:

$$
\omega_{0} C = \frac{1}{L\omega_{0}}
$$
por lo tanto podemos substituir $L$ por $1/\omega_{0}^{2}C$ lo que nos dejaria con:

$$
Y = G + j\left(\omega C - \frac{C\omega_{0}^{2}}{\omega}\right)
$$
Luego sacando como factor comun $\omega_{0}C$ quedamos con:
$$
Y = G + j\omega_{0}C \left(\frac{\omega}{\omega_{0}}- \frac{\omega_{0}}{\omega}\right)
$$
Luego introducimos la **Desintonizacion Fracional**:
$$
\delta = \frac{\omega-\omega_{0}}{\omega_{0}}
$$
desde la cual podemos ver que:

$$
1+ \delta = \frac{\omega_{0}-\omega+\omega_{0}}{\omega_{0}}= \frac{\omega}{\omega_{0}}
$$
por lo que podemos remplazar lo que teníamos entre paréntesis por:

$$
\frac{\omega}{\omega_{0}}- \frac{\omega_{0}}{\omega}= 
(1+\delta )- \frac{1}{1+\delta}=
\frac{(1+\delta)^{2}-1}{1+\delta} = \frac{\delta^{2}+2\delta}{\delta + 1} = \delta \frac{\delta+2}{\delta+1}
$$
Lo que nos deja con:

$$
Y = G + j\omega_{0}C\delta \frac{\delta+2}{\delta+1} 
$$
Y dado que el factor de calidad es:
$$
Q_{0}= \omega_{0}R_{0}C= \frac{\omega_{0}C}{G_{0}}
$$
Vamos a multiplicar y dividir por $G_{0}$ para poder introducir $Q_{0}$ a la formula:

$$
Y = G \frac{G_{0}}{G_{0}}+ j\omega_{0}C \frac{G_{0}}{G_{0}} \delta \frac{\delta+2}{\delta+1} = G_{0}\left(\frac{G}{G_{0}}+ jQ\delta \frac{\delta+2}{\delta+1} \right)
$$
y dado que en resonancia la desintonizacion factorial va a ser 0, para frecuencias cercanas a rasonancia $\delta$ se vuelve muy pequeña en comparacion a 1, y $G\rightarrow G_{0}$ si es independiente de la frecuencia, entonces podemos reducir la ecuacion a:

$$
Y = G_{0}(1+j2Q\delta)
$$

Podemos calcular $Z$ ahora como $1/Y$:

$$
Z = \frac{Z_{0}}{1+j2Q\delta}
$$
donde $Z_{0}$ es la admitancia en resonancia, inversa de $G_{0}$, la forma mas util de escribir esta formula es:

$$
\frac{Z}{Z_{0}} = \frac{1}{1+j2Q_{0}\delta}
$$
la impedancia en resonancia $Z_{0}$ es puramente resistiva $R_{0}$. para frecuencias por sobre o por abajo de la resonancia la impedancia es menor.

El angulo de la impedancia se incrementa desde 0 en resonancia hasta cerca de 90° cuando se pierde la resonancia.


Usando esta formula se forma la curva universal de resonancia, esta es la misma para todos los circuitos, solo cambia la altura y ancho, para diferentes frecuencias de resonancia y perdida , por lo tanto se puede usar para representar la resonancia en todos los circuitos modificando la escala apropiadamente.

![](ZImages/Pasted%20image%2020220715101238.png)

Las componentes se encuentran racionalizando la formula:

$$
\frac{Z}{Z_{0}}= \frac{1}{1+j2Q_{0}\delta} = \frac{1-j2Q_{0}\delta}{1+(2Q_{0}\delta)^{2}}
$$

donde la compotente real sera:

$$
Re\left[\frac{Z}{Z_{0}}\right]= \frac{R}{Z_{0}} = \frac{1}{1+(2Q_{0}\delta)^{2}}
$$
La componte imaginaria sera:
$$
Im\left[\frac{Z}{Z_{0}}\right]= \frac{X}{Z_{0}}= \frac{-2Q_{0}\delta}{1+(2Q_{0}\delta)^{2}}
$$
y la magnitud de la impedancia total sera:

$$
\frac{|Z|}{Z_{0}} = \frac{\sqrt{1+(2Q_{0}\delta)^{2}}}{1+(2Q_{0}\delta)^{2}} = \frac{1}{\sqrt{1+(2Q_{0}\delta)^{2}}}
$$
es importante notar que:
-   La total tiene maximo en 1
-   La imaginaria cruza 0.5 en 0.5 y luego disminuye. 
-   a $1/\sqrt2$ tenemos la mitad de la potencia y coincide con 0.5 en frecuencia.

## Diagrama Fasorial En Serie

En un circuito RLC en serie podemos ver la impedancia como:
$$
Z = R + j\left(\omega L - \frac{1}{\omega C}\right)
$$
donde podemos ver que la reactancia inductiva sera positiva mientras que la reactancia capacitiva es negativa.

es entonces evidente que va a haber una frecuencia $\omega_0$ a la cual vamos a llamar de resonancia donde las reactancias capacitivas e inductivas sean iguales y opuestas, por lo que la total sera 0, a esto llamamos resonancia.

La impedancia $Z$ de un circuito $RLC$ en serie puede observarse como una representación gráfica de la magnitud del voltaje en funcion de la frecuencia, porque en el diagrama de transformadas $I$ se mantiene constante.

![](ZImages/Pasted%20image%2020220708110319.png)

donde $f_{0}$ es la frecuencia de resonancia.

## Diagrama Fasorial En Paralelo

Dado un circuito en paralelo:
![](ZImages/Pasted%20image%2020220708111612.png)
la expresión para la admitancia se escribirá como:

$$
Y = G + j\left(\omega C- \frac{1}{\omega L}\right)
$$
donde vemos que la susceptancia capcitiva es positiva y la susceptancia inductiva es negativa.

en resonancia tendremos el valor de $\omega_0$ que hace que las susceptancias sean iguales y opuestas, dejando la total en 0.

podemos visualizar en un diagrama donde observaremos las corrientes resultantes de aplicar un voltaje a un circuito resonante en paralelo, y vemos como $V$ se mantiene constante en el diagrama fasorial:

![](ZImages/Pasted%20image%2020220708112031.png)

podemos encontrar algunas veces que tanto la corriente de $C$ como la de $L$ sean muchas veces mayores que la corriente total en los terminales.

## Sobre Intensidades Y Sobretensiones

### Sobretensiones

dado un circuito RLC en serie el voltaje entre terminales de uno de los elementos individuales del circuito resonante puede ser muchas veces mayor que el voltaje aplicado, esto se puede ver en el diagrama fasorial en serie.

En resonancia la impedancia de entrada del circuito resonante es $R$ por lo que si la corriente es $I$ el voltaje terminal sera $V=RI$.
Pero el voltaje entre los terminales de la inductancia sola es $j\omega L I$, lo cual en resonancia es $j\omega_0 LI$, y como sabemos que $Q_{0}= \omega_{0}L/R$, entonces podemos introducir el factor de calidad como $\omega L = R Q_{0}$, lo que nos deja con el voltaje entre terminales de la inductancia expresado como:
$$
V_{L}=j\omega_{0}L I = jQ_{0}RI=jQ_{0}V
$$
esto significa que el voltaje en la inductancia sera en resonancia $Q_{0}$ veces mayor que el voltaje terminal aplicado, y estará adelantado 90°.

El voltaje entre los terminales de la capacitancia también sera varias veces el voltaje aplicado si la $Q$ del circuito es alta.
En resonancia el voltaje entre los terminales de la capacitancia sera igual y opuesto al de los terminales de la inductancia, por lo tanto:
$$
V_{C}= -jQ_{0}V
$$

### Sobreintensidades O Sobrecorrientes

Dado un circuito $RLC$ en paralelo, la corriente que pase por uno de los elementos puede ser mucho mayor a la corriente total, esto puede ser visto en el diagrama fasorial en paralelo.

En resonancia la admitancia de entrada del circuito es $G=1/R$ por lo que si el voltaje aplicado es $V$, la corriente total sera $I=GV$.
Pero la corriente que circula solo por el capacitor sera $j\omega C V$, y en resonancia sera $j\omega_{0}CV$, y como sabemos que el factor de calidad en paralelo es $Q_{0}= C\omega_{0}/G$ podemos introducirlo a nuestra formula para la corriente como $Q_{0}G=\omega_{0}C$:
$$
I_{C}= j\omega_{0}C V = jQ_{0}G V = jQ_{0}I
$$
por lo que podemos decir que la corriente que circula por la capacitancia sera $Q_{0}$ veces mayor a la corriente total del circuito, y estara adelantada $90°$.

La corriente en el elemento inductivo también sera varias veces mayor al voltaje aplicado si la $Q$ del circuito es alta. En resonancia la corriente que circule por el inductor sera igual y opuesta a la que circula por la capacitancia, por lo tanto:
$$
I_{L} = -jQ_{0}I
$$

## Parametros $y, z$, Y $abcd$

### Definicion De Cuadripolo

un cuadripolo es un set de elementos electricos con 4 terminales de acceso, o dos puertos, los cuales son accesibles desde el exterior de tal forma que en cada par la corriente que entra por uno sale por el otro.

![image-20220710110134845](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710110134845.png)

### Planteo De Ecuaciones

Para plantear las relaciones entre las 4 variables observables vamos a suponer que tenemos un cuadripolo pasivo (sin fuentes en su interior) de $n$ mallas:

![image-20220710110452780](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710110452780.png)

Analizamos este circuito por el metodo de mallas, donde vamos a usar la siguiente simbologia:

- $Z_{ii}$ es la suma de impedancias en la malla $i$ 
- $Z_{ij}$ es la suma de impedancias comunes entre $i$ y $j$
- $E_i$ es la suma de las f.e.ms en la malla $i$

Lo que nos deja con el sistema de ecuaciones $V=ZI$:
$$
\begin{align*}
E_{1} &= Z_{11}I_{1}+ Z_{12}I_{2}+\cdots+Z_{1n}I_{n} \\
E_{2} &= Z_{21}I_{1}+ Z_{22}I_{2}+\cdots+Z_{2n}I_{n} \\
\vdots   \ \   &= \ \ \  \ \vdots \space \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ddots \ \  \ \ \ \ \ \ \ \ \  \ \ \ \ \vdots\\
E_{n}&= Z_{n1}I_{1}+ Z_{n2}I_{2}+\cdots+Z_{nn}I_{n}
\end{align*}
$$
como este es un sistema de $n$ ecuaciones con $n$ incógnitas, si aplicamos la restricción de que que no hallas fuentes independientes dentro:
$$
E_3 =E_4 =\cdots = E_n = 0
$$
Y la restriccion que las mallas $1$ y $2$ asomen al exterior:
$$
\begin{align*}
E_{1}=V_{1}&&E_{2}=V_{2}
\end{align*}
$$
Entonces el sistema queda:
$$
\begin{align*}
V_{1} &= Z_{11}I_{1}+ Z_{12}I_{2}+\cdots+Z_{1n}I_{n} \\
V_{2} &= Z_{21}I_{1}+ Z_{22}I_{2}+\cdots+Z_{2n}I_{n} \\
0 &= Z_{31}I_{1}+ Z_{32}I_{2}+\cdots+Z_{3n}I_{n} \\
\vdots   \ \   &= \ \ \  \ \vdots \space \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ddots \ \  \ \ \ \ \ \ \ \ \  \ \ \ \ \vdots\\
0&= Z_{n1}I_{1}+ Z_{n2}I_{2}+\cdots+Z_{nn}I_{n}
\end{align*}
$$
Desde donde podemos resolver con regla de Cramer como:
$$
I_{1} = 
\frac{\left|\begin{matrix}
V_{1} & Z_{12} & Z_{13} & \cdots & Z_{1n} \\ 
V_{2} & Z_{22} & Z_{23} & \cdots & Z_{2n} \\
0     & Z_{32} & Z_{33} & \cdots & Z_{3n} \\
\vdots &  & \ddots &  & \vdots \\ 
0     & Z_{n2} & Z_{n3} & \cdots & Z_{nn}
\end{matrix}\right|}{\left|\begin{matrix}
Z_{11} & Z_{12} & Z_{13} & \cdots & Z_{1n} \\ 
Z_{21} & Z_{22} & Z_{23} & \cdots & Z_{2n} \\
Z_{31}     & Z_{32} & Z_{33} & \cdots & Z_{3n} \\
\vdots &  & \ddots &  & \vdots \\ 
Z_{n1}     & Z_{n2} & Z_{n3} & \cdots & Z_{nn}
\end{matrix}\right|
}
= V_{1} \frac{\Delta_{11}}{\Delta}+ V_{2} \frac{\Delta_{21}}{\Delta}
$$
donde $\Delta$ es el determinante de la matriz $Z$, $\Delta_{12}$ es el cofactor del elemento de la 2da fila y 1era columna, mientras que $\Delta_{11}$ es el cofactor del primer elemento de la primera fila, el resto de los elementos de la primer columna son nulos.

Análogamente si substituimos $V$ en la segunda columna y resolviendo por Cramer para la segunda columna hubiésemos conseguido:
$$
I_2 = V_1 \frac{\Delta_{12}}{\Delta} + V_2 \frac{\Delta_{22}}{\Delta}
$$
Y dado que el determinante va a tener la dimensión de $Z^n$ y el cofactor la dimension de $Z^{n-1}$ entonces cada una de estas razones multiplicando los voltajes en los terminales tendran la dimencion de $1/Z=Y$ de admitancia:
$$
\begin{align*}
\frac{\Delta_{11}}{\Delta} = y_{11} && \frac{\Delta_{12}}{\Delta} = y_{21} && \frac{\Delta_{21}}{\Delta} = y_{12} &&
\frac{\Delta_{22}}{\Delta} = y_{22}
\end{align*}
$$
 por lo que podemos escribir las ecuaciones para las corrientes como:
$$
\begin{align*}
I_{1}&= y_{11}V_{1}+y_{12}V_{2}\\
I_{2} &= y_{21}V_{1}+ y_{22}V_{2}
\end{align*}
\implies 
\begin{bmatrix}I_{1} \\ I_{2}\end{bmatrix}
=\underbrace{\begin{bmatrix}y_{11} & y_{12} \\ y_{21} & y_{22}\end{bmatrix}}_Y
\begin{bmatrix}V_1 \\ V_{2}\end{bmatrix}
$$
donde a la matriz $Y$ la llamamos matriz admitancia del cuadripolo, y esta esta compuesta por los **parametros** $y_{11}, y_{12}, y_{21}$ y $y_{22}$, y en base a estos parametros podemos obtener las corrientes en funcion de las tensiones.

### Tipos De Parametros

 De manera analoga al ejemplo hecho, se pueden obtener 6 juegos de parametros, desde las relaciones entre $V_1, I_1, V_2$ y $I_2$, estos son:

![image-20220710114413919](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710114413919.png)

Entre estos, cualquier juego de parametros puede ser obtenidos en funcion de los otros 5.

### Obtension De Parametros

Estos parametros se pueden obtener de dos formas:

- Por calculo, conociendo las componentes del cuadripolo
- Por ensayo, midiendo las tensiones y corrientes en los puertos

Para la medicion por calculo se deben obtener los parametros $Y$ a partir de las ecuaciones:
$$
\begin{align*}
I_{1}&= y_{11}V_{1}+y_{12}V_{2}\\
I_{2} &= y_{21}V_{1}+ y_{22}V_{2}
\end{align*}
$$
Donde vamos a calcular las impedancias haciendo 0, los voltajes en cada terminal, es con cada terminal en corto, ya que:
$$
\begin{align*}
y_{11} = \left. \frac{I_{1}}{V_{1}} \right|_{V_{2}=0} &&
y_{12} = \left. \frac{I_{1}}{V_{2}} \right|_{V_{1}=0} &&
y_{21} = \left. \frac{I_{2}}{V_{1}} \right|_{V_{2}=0} &&
y_{22} = \left. \frac{I_{2}}{V_{2}} \right|_{V_{1}=0}
\end{align*}
$$

#### Ejemplo

![image-20220710115528673](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710115528673.png)

Dejando el segundo terminal en corto podemos encontrar $y_{11}$ y $y_{21}$:

![image-20220710115620287](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710115620287.png)

Vamos a ver que como $Y_1$ y $Y_2$ forman un paralelo por el que circula $I_1$ entonces:
$$
\begin{align*}
y_{11} = \left. \frac{I_{1}}{V_{1}} \right|_{V_{2}=0}=Y_1+Y_2 

\end{align*}
$$
Y como no circula corriente por $Y_3$ la corriente que pasa por $Y_2$ sera $-I_2=V_1 Y_2$ por lo tanto:
$$
y_{21} = \left. \frac{I_{2}}{V_{1}} \right|_{V_{2}=0}=-Y_2
$$
 Dejando en corto el otro terminal conseguimos $y_{22}$ y $y_{12}$:

![image-20220710120329760](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710120329760.png)

donde terminamos con:
$$
y_{22} = \left. \frac{I_{2}}{V_{2}} \right|_{V_{1}=0}=Y_2+Y_3 
$$
y con:
$$
y_{12} = \left. \frac{I_{1}}{V_{2}} \right|_{V_{1}=0}=-Y_2 
$$

#### Por Ensayo

Por ensayo para calcular cada parámetro se debe crear la condición que corresponde y medir las dos magnitudes que intervienen en su cálculo.

Una de las dos magnitudes $I$ o $V$ sera proporcionada por una fuente, y la otra debe ser medida, por ejemplo para encontrar el parámetro $y_{11}$ se debe cortocircuitar el puerto de salida, y medir la corriente y tensión en la entrada:
$$
y_{11} = \left. \frac{I_{1}}{V_{1}} \right|_{V_{2}=0}
$$
si es que trabajamos con magnitudes fasoriales, los fasores $I_1$ y $V_1$ van a ser definidos cada uno por un modulo y angulo de fase. por esto el parámetro terminara siendo un numero complejo:
$$
y_{11} = \left. \left|\frac{I_{1}}{V_{1}}\right| \right|_{\phi_i -\phi_v}
$$

## Impedancia Imagen

Primero definimos impedancia de entrada y impedancia de salida

### Impedancia De Entrada

Esta es el cociente entre el voltaje y la corriente de entrada.

Teniendo en cuenta que los parametros de transmicion son:
$$
\begin{align*}
V_{1}&= A V_{2}+ B I_{2}\\
I_{1}&= C V_{2}+ D I_{2}
\end{align*}
$$
entonces podemos escribir la impedancia de entrada como función de los parámetros de la red, haciendo el cociente entre estas dos funciones de parametros, y luego dividiendo denominador y numerador por $I_2$ para introducir la impedancia de carga $V_2/I_2$ nos queda:
$$
Z_{1} = \frac{V_{1}}{I_{1}}= \frac{A V_{2}+BI_{2}}{CV_{2}+DI_{2}} = \frac{A\frac{V_{2}}{I_{2}}+B}{C \frac{V_{2}}{I_{2}}+D} = \frac{AZ_{c}+B}{CZ_{c}+D}
$$

### Impedancia De Salida

Esta esta dada por el voltaje y corriente que ingresa al puerto de salida.

Teniendo en cuenta que los parametros de trasmision inversa son:
$$
\begin{align*}
V_{2}&= A' V_{1}+ B' I_{1}\\
I_{2}&= C' V_{1}+ D' I_{1}
\end{align*}
$$
Entonces podemos escribir la impedancia de salida como función de los parámetros de la red, haciendo el cociente entre estas dos funciones de parametros y luego multiplicando numerador y denominador por la impedancia de entrada:
$$
Z_2 = \frac{V_2}{-I_2} = \frac{A'V_1 +B'I_1}{-C'V_1 -D'}=  \frac{A' \frac{V_{1}}{I_{1}}+B'}{-C' \frac{V_1}{I_{1}}-D'}
$$
y como para un cuadripolo pasivo $A'=D$, $D'=A$, $B'=-B$ y $C'=-C$ entonces:
$$
Z_{2} = \frac{DV_{1}-BI_{1}}{CV_{1}-AI_{1}}= \frac{DZ_{1}-B}{CZ_{1}-A}
$$

### Impedancias De Entrada Y Salida En Corto O Abiertas

en caso de tener un corto en el terminal de salida $V_2=0$, recordamos que los parametros de impedancia y admitancia eran:
$$
\begin{align*}
V_{1}= Z_{11}I_{1}+ Z_{12}I_{2}
&& I_{1}=Y_{11}V_{1}+Y_{12}V_{2}
\\
V_{2}= Z_{21}I_{1}+Z_{22}I_{2} &&
I_{2}= Y_{21}V_{1}+Y_{22}V_{2}
\end{align*}
$$
por lo tanto podemos ver que con $V_2=0$ obtenemos, la admitancia como $y_{11} =I_1/V_1$,  lo que es equivalente a lo que conseguimos sibstituyendo en la ecuacion para la impedancia de entrada:
$$
Z_{1C} = \left.{\frac{AV_{2}+BI_{2}}{CV_{2}+DI_{2}}}\right|_{V_{2}=0} = \frac{B}{D}= \frac{1}{y_{11}}
$$
y en caso de tener un circuito abierto en el terminal de salida $I_2=0$, recordamos que con $I_2=0$ podiamos conseguir la impedancia $z_{11} = V_1/I_1$, lo que es lo mismo a lo que conseguimos substituyendo en nuestra formula de impedancia de entrada:
$$
Z_{1V} = \left.{\frac{AV_{2}+BI_{2}}{CV_{2}+DI_{2}}}\right|_{I_{2}=0} = \frac{A}{C}= z_{11}
$$
Lo mismo pasa con las salidas pero con el otro terminal:

$$
\begin{align*}
Z_{2V} &= \frac{D}{C}= z_{22}\\
Z_{2C}&= \frac{B}{A} = \frac{1}{y_{22}}
\end{align*}
$$

Y dado que en cuadripolos simétricos $y_{11} = y_{22}$ and $z_{11}=z_{22}$, We get: $Z_{1V}=Z_{2V}$ and $Z_{1C}=Z_{2C}$ .

### Impedancia Imagen

Cuando un generador esta vinculado a la carga $Z_c$ por medio de una red con influencia no despresiable, esta red se puede pensar como un cuadripolo, generalmente simetrico.

![image-20220710142648989](/home/bbruno/snap/typora/57/.config/Typora/typora-user-images/image-20220710142648989.png)

si la impedancia de entrada fuera igual a la impedancia de carga, el generador seguiria viendo el mismo valor de impedancia en sus bornes, y estariamos entonces en la condicion de maxima transferencia de potencia ($Z_g = Z_c^*$) con el cuadripolo insertado entre el generador y la carga, pero si no hubiera cuadripolo la transferencia seria mayor.

sabemos que la impedancia de entrada es:
$$
Z_1 =\frac{AZ_{c}+B}{CZ_{c}+D}
$$
 Proponemos que la **Impedancia imagen** es el valor de impedancia para cuando la impedancia de entrada sea igual a la impedancia de la carga:
$$
Z_0  = \frac{AZ_{0}+B}{CZ_{0}+D}
$$
 Despejamos $Z_0$ y quedamos con una cuadratica:
$$
C Z_{0}^{2}+(D-A) Z_{0}- B = 0
$$
por lo tanto:
$$
Z_{0} = \frac{-(D-A)\pm\sqrt{(D-A)^{2}+4BC}}{2C}
$$
y dado que es una red simetrica, vamos a tener $A=D$:
$$
Z_{0}= \sqrt{\frac{B}{C}} 
$$
y si tenemos en cuenta las impedancias de entrada y salida de corte y en vacio:
$$
\begin{align*}
Z_{1V} = \frac{B}{D}&& Z_{1C}= \frac{A}{C}&&
Z_{2V}= \frac{D}{C} && Z_{2C}= \frac{B}{A}
\end{align*}
$$
Junto con la simetria $A=D$, entonces notamos que el producto de ambas impedancias de entrada es igual al producto de ambas impedancias de salida:
$$
\begin{align*}
z_{1V}z_{1C} = \frac{B}{D} \frac{A}{C}= \frac{B}{C}\\
z_{2V}z_{2C} = \frac{D}{C} \frac{B}{A} = \frac{B}{C}
\end{align*}
$$
por lo que podemos finalmente escribir la impedancia imagen tambien como:
$$
Z_{0}= \sqrt{z_{1V}z_{1C}}=\sqrt{z_{2V}z_{2C}}
$$

## Relacion Tension, Corriente, Potencia Y Impedancia Imagen

> No se, No he encontrado de que trata esto

# Corrientes Poliarmonicas

Dado un voltaje cuya magnitud en el tiempo sea $x(t)=X_{m}\sin(\omega t+\phi)$ esta informacion se puede representar en el dominio temporal como:

![](ZImages/Pasted%20image%2020220710175856.png)

En el dominio frecuencial.

En caso de tener señales mas complejas, utilizando series de fourier podemos describirlas en dominio de frecuencia enterminos de su magnitud y fase:

$$
X(t) = x(0)+ \sum\limits_{n=1}^{\infty} |x_{nm}|\sin(n\omega t+\theta_n)
$$

![](ZImages/Pasted%20image%2020220710175929.png)

cada $\omega$ es la pulsacion de la componente sinusoidal de menor frecuencia, a esta la llamamos primera armonica.

Los demas valores de pulsacion se muestran en los espectros discontinuos multiplos enteros de $\omega$.
Si tenemos muchas señales llamadas poliarmonicas, se descompone en componentes de amplitud y frecuencia.
Si la señal tiene alto periodo, el intervalo entre las frecuencias se hace mas chico, cuando $T \rightarrow \infty$ se tendra un espectro continuo.

Para obtener la respuesta permanente en un circuito con lineal con un generador que provee una señal poliarmonica, se aplicara el siguiente metodo:

Primero se descompone la poliarmonica con fourier:

$$
V(t) = V_{0}+ \sum\limits_{n=1}^{\infty} |V_{m_n}|\sin(\omega n t+\theta_{n})
$$
$$
V(t) = V_{0}+ V_{m_1}\sin(\omega t+\theta_{1})+\cdots +V_{m_n}\sin(n\omega t+\theta_{n})
$$
lo que se puede ver como:
$$
V(t) = V_{0}+V_{1}(t)+V_{2}(t)+\cdots V_{n}(t)
$$
de acuerdo a esta expresion la señal de la fuente no sinusoidal esta representada por la suma de tension continua y sinusoidales de distintas frecuencias y amplitudes. Por lo tanto se puede remplazar por una conexión en serie de generadores de tension continua y aplicamos superposicion debido a la linealidad de la carga:

![](ZImages/Pasted%20image%2020220710180010.png)

y podemos ver la respuesta de este circuito como la suma de las respuestas individuales causadas por cada uno de los generadores actuando por su cuenta

![](ZImages/Pasted%20image%2020220710180041.png)


Dejandonos con fuentes cada una del tipo:

$$
V_{n}(t) = V_{m}\sin(n\omega t+\phi_{i})
$$

por lo que se podra aplicar el metodo fasorial a cada una, y llegar asi a la corrientes del tipo:

$$
\bar I_{n} = \frac{\bar V_{n}}{\bar Z_{n}}
$$
llegando a si a respuestas temporales asociadas a cada generador:
$$
i_{n}(t) = |I| \sin(n\omega t+\phi_{i})
$$
donde la respuesta temporal correspondiente a la excitacion poliarmonica sera:
$$
i(t) = I_{0}+i_{1}(t)+i_{2}(t)+\cdots+i_{n}(t)
$$

> Falta potencia de poli-armonica, valor eficaz, y simetria
