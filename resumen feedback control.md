# Sistemas de Control

[TOC]

## Transfer Function and Impulse-Response Function

Un sistema linear de una single input con single output, [Linear time invariant (LTI)](000%20Notes/Linear%20and%20Time%20Invariance%20(LTI)%20Systems.md) system is completely described by a linear differential equation with constant coefficients:

$$
a_{n} \frac{d^ny}{dt^n} + \cdots + a_{1} \frac{dy(t)}{dt}+ a_{0} y(t) = b_{m} \frac{d^mx(t)}{dt^m} + \cdots + b_{1} \frac{dx(t)}{dt} + b_{0} x(t)
$$
the coefficients $a_{i}$, $b_{j}$ are constants. y suponiendo que las condiciones iniciales son $\hspace{0pt}0$, aplicar la transformada de Laplace nos da:

$$
a_{n}s^n Y(s)+ a_{n-1}s^{n-1} Y(s)+ \cdots + a_{0} Y(s) = b_{m}s^m X(s) + b_{m-1}s^{m-1} X(s)+ \cdots +b_{0}X(s)
$$
por lo tanto podemos sacar $Y(s)$ $y$ $X(s)$ como factor comun y escribir la relacion como una **funcion de transferencia**:

$$
G(s) = \frac{Y(s)}{X(s)} = \frac{{b_{m}s^m+b_{m-1}s^{m-1}+\cdots+b_{0}}}{ a_{n}s^n+ a_{n-1}s^{n-1}+ \cdots + a_{0}}
$$
la función de transferencia nos da el ratio de la transformada de Laplace de la salida en relación con la entrada, dado que las condiciones iniciales sean 0.

el polinomio del denominador de la funcion de transferencia es llamado **polinomio caracteristico**, mientras que la **ecuacion caracteristica** del sistema es formada cuando asumimos que el polinomio característico es igual a $\hspace{0pt}0$. 
Propiedades del sistema tales coo la estabilidad o el comportamiento del sistema pueden ser examinados estudiando el polinomio caracteristica, podemos vera funcion de transferencia como:

$$
G(s) = \frac{k(s+z_{1})(s+z_{2})\dots (s+z_{m})}{(s+p_{1})(s+p_{2})\dots(s+p_{n})}
$$
las raices del polinomio del numerador $z_{1},\dots,z_{m}$ son llamadas **zeros** $y$ las raices del polinomio del denominador $p_{1}, \dots, p_{n}$ son llamados polos, y $k$ es la ganancia constante, la cual es siempre un numero real.

### Integral De Convolucion

para un sistema linear invariante del tiempo la funcion de transferencia es:

$$
G(s) = \frac{Y(s)}{X(s)}
$$
por lo tanto la salida puede ser escrita como:

$$
Y(s)=G(s)X(s)
$$
y ya sabemos que la multiplicacion en el dominio complejo es lo mismo que la convolucion en el dominio del tiempo, por lo tanto la salida es dada por:

$$
\begin{align}
y(t) &= \int _{0}^t x(\tau) g(t-\tau)\, d\tau \\
&= \int _{0}^t g(t)x(t-\tau) \, dx 
\end{align}
$$
donde $g(t)$ y $x(t)$ son $\hspace{0pt}0$ para $t<0$, debido a las condiciones iniciales.

### Diagramas De Bloques

un diagrama de bloques es la representacion grafica de la conexion entre subsistemas que forma un sistema. es una representacion de las funciones cumplidas por cada componente y del flujo de las señales.

