# TrabajoPractico4_Programaci-nFuncional
TRABAJO PRACTICO: PARADIGMA FUNCIONAL (HASKELL)
UTN - Facultad Regional Mendoza
Catedra: Paradigmas de Programacion
Alumna: Coronel, Erika

==================================================
DESCRIPCION DE FUNCIONES Y SOLUCIONES
==================================================

1. DEFINICIONES FUNCIONALES
- potencia :: Int -> Int -> Int
  Funcionamiento: Calcula la potencia de una base elevada a un exponente de forma recursiva multiplicando la base por si misma. Su caso base es cuando el exponente llega a 0, devolviendo 1.
  Ejemplo: potencia 2 3 -> 8

- valAbsoluto :: Int -> Int
  Funcionamiento: Evalua si el numero ingresado es negativo (n < 0). Si es verdadero, le invierte el signo para convertirlo en positivo; si es cero o positivo, mantiene su valor original.
  Ejemplo: valAbsoluto (-15) -> 15

- sumatoria :: Int -> Int

 Funcionamiento: Suma los primeros N numeros naturales de manera recursiva descontando de a 1 hasta alcanzar el caso base 0, acumulando la suma de cada valor.
  Ejemplo: sumatoria 5 -> 15

- divisor :: Int -> Int -> Bool / divisorG
  Funcionamiento: Verifica si el primer argumento divide exactamente al segundo implementando restas sucesivas (sin usar el operador mod). Resta reiteradamente el divisor al dividendo: si el resultado final llega a 0 devuelve True; si queda un valor positivo menor que el divisor, devuelve False.
  Ejemplo: divisor 3 12 -> True

- mcd :: Int -> Int -> Int
  Funcionamiento: Calcula el Maximo Comun Divisor aplicando el algoritmo de los restos (Algoritmo de Euclides) utilizando mod de forma recursiva hasta que el resto sea igual a 0.
  Ejemplo: mcd 12 18 -> 6

2. FUNCIONES LAMBDA (EJECUCION EN CONSOLA)
- Punto 7. Mayor de dos numeros: (\x y -> if x >= y then x else y)
  Funcionamiento: Funcion anonima ejecutada en consola que toma dos valores en el momento y retorna el mayor entre ambos.
  Ejemplo: (\x y -> if x >= y then x else y) (8::Int) 3 -> 8
- Punto 8. Verificar paridad: (\x -> x `mod` 2 == 0)
  Funcionamiento: Funcion anonima que calcula el resto de la division por 2 de un numero dado y retorna True si es par o False si es impar.
  Ejemplo: (\x -> x `mod` 2 == 0) (6::Int) -> True

3. TRATAMIENTO DE LISTAS
- q1 :: [a] -> [[a]]
  Funcionamiento: Calcula el conjunto potencia (todas las sublistas posibles de una lista dada) mediante recursion y listas por comprension.
  Ejemplo: q1 [1,2] -> [[1,2],[1],[2],[]]
- suma :: Num a => [a] -> a
  Funcionamiento: Suma todos los elementos numericos de una lista sumando el primer elemento (cabeza) a la suma del resto de la lista (cola).
  Ejemplo: suma [1,2,3] -> 6
- cantidad :: [a] -> Int
  Funcionamiento: Cuenta la cantidad de elementos de una lista sumando 1 recursivamente por cada elemento que descompone de la lista.
  Ejemplo: cantidad [4,5,6] -> 3
- ultimo :: [a] -> a / ultimoG
  Funcionamiento: Recorre la lista de forma recursiva eliminando la cabeza hasta aislar y devolver el unico elemento que queda al final.
  Ejemplo: ultimo [1,2,3] -> 3
- inversa :: Eq a => [a] -> [a]
  Funcionamiento: Invierte el orden de los elementos de una lista colocando la cabeza al final de la lista invertida resultante de la cola.
  Ejemplo: inversa [1,2,3] -> [3,2,1]
- sacar :: Eq a => Int -> [a] -> [a] / sacarG
  Funcionamiento: Recorre la lista descontando la posicion deseada en cada llamada recursiva. Al alcanzar la posicion 1, remueve dicho elemento de la lista devuelta.
  Ejemplo: sacar 2 [10,20,30] -> [10,30]
- eliminar :: Eq a => a -> [a] -> [a]
  Funcionamiento: Filtra todos los elementos de una lista descartando todas las apariciones que coincidan con el valor buscado.
  Ejemplo: eliminar 2 [2,1,2,3,2] -> [1,3]
