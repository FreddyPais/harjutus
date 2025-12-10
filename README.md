class Soiduk:
    def __init__(self, mark: str, aasta: int, kiirus: int = 0):
        self.mark = mark
        self.aasta = aasta
        self.kiirus = kiirus
        self.labisoit = 0
        
    def soida(self, km: float):
        self.labisoit += 0
        print(f"{self.mark} sõitis {km} km. Kokku läbitud: {self.labisoit} km.")
        
class Auto(Soiduk):
    def __init__(self, mark: str, aasta: int):
        super().__init__(mark, aasta)
        self.kytus = 0.0
        
    def kiirenda(self):
        if self.kytus >= 0.5:
            if self.kiirus + 10 <= 200:
                self.kiirus += 10
                self.kytus -= 0.5
                print(f"Auto kiirendas. Kiirus: {self.kiirus} km/h, kütus: {self.kytus} l")
            else:
                prit(f"Kiirus ei saa ületada 200 km/h.")
                
    def tankida(self, liitrid: float):
        enne = self.kytus
        self.kytus = min(60, self.kytus + liitrid)
        print(f"Kütus tõusis {enne} -> {self.kytus} l")
        
class Jalgratas(Soiduk):
    def __init__(self, mark: str, aasta: int):
        super().__init__(mark, aasta)
        self.ratturiEnergia = 100
        
    def kiirenda(self):
        if self.ratturiEnergia >= 10:
            if self.kiirus + 5 <= 200:
                self.kiirus += 5
                self.ratturiEnergia -= 10
                print(f"Jalgratas kiirendas. Kiirus: {self.kiirus} km/h, energia: {self.ratturiEnergia}")
            else:
                print("Kiirus ei ületa 200 km/h.")
        else:
            print("Pole piisavalt energiat kiirendamiseks!")
            
    def puhka(self, minutid: int):
        taastub = minutid / 2
        enne = self.ratturiEnergia
        self.ratturiEnergia = min(100, self.ratturiEnergia + taastub)
        print(f"Energiat taastati {enne} -> {self.ratturiEnergia}")
        
print("Auto test")
auto = Auto("Toyota", 2015)
auto.tankida(20)
auto.kiirenda()
auto.kiirenda()
auto.soida(50)

print("jalgratta test")
ratas = Jalgratas("Trek", 2022)
ratas.kiirenda()
ratas.kiirenda()
ratas.puhka(30)
ratas.soida(12)
