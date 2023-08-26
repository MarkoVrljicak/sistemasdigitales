![Alt text](calendario.png)

# Clase 1: 26 de Agosto

## Conceptos Introductorios

- **Circuito secuencial**: Un circuito que toma una entrada indexada.
- **Indexada**: Se refiere a una ordenación por los números naturales.
- **Xi**: Representa un alfabeto finito que puede tomar solo `n` símbolos.

![Diagrama de circuito secuencial](secuencial.png)

## Implementación

Existen dos métodos para implementar en la práctica: 

- **Síncronica**: Es la que se estudiará en esta materia.
- **Asincrónica**: No se utiliza en la industria.

El circuito secuencial más básico es la **Máquina de estado finito (FSM)**. La cantidad de estados en una FSM es finita y se pueden enumerar como un tercer alfabeto, denominado "el estado de la máquina", por ejemplo: S<sub>0</sub>, S<sub>1</sub>, etc.

### Máquina de estado

Una máquina de estado tiene:

- X<sub>i</sub> ∈ N
- Y<sub>i</sub> ∈ N
- S<sub>i</sub> ∈ N
- x<sub>i</sub> ∈ Ax (Donde A es un alfabeto)
- y<sub>i</sub> ∈ Ay
- s<sub>i</sub> ∈ As

**Función de transición**:

δ : Ax x As → As

Ejemplo: δ(X1, S3) -> S5

Existen dos definiciones principales de máquina de estado:

1. **Mealy**: ω : As x Ax → Ay
2. **Moore**: ω : As → Ay (Es la que generalmente se utilizará)

Ambas definiciones representan **funciones de traducción**.

Ejemplo:

ω(s<sub>4</sub>) = Υ<sub>3</sub>

Si existe una máquina de Moore que implementa una máquina de estado, entonces existe una de Mealy. Pero desde el punto de vista eléctrico, Moore tiene ventajas que se prefieren.

### Definición Formal

La definición formal de una máquina de estado es una 6-tupla: 

(Ax, Ay, As, δ, ω, s<sub>0</sub>)

Esto define completamente una máquina de estado que puede ser implementada como máquina de Moore. Usualmente, esto se representa a través de un grafo.

![Diagrama de grafo](grafo.png)

## Aplicaciones

¿Qué tipo de problemas podemos resolver con una máquina de estado? 

Un libro podría mencionar el análisis (parsing) de expresiones regulares. Esencialmente, una máquina de estado puede reconocer símbolos de una secuencia finita de estados.

Ejemplo: e=Χ<sub>7</sub>,Χ<sub>9</sub>\*, Χ<sub>10</sub> 

### Tipos de FSM

1. **Aceptador**: Su alfabeto de salida es {0, 1} o {a, r}.
2. **Traductor**: Su alfabeto de salida tiene más de 2 símbolos.

Definir una máquina de estado se suele reducir a definir δ y ω.

Ejemplo:

| S<sub>i</sub> | ω(S<sub>i</sub>) |
|---------------|------------------|
| S<sub>0</sub>   | 0   |
| S<sub>1</sub>   | 0   |
| S<sub>2</sub>   | 0   |
| S<sub>3</sub>   | 0   |
| S<sub>4</sub>   | 1   |
| S<sub>5</sub>   | 2   |

| X<sub>i</sub> | S<sub>i</sub> | δ(X<sub>i</sub>,S<sub>i</sub>) |
|---------------|-----------------|--------------------------------|
| X<sub>1</sub>   | S<sub>0</sub>  | S<sub>0</sub> |
| X<sub>2</sub>   | S<sub>0</sub>  | S<sub>0</sub> |
| X<sub>3</sub>   | S<sub>0</sub>  | S<sub>0</sub> |
| X<sub>4</sub>   | S<sub>0</sub>  | S<sub>0</sub> |
| X<sub>5</sub>   | S<sub>0</sub>  | S<sub>2</sub> | 
| X<sub>6</sub>   | S<sub>0</sub>  | S<sub>0</sub> |
| X<sub>7</sub>   | S<sub>0</sub>  | S<sub>1</sub> |
| etc   | etc  | etc |

En circuitos digitales vamos a codificar en binario

| S<sub>i</sub> | Valor |
|--------|-------|
| S<sub>0</sub> | 000 |
| S<sub>1</sub> | 001 |
| S<sub>2</sub> | 010 |
| S<sub>3</sub> | 011 |
| S<sub>4</sub> | 100 |
| S<sub>5</sub> | 101 |
| S<sub>6</sub> | 110 |
| S<sub>7</sub> | 111 |

| X<sub>i</sub>     | Valor |
|------------|-------|
| X<sub>0</sub>   | 0000 |
| X<sub>1</sub>   | 0001 |
| X<sub>2</sub>   | 0010 |
| X<sub>3</sub>   | 0011 |
| X<sub>4</sub>   | 0100 |
| X<sub>5</sub>   | 0101 |
| X<sub>6</sub>   | 0110 |
| X<sub>7</sub>   | 0111 |
| X<sub>8</sub>   | 1000 |
| X<sub>9</sub>   | 1001 |
| X<sub>10</sub>  | 1010 |
| ...       | ...   |
| X<sub>15</sub>  | 1111 |

| Y<sub>i</sub> | Valor |
|--------|-------|
| Y<sub>0</sub> | 00 |
| Y<sub>1</sub> | 01 |
| Y<sub>2</sub> | 10 |
| Y<sub>3</sub> | 11 |

| S<sub>i</sub> | ω(S<sub>i</sub>) |
|--------|-------|
| 000 | 00 |
| 001 | 00 |
| 010 | 00 |
| 011 | 00 |
| 100 | 01 |
| 101 | 10 |

Esto define 2 tablas de verdad:

![Alt text](tablasverdad.png)

![Alt text](d.png)

## Registros

Registro, definición informal: La FSM más pequeña posible. Más pequeña significa

Ax = {0,1}
Ay = {0,1}
As = {0,1}
S<sub>0</sub> = puede ser 0 (rst) o puede ser 1 (set)