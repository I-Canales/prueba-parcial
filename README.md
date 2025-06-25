compradores = {}

def validar_codigo(codigo):
    if len(codigo) < 6:
        return False
    if " " in codigo:
        return False
    if not any(c.isupper() for c in codigo):
        return False
    if not any(c.isdigit() for c in codigo):
        return False
    return True

def comprar_entrada():
    nombre = input("Ingrese nombre del comprador: ").strip()
    if nombre in compradores:
        print("El comprador ya está registrado.")
        return

    tipo = input("Ingrese tipo de entrada (G = General, V = VIP): ").strip().upper()
    if tipo not in ['G', 'V']:
        print("Tipo de entrada inválido. Solo se acepta 'G' o 'V'.")
        return

    codigo = input("Ingrese código de confirmación: ").strip()
    if not validar_codigo(codigo):
        print("Código es invalido vuelva a intentar.")
        return

    compradores[nombre] = {"tipo": tipo, "codigo": codigo}
    print("Entrada registrada exitosamente.")

def consultar_comprador():
    nombre = input("ingrese el nombre del comprador: ").strip()
    if nombre in compradores:
        datos = compradores[nombre]
        print(f"Tipo de entrada: {datos['tipo']}")
        print(f"Código de confirmación: {datos['codigo']}")
    else:
        print("El comprador no se encuentra vuelva a intentar.")

def cancelar_compra():
    nombre = input("Ingrese nombre del comprador a cancelar: ").strip()
    if nombre in compradores:
        del compradores[nombre]
        print("¡Compra cancelada!")
    else:
        print("No se pudo cancelar la compra.")


def main():
    while True:
        print("\n~~MENU PRINCIPAL DE ENTRADAS~~")
        print("1.- Comprar entrada.")
        print("2.- Consultar comprador.")
        print("3.- Cancelar compra.")
        print("4.- Salir.")
        
        opcion = input("Seleccione una opción: ").strip()
        
        if opcion == '1':
            comprar_entrada()
        elif opcion == '2':
            consultar_comprador()
        elif opcion == '3':
            cancelar_compra()
        elif opcion == '4':
            print("GARCIAS POR USAR EL SISTEMA")
            break
        else:
            print("Debe ingresar una opción válida!")


if __name__ == "__main__":
    main()
