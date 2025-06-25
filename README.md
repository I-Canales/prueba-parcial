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

 
