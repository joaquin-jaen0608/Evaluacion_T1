import random

class Equipo:
    def __init__(self, nom):  
        self.nombre = nom
        self.partidosGanados = 0
        self.partidosPerdidos = 0
        self.setGanados = 0

def RegistraSet(equipo1, equipo2, ganador_num):
    if ganador_num == 1:
        equipo1.setGanados += 1
        if equipo1.setGanados == 3:
            equipo1.partidosGanados += 1
            equipo2.partidosPerdidos += 1
            equipo1.setGanados = 0
            equipo2.setGanados = 0
    elif ganador_num == 2:
        equipo2.setGanados += 1
        if equipo2.setGanados == 3:
            equipo2.partidosGanados += 1
            equipo1.partidosPerdidos += 1
            equipo1.setGanados = 0
            equipo2.setGanados = 0

def Puntos():
    return random.randint(10, 28)

def PuntosExtras():
    return random.randint(0, 6)

def JugarPartido(equipo1, equipo2):
    while equipo1.setGanados < 3 and equipo2.setGanados < 3:
        puntos1 = Puntos()
        puntos2 = Puntos()

        while puntos1 < 25 and puntos2 < 25:
            puntos1 += PuntosExtras()
            puntos2 += PuntosExtras()
            print(f"Puntos extra: {equipo1.nombre}: {puntos1}, {equipo2.nombre}: {puntos2}")

        if puntos1 >= 25 and puntos1 > puntos2:
            RegistraSet(equipo1, equipo2, 1)
            print(f"{equipo1.nombre} gana el set con {puntos1} vs {puntos2}")
        else:
            RegistraSet(equipo1, equipo2, 2)
            print(f"{equipo2.nombre} gana el set con {puntos2} vs {puntos1}")

def ResultadoTorneo(equipo1, equipo2):
    print("\nResultados finales:")
    print(f"{equipo1.nombre} - Ganados: {equipo1.partidosGanados}, Perdidos: {equipo1.partidosPerdidos}")
    print(f"{equipo2.nombre} - Ganados: {equipo2.partidosGanados}, Perdidos: {equipo2.partidosPerdidos}")

if __name__ == "__main__":  
    nombre1 = input("Equipo 1: ")
    nombre2 = input("Equipo 2: ")

    equipo1 = Equipo(nombre1)
    equipo2 = Equipo(nombre2)

    partidos_jugados = int(input("¿Cuántos partidos deben jugar?: "))

    for _ in range(partidos_jugados):
        JugarPartido(equipo1, equipo2)

    ResultadoTorneo(equipo1, equipo2)


