# Tarea4
Tarea 4, C++ y Python 
Ejercicio1 C++
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

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------Ejercicio 2 C++
