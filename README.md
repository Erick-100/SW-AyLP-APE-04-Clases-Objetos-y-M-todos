# SW-AyLP-APE-04-Clases-Objetos-y-M-todos
# 📱 Sistema de Gestión de Ventas - POO (Ejercicio 3)

> Actividad Práctica de Integración de Clases, Objetos y Métodos en Java.

## 📋 Descripción del Proyecto
Este proyecto forma parte de las actividades prácticas de la asignatura de **Algoritmos y Lógica de Programación**. Implementa los pilares de la Programación Orientada a Objetos (POO) en Java, centrándose específicamente en la **asociación y paso de objetos como parámetros** a través de un escenario real: la gestión de un producto tecnológico (**Xiaomi Redmi**) y el procesamiento de su respectiva **venta**[span_2](start_span)[span_2](end_span)[span_3](start_span)[span_3](end_span).

## ⚙️ Estructura del Modelo
El sistema está compuesto por dos clases principales que colaboran entre sí:

1. **Clase `Producto`**[span_4](start_span)[span_4](end_span):
   - **Atributos:** `nombre`, `precio`, `stock`[span_5](start_span)[span_5](end_span).
   - **Métodos:** 
     - `reducirStock(int cantidad)`: Valida y actualiza el inventario disponible de manera segura[span_6](start_span)[span_6](end_span).
     - `mostrarProducto()`: Despliega la información detallada del artículo en consola.

2. **Clase `Venta`**[span_7](start_span)[span_7](end_span):
   - **Atributos:** `cantidad`.
   - **Métodos:**
     - `aplicar(Producto producto)`: Recibe un objeto de tipo `Producto` por parámetro para calcular totales, aplicar impuestos y efectuar la reducción de stock[span_8](start_span)[span_8](end_span).

## 🚀 Características Destacadas
* **Paso de objetos por parámetro:** Demuestra cómo una clase (`Venta`) interactúa directamente con los métodos y atributos de otra (`Producto`).
* **Control de excepciones lógicas:** Manejo de validaciones mediante estructuras condicionales para evitar stock negativo (imprime alertas cuando no hay suficientes unidades)[span_9](start_span)[span_9](end_span).
* **Interfaz en consola estilizada:** Uso de formato de texto claro con separadores e indicadores visuales para un mejor seguimiento de las transacciones.

## 💻 Código Fuente Principal

Puedes encontrar la implementación completa en el archivo adjunto o en el siguiente bloque de código:

```java
class Producto {
    private String nombre;
    private double precio;
    private int stock;

    public Producto(String nombre, double precio, int stock) {
        this.nombre = nombre;
        this.precio = precio;
        this.stock = stock;
    }

    public void reducirStock(int cantidad) {
        if (this.stock >= cantidad) {
            this.stock -= cantidad;
            System.out.println("  [✔] Stock actualizado. Restantes: " + this.stock);
        } else {
            System.out.println("  [✖] Stock insuficiente.");
        }
    }

    public void mostrarProducto() {
        System.out.println(" Producto: " + this.nombre + " | Precio: $" + this.precio + " | Stock: " + this.stock);
    }

    public String getNombre() { return nombre; }
    public double getPrecio() { return precio; }
    public int getStock() { return stock; }
}

class Venta {
    private int cantidad;

    public Venta(int cantidad) {
        this.cantidad = cantidad;
    }

    public void aplicar(Producto producto) {
        System.out.println("\nProcesando venta de " + this.cantidad + " unidad(es) de " + producto.getNombre());
        if (producto.getStock() >= this.cantidad) {
            double total = this.cantidad * producto.getPrecio();
            producto.reducirStock(this.cantidad);
            System.out.println(" Total a pagar: $" + total);
            System.out.println(" Estado: ¡Compra exitosa! 🎉");
        } else {
            System.out.println(" Estado: Transacción rechazada ❌");
            producto.reducirStock(this.cantidad);
        }
    }
}
