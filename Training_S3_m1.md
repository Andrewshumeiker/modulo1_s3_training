# inventario_tienda.py

# Diccionario para almacenar productos: clave = nombre, valor = (precio, cantidad)
inventario = {}

```python
# Función para añadir un producto
def agregar_producto(nombre, precio, cantidad):
    if nombre in inventario:
        print("El producto ya existe. Use la opción de actualizar si desea cambiar los datos.")
    else:
        inventario[nombre] = (precio, cantidad)
        print(f"Producto '{nombre}' añadido con éxito.")

# Función para buscar un producto
def buscar_producto(nombre):
    return inventario.get(nombre, None)

# Función para actualizar el precio de un producto existente
def actualizar_precio(nombre, nuevo_precio):
    if nombre in inventario:
        cantidad = inventario[nombre][1]
        inventario[nombre] = (nuevo_precio, cantidad)
        print(f"Precio del producto '{nombre}' actualizado a {nuevo_precio}.")
    else:
        print("Producto no encontrado.")

# Función para eliminar un producto
def eliminar_producto(nombre):
    if nombre in inventario:
        del inventario[nombre]
        print(f"Producto '{nombre}' eliminado del inventario.")
    else:
        print("Producto no encontrado.")

# Función para calcular el valor total del inventario usando lambda
def calcular_valor_total():
    total = sum(map(lambda item: item[1][0] * item[1][1], inventario.items()))
    return total

# Función para validar entrada numérica
def solicitar_numero(mensaje):
    while True:
        entrada = input(mensaje)
        if entrada.replace('.', '', 1).isdigit():
            return float(entrada)
        else:
            print("Entrada inválida. Por favor, ingrese un número.")

# Menú interactivo
def menu():
    while True:
        print("\n--- MENÚ DE INVENTARIO ---")
        print("1. Añadir producto")
        print("2. Consultar producto")
        print("3. Actualizar precio")
        print("4. Eliminar producto")
        print("5. Calcular valor total del inventario")
        print("6. Ver todos los productos")
        print("7. Salir")

        opcion = input("Seleccione una opción (1-7): ")

        if opcion == "1":
            nombre = input("Nombre del producto: ")
            precio = solicitar_numero("Precio del producto: ")
            cantidad = solicitar_numero("Cantidad disponible: ")
            agregar_producto(nombre, precio, int(cantidad))

        elif opcion == "2":
            nombre = input("Nombre del producto a buscar: ")
            resultado = buscar_producto(nombre)
            if resultado:
                print(f"Producto: {nombre}, Precio: {resultado[0]}, Cantidad: {resultado[1]}")
            else:
                print("Producto no encontrado.")

        elif opcion == "3":
            nombre = input("Nombre del producto a actualizar: ")
            nuevo_precio = solicitar_numero("Nuevo precio: ")
            actualizar_precio(nombre, nuevo_precio)

        elif opcion == "4":
            nombre = input("Nombre del producto a eliminar: ")
            eliminar_producto(nombre)

        elif opcion == "5":
            total = calcular_valor_total()
            print(f"Valor total del inventario: ${total:.2f}")

        elif opcion == "6":
            if inventario:
                for nombre, (precio, cantidad) in inventario.items():
                    print(f"{nombre} - Precio: ${precio}, Cantidad: {cantidad}")
            else:
                print("El inventario está vacío.")

        elif opcion == "7":
            print("Saliendo del programa.")
            break

        else:
            print("Opción inválida. Intente nuevamente.")

# Ejecutar el menú principal
menu()
```
