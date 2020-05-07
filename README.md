# class-Football-Player
Task about class Football player
class Sportista():

    def __init__(self, visina, ime, prezime, zemlja, broj_godina):
        self.visina = visina
        self.ime = ime
        self.prezime = prezime
        self.zemlja = zemlja
        self.broj_godina = broj_godina

    def prestupna_godina(self):
        danas = 2020
        self.godina_rodjenja = 2020 - self.broj_godina
        if self.godina_rodjenja % 4 == 0:
            return 'Sportista {} {} je rodjen prestupne godine. '.format(self.ime, self.prezime)
        else:
            return 'Sportista {} {} nije rodjen prestupne godine. '.format(self.ime, self.prezime)

    def savrsen_broj(self):
        lista_djelilaca = []
        suma_liste_djelilaca = 0
        for num in range(1,self.godina_rodjenja):
            if self.godina_rodjenja % num == 0:
                lista_djelilaca.append(num)
        for num in lista_djelilaca:
            suma_liste_djelilaca += num
        if suma_liste_djelilaca == self.godina_rodjenja:
            return 'Godina rodjenja {} sportiste {} {} je savrsen broj. '.format(self.godina_rodjenja, self.ime, self.prezime)
        else:
            return 'Godina rodjenja {} sportiste {} {} nije savrsen broj. '.format(self.godina_rodjenja, self.ime, self.prezime)

class Fudbaler(Sportista):

    rjecnik_fudbalera = {}

    def __init__(self, visina, ime, prezime, zemlja, broj_godina, pozicija, broj_golova):
        Sportista.__init__(self, visina, ime, prezime, zemlja, broj_godina)
        self.pozicija = pozicija
        self.broj_golova = broj_golova
        self.mail = self.ime + self.prezime + '@gmail.com '

    def ubaci_fudbalera(self):
        ime_prezime = self.ime + ' ' + self.prezime
        Fudbaler.rjecnik_fudbalera[ime_prezime] = self.pozicija

    def __add__(self, other):
        visina_svih_fudbalera = self.visina + other.visina
        return visina_svih_fudbalera

    def __mul__(self, other):
        visina_svih_fubalera = self.visina + other.visina
        proizvod = self.broj_godina * other.broj_godina + visina_svih_fubalera
        return proizvod

"""    def pozicija(self, upit_pozicija):
        upit_pozicija = input('Koja pozicija te zanima? ')
        for item in Fudbaler.rjecnik_fudbalera.items():
            if upit_pozicija in item:
                return item[0]"""



s1 = Sportista(180, 'Dragan', 'Draganovic', 'BiH', 1524)
s2 = Sportista(200, 'Mitar', 'Miric', 'Srbija', 30)
f1 = Fudbaler(190, 'Petar', 'Petrovic', 'Hrvatska', 33, 'golman', 1)
f2 = Fudbaler(160, 'Halid', 'Haliovic', 'Makedonija', 45, 'bek', 101)

print(s1.prestupna_godina())
print()
print(s1.savrsen_broj())
print()
f1.ubaci_fudbalera()
f2.ubaci_fudbalera()
print(f2.rjecnik_fudbalera)
print()
print(f1 + f2)
print(f1*f2)
print()
#print(f1.pozicija())
