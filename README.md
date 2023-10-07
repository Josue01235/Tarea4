# Tarea4
                                        Tarea 4, C++ y Python 
                                                        Ejercicio 1 C++
#include <iostream>
#include <vector>

using namespace std;

double calcular_subsidio(int cantidad_hijos, const vector<int>& edades_hijos, bool madre_viuda) {
    double monto_subsidio = 0;

    if (cantidad_hijos <= 2) {
        monto_subsidio = 70.00;
    } else if (3 <= cantidad_hijos & cantidad_hijos <= 5) {
        monto_subsidio = 90.00;
    } else if (cantidad_hijos >= 6) {
        monto_subsidio = 120.00;
    }

    // Contar cuántos hijos están en edad escolar (entre 6 y 18 años)
    int hijos_en_edad_escolar = 0;
    for (int i = 0; i < cantidad_hijos; ++i) {
        if (edades_hijos[i] >= 6 & edades_hijos[i] <= 18) {
            ++hijos_en_edad_escolar;
        }
    }

    // Agregar monto adicional por cada hijo en edad escolar
    monto_subsidio += 10.00 * hijos_en_edad_escolar;

    // Agregar monto adicional por viudez
    if (madre_viuda) {
        monto_subsidio += 20.00;
    }

    return monto_subsidio;
}

int main() {
    int cantidad_hijos;
    cout << "Ingrese la cantidad de hijos: ";
    cin >> cantidad_hijos;

    // Guardar la edad de cada hijo en un vector
    vector<int> edades_hijos(cantidad_hijos);
    for (int i = 0; i < cantidad_hijos; ++i) {
        cout << "Ingrese la edad del hijo " << i + 1 << ": ";
        cin >> edades_hijos[i];
    }

    bool madre_viuda;
    cout << "La madre de familia es viuda? (1 para sí, 0 para no): ";
    cin >> madre_viuda;

    double subsidio = calcular_subsidio(cantidad_hijos, edades_hijos, madre_viuda);

    cout << "El monto mensual del subsidio es: Q. " << subsidio << endl;

    return 0;
}

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                        Ejercicio 2 C++
#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>

using namespace std;

// Función para llenar un vector con valores aleatorios
void llenarVectorAleatorio(vector<int> &vec, int longitud) {
    for (int i = 0; i < longitud; ++i) {
        vec.push_back(rand() % 100); // Valores aleatorios entre 0 y 99
    }
}

// Función para sumar los elementos de un vector
int sumarVector(const vector<int> &vec) {
    int suma = 0;
    for (int valor : vec) {
        suma += valor;
    }
    return suma;
}

int main() {
    // Configurar la semilla para generar números aleatorios
    srand(static_cast<unsigned>(time(0)));

    // Solicitar la longitud de los vectores al usuario
    int longitud;
    cout << "Ingrese la longitud de los vectores: ";
    cin >> longitud;

    // Crear y llenar los vectores aleatoriamente
    vector<int> vectorA, vectorB;
    llenarVectorAleatorio(vectorA, longitud);
    llenarVectorAleatorio(vectorB, longitud);

    // Sumar los elementos de los vectores
    int sumaA = sumarVector(vectorA);
    int sumaB = sumarVector(vectorB);

    // Comparar las sumas para determinar el escenario
    if (sumaA == sumaB) {
        cout << "Los vectores son iguales." << endl;
    } else if (sumaA < sumaB) {
        cout << "El vector A es menor que el vector B." << endl;
    } else {
        cout << "El vector B es menor que el vector A." << endl;
    }

    return 0;
}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                        Ejercicio 3 C++
#include <iostream>
#include <vector>

using namespace std;

int main() {
    int cantidadDatos;
    //Pedimos datos al usuario
    cout << "Ingrese la cantidad de datos: ";
    cin >> cantidadDatos;

    vector<double> datos;
    for (int i = 0; i < cantidadDatos; ++i) {
        double dato;
        cout << "Ingrese el dato " << i + 1 << ": ";
        cin >> dato;
        datos.push_back(dato);
    }

    // Verificar que haya al menos un dato y no vaya vacio o null
    if (datos.empty()) {
        cout << "No se ingresaron datos." << endl;
        return 1; // Salir del programa con código de error
    }

    // Inicializar maximo y minimo con el primer elemento del vector para despues recorrerlo
    double maximo = datos[0];
    double minimo = datos[0];

    // Recorrer el vector para encontrar el máximo y el mínimo
    for (int i = 1; i < cantidadDatos; ++i) {
        if (datos[i] > maximo) {
            maximo = datos[i];
        }
        if (datos[i] < minimo) {
            minimo = datos[i];
        }
    }

    // Calcular el rango y mostrar el resultado
    double rango = maximo - minimo;
    cout << "El rango de los datos es: " << rango << endl;

    return 0;
}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                        Ejercicio 4 C++
include <iostream>