- intersec :: Eq a => [a] -> [a] -> [a]
  Funcionamiento: Retorna una lista con la interseccion de dos listas manteniendo unicamente los elementos que pertenecen a ambas.
  Ejemplo: intersec [1,2,2,3] [2,3,4] -> [2,3]
- rotarIzq :: Eq a => Int -> [a] -> [a]
  Funcionamiento: Desplaza los elementos de una lista N posiciones hacia la izquierda, moviendo los elementos extraidos al final de la misma.
  Ejemplo: rotarIzq 5 [1,2,3,4] -> [2,3,4,1]
- insertarEn :: Int -> a -> [a] -> [a]
  Funcionamiento: Inserta un elemento en una posicion especifica de la lista reconstruyendo recursivamente los elementos anteriores.
  Ejemplo: insertarEn 3 9 [1,2] -> [1,2,9]
- insertOrd :: Ord a => a -> [a] -> [a]
  Funcionamiento: Inserta un nuevo elemento manteniendo el orden ascendente dentro de una lista que previamente ya se encuentra ordenada.
  Ejemplo: insertOrd 3 [1,2,4] -> [1,2,3,4]
- ordenada :: Ord a => [a] -> [a]
  Funcionamiento: Ordena una lista desordenada aplicando el algoritmo de insercion (Insertion Sort), insertando recursivamente cada elemento en su lugar correcto mediante insertOrd.
  Ejemplo: ordenada [3,1,2,1] -> [1,1,2,3]

4. INSTANCIACION PARCIAL
- Instanciacion con map:
  Funcionamiento: Se fija el primer argumento de la funcion (base = 2 en potencia y a = 12 en mcd) y luego se aplica dicha funcion currificada a cada elemento de una lista mediante map.
  Ejemplos:
    map (potencia 2) [0,1,2,3,4] -> [1,2,4,8,16]
    map (mcd 12) [8,18,24,25] -> [4,6,12,1]

5. ESTRUCTURAS DE DATOS
- parejas :: [a] -> [a] -> [(a,a)]
  Funcionamiento: Toma dos listas de igual longitud y construye una lista de tuplas con los pares de elementos correspondientes a cada indice.
  Ejemplo: parejas [1,2] [3,4] -> [(1,3),(2,4)]
- Paseo y Mov:
  Funcionamiento: Define la estructura de tipos algebraicos para modelar movimientos con direccion y distancia (N, S, E, O) encadenados recursivamente hasta llegar a un descanso final.
  Instanciacion: paseo = Pasos (N 20) (Pasos (S 30) (Pasos (E 10) (Pasos (O 40) (Descansa 0)))))
- aplica :: (a -> b) -> [a] -> [b]
  Funcionamiento: Aplica una funcion ingresada por argumento sobre cada uno de los elementos de una lista (comportamiento equivalente a map).
  Ejemplo: aplica (+1) [1,2,3] -> [2,3,4]
- Circuito Logico:
  Funcionamiento: Define los operadores logicos basicos _and, _or, _not y combina sus comportamientos para evaluar un circuito equivalente a un XOR y generar su tabla de verdad completa.
  Ejemplo: map snd tablaCircuito -> [False,True,True,False]
- Arbol Binario:
  - cantidadNodos: Cuenta el total de nodos (incluyendo hojas) recorriendo recursivamente las ramas izquierda y derecha.
  - valores: Recorre el arbol extrayendo en una lista los valores almacenados en las hojas de izquierda a derecha.
  - profundidad: Mide la altura maxima o nivel de aristas desde la raiz del arbol hasta su hoja mas lejana usando max.
  - reemplazarHoja: Busca un valor puntual en las hojas del arbol y lo sustituye dinamicamente por un nuevo subarbol.
  Ejemplos:
    (cantidadNodos arbol, valores arbol, profundidad arbol) -> (9, [45,78,12,23,13], 3)
    (cantidadNodos arbolModificado, valores arbolModificado, profundidad arbolModificado) -> (11, [45,78,12,30,23,13], 4)

==================================================
EJECUCION Y TESTEO AUTOMATIZADO
==================================================

El archivo ProgramacionFuncional.hs incluye una suite de pruebas integradas (pruebas). Para verificar todo el desarrollo en WinHugs, ejecutar en consola:
Hugs> pruebas
True
