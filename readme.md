Para resolver este problema de programación lineal, primero definimos nuestras variables de decisión, restricciones y función objetivo. Utilizaremos el software de optimización Solver que se encuentra en programas de hoja de cálculo como Excel para este ejemplo.

### Variables de decisión:
- \( B \) = Número de viajes con Boeing 757
- \( A \) = Número de viajes con Airbus 330

### Función objetivo:
Para maximizar los beneficios y minimizar el consumo de combustible, podemos tener dos funciones objetivo. Sin embargo, Solver en Excel sólo puede manejar una función objetivo a la vez. Entonces necesitaríamos resolver el problema dos veces, una para cada objetivo, o combinar los dos objetivos en una única función objetivo.

1. Maximizar la ganancia: \( Z1 = 300,000 \times B + 200,000 \times A \)
2. Minimizar el consumo de combustible: \( Z2 = -(900 \times B + 700 \times A) \)

### Restricciones:

1. \( B \leq 120 \) (Los Boeing no pueden sobrepasar los 120 viajes)
2. \( 60 \leq B + A \leq 200 \) (Entre los 2 tipos de aviones deben hacer más de 60 vuelos pero menos de 200)

#### Opciones adicionales:

1. Opción 1: Resolver con ambas funciones objetivo por separado o combinarlas.
2. Opción 2: \( B = 120 \rightarrow A \geq 0 \) (Los vuelos de Airbus solo se habilitan después de 120 vuelos de Boeing)
3. Opción 3: \( A = 60 \rightarrow B \geq 0 \) (Los vuelos de Boeing se habilitan después de 60 vuelos de Airbus)
4. Opción 4: \( B \geq 1, A \geq 1 \) (Deben realizarse vuelos de ambos tipos de aviones)
5. Opción 5: \( A \geq 1 \rightarrow B = 0, B \geq 1 \rightarrow A = 0 \) (Si vuelan los Airbus no vuelan los Boeing y viceversa)
6. Opción 6: \( A \geq 1 \rightarrow B \geq 1 \) (Si se habilitan vuelos Airbus también deben habilitar los Boeing)
7. Opción 7: \( A \geq 1 \rightarrow B \geq 0 \) (Si se habilitan vuelos Airbus también pueden habilitar los Boeing)

Para utilizar Solver en Excel, deberías:

1. Colocar en una celda la fórmula para la función objetivo (puedes usar la celda `C1` para \( Z1 \) y `C2` para \( Z2 \)).
2. Colocar en otra celda las variables de decisión \( B \) y \( A \) (por ejemplo `A1` para \( B \) y `A2` para \( A \)).
3. Colocar las restricciones en otras celdas (por ejemplo, `B4` para \( B \leq 120 \), `B5` para \( 60 \leq B + A \leq 200 \)).
4. Abrir Solver (en la pestaña "Datos" en Excel) y configurar:
    - Definir la función objetivo \( Z \) a maximizar o minimizar.
    - Definir las variables de decisión.
    - Agregar las restricciones.
5. Resolver y analizar los resultados.

Ten en cuenta que si quieres aplicar varias de las opciones adicionales al mismo tiempo, tendrás que resolver el problema múltiples veces o usar técnicas más avanzadas que van más allá de la capacidad estándar del Solver de Excel.

Claro, puedo darte instrucciones detalladas sobre cómo configurar este problema en Excel. Supongamos que estás utilizando una hoja de Excel en blanco:

### Paso 1: Preparación de la hoja de Excel
- En `A1`, escribe "Boeing 757" (esto es solo una etiqueta para que sepas que la variable de decisión relacionada con el Boeing estará aquí).
- En `A2`, escribe "Airbus 330" (esto es similar a lo anterior pero para el Airbus).
- En `A4`, escribe "Función objetivo Z1" (esto es donde colocaremos la fórmula para maximizar la ganancia).
- En `A6`, escribe "Función objetivo Z2" (esto es donde colocaremos la fórmula para minimizar el consumo de combustible).

### Paso 2: Ingreso de las ecuaciones
- En `B1`, escribe "0" (esto será nuestra variable de decisión inicial para el Boeing, que Solver modificará).
- En `B2`, escribe "0" (esto será nuestra variable de decisión inicial para el Airbus, que Solver modificará).
- En `B4`, escribe `=300000*B1 + 200000*B2` (esto representa la fórmula \( Z1 = 300,000 \times B + 200,000 \times A \)).
- En `B6`, escribe `=-(900*B1 + 700*B2)` (esto representa la fórmula \( Z2 = -(900 \times B + 700 \times A) \)).

### Paso 3: Configuración de Solver
1. Ve a la pestaña "Datos" y haz clic en "Solver". Si no ves "Solver", es posible que debas instalarlo desde las "Opciones de Excel" bajo "Complementos".
2. En el cuadro de diálogo de Solver:
    - Establece la celda "Objetivo" a `B4` si quieres maximizar la ganancia o a `B6` si quieres minimizar el consumo de combustible.
    - Elige "Maximizar" si estás usando `B4` o "Minimizar" si estás usando `B6`.
    - En "Variable de decisión", agrega las celdas `B1` y `B2`.
3. Ahora, agrega las restricciones:
    - Haz clic en "Agregar" para ingresar una nueva restricción.
        - Primera restricción: \( B \leq 120 \)  
          - En la celda "Referencia de celda", escribe `B1`.
          - En el operador, selecciona "<=".
          - En "Valor de la restricción", escribe "120".
        - Segunda restricción: \( 60 \leq B + A \)  
          - En "Referencia de celda", escribe `B1 + B2`.
          - En el operador, selecciona ">=".
          - En "Valor de la restricción", escribe "60".
        - Tercera restricción: \( B + A \leq 200 \)
          - Similar a la segunda restricción, pero con "<=" y "200" como el valor de la restricción.
4. Si tienes alguna opción adicional que quieras aplicar, añádela como una restricción adicional siguiendo los pasos anteriores.

### Paso 4: Resolución
- Haz clic en "Resolver" en el cuadro de diálogo de Solver.
- Una vez que Solver haya encontrado una solución, podrás ver los resultados en las celdas `B1` y `B2`.

Este es un tutorial básico. Las opciones adicionales pueden requerir una mayor manipulación y posiblemente más variables o restricciones. Sin embargo, este es un buen punto de partida.

Por supuesto. Aquí está cómo podrías abordar cada una de las opciones adicionales utilizando el mismo esquema básico que hemos establecido previamente en Excel. Ten en cuenta que algunas de estas opciones son mutuamente excluyentes y deberás resolverlas en distintas corridas de Solver.

### Opción 1: Maximizar beneficios y minimizar combustible
Para esta opción, tendrías que resolver el problema dos veces: una para la función objetivo de maximizar los beneficios (`B4` en nuestro esquema de Excel) y otra para minimizar el combustible (`B6` en nuestro esquema). Luego, podrías comparar y analizar los dos conjuntos de resultados para tomar una decisión.

### Opción 2: Vuelos de Airbus habilitados después de 120 vuelos de Boeing
Añadirías una restricción adicional:
- \( B = 120 \) 
  - En "Referencia de celda", pones `B1`.
  - En el operador, selecciona "=".
  - En "Valor de la restricción", escribe "120".

### Opción 3: Vuelos de Boeing habilitados después de 60 vuelos de Airbus
Añadirías una restricción adicional:
- \( A = 60 \) 
  - En "Referencia de celda", pones `B2`.
  - En el operador, selecciona "=".
  - En "Valor de la restricción", escribe "60".

### Opción 4: Deben realizarse vuelos de ambos tipos de aviones
Añadirías dos restricciones adicionales:
- \( B \geq 1 \)  
  - En "Referencia de celda", pones `B1`.
  - En el operador, selecciona ">=".
  - En "Valor de la restricción", escribe "1".
  
- \( A \geq 1 \)  
  - En "Referencia de celda", pones `B2`.
  - En el operador, selecciona ">=".
  - En "Valor de la restricción", escribe "1".

### Opción 5: Si vuelan los Airbus no vuelan los Boeing
Añadirías una restricción adicional para modelar esto como un problema de "o bien... o bien...".
- En este caso, resolverías el problema dos veces: una vez con la restricción \( B = 0 \) y otra vez con \( A = 0 \), y luego compararías las soluciones.

### Opción 6: Si se habilitan vuelos Airbus también deben habilitar los Boeing
Aquí, la restricción sería similar a la Opción 4, es decir, \( B \geq 1 \) y \( A \geq 1 \).

### Opción 7: Si se habilitan vuelos Airbus también pueden habilitar los Boeing
No es necesario añadir restricciones adicionales para esta opción ya que es intrínseca en el modelo original. Resolverías el problema de optimización como se definió originalmente.

En cada caso, después de añadir las restricciones adicionales correspondientes, ejecutarías Solver nuevamente para encontrar la solución óptima. Ten en cuenta que cada una de estas opciones podría requerir su propia hoja de Excel para evitar confusiones.

Por supuesto, aquí te muestro cómo podría verse la hoja de Excel para resolver este problema. Cada "Opción" representa un conjunto diferente de restricciones que podrías aplicar en distintas corridas de Solver. Por simplicidad, he centrado cada conjunto de restricciones en un solo objetivo: maximizar la ganancia.

|   A  |       B      |       C      |    D   |          E           |              F               |          G          |
|------|--------------|--------------|--------|----------------------|------------------------------|---------------------|
|      | Boeing 757   | Airbus 330   |        |                      |                              |                     |
|      |      0       |      0       |        |                      |                              |                     |
|      |              |              |        |                      |                              |                     |
|      | Función objetivo Z1  |              |        | `=300000*B2+200000*B3` |                              |                     |
|      |              |              |        |                      |                              |                     |
|      | Función objetivo Z2  |              |        | `=-(900*B2+700*B3)`   |                              |                     |
|      |              |              |        |                      |                              |                     |
|      |              |              |        |                      |                              |                     |
| Opción 1  |   Restricción  |   Restricción |        |  Resolver dos veces:  |  una para Z1, otra para Z2  |                     |
| Opción 2  |   Restricción  |   Restricción |        |   `B2=120`            |                              |                     |
| Opción 3  |   Restricción  |   Restricción |        |   `B3=60`             |                              |                     |
| Opción 4  |   Restricción  |   Restricción |        |   `B2>=1`, `B3>=1`    |                              |                     |
| Opción 5  |   Restricción  |   Restricción |        |   Resolver dos veces: |  una con `B2=0`, otra con `B3=0` |               |
| Opción 6  |   Restricción  |   Restricción |        |   `B2>=1`, `B3>=1`    |                              |                     |
| Opción 7  |   Restricción  |   Restricción |        |   Sin restricción adicional |                      |                     |
|      |              |              |        |                      |                              |                     |
|      |              |              |        |                      |                              |                     |
|      |   Restricción Común |              |        |   `B2+B3>=60`, `B2<=120`, `B2+B3<=200`             |                     |

Las celdas B2 y B3 son tus variables de decisión. En el Solver, establecerías B4 como tu función objetivo para maximizar la ganancia y B6 si deseas minimizar el combustible. Las restricciones comunes se aplican a todas las opciones. Cada "Opción" tendría su propio conjunto de restricciones adicionales que deberías añadir en Solver antes de resolver el problema.

Espero que esta tabla aclare cómo configurar tu hoja de Excel y Solver para abordar cada una de las opciones.
