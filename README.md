# U3GB-Ejercicios-Guiados-3
## Ejercicios de Programación – UTNG

Repositorio creado para almacenar y organizar los ejercicios realizados durante las clases de **Estructura de Datos**.

---

## 🚀 Tecnologías utilizadas

| Tecnología | Uso |
|-----------|-----|
| **Java** | Programación orientada a objetos y desarrollo con Swing |
| **NetBeans** | Entorno principal de desarrollo |

---

## 📄 Ejercicios 

| 🌟 Ejercicio | 🧠 Tema | 🔗 Enlace |
|--------------|---------|-----------|
| **Ventana básica Swing** | Java / Swing | [📄 Ver ejercicio](https://github.com/diabegarciamtz-coder/U3GB-Ejercicios-Guiados-3/blob/main/Ejercicio%20Guiado%20Swing.pdf) |
| **Nearpod Árboles** | Nearpod | [📄 Ver ejercicio](https://github.com/diabegarciamtz-coder/U3GB-Ejercicios-Guiados-3/blob/main/Ejercicio%20de%20%20Nearpod%20%C3%81rboles.pdf) |
| **Guiados Construccion de arboles** | Actividad e clase | [📄 Ver ejercicio](https://github.com/diabegarciamtz-coder/U3GB-Ejercicios-Guiados-3/blob/main/Guiados%20Construccion%20de%20arboles.pdf) |

## Codigo arboles

### NodoArbol
```
package guiados;
/**
 *         Esta clase simula el nodo de un árbol
 * @author Diana Mabel Garcia
 *         diabegarciamtz@gmail.com    25/11/2025
 *         
 */
public class NodoArbol <T> {
    private T dato;  
     
    public NodoArbol hijoIzquierdo; 
    public NodoArbol hijoDerecho; 

    public NodoArbol(T dato) {
        this.dato = dato;
        this.hijoIzquierdo = hijoIzquierdo;
        this.hijoDerecho = hijoDerecho;
    }

    public T getDato() {
        return dato;
    }

    public NodoArbol getHijoIzquierdo() {
        return hijoIzquierdo;
    }

    public NodoArbol getHijoDerecho() {
        return hijoDerecho;
    }

    public void setDato(T dato) {
        this.dato = dato;
    }

    public void setHijoIzquierdo(NodoArbol hijoIzquierdo) {
        this.hijoIzquierdo = hijoIzquierdo;
    }

    public void setHijoDerecho(NodoArbol hijoDerecho) {
        this.hijoDerecho = hijoDerecho;
    }
 
    
}
```

### PruebaArbol
```
package guiados;

/**
 *         Esta clase es la prueba de un árbol
 * @author Diana Mabel Garcia
 *         diabegarciamtz@gmail.com    25/11/2025
 *         
 */
public class PruebaArbol {
    public static void main(String[] args) { 
        // 1. Crear una instancia de la clase gestora del árbol 
        ArbolBinario arbol = new ArbolBinario(); 
        System.out.println("Insertando valores: 10,20,30,40,50"); 
        // 2. Insertar valores usando el método público 
        arbol.insertar(10); // Raíz 
        arbol.insertar(20); // Izquierda de 50 
        arbol.insertar(30); // Derecha de 50 
        arbol.insertar(40); // Izquierda de 30 
        arbol.insertar(50); // Derecha de 30
        
        // 3. Ejecutar el recorrido para verificar el orden 
        // Resultado esperado (ordenado): 20 30 40 50 70  
        arbol.recorrerInorden(); 
    } 
}
```
### ArbolBinario
```
package guiados;

/**
 *         Esta clase simula un árbol binario
 * @author Diana Mabel Garcia
 *         diabegarciamtz@gmail.com    25/11/2025
 *         
 */
public class ArbolBinario {
    
    private NodoArbol raiz;  
    
    public ArbolBinario() { 
    this.raiz = null; 
    } 
    
    /** 
    * Método Público de Inserción: Punto de entrada para el usuario. 
    * Inicia la recursión desde la raíz. 
    */ 
    public void insertar(int valor) { 
    this.raiz = insertarRecursivo(this.raiz, valor); 
    } 
    /** 
    * Método Privado y Recursivo de Inserción. 
    * @param actual El nodo que se está examinando en la recursión. 
    * @param valor El valor a insertar. 
    * @return El nodo modificado o el nuevo nodo creado. 
    */ 
    private NodoArbol<Integer> insertarRecursivo(NodoArbol<Integer> actual, int valor) {
        // Caso base: si el nodo actual es null, se crea uno nuevo con el valor.
        if (actual == null) {
            return new NodoArbol<>(valor);
        }

        if (valor < actual.getDato()) {
            actual.setHijoIzquierdo(insertarRecursivo(actual.getHijoIzquierdo(), valor));
        } else if (valor > actual.getDato()) {
            actual.setHijoDerecho(insertarRecursivo(actual.getHijoDerecho(), valor));
        }
        // Si el valor ya existe, no se inserta (evita duplicados).
        return actual;
    }
    
    /** 
    * Método Público de Recorrido Inorden. 
    * Inicia la recursión desde la raíz y muestra el resultado. 
    */ 
    public void recorrerInorden() { 
        System.out.print("Recorrido Inorden: "); 
        recorrerInordenRecursivo(this.raiz); 
        System.out.println(); 
    } 
    
    /** 
    * Método Privado y Recursivo de Recorrido Inorden (Izquierda -> Raíz -> 
    Derecha). 
    */ 
    private void recorrerInordenRecursivo(NodoArbol nodo) { 
        if (nodo != null) { 
        recorrerInordenRecursivo(nodo.hijoIzquierdo); // 1. Izquierda 
        System.out.print(nodo.getDato() + " ");       
        // 2. Raíz (Imprimir) 
        recorrerInordenRecursivo(nodo.hijoDerecho);  // 3. Derecha 
        } 
    } 
}


```
