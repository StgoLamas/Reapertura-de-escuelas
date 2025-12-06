# Reapertura-de-escuelas
Proyecto semestral de control óptimo, en el cual se estudió un modelo SIR compartimentalizado para estudiar la política óptima de reapertura de escuelas en el contexto de transmisión de una enfermedad. 

Se considera un modelo epidemiológico SIR que divide la población en dos rangos etarios, uno de personas en edad escolar ($E$) y otro que no ($NE$), que siguen la siguiente dinámica

$$\begin{equation*}
\begin{cases}
    S'_i &= -\beta_1 S_i(I_i + I_j) − u(t)\beta_2 S_E I_E \delta_{i,E}\\
    I'_i &= \beta_1 S_i(I_i + I_j) + u(t)\beta_2 S_E I_E \delta_{i,E} - \gamma I_i \\
    R'_i &= \gamma I_i
\end{cases}  
\end{equation*}$$

donde

   - $i \in$ {E,NE}, $\delta_{i,E} = \mathbf{1}_{i=E}$,
   - $\gamma$ es la tasa de recuperación  de la enfermedad,
   - $\beta_1$ y $\beta_2$ son las tasas de transmisión de la enfermedad fuera y dentro de la escuela, respectivamente,
   - $u(t) \in [0,1]$ es un control que regula la apertura de las escuelas.

 Se busca maximizar una función objetivo que promueve la asistencia de estudiantes no infectados a las escuelas a la vez que penaliza el acumulado de personas infectadas
 $J(u(\cdot)) := \lambda_E \int^T_0 u(t)(S_E(t) + R_E(t))\,\text{d}t - \lambda_I \int^T_0 (I_E(t) + I_{NE}(t))\,\text{d}t,$
    donde $\lambda_E$ y $\lambda_{I}$ ponderan la preferencia de cada criterio.

Para las simulaciones, se utilizaron datos del Centro de Modelamiento Matemático, que se pueden encontrar haciendo click [aquí](https://covid-19vis.cmm.uchile.cl/chart).
