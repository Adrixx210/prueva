productos = {
    '8475HD': ['HP', 15.6, '8GB', 'DD', '1T', 'Intel Core i5', 'Nvidia GTX1050'],
    '2175HD': ['Acer', 14, '4GB', 'SSD', '512GB', 'Intel Core i5', 'Nvidia GTX1050'],
    'JjfFHD': ['Asus', 14, '16GB', 'SSD', '256GB', 'Intel Core i7', 'Nvidia RTX2080Ti'],
    'fgdxFHD': ['HP', 15.6, '12GB', 'DD', '1T', 'Intel Core i3', 'integrada'],
    'GF75HD': ['Asus', 15.6, '12GB', 'DD', '1T', 'Intel Core i7', 'Nvidia GTX1050'],
    '123FHD': ['Acer', 14, '6GB', 'DD', '1T', 'AMD Ryzen 5', 'integrada'],
    '342FHD': ['Acer', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 7', 'Nvidia GTX1050'],
    'UWU131HD': ['Dell', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 3', 'Nvidia GTX1050']
    }

stock = {
    '8475HD': [387990,10], 
    '2175HD': [327990,4], 
    'JjfFHD': [424990,1],             
    'fgdxFHD': [664990,21], 
    '123FHD': [290890,32],
    '342FHD': [444990,7], 
    'GF75HD': [749990,2], 
    'UWU131HD': [349990,1], 
    'FS1230HD': [249990,0]
                 }
def error():
    print("Debe seleccionar una opción válida!!")

def stock_marca(marca):
    cant =0
    for modelo, datos in productos.items():
        if datos[0].upper() == marca.upper():
            if modelo in stock:
                cant += stock[modelo][1]
    print(f"El stock es: {cant}")

def Búsqueda_por_precio():
    try:
        precio_minimo = int(input("Ingrese precio mínimo : "))
        precio_maximo = int(input("Ingrese precio máximo : "))
    except ValueError:
        error()
        return
    cant = 0
    for modelo, datos in stock.items():
        precio = datos[0]
        cantidad = datos[1]
        if precio_minimo <= precio <= precio_maximo:
            cant += cantidad
    print(f"El stock entre ${precio_minimo} y ${precio_maximo} es: {cant}")


def eliminar_producto(modelo):
    while True:
        if modelo in productos:
            productos.pop(modelo)
            stock.pop(modelo, None)
            print("Producto eliminado!!")
        else:
            print("El modelo no existe!!")
        try:
            validar = input("¿Desea eliminar otro producto (s/n)?: ").strip().upper()
            if validar in ("S", "SI"):
                modelo = input("Ingrese modelo a eliminar: ").strip()
                continue
            elif validar in ("N", "NO"):
                break
            else:
                error()
        except ValueError:
            error()
            
while True:
    try:
        op=int(input("""
        *** MENU PRINCIPAL *** 
        1.	Stock marca. 
        2.	Búsqueda por precio. 
        3.	Eliminar producto. 
        4.	Salir
        """))
    except ValueError:
        error()
    if op == 1 :
        marca=input("Ingrese marca : ")
        stock_marca(marca)
    elif op == 2 :
        Búsqueda_por_precio()
    elif op == 3 :
        modelo=input("Ingrese modelo a actualizar : ")
        eliminar_producto(modelo) 
    else:
         print("Programa finalizado.")
         break    
