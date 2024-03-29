# Sistemas de Control

[TOC]



> Cualquier Seccion con * probablemente no es necesaria para entender el resto de las cosas

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

### Sistemas De Segundo Orden

Podemos extender estos conceptos de polos y zeros a los sistemas de segundo orden.

mientras que cambios en los parámetros de un sistema de primer orden solo causan cambios en la velocidad de respuesta, en un sistema de segundo orden estos parámetros pueden cambiar la forma de la respuesta.

![](https://i.imgur.com/CRn23bB.png)

En general vamos a tener $\hspace{0pt}4$ tipos de respuestas:
![](https://i.imgur.com/C4o3HZh.png)

**Respuesta Sobreamortiguada**: en este caso tenemos dos polos reales en $-\sigma_{1},-\sigma_{2}$ que nos generan una repuesta natural:
$$
c(t)=K_{1}e^{-\sigma_{1}t}+K_{2}e^{-\sigma_{2}t}
$$
**Respuesta Subamoriguada**: en este caso tenemos dos polos complejos en $-\sigma_{d}\pm j \omega_{d}$
la respuesta natural por lo tanto sera:
$$
c(t) = Ae^{-\sigma_{d} t}\cos(\omega_{d}t-\phi) = B_{1}e^{-\sigma_{d}t}\cos(\omega_{d}t)+B_{2} e^{-\sigma_{d}t}\sin(\omega_{d}t)
$$
**Respuesta no amortiguada**: en este caso tenemos polos imaginarios $\pm j\omega_{1}$
$$
c(t) = A \cos(\omega_{1}t-\phi) = B_{1} \cos(\omega_{1}t)+B_{2}\sin(\omega_{1}t)
$$
**Respuesta criticamente amortiguada**: este este caso ambos polos son reales y iguales $-\sigma_{1}$.

$$
c(t)=K_{1}e^{-\sigma_{1}t}+K_{2} t e^{-\sigma_{1}t}
$$

#### Interpretacion Con Dinamica No Linear*

Podemos también entender cada respuesta al formular esto en dominio del tiempo, ya que funcion de transferencia muestra el efecto de una ecuacion diferencial cuyos eigenvalores son correspondientes a los polos en el dominio de frecuencia, podemos entender el funcionamiento de estas respuestas desde los eigenvalores.

podemos trazar un paralelo con los tipos de sistemas lineales que podemos encontrar con sus respectivos [[https://personal.math.ubc.ca/~israel/m215/nonlin/nonlin.html| phase portrait]], dependiendo del tipo de sistema linear que tengamos, podemos encontrar que tipo de sistema lineal tenemos al analizar la traza y el determinante de su matriz $A$:

![](https://i.imgur.com/kwdmkuz.png)

Otra alternativa es encontrar el tipo de punto fijo mediante sus eigenvalores:
![](https://i.imgur.com/6rpk6kN.png)
![](https://i.imgur.com/zHXAEHo.png)

y considerando que en este sistema de segundo orden tomamos las variables $x$ y $v= \dot{x}$, entonces proyectando en el eje de las $x$ a medida que la trajectoria se desarrolla en el tiempo obtenemos la posicion en cada momento, mientras que projectando en el eje de las $y$ obtenemos la velocidad en cada momento.

#### Forma General De Los Sistemas De Segundo Orden

Para una mejor descripcion del comportamiento necesitamos definir parametros significativos, para esto vamos a establecer dos cantidades llamadas **frecuencia natural** y **coeficiente de amortiguamiento**.

**Frecuencia Natural** $\omega_{n}$: la frecuencia natural de un sistema de segundo orden es la frecuencia de oscilación del sistema sin amortiguacion.

**Coeficiente de Amortiguacion** $\zeta$: queremos describir esta cantidad como una magnitud de la oscilacion amortiguada independientemente de la escala de tiempo, una manera de definir esto es comparando la frecuencia de decaimiento exponencial con la frecuencia natural, por lo tanto definimos esta cantidad como:
$$
\zeta = \frac{\text{Exponential decay frequency}}{\text{Natural Frequency}} = \frac{1}{2\pi} \frac{\text{Natural period(Seconds)}}{\text{Exponential time constant}}
$$
ahora apliquemos estas definiciones a nuestro sistema:
$$
G(s)= \frac{b}{s^2+as+b}
$$
sin damping los polos estarian en los ejes imaginarios, y la respuesta seria una sinusoidal sin amortiguacion, osea los polos serian puramente imaginarios, y para esto tiene que cumplirse que $a=0$ como vimos en el cuadro antes, por lo tanto:
$$
G(s) = \frac{b}{s^2+b}
$$
por definicion entonces la frecuencia natural es la la frecuencia de oscilacion de este sistema, y como los polos de este sistema estan en el eje imaginario esta frecuencia sera $\pm j\sqrt{ b }$
$$
\omega_{n} = \sqrt{ b } \implies b = \omega_{n}^2
$$
y dado que los polos complejos tienen una parte real $\sigma= -a/2$ desde aca podemos calcular el coeficiente de amortiguamiento como:
$$
\zeta = \frac{|\sigma|}{\omega_{n}} = \frac{a/2}{\omega_{n}}
$$
desde donde podemos encontrar:
$$
a = 2\zeta\omega_{n}
$$
Por lo tanto nuestra funcion de transferencia para un sistema general de segundo orden queda como:
$$
G(s) = \frac{\omega_{n}^2}{s^2 + 2\zeta\omega_{n} s+ \omega_{n}^2}
$$
y resolviendo para las raices de la ecuacion caracteristica encontramos los valores de los exponenciales que definen el comportamiento del sistema:

$$
s_{1,2} = -\xi \omega_{n} \pm \omega_{n} \sqrt{ \zeta^2 -1 }
$$

**Ejemplo**: Sistema de Servo, en este sistema nosotros queremos controlar la posicion de salida $c$, en vase del torque producido por el controlador $T$ con ganancia $K$, controlado por la diferencia entre la salida actual y la entrada de referencia $r$:
$$
\begin{align}
J \ddot{c}+B \dot{c} & =T \\
Js^2C(s)+BsC(s) & = T(s)
\end{align}
$$
asi que la funcion de transferencia entre la posicion y el torque es:
$$
\frac{C(s)}{T(s)}= \frac{1}{s(Js+B)}
$$
![](https://i.imgur.com/wocNmLD.png)

Por lo que podemos reducir el diagrama a:
![](https://i.imgur.com/16p6yxb.png)
![](https://i.imgur.com/F56e0ks.png)

y para reducir esto utilizamos la propiedad para reducir systema a uno de lazo abierto, y teninendo en cuenta que en la rama de feedback tenemos $H(s)=1$:
$$
\begin{align}
\frac{C(s)}{R(s)} & = \frac{K / (s^2J+sB)}{ 1+ 1\times K / (s^2J+sB)} \\
  & = \frac{K}{s^2J+sB+K} & \text{multiplicando y dividiendo por } (s^2J+sB) \\
  & = \frac{K / J}{ s + \frac{B}{J} s + K/s}
\end{align}
$$

#### Respuesta a Impulso De Un Sistema De Segundo Orden

##### Subamortiguado

primero encontramos la respuesta general al sistema de segundo orden dado un pulso:
$$
C(s) = \frac{\omega_{n}^2}{s(s^2 + 2 \zeta \omega_{n} s+ \omega_{n}^2)} = \frac{K_{1}}{s} + \frac{K_{2}s+K_{3}}{s^2 + 2\zeta \omega_{n}s+\omega_{n}^2}
$$
donde asumimos que $\zeta < 1$, y al expandir utilizando [partial fractions](partial%20fractions.md) entonces encontramos:
$$
\begin{align}
C(s)&= \frac{1}{s} - \frac{s+2\zeta\omega_{n}}{s^2 +2\zeta\omega_{n}s+\omega_{n}^2} \\
&= \frac{1}{s}- \frac{s+\zeta\omega_{n}}{(s+\zeta\omega_{n})^2+\omega_{d}^2}- \frac{\zeta\omega_{n}}{(s+\zeta\omega_{n})^2+\omega_{d}^2}
\end{align}
$$
donde $\omega_{d}= \omega_{n}\sqrt{ 1-\zeta^2 }$, es la **frecuencia natural amortiguada**.

Y dado que:

| dominio de tiempo | dominio de frecuencia         |
| ----------------- | ----------------------------- |
| $\sin(\omega t)$  | $\frac{\omega}{s^2+\omega^2}$ |
| $\cos(\omega t)$  | $\frac{s}{s^2+\omega^2}$      |

entonces podemos aplicar la transformada inversa de laplace para conseguir la respuesta en el tiempo:
$$
\begin{align}
c(t) &= 1 - e^{-\zeta \omega_{d}t}\left( \cos(\omega_{n}\sqrt{ 1-\zeta^2 }t)+ \frac{\zeta}{\sqrt{ 1-\zeta^2 }}\sin(\omega_{n}\sqrt{1-\zeta^2}t) \right) \\
&= 1 - \frac{e^{-\zeta\omega_{n}t} }{\sqrt{ 1-\zeta^2 }} \sin(\omega_{n }\sqrt{ 1-\zeta^2} t + \phi)
\end{align}
$$
donde $\phi= \tan^{-1} (\zeta/\sqrt{ 1-\zeta^2 })$.

podemos ver entonces que la frecuencia de oscilacion es la frecuencia natural amortiguada $\omega_{d}$, y varia con el coeficiente de amortiguacion $\zeta$.

La señal de error es:
$$
\begin{align}
e(t) & = r(t)-c(t) \\
&= 1 - (1 - \frac{e^{-\zeta\omega_{n}t} }{\sqrt{ 1-\zeta^2 }} \cos(\omega_{n }\sqrt{ 1-\zeta^2} t - \phi) ) \\
&= \frac{e^{-\zeta\omega_{n}t} }{\sqrt{ 1-\zeta^2 }} \cos(\omega_{n }\sqrt{ 1-\zeta^2} t - \phi)
\end{align}
$$
y como podemos ver la señal de error tambien muestra una oscilación amortiguada, por lo que cuando $t=\infty$ el error es inexistente entre la salida $y$ la entrada.

si el coefficiente de amortiguacion $\zeta$ es $\hspace{0pt}0$, entonces la respuesta se vuelve no amortiguada y las oscilaciones continuan indefinidamente.
$$
c(t)= 1- \cos\omega_{n}t
$$
por lo que tambien podemos ver que las oscilaciones en este caso se producirian a la frecuencia natural, y un incremento en $\zeta$ reducirira la frecuencia natural amortiguada, si $\zeta$ es incrementado por sobre la unidad la respuesta se vuelve sobreamortiguada y la respuesta no oscilara.

**Ejemplo**: Continuando con el ejemplo anterior del sistema de servo, tenemos:
$$
\frac{C(s)}{R(s)} = \frac{K}{Js^2+Bs+K}
$$
entonces podemos ver que como vimos antes $\omega_{n}= \sqrt{ b }$, y en este caso el valor en esa posicion es $\frac{K}{J}$ por lo tanto:
$$
\omega_{n}^2 = \frac{K}{J} 
$$
y vimos que $\zeta= \frac{a / 2}{\omega_{n}}$ entonces:
$$
\zeta= \frac{a / 2}{\omega_{n}} = \frac{B / J}{2 \sqrt{ K / J}} = \frac{B}{2 \sqrt{ KJ }} 
$$
Porque recordando la forma standard de los sistemas de segundo orden:
$$
\frac{C(s)}{R(s)} = \frac{\omega_{n}^2}{s^2+2\zeta\omega_{n}s+\omega^2_{n}}
$$

##### Caso Criticamente Amortiguado

en este caso $\zeta=1$, es decir ambos polos son iguales, entonces para un impulso unitario la respuesta sera:
$$
C(s) = \frac{\omega_{n}^2}{(s+\omega_{n}t)^2 s}
$$
al aplicar fracciones parciales y la trasformada inversa de laplace nos deja con:
$$
c(t) = 1 - e^{-\omega_{n}t} (1+\omega_{n}t) 
$$
> Este resultado tambien puede ser obtenido al tomar el limite de la respuesta en el caso subamortiguado cuando $\zeta\to 1$
> $$
> \lim_{ \zeta \to 1 } \frac{\sin(\omega_{d}t)}{\sqrt{ 1-\zeta^2 }} = \lim_{ \zeta \to 1 } \frac{\sin\omega_{n}\sqrt{ 1-\zeta^2}t}{\sqrt{ 1-\zeta^2 }}=\omega_{n} t
> $$
#### Especificaciones En El Dominio Del Tiempo

Podemos visualizar la grafica de las raices y polos a partir de los parametros $\omega_{n}$ y $\zeta$ como:

![](https://i.imgur.com/01DwT5H.png)

donde llamamos a $\sigma_{d}$ la *frecuencia exponencial amortiguada*.

Podemos describir el comportamiento de la respuesta con parametros temporales:
![](https://i.imgur.com/MxPCN5S.png)
donde:
- el *tiempo de subida* es $t_{r} = (\pi-\beta)/ \omega_{d}$
- el *tiempo de retardo* es $t_{d}$
- el *tiempo pico* es $t_{p}$
- la *Sobreelongacion* es $M_{p}= (c(t_{p}) - c(\infty) ) / c(\infty)$ es decir, que porcentaje de la respuesta en regimen permanente es por la que no pasamos de esta en el pico de la respuesta.
- el *tiempo de asentamiento* es dependiendo de la tolerancia permitida $t_{s}=4 /(\zeta\omega_{n})$ o $t_{s}= 3 / (\zeta\omega_{n})$ para el $\hspace{0pt}2\%$ y $5 \%$ respectivamente. 

podemos visualizar los efectos que tiene el desplazamiento de las raices observando las siguientes graficas:

![](https://i.imgur.com/nTPHzht.png)

desplazamientos verticales incrementan la frecuencia amortiguada pero mantienen el mismo marco, desplazamientos horizontales mantienen la misma frecuencia pero mientras mas a la izquierda menor overshoot (sobreelongacion), y el desplazamientos a $\hspace{0pt}45°$ mantienen el mismo sobreelongacion pero varia el marco y la frecuencia.

### Sistemas De Orden Superior

la respuesta de los sistemas de orden superior es la suma de las respuestas de los sistemas de primer y segundo orden.

$$
\frac{C(s)}{R(s)} = \frac{G(s)}{1+G(s)H(s)}
$$
![](https://i.imgur.com/Mi0mTTG.png)

en general $G(s)$ y $H(s)$ estan dados por un cociente de polinomios, por lo tanto:
$$
\begin{align}
G(s) = \frac{p(s)}{q(s)} & & H(s)= \frac{n(s)}{d(s)}
\end{align}
$$
donde cada uno de estos: $p(s)$, $q(s)$, $d(s)$, y $n(s)$ son polinomios, entonces la function de transferencia entre la salida y la entrada es:
$$
\begin{align}
\frac{C(s)}{R(s)} & = \frac{p(s)d(s)}{q(s)d(s)+p(s)n(s)} \\
  & = \frac{b_{0}s^m+b_{1}s^{m-1}+\cdots+b_{m-1}s+b_{m}}{a_{0}s^n+a_{1}s^{n-1}+\cdots + a_{n-1}s+a_{n}}
\end{align}
$$
es nesesario ahora factorizar el denominador, y numerador para encontrar los zeros y polos.

$$
\frac{C(s)}{R(s)} = \frac{K(s+z_{1})(s+z_{2})\cdots (s+z_{m})}{(s+p_{1})(s+p_{2})\cdots (s+p_{n})}
$$
y examinando el comportamiento de este sistema ante un una entrada escalon unitaria, tendremos:
$$
C(s) = \frac{a}{s} + \sum_{i=1}^n \frac{a_{i}}{s+p_{i}}
$$
donde cada $a_{i}$ es el residuo del polo en $s=-p_{i}$.

en el caso que los polos de $C(s)$ consistan de polos reales y pares de polos complejos, entonces los factores consisten de terminos de primer y segundo orden por lo tanto la respuesta sera:
$$
C(s) = \frac{a}{s}+ \sum_{j=1}^q \frac{a_{j}}{s+p_{j}}+ \sum_{k=1}^r \frac{b_{k}(s+\zeta_{k}\omega_{k})+c_{k}\omega_{k}\sqrt{ 1-\zeta^2_{k} }}{s^2+2\zeta_{k}\omega_{k}s+\omega_{k}^2}
$$
y desde esta ultima ecuacion vemos que la respuesta de un sistema de orden mayor esta compuesta de terminos involucrando funciones encontradas en sistemas de primer y segundo orden, la respuesta final en el tiempo sera:
$$
c(t) = a + \sum_{j=1}^q a_{j}e^{-p_{j}t} +\sum_{k=1}^r b_{k}e^{-\zeta_{k}\omega_{k}t}\cos(\omega_{k}\sqrt{ 1-\zeta_{k}^2 } \ t)+
\sum_{k=1}^r c_{k} e^{-\zeta_{k}\omega_{k}t} \sin(\omega_{k}\sqrt{ 1-\zeta_k^2 }\ t)
$$
por lo que es la suma de exponenciales y oscillaciones amortiguadas.

#### Polos Dominantes

Las formulas que vimos antes para calcular los tiempos de subida, bajada, sobrelevacion, etc... ya no son validas para sistemas con mas de dos polos o con zeros, pero no desesperes, bajo ciertas condiciones podemos approximar (como un buen ingeniero) un sistema con mas de dos polos o con zeros como un sistema de segundo orden que tiene solo dos **Polos dominantes** complejos.

Supongamos que tenemos una respuesta:
$$
c(t) = Au(t)+ e^{-\zeta\omega_{n}t}(B \cos\omega_{d}t +C\sin \omega_{d}t) + De^{-\alpha_{r}t}
$$
y tenemos $\hspace{0pt}3$ casos para evaluar:
- Caso $\hspace{0pt}1$: $\alpha_{r}$ no es mucho mas grande que $\zeta \omega_{n}$
- Caso 2: $\alpha_{r}$ es mucho mayor que $\zeta\omega_{n}$
- Caso 3: $\alpha_{r}=\infty$

![](https://i.imgur.com/pDNy1aF.png)

podemos que ver que cuando $\alpha_{r}\gg \zeta\omega_{n}$ (Caso 2), la exponencial pura va a morir mucho mas rapido que la oscilación de segundo orden, podemos razonar entonces que si la exponencial pura decae a un valor insigte para cuando llegamos a la primer sobreelevacion, entonces nuestras formulas para sobreelevacion, y tiempos de subida, etc... siguen siendo validas con cierto error dependiente de que tan lejos este el polo real de los polos dominantes.

### Error De Estado Estable

Errores en un sistema de control pueden ser atribuidos a multiples factores, cambios en la input de referencia.

dado un sistema:
![](https://i.imgur.com/au2MWJU.png)

con función de transferencia:
$$
G(s) = \frac{K(T_{a}s+1)(T_{b}s+1)\cdots (T_{m}s+1)}{s^N (T_{1}s+1)(T_{2}s+1)\cdots (T_{p}s+1)}
$$
podemos ver que incluye un termino $s^N$ este representa la multiplicidad($N$) del polo 0, esto el numero de veces que el polo se repite, usando este numero definimos el tipo del sistema, a medida que aumentamos esta multiplicidad el sistema se hace mas preciso, sin embargo a la vez complica el problema de la estabilidad.

para calcular el error de estado estable de este sistema primero analizamos la función de transferencia entre la salida y la entrada:
$$
\frac{C(s)}{R(s)} = \frac{G(s)}{1+G(s)}
$$
la función de transferencia entre la señal de error $e(t)$ y la señal de entrada $r(t)$, teniendo en cuenta que la señal de error es la diferencia entre la entrada y la salida, es:
$$
\begin{align}
E(s) & = R(s)-C(s) \\

\frac{E(s)}{R(s)} & = 1- \frac{C(s)}{R(s)} = \frac{1}{1+G(s)}
\end{align}
$$
el valor final nos da una forma conveniente de encontrar el error de estado estable:
$$
E(s) = \frac{1}{1+G(s)} R(s)
$$
el error de estado estable es entonces:
$$
e_{ss}(t) = \lim_{ t \to \infty }e(t) = \lim_{ s \to 0 } sE(s) = \lim_{ s \to 0 } \frac{sR(s)}{1+G(s)} 
$$

#### Para Un Sistema Con Input Escalon Unitaria

$$
e_{ss} = \lim_{ s \to 0 } \frac{s}{1+G(s)} \frac{1}{s} = \frac{1}{1+G(0)}
$$
Entonces la error de posicion estatica constante $K_{p}$ esta dada por:
$$
K_{p} = \lim_{ s \to 0 } G(s) = G(0)
$$
y el error de estado estable en terminos del error constante sera:
$$
e_{ss} = \frac{1}{1+K_{p}}
$$
para un sistema de tipo $\hspace{0pt}0$, es decir multiplicidad $\hspace{0pt}0$ en el polo $\hspace{0pt}0$, tenemos:
$$
K_{p} = \lim_{ s \to 0 } \frac{K (T_{a}s+1)(T_{b}s+1)\cdots}{(T_{1}s+1)(T_{2}s+1)\cdots} = K
$$
para un sistema de tipo $\hspace{0pt}1$ o mayor:
$$
\begin{align}
K_{p} = \lim_{ s \to 0 } \frac{K (T_{a}s+1)(T_{b}s+1)\cdots}{s^N(T_{1}s+1)(T_{2}s+1)\cdots} = \infty & & \text{for $N\geq 1$}
\end{align}
$$
por lo tanto si $K_{p}$ es infinito para sistemas de tipo $\hspace{0pt}1$ o mayor el error de estado estable sera 0. 

$$
\begin{align}
e_{ss} & = \frac{1}{1+K} & & \text{tipo 0} \\
e_{ss} & = 0 & & \text{tipo }\geq 1
\end{align}
$$

#### Para Entrada Tipo Rampa

en este caso:
$$
\begin{align}
e_{ss} & = \lim_{ s \to 0 } \frac{s}{1+G(s)} \frac{1}{s^2} \\
&= \lim_{ s \to 0 } \frac{1}{sG(s)}
\end{align}
$$
la constante de error de velocidad constate $K_{v}$ esta definida por:
$$
K_{v} = \lim_{ s \to 0 } sG(s)
$$
Por lo tanto el error de estado estable en terminos de la velocidad estable esta dado por:
$$
e_{ss} = \frac{1}{K_{v}}
$$
La dimension del error de velocidad es la misma que la del error del sistema, por lo tanto la el error de velocidad no es un error en la velocidad, sino que un error en posicion debido a una entrada rampa (velocidad constante).
![](https://i.imgur.com/XRWw2EQ.png)

para un sistema de tipo 0:

$$
K_{v } = \lim_{ s \to 0 } \frac{sK (T_{a}s+1)(T_{b}s+1)\cdots}{(T_{1}s+1)(T_{2}s+1)\cdots} = 0
$$
para un sistema de tipo $\hspace{0pt}1$ 
$$
K_{v } = \lim_{ s \to 0 } \frac{sK (T_{a}s+1)(T_{b}s+1)\cdots}{s(T_{1}s+1)(T_{2}s+1)\cdots} = K
$$
para un sistema de tipo $\hspace{0pt}2$ $o$ mayor:
$$
K_{v } = \lim_{ s \to 0 } \frac{sK (T_{a}s+1)(T_{b}s+1)\cdots}{s^N(T_{1}s+1)(T_{2}s+1)\cdots} = \infty
$$
por lo tanto tendremos:

$$
\begin{align}
e_{ss} & = \frac{1}{K_{v}}= \infty & & \text{tipo 0} \\
e_{ss} & = \frac{1}{K_{v}}= \frac{1}{K} & & \text{tipo }1 \\
e_{ss} & = \frac{1}{K_{v}} = 0 & & \text{tipo }N\geq 2
\end{align}
$$

#### Sistemas Con Entrada Parabolica

$$
e_{ss} = \lim_{ s \to 0 } \frac{s}{1+G(s)} \frac{1}{s^3} = \frac{1}{\lim_{ s \to 0 } s^2 G(s)}
$$
la constante de error de acceleracion estatica es entonces:
$$
K_{a} = \lim_{ s \to 0 } s^2G(s)
$$
el error de estado estable entonces pasa a ser:
$$
e_{ss} = \frac{1}{K_{a}}
$$
y obtenemos los valores de $K_{a}$ como:

tipo 0:
$$
K_{p} = \lim_{s \to 0 } \frac{s^2K (T_{a}s+1)(T_{b}s+1)\cdots}{(T_{1}s+1)(T_{2}s+1)\cdots} = 0
$$
tipo 1:
$$
K_{p} = \lim_{ s \to 0 } \frac{s^2K (T_{a}s+1)(T_{b}s+1)\cdots}{s(T_{1}s+1)(T_{2}s+1)\cdots} = 0
$$
tipo 2:
$$
K_{p} = \lim_{ s \to 0 } \frac{s^2K (T_{a}s+1)(T_{b}s+1)\cdots}{s^2(T_{1}s+1)(T_{2}s+1)\cdots} = K
$$
tipo $\geq 3$:
$$
K_{p} = \lim_{ s \to 0 } \frac{s^2K (T_{a}s+1)(T_{b}s+1)\cdots}{s^N(T_{1}s+1)(T_{2}s+1)\cdots} = \infty
$$
por lo tanto quedamos con:

$$
\begin{align}
e_{ss} & = \frac{1}{K_{a}}= \infty & & \text{tipo $\hspace{0pt}0$ y tipo 1} \\
e_{ss} & = \frac{1}{K_{a}}= \frac{1}{K} & & \text{tipo }2 \\
e_{ss} & = \frac{1}{K_{a}} = 0 & & \text{tipo }N\geq 3
\end{align}
$$
![](https://i.imgur.com/z5ppOQ5.png)

en resumen:
los errores de posicion, velocidad y acceleracion, definen error en la posicion de salida, por ejemplo un error de velocidad nos dice que una vez que la respuesta transitoria desparece y la velocidad de entrada coincide con la de salida vamos a tener un error en la posicion.

![](https://i.imgur.com/wjJHcWc.png)

las constantes de error $K_{p}, K_{v}, K_{a}$ describen la habilidad de un sistema de reducir o eliminar error de estado estable, y son indicativos de la performance en estado estable del sistema, por lo general queremos que estas constantes sean altas y mantener las respuestas transitorias en un rango acceptable.
Para incrementar la perfomance en estado estable podemos agregar un integrador o integradores en la rama de $G(s)$, pero esto nos introduce otro problema, la estabilidad.

## Stabiity

Existen tres requerimientos basicos para el diseño de un sistema de control:
- Respuesta transitoria
- Error en estado estable
- **Estabilidad**

### Definicion

**Respuesta de estado cero**: es la que se debe a la entrada unicamente y todas las condiciones iniciales del sistema son 0.

**Respuesta de entrada cero**: es la que se debe a las condiciones iniciales unicamente y todas las entradas son cero

Respuesta total = Respuesta de estado cero + respuesta de entrada 0

un sistema [LTI](Linear%20and%20Time%20Invariance%20(LTI)%20Systems.md) es **estable** si la respuesta de entrada cero tiende a cero cuando $t\to \infty$

un sistema [LTI](Linear%20and%20Time%20Invariance%20(LTI)%20Systems.md) es **inestable** si la respuesta de entrada cero crece sin limite cuando $t\to \infty$

un sistema [LTI](Linear%20and%20Time%20Invariance%20(LTI)%20Systems.md) es **marginalmente estable** si la respuesta de entrada cero no crece ni decrece cuando $t\to \infty$

podemos ver esto en funcion de nuestros polos complejos como:
![](https://i.imgur.com/AHnjCud.png)

### Nyquist Stability Criterion

Este criterio determina la estabilidad de un sistema de lazo cerrado desde la respuesta de la respuesta de lazo abierto y sus polos a lazo abierto, sin la necesidad de determinar las raíces de la ecuacion característica.

$$
\frac{C(S)}{R(s)} = G(s)
$$
**Permite determinar**:
- La cantidad de polos en el semiplano izquierdo
- La cantidad de polos en el semiplano derecho
- La cantidad de polos sobre el eje imaginario

**El metodo requiere**:
- Generar el arreglo de Routh
- Interpretar el arreglo para determinar la cantidad de polos en cada semiplano y sobre el eje imaginario

si tenemos una función de transferencia:
![](https://i.imgur.com/4owHemH.png)

Entonces armamos el arreglo de la siguiente manera:
![](https://i.imgur.com/kBpU56I.png)

el numero de raíces del polinomio característico positivas es igual al numero de cambios de signo de los elementos de la primera columna, y el sistema es estable si no hay cambios de signo en la primera columna.

**Ejemplo:**

![](https://i.imgur.com/OwIHnPc.png)

en este caso hay dos cambios de signo por lo que el sistema es inestable, y tiene dos polos positivos.

#### Casos Especiales

##### Zero En La Primera Columna

si es que tenemos un zero en la primera columna, asignamos un valor muy pequeño para substituir el zero $\epsilon$.

![](https://i.imgur.com/aZRg7PH.png)

luego evaluamos que pasa si tomamos $\epsilon$ como positivo o negativo:

![](https://i.imgur.com/iKVbqx9.png)
podemos ver que si lo tomamos como positivo tendremos dos cambios de signo, lo que es lo mismo que obtendríamos si lo tomaríamos como negativo, por lo que el sistema es inestable.


Otro metodo que puede ser utilizado cuando un zero aparece solo en la primera columna, es derivado del hecho que un polinomio tiene sus raices reciprocas del polinomio original distribuidas de la misma manera, porque tomar el reciproco de las raices no las mueve a otra region.

asume que estamos buscando un polinomio, $y$ el reciproco es simple el original con sus coeficientes escritos al revés, asumí la ecuación:

$$
s^n +a_{n-1}s^{n-1} + \cdots +a_{1}+a_{0}=0
$$
si remplazamos $s$ por $1/d$ entonces $d$ va a tener raices reciprocas a $s$:
$$
\left( \frac{1}{d} \right)^n + a_{n-1}\left( \frac{1}{d} \right)^{n-1} + \cdots+ a_{1}\left( \frac{1}{d} \right) +a_{0}=0
$$
sacando de factor comun $1/d$:
$$
\begin{align}
 & \left( \frac{1}{d} \right)^n \left[1+ a_{n}\left( \frac{1}{d} \right)^{-1}+ \cdots + + a_{1} \left( \frac{1}{d} \right)^{(1-n)}+a_{0}\left( \frac{1}{d} \right)^{-n} \right] \\
 & = \left( \frac{1}{d} \right)^n [1+a_{n-1}d+\cdots+a_{1}d^{n-1}+ a_{0}d^n] = 0
\end{align}
$$
por lo tanto podemos ver que el polinomio con raíces reciprocas es un polinomio con los coeficientes escritos al revés.

![](https://i.imgur.com/kl3afia.png)

##### Todo Un Renglón Formado Por Ceros

Si tenemos un renglón de todos ceros en la tabla de Routh entonces vamos al renglon arriba y remplazamos el renglón de zeros por la derivada del polinomio de arriba.

![](https://i.imgur.com/tlDwqi7.png)


Los polinomios pares solo tienen raíces simétricas respecto del origen, por lo tanto se puede determinar la ubicación de los polos mediante la inspección del arreglo a partir del polinomio par (el renglón previo al de ceros)



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

## Tipos de Entrada:

![image-20221231090156290](/home/bbruno/.config/Typora/typora-user-images/image-20221231090156290.png)