![](https://i.imgur.com/YtfsX6U.png)

el diagrama de bloques de un sistema no es unico y puede haber multiples diagramas de bloques representando el mismo sistema.

para conectar estos bloques se pueden utilizar **puntos sumadores** los cuales indican una operacion de suma o resta.

![](https://i.imgur.com/nX94otA.png)

Tambien tenemos puntos de rama, desde los cuales la salida de una señal se alimenta a otros bloques o puntos sumadores:

![](https://i.imgur.com/NnDtbQF.png)

cuando la salida es retroalimentada al punto sumador es necesario convertir la forma de la señal de salida a la misma que la de la señal de entrada.

ejemplo: digamos que tenemos un controlador de temperatura, entonces la salida va a ser la temperatura controlada, pero no podemos simplemente alimentarle una temperatura a esto, le tenemos que alimentar un voltaje, por lo tanto hace falta convertir esa temperatura de salida en un voltaje antes de retroalimentarlo a la entrada.

Esta conversion es hecha por un elemento de retroalimentacion con una funcion de transferencia $H(s)$.

![](https://i.imgur.com/GqphV2l.png)

Aca tenemos un sistema de lazo cerrado donde tenemos una entrada de referencia $R(s)$, una salida $C(s)$ y una retroalimentacion $B(s)$, la cual estara definida por la funcion de retroaliementacion y la salida, es decir $B(s) = H(s)C(s)$, $y$ un error proveniente de la comparacion entre la referencia y $B$, $E(s)$.

En este diagrama tambien podemos observar la *funcion de transferencia de lazo abierto*, la cual es es:

$$
\text{Open-loop transfer function} = \frac{B(s)}{E(s)} = G(s)H(s)
$$
la señal de retroalimentacion $B(s)$ en relacion de el error de la señal $E(s)$ .

Tambien llamamos a la relacion entre la salida $C(s)$ y el error de la señal $E(s)$ como *funcion de transferencia de propagacion*:
$$
\text{Feedfoward transfer function} = \frac{C(s)}{E(s)} = G(s)
$$
si la funcion de transferencia de feedback es $\hspace{0pt}1$ entonces las funciones de trasferencia de propagacion $y$ de open loop son las mismas.

vemos que la salida es:
$$
C(s) = G(s)E(s)
$$
pero el error esta dado por la diferencia entre la referencia y la retroalimentacion, por lo tanto es:
$$
\begin{align}
E(s) & = R(s) - B(s) \\
 & = R(s) - H(s)C(s) 
\end{align}
$$
por lo tanto la salida entonces sera:
$$
C(s) = G(s)[R(s)- H(s)C(s)]
$$
pero queremos tener la funcion de transferencia que nos relacione la entrada $R(s)$ con la salida $C(s)$, por lo tanto tenemos que despejar:
$$
\begin{align}
C(s) &= G(s)R(s) - H(s)C(s)G(s) \\
C(s)+ H(s)C(s)G(s) & = G(s)R(s) \\
1 + H(s)G(s) &= G(s) \frac{R(s)}{C(s)} \\
\frac{1+H(s)G(s)}{G(s)} &= \frac{R(s)}{C(s)} \\
\frac{C(s)}{R(s)} & = \frac{G(s)}{1+H(s)G(s)}
\end{align}
$$
Y esta función de transferencia es la que llamamos *funcion de transferencia de lazo cerrado* y nos da la salida en función de la entrada:
$$
C(s) = \frac{G(s)}{1+H(s)G(s)} R(s)
$$

### Reduccion De Diagrama De Bloques

Dado un diagrama de bloques la manera en la que se opera es la siguiente:

si tenemos bloques en serie, entonces se estan multiplicando las funciones de transferencia, lo que corresponde a una convolucion en dominio del tiempo:

![](https://i.imgur.com/WQN2Bmr.png)
pasa a ser:
![](https://i.imgur.com/tH29XzC.png)

si tenemos ramas en paralelo sin feedback concluyendo en un punto sumador entonces:
![](https://i.imgur.com/GaevWfF.png)
podemos representar esto como la suma de las funciones de transferencia:
![](https://i.imgur.com/dhC3Fxe.png)

si tenemos feedback entonces aplicamos la *funcion de transferencia de lazo cerrado* para representar ese subsistema.
![](https://i.imgur.com/DFzekim.png)
pasa a ser:
![](https://i.imgur.com/dZzQhRG.png)

#### Transformaciones

Hay ciertas transformaciones que podemos utilizar para desplazar bloques y ayudarnos a simplificar estos diagramas:

**mover un punto de suma desde atras de un bloque**
![](https://i.imgur.com/iCQOSTV.png)

**Mover un punto de retroalimentacion enfrente de un bloque**
![](https://i.imgur.com/MQxHvZF.png)

**Mover un punto de retroalimentacion desde atras de un bloque**
![](https://i.imgur.com/tb7g4Fl.png)

**Mover un punto sumador frente a un bloque**
![](https://i.imgur.com/2k7B1zW.png)

### Respuesta Con Multiple Inputs

si tenemos multiples inputs o una disturbacion en el sistema entonces tendremos un sistema:
![](https://i.imgur.com/aoCULa3.png)

y trabajaremos con cada entrada en separado, produciendo $Y_{X}$, $Y_{V}$ y $Y_{R}$, para encontrar $Y_{m}$ graficamos el siguiente diagrama:

![](https://i.imgur.com/WZ4CuXl.png)

el cual nos permite encontrar:
$$
Y_{X} (s) = \frac{G_{1}(s)G_{2}(s)G_{3}(s)}{1+H(s)G_{1}(s)G_{2}(s)G_{3}(s)} X(s)
$$
ahora si queremos encontrar $Y_{V}$ entonces el diagrama observado desde esta entrada es un poco diferente:
![](https://i.imgur.com/1PNaUfY.png)
con lo que observamos que la salida sera:
$$
Y_{V}(s) = \frac{G_{2}(s)G_{3}(s)}{1+H(s)G_{1}(s)G_{2}(s)G_{3}(s)} V(s)
$$
y para $R(s)$ tendremos:
![](https://i.imgur.com/xDzpORm.png)
cuya ecuacion de salida queda como un ejercicio para el lector.

$Y$ finalmente la respuesta a la aplicacion simultanea sera la superposicion de las anteriores:
$$
Y(s) = Y_{X}(s)+Y_{V}(s)+Y_{R}(s)
$$

## Modelado en espacio de estados

The primary disadvantage of the classical approach (using Frecuency domain representation taking the system's [[Transfer Function]] with Laplace) is its limited applicability: It can be applied only to linear, time-invariant systems or systems that can be approximated as such.

The state-space approach can be used to represent nonlinear systems that have backlash, saturation, and dead zone. 

Also multiple systems have multiple inputs and outputs that can be compactly represented in state-space.

The time-domain approach can also be used for the same class of systems modeled by the classical approach.

**Aproach**

1. Select a particular subset of all possible system variables and call them the *state* variables.
2. for a *n*th order system we write $n$ simultaneos, first order diferential equations in terms of state variables. we call this system of simultaneus diferential equations **State Equations**
3. if we know the inital condition of all the states variables at $t_0$ as well as the system input for $t\geq 0$, we can solve the simultaneous DEs for the states variables for $t\geq0$
4. We algebraically combine the state variables with the system's input and find other system variables for $t\geq t_0$, we call this equation the **Output Equation**
5. We consider the state equations and the output equations a viable representation of the system. we call this representation of the system a **State-Space Representation**

**Example**:

Let's say we have the following circuit:

![](https://i.imgur.com/lxVQqb6.png)

We then have:

 $$L \frac{di}{dt}+Ri+ \frac{1}{C}\int i \ dt=v(t)$$

 we can convert this to charge:
$$
L \frac{d^{2}q}{dt^{2}}+R \frac{dq}{dt}+ \frac{1}{C}q = v(t)
$$
Then we turn this into a system of equations:
$$
\frac{d{\bf{q}}}{{dt}} =\begin{pmatrix}\dot q \\ \ddot q \end{pmatrix} = \begin{pmatrix}i \\ \frac{di}{dt}\end{pmatrix} = 
\begin{pmatrix}
0 & 1 \\ -\frac{1}{LC} & \frac{-R}{L}
\end{pmatrix}
\begin{pmatrix} q \\ i\end{pmatrix}
+ \begin{pmatrix}0 \\ \frac{1}{L}\end{pmatrix}v(t)
$$

### General Representation

The **State Equations** are a set of $n$ simultaneous first oredr ODEs with $n$ variables, where the variables to be solved for are the state variables.

$${\bf \dot x = Ax+Bu}$$

where:
- $\bf x$ = state vector
- $\bf \dot x$ = Derivative respect time of state vector
- $\bf u$ = input or control vector
- $\bf A$ = system matrix
- $\bf B$ = Input Matrix

And the **output equation** it's the algebraic equation that expreses the output of the system as a linear combinations fo the state variables and the inputs.

$${\bf y =Cx + Du}$$

where:
- $\bf y$ = Output vector
- $\bf C$ = Output Matrix
- $\bf D$ = Feedfoward matrix

we can also think of this system as the following [Block diagram](Diagramas%20De%20Bloques%20(Control).md)
![](https://i.imgur.com/p5Le9kM.png)

### Applying State-Space Representation.

the first step it's tow select the state vector with the following considerations:

1. A minimum number of state variables must be selected as components of the state vector. and this number must be sufficient to describe completely the state of the system.
2. the components of the state vector must be [[Linear Independence | linearly independent]]. (Variables and their successive derivatives are linearly independent)

The minimun number of variables required equals the order of the differential equation.

 Often state variables are chosen to be physical variables of a system, such as position and velocity in a mechanical system. Cases arise where these variables, although linearly independent, are also **decoupled** .

```ad-Definition
title: System of Decoupled equations

Some linearly independent variables are not needed to solve for any of the other linearly independent variables.

```

Another case that increases the size of the state vector rises when the added variable is not linearly independent of the other members of the state vector. This usually occurs when a variable is selected as a state variable but its dependence on the other state variables is not immediately apparent.


**Example:** damped oscilator

![](https://i.imgur.com/iKgOMen.png)

from this diagram we figure out the equation of motion:

$$
m \ddot{y} +b \dot{y} +ky=u
$$
considering this linear system, the force $u(t)$ is the input to the system and the displacement $y(t)$ of the mass is the output.

this is a second order system, that means that we'll have two integrators, let's define the state variables $x_{1}(t) = y(t)$ and $x_{2}=\dot{y}(t)$, then we'll have:
$$
\begin{align}
x_{1}(t) & =y(t) \\
x_{2}(t) & =\dot{y}(t)
\end{align}
$$
so their derivatives are going to be:
$$
\begin{align}
\dot{x}_{1}(t) & = \dot{y}(t) \\
\dot{x}_{2}(t) & = \ddot{y}(t)
\end{align}
$$
and we can get $\ddot{y}$ from the equations of motion:
$$
\begin{align}
\dot{x}_{1} & = x_{2} \\
\dot{x}_{2} & = \frac{1}{m}(-ky-b\dot{y}) + \frac{1}{m} u
\end{align}
$$
which in terms of $x_{1}$ and $x_{2}$ is:

$$
\begin{align}
\dot{x}_{1} & = x_{2} \\
\dot{x}_{2} & = \frac{1}{m}(-kx_{1}-bx_{2}) + \frac{1}{m} u
\end{align}
$$
which we can frame as:
$$
\begin{bmatrix}
\dot{x}_{1} \\
\dot{x}_{2}
\end{bmatrix}
=
\underbrace{ \begin{bmatrix}
0 & 1 \\
-\frac{k}{m} & - \frac{b}{m}
\end{bmatrix} }_{ A }
\begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}
+
\underbrace{ \begin{bmatrix}
0 \\
\frac{1}{m}
\end{bmatrix} }_{ B }
u
$$
and given that we're only looking at the position we can write the output equation as:
$$
y = \underbrace{ \begin{bmatrix}
1 & 0
\end{bmatrix}}_{ C }
\begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}
$$
and if we were to see this as a block diagram we'd have:

### Correlation Between Transfer Functions and State-Space Equations

if we consider a system whose transfer function is given by:
$$
\frac{Y(s)}{U(s)} = G(s)
$$
this system may be represented in state space by:
$$
\begin{align}
\mathbf{\dot{ x}} & = \mathbf{Ax}+\mathbf{B}u \\
y &= \mathbf{Cx}+Du
\end{align}
$$
then if we applied the Laplace transform to this system we would get:
$$
s \mathbf{X}(s) -\mathbf{AX}(s) = \mathbf{B}U(s)
$$
which is the same as:
$$
(s\mathbf{I}-\mathbf{A})\mathbf{X}(x) = \mathbf{B}U(s)
$$
and by multiplying in the left side by $(s\mathbf{I}-\mathbf{A})^{-1}$, then we get:
$$
\mathbf{X}(s)= (s\mathbf{I}-\mathbf{A})^{-1} \mathbf{B}U(s)
$$
by substituting this into the equation for the measured output $y$ then we have:
$$
Y(s) = [\mathbf{C} (s\mathbf{I}-\mathbf{A})^{-1} \mathbf{B} + D]U(s)
$$
then our transfer function is:
$$
G(s) = \frac{Y(s)}{U(s)} = \mathbf{C} (s\mathbf{I}-\mathbf{A})^{-1} \mathbf{B} + D
$$
so now we have an expression for the transfer function in terms of $A$, $B$, $C$ and $D$, and given that the right hand side has an inverted term this can also be written as:
$$
G(s) = \frac{Q(s)}{|s\mathbf{I}-\mathbf{A}|}
$$
so $|s\mathbf{I}-\mathbf{A}|$ gives us the **characteristic equation**, which means that the [Eigenvalues](000%20Notes/Eigenvalues%20and%20Eigenvectors.md) of $\mathbf{A}$ are the poles of $\mathbf{G}(s)$, which is called the **Transfer Matrix**.

### Linealizacion De Modelos No Lineales

si tenemos un sistema cuyo modelo no lineal esta dado por:
$$
\begin{array}{c}
\dot{x} = f(x,y)\\
\dot{y} = g(x,y)
\end{array}
$$
entonces podemos linearizar este sistema al rededor de un [Punto Fijo](000%20Notes/Fixed%20Points%20and%20Linearization.md) o punto de equilibrio, esto es un punto tal que si el sistema esta ahi, de ahi no se mueve sin una disturbacion externa.

suponiendo que tenemos un punto fijo $(x^{*}, y^{*})$ entonces:

$$f(x^{*}, y^{*}) = 0$$
 $$g(x^{*}, y^{*}) = 0$$
entonces podemos hacer un desplazamiento de nuestro origen a las coordenadas del punto fijo:

$$
u = x - x^{*},\ \ \ \ \ v=y- y^{*}
$$
y ahora tenemos que derivar las ecuaciones diferenciales para nuestras nuevas variables , para esto necesitamos derivar, y como $x^*$ es constante tenemos $\dot{u}=\dot{x}$, por substitucion entonces tenemos:
$$
\dot{u}=f(x^*+u,y^*+v)
$$
y usando [Series de Taylor](000%20Notes/Taylor%20series.md) con la regla de la cadena vemos que:
$$
\dot{u}=f(x^*,y^*)+ u \frac{\partial f}{\partial x}+v \frac{\partial f}{\partial y}+ O(u^2,v^2,uv)
$$
donde $O(u^2,v^2,uv)$ es como representamos los terminos de orden $\hspace{0pt}2$ o mayor los cuales para disturbaciones pequeñas de $u$ y $v$ son minimos.

entonces podemos reescribir el sistema como:

$$
\left(
\begin{array}{c}
\dot{u}\\ \dot{v}
\end{array}
\right)
= 
\left(
\begin{array}{cc}
\frac{\partial f}{\partial x} \frac{\partial f}{\partial y}\\ \frac{\partial g}{\partial x} \frac{\partial g}{\partial y}
\end{array}
\right)
\left(
\begin{array}{c}
u\\ v
\end{array}
\right)
+ \text{Quadratic Terms}
$$
donde la matrix:
$$
A = \left(
\begin{array}{cc}
\frac{\partial f}{\partial x} \frac{\partial f}{\partial y}\\ \frac{\partial g}{\partial x} \frac{\partial g}{\partial y}
\end{array}
\right)
$$
es la matrix [Jacobiana](Jacobian%20Matrix) del punto fijo, y este es el analogo multivariable de $f'(x^*)$.

> El efecto de los esta aproximacion eliminando los terminos quadraticos se puede hacer siempre que el punto fijo no sea un caso limite, esto se puede hacer en los casos robustos, es decir, cuando:
> - ambos eigenvalores tienen una parte real positiva
> - ambos eigenvalores tienen una parte real negativa
> - caundo un eigenvalor es positivo y el otro negativo
> no se puede aplicar cuando:
> - ambos eigenvalores son puros imaginarios
> - en casos cuando un eigenvalor es 0



## Transient and Steady-State Response Analysis

la respuesta de un sistema de control consiste en dos partes, la respuesta transitoria y la de estado estable o permanente.

$$
c(t) = c_{tr}(t)+c_{ss}(t)
$$
diseñando un sistema de control debemos ser capaces de predecir el comportamiento dinámico del sistema desde nuestro conocimiento de los componentes. La característica mas importante del comportamiento de un sistema es la **estabilidad**.

un sistema esta en equilibrio si en caso de cualquier disturbacion la salida se mantiene en el mismo estado, un sistema [LTI](000%20Notes/Linear%20and%20Time%20Invariance%20(LTI)%20Systems.md) es **estable** si la salida eventualmente vuelve a su estado de equilibrio cuando al sistema se le da una condicion inicial.
un sitema es **criticamente estable** si las oscilaciones alrededor del punto de equilibrio duran para siempre, y es **inestable** si la salida diverge sin frontera (bound).

otras características importantes son la estabilidad relativa y el error de estado estable, si la salida en estado estable de un sistema no coincide exactamente con la entrada se dice que el sistema tiene error de estado estable.

### Efecto de Polos y Raices

los **Polos** de una funcion de transferencia son los valores de la variable $s$ que hacen que la funcion de transferencia que tienda a infinito o raices del denominador que sean raices del numerador tambien.

Los **Zeros** de una funcion de transferencia son los valores de la variable $s$ que causan que la funcion de transferencia se vuelva $\hspace{0pt}0$, o que sean raices del numerador y del denominador.

dada una funcion de transferencia:

$$
G(s) = \frac{s+2}{s+5}
$$
podemos obtener las componentes de la respuesta desde los polos y zeros del sistema:

$$
C(s)=\frac{(s+2)}{s(s+5)} = \frac{A}{s} + \frac{B}{s+5}
$$

resolviendo con fracciones parciales:

$$
\begin{align}
A = \left.\frac{s+2}{s+5}\right|_{s\to0} &= \frac{2}{5} \\
B = \left.\frac{s+2}{s}\right|_{s\to-5} &= \frac{3}{5} 
\end{align}
$$
por lo tanto:
$$
C(s)= \frac{2/5}{s} + \frac{3/5}{s+5}
$$
y pasando a dominio del tiempo obtenemos la respuesta:
$$
c(t) = \frac{2}{5} + \frac{3}{5}e^{-5t}
$$

![](https://i.imgur.com/nOz5HdH.png)

El polo de la function de entrada genera la forma de la respuesta forzada, este es el polo en el origen que genera una función escalón en la salida.

el polo de la función de transferencia general la forma de la respuesta natural, la cual se reduce en el tiempo.

el polo en el eje real genera una exponencial de la forma $e^{-\alpha t}$ donde $\alpha$ es la ubicación del polo en el eje real, por lo tanto mientras mas a la izquierda en los números negativos este mas rápido decae a 0.

![](https://i.imgur.com/SNYZ1RD.png)

los zeros y polos definen la amplitud para las respuestas forzada y natural, como podemos ver al calcular $A$ y $B$.

#### Example

si tenemos el sistema:
![](https://i.imgur.com/Qg0sIDJ.png)


la respuesta en el dominio de frecuencia sera:
$$
C(s) = \underbrace{ \frac{K_{1}}{s} }_{ \text{Respuesta Forzada} } + \underbrace{ \frac{K_{2}}{s+2} + \frac{K_{3}}{s+4}+ \frac{K_{4}}{s+5} }_{ \text{Respuesta Natural} }
$$
lo que corresponde a la siguiente respuesta en dominio del tiempo:
$$
c(t) = K_{1}+ K_{2} e^{-2t}+ K_{3}e^{-4t}+ K_{4}e^{-5t}
$$

### Sistemas De Primer Orden

dado un sistema de primer orden:
![](https://i.imgur.com/ZuQ0WTa.png)

si la entrada es una funcion escalon $R(s)=\frac{1}{s}$, la respuesta sera:
$$
C(s)= R(s)G(s) = \frac{a}{s(s+a)}
$$
Taking the inverse transform, la respuesta esta dada por:
$$
c(t) = c_{f}(t) + c_{n}(t) = 1-e^{-at}
$$
donde el polo de la entrada genera la respuesta forzada $c_{f}(t)=1$, y el polo del sistema en $-a$ genera la respuesta natural $c_{n}(t)=-e^{-a t}$

podemos llamar a $\tau =1/a$ la constante de tiempo.

![](https://i.imgur.com/qLnU1UI.png)

llamamos al parametro $a$ la frecuencia exponencial. y como la derivada de $e^{-at}$ es $-a$, cuando $t=0$ la pendiente inicial es dada por $a$.

para un sistema de primer orden general con $G(s) = K/(s+a)$, y la respuesta escalon es:
$$
C(s) = \frac{K}{s(s+a)} = \frac{K/a}{s}- \frac{K/a}{s+a}
$$
si podemos identificar $K$ y $a$ desde mediciones entonces podemos obtener la función de transferencia del sistema, podemos hacer esto midiendo la constante de tiempo, $1/a$ es decir el tiempo que tarda en llegar a la amplitud del 63% del valor final, encontrando $a$ de esa manera.

en cambio podemos identificar $K$ una vez que el sistema llegue al regimen permanente ya que en este el sistema tendra el valor de $K/a$.

#### Respuesta a la Entrada Rampa

si en vez de una entrada escalon le damos una entrada rampa:
![](https://i.imgur.com/VUcrdUu.png)

suponiendo que tenemos el sistema de primer orden:

![](https://i.imgur.com/2oy2hWB.png)

$$
G(s)= \frac{1}{Ts+1} = \frac{1/T}{s+ 1/T}
$$
es igual a nuestra formulacion con $a = \frac{1}{T}$
la respuesta a la entrada rampa sera:
$$
C(s) = \frac{1}{s^2} \frac{1}{Ts+1} = \frac{1}{s^2} - \frac{T}{s} + \frac{T^2}{Ts+1}
$$
lo que nos deja con:
$$
c(t) = t- T + T e^{-t/\tau}
$$
pero al visualizar esto vemos que tenemos un error constante con respecto a la entrada:
![](https://i.imgur.com/bDK2oJR.png)

este error $e(t)$ esta dado por:
$$
\begin{align}
e(t) & = r(t)- c(t) \\
	 & = T(1-e^{-t/T})
\end{align}
$$
y a medida que $t$ se hace infinito, el termino $e^{-t/T}$ se hace $\hspace{0pt}0$ $y$ por lo tanto la señal de error se aproxima a $T$.
$$
e(\infty)=T
$$

#### Respuesta al Impulso

dando un impulso unitario al sistema en dominio de frecuencia esto se traduce a $R(s)= 1$, por lo tanto:
$$
C(s) = R(s)G(s) = \frac{1}{Ts+1}
$$
y la transformada inversa de laplace nos da:
$$
c(t) = \frac{1}{T} e^{-t/T},\ \ \text{para }t\geq 0
$$
por lo tanto la curva de la respuesta sera:
![](https://i.imgur.com/eVXB5xB.png)

> Comparando estas respuestas podemos ver que la respuesta a la derivada de una señal de entrada se puede obtener diferenciando la respuesta del sistema a la entrada original.
> por ejemplo sabemos que la derivada la entrada rampa es la funcion escalon, y dado que la respuesta de la funcion rampa es:
> $$c(t)=t-T+Te^{-t/T}$$
> derivando encontramos:
> $$\frac{d c(t)}{dt} = 1- e^{-t/\tau}$$
> la cual es la respuesta a la funcion escalon.
>
> 
>
> Tambien se puede ver que la respuesta al integral de la entrada es igual a la respuesta integrada del original, esta es una propiedad de sistemas lineales invariantes en el tiempo



# Apendix



## Partial Fractions 

this is a method to separate the poles of a function.

per example given:
$$
\frac{5x-4}{(x-2)(x+1)} = \frac{A}{x-2} + \frac{B}{x+1}
$$
then we need to solve this, to do this we multiply by the denominator of the original function:
$$
5x-4 = A(x+1) + B(x-2)
$$
then we get a system of equations:
$$
\begin{align}
5x & = Ax + Bx \\
-4 & = A -2B
\end{align}
$$
and we solve it to find $A=2$ and $B=3$, allowing us to rewrite our equation with the poles in different terms:
$$
\frac{5x-4}{x^2-x-2} = \frac{2}{x-2} + \frac{3}{x+1}
$$

### Polos Con Exponentes

$$
\frac{1}{(x-2)^3} = \frac{A_{1}}{x-2}+ \frac{A_{2}}{(x-2)^2}+ \frac{A_{2}}{(x-2)^3}
$$

### Polos Cuadraticos

$$
\frac{1}{(x^2+2x+3)^2} = \frac{B_{1}x+C_{1}}{x^2+2x+3} + \frac{B_{2}x+C_{2}}{(x^2+2x+3)^2}
$$
en resumen, para cada polo cuadratico agregar un termino $(Bx+C)/\text{polo}$ y para cada polo normal agregar un termino $A/\text{polo}$, y si un polo esta exponenciado agregar un termino para cada potencia menor o igual al exponente.