using namespace std;

int main() {
    // Solicitar al usuario ingresar el lado del cuadrado
    int lado;
    cout << "Ingrese el lado del cuadrado: ";
    cin >> lado;

    // Dibujar el cuadrado
    for (int i = 1; i <= lado; ++i) {
        for (int j = 1; j <= lado; ++j) {
            // Verificar si estamos en los lados del cuadrado para pintar un *
            if (i == 1 | i == lado | j == 1 | j == lado) {
                cout << "* ";
            } else {
                // Rellenar el interior con espacios
                cout << "  ";
            }
        }
        cout << endl;
    }

    return 0;
}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                        Ejercicio  1 Python
def calcular_subsidio(cantidad_hijos, edades_hijos, madre_viuda):
    monto_subsidio = 0

    if cantidad_hijos <= 2:
        monto_subsidio = 70.00
    elif 3 <= cantidad_hijos <= 5:
        monto_subsidio = 90.00
    elif cantidad_hijos >= 6:
        monto_subsidio = 120.00

    # Contar cuántos hijos están en edad escolar (entre 6 y 18 años)
    hijos_en_edad_escolar = sum(1 for edad in edades_hijos if 6 <= edad <= 18)

    # Agregar monto adicional por cada hijo en edad escolar
    monto_subsidio += 10.00 * hijos_en_edad_escolar

    # Agregar monto adicional por viudez
    if madre_viuda:
        monto_subsidio += 20.00

    return monto_subsidio


# Pedimos la cantidad de hijos
cantidad_hijos = int(input("Ingrese la cantidad de hijos: "))

# Guardar la edad de cada hijo en una lista o un vector
edades_hijos = []
for i in range(cantidad_hijos):
    edad = int(input(f"Ingrese la edad del hijo {i + 1}: "))
    edades_hijos.append(edad)

madre_viuda = bool(int(input("La madre de familia es viuda? (1 para sí, 0 para no): ")))

subsidio = calcular_subsidio(cantidad_hijos, edades_hijos, madre_viuda)

print(f"El monto mensual del subsidio es: Q. {subsidio:.2f}")
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                             Ejercicio 2 Python
import random

def comparar_vectores(vector_a, vector_b):
    suma_a = sum(vector_a)
    suma_b = sum(vector_b)

    if suma_a == suma_b:
        return "Los vectores son iguales."
    elif suma_a < suma_b:
        return "El vector A es menor que el vector B."
    else:
        return "El vector B es menor que el vector A."

# Solicitamos al usuario la longitud de los vectores
longitud = int(input("Ingrese la longitud de los vectores: "))

# llenamos los vectores aleatoriamente
vector_a = [random.randint(1, 100) for _ in range(longitud)]
vector_b = [random.randint(1, 100) for _ in range(longitud)]

# Mostrar los vectores
print("Vector A:", vector_a)
print("Vector B:", vector_b)

# Comparar y mostrar el resultado
resultado = comparar_vectores(vector_a, vector_b)
print(resultado)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                        Ejercicio 3 Python
def calcular_rango(datos):
    if not datos:
        return None  # Devolver None si la lista de datos está vacía

    maximo = datos[0]
    minimo = datos[0]

    for dato in datos:
        if dato > maximo:
            maximo = dato
        if dato < minimo:
            minimo = dato

    return maximo - minimo

# Preguntar al usuario cuántos datos serán ingresados
cantidad_datos = int(input("Ingrese la cantidad de datos: "))

# Pida al usuario ingresar los datos uno por uno
datos = []
for i in range(cantidad_datos):
    dato = float(input(f"Ingrese el dato {i + 1}: "))
    datos.append(dato)

# Calcular y mostrar el rango de los datos
rango = calcular_rango(datos)
if rango is not None:
    print(f"El rango de los datos es: {rango}")
else:
    print("No se ingresaron datos.")
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                    Ejercicio 4 Python
def dibujar_cuadrado(lado):
    for i in range(lado):
        for j in range(lado):
            if i == 0 or i == lado - 1 or j == 0 or j == lado - 1:
                print("* ", end="")
            else:
                print("  ", end="")
        print()

# Solicitar al usuario ingresar el lado del cuadrado
lado = int(input("Ingrese el lado del cuadrado: "))

# Dibujar el cuadrado
dibujar_cuadrado(lado
