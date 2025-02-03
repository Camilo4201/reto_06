# reto_06
1. Add the required exceptions in the Reto 1 code assigments.
# Crear una función que realice operaciones básicas (suma, resta, multiplicación, división) entre dos números, según la elección del usuario, la forma de entrada de la función será los dos operandos y el caracter usado para la operación. entrada: (1,2,"+"), salida (3).
```python
        # Verifica la operación y realiza la correspondiente
        if operacion == "+":
            return numero1 + numero2
        elif operacion == "-":
            return numero1 - numero2
        elif operacion == "*":
            return numero1 * numero2
        elif operacion == "/":
            # La excepción ZeroDivisionError se maneja automáticamente si numero2 es 0
            return numero1 / numero2
        else:
            # Si la operación no es válida, se lanza una excepción ValueError
            raise ValueError("Operación inválida. Use '+', '-', '*' o '/'.")
    except ZeroDivisionError:
        # Captura el error de división por cero y retorna un mensaje adecuado
        return "Error: División por cero no permitida."
    except TypeError:
        # Captura errores de tipo, como si los operandos no son números
        return "Error: Los operandos deben ser números."
    except Exception as e:
        # Captura cualquier otra excepción inesperada y retorna el mensaje de error
        return f"Error inesperado: {e}"

# Entrada de usuario con manejo de excepciones
try:
    # Solicita al usuario el primer número y lo convierte a float
    numero1 = float(input("Ingrese el primer número: "))
    # Solicita al usuario el segundo número y lo convierte a float
    numero2 = float(input("Ingrese el segundo número: "))
    # Solicita al usuario la operación a realizar
    operacion = input("Ingrese la operación a realizar (+, -, *, /): ")

    # Llama a la función calculadora con los valores ingresados
    resultado = calculadora(numero1, numero2, operacion)
    # Muestra el resultado de la operación
    print("El resultado es:", resultado)

except ValueError:
    # Captura errores de valor, como si la entrada no es un número válido
    print("Error: Entrada inválida. Debe ingresar números válidos.")
except Exception as e:
    # Captura cualquier otra excepción inesperada y muestra el mensaje de error
    print(f"Error inesperado: {e}")

```
# Escribir una función que reciba una lista de números y devuelva solo aquellos que son primos. 
La función debe recibir una lista de enteros y retornar solo aquellos que sean primos.
```python
def es_primo(numero):
    if numero < 2:
        # Si el número es menor que 2, no es primo
        return False
    for i in range(2, int(numero ** 0.5) + 1):
        if numero % i == 0:
            # Si el número es divisible por i, no es primo
            return False
    return True

def filtrar_primos(lista):
 
    if not isinstance(lista, list):
        # Verifica que la entrada sea una lista
        raise TypeError("La entrada debe ser una lista de números enteros.")
    if not all(isinstance(x, int) for x in lista):
        # Verifica que todos los elementos de la lista sean enteros
        raise ValueError("Todos los elementos de la lista deben ser números enteros.")
    
    primos = []
    for numero in lista:
        if es_primo(numero):
            primos.append(numero)
    return primos

# Lista de números del 0 al 19
Lista = list(range(20))

try:
    # Intenta filtrar los números primos de la lista
    Lista_Numeros_Primos = filtrar_primos(Lista)
    print("Números primos:", Lista_Numeros_Primos)
except (TypeError, ValueError) as e:
    # Captura errores de tipo o valor y muestra el mensaje de error
    print(f"Error: {e}")
```
# Escribir una función que reciba una lista de números enteros  y retorne la mayor suma entre dos elementos consecutivos.
```python
def mayor_suma(lista):
    if len(lista) < 2:
        # Si la lista tiene menos de dos elementos, no es posible calcular la suma
        return None
    return max(a + b for a, b in zip(lista, lista[1:]))

# Solicita al usuario que ingrese una lista de números separados por espacios
entrada = input("Ingrese la lista de números (separados por espacios): ")

    # Convierte la entrada en una lista de enteros
    lista = list(map(int, entrada.split()))
    
    # Llama a la función mayor_suma con la lista proporcionada
    resultado = mayor_suma(lista)
    
    if resultado is None:
        # Si la lista tiene menos de dos elementos, no se puede calcular la suma
        print("La lista debe contener al menos dos elementos.")
    else:
        # Muestra el resultado de la mayor suma
        print(f"La mayor suma entre dos elementos consecutivos es: {resultado}")
except ValueError:
    # Captura el error si la entrada no puede convertirse a enteros
    print("Error: Todos los elementos deben ser números enteros.")
except Exception as e:
    # Captura cualquier otra excepción inesperada y muestra el mensaje de error
    print(f"Error inesperado: {e}")
```
# Escribir una función que reciba una lista de string y retorne unicamente aquellos elementos que tengan los mismos caracteres. e.g. entrada: ["amor", "roma", "perro"], salida ["amor", "roma"]
```python
from collections import defaultdict

def agrupar_anagramas(lista):

    if not isinstance(lista, list):
        raise TypeError("La entrada debe ser una lista de cadenas de texto.")
    if not all(isinstance(palabra, str) for palabra in lista):
        raise ValueError("Todos los elementos de la lista deben ser cadenas de texto.")
    
    anagramas = defaultdict(list)
    for palabra in lista:
        clave = ''.join(sorted(palabra))
        anagramas[clave].append(palabra)
    
    # Filtra y devuelve solo las listas que contienen más de una palabra
    return [grupo for grupo in anagramas.values() if len(grupo) > 1]

# Lista de palabras de ejemplo
elementos = ["amor", "roma", "arte", "trae", "esteban", "juan", "nuevo"]

try:
    # Agrupa las palabras que son anagramas entre sí
    grupos_anagramas = agrupar_anagramas(elementos)
    
    # Muestra los grupos de anagramas encontrados
    if grupos_anagramas:
        print("Grupos de anagramas encontrados:")
        for grupo in grupos_anagramas:
            print(grupo)
    else:
        print("No se encontraron anagramas en la lista.")
except (TypeError, ValueError) as e:
    # Captura y muestra errores de tipo o valor
    print(f"Error: {e}")
except Exception as e:
    # Captura y muestra cualquier otro error inesperado
    print(f"Error inesperado: {e}")
```
3. In the package Shape identify at least cases where exceptions are needed (maybe when validate input data, or math procedures) explain them clearly using comments and add them to the code.
