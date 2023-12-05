def szyfruj(slowo, klucz):
    zaszyfrowane_slowo = ""
    for litera in slowo:
        if litera.isalpha():
            kod_litery = ord(litera)
            nowy_kod = (kod_litery + klucz) % 256
            zaszyfrowana_litera = chr(nowy_kod)
            zaszyfrowane_slowo += zaszyfrowana_litera
        else:
            zaszyfrowane_slowo += litera
    return zaszyfrowane_slowo


def main():
    klucz = 107

    with open("dane_6_1.txt", "r") as plik_wejsciowy:
        slowa = plik_wejsciowy.readlines()

    zaszyfrowane_slowa = [szyfruj(slowo.strip(), klucz) for slowo in slowa]

    with open("wyniki_6_1.txt", "w") as plik_wyjsciowy:
        for zaszyfrowane_slowo in zaszyfrowane_slowa:
            plik_wyjsciowy.write(zaszyfrowane_slowo + "\n")

if __name__ == "__main__":
    main()







def odszyfruj(szyfrogram, klucz):
    odszyfrowane_slowo = ""
    for litera in szyfrogram:
        if litera.isalpha():
            kod_litery = ord(litera)
            nowy_kod = (kod_litery - klucz) % 256
            odszyfrowana_litera = chr(nowy_kod)
            odszyfrowane_slowo += odszyfrowana_litera
        else:
            odszyfrowane_slowo += litera
    return odszyfrowane_slowo


def main():
    with open("dane_6_2.txt", "r") as plik_wejsciowy:
        dane = plik_wejsciowy.readlines()

    odszyfrowane_slowa = []
    for linia in dane:
        szyfrogram, klucz = linia.split()
        klucz = int(klucz)
        odszyfrowane_slowo = odszyfruj(szyfrogram, klucz)
        odszyfrowane_slowa.append(odszyfrowane_slowo)

    with open("wyniki_6_2.txt", "w") as plik_wyjsciowy:
        for odszyfrowane_slowo in odszyfrowane_slowa:
            plik_wyjsciowy.write(odszyfrowane_slowo + "\n")

if __name__ == "__main__":
    main()









def znajdz_bledy(slowo, szyfrogram):
    if len(slowo) != len(szyfrogram):
        return True
    for litera_slowa, litera_szyfr in zip(slowo, szyfrogram):
        if litera_slowa.isalpha() and litera_szyfr.isalpha():
            przesuniecie = ord(litera_slowa) - ord(litera_szyfr)
            if przesuniecie != 0:
                return True
    return False


def main():
    with open("dane_6_3.txt", "r") as plik_wejsciowy:
        dane = plik_wejsciowy.readlines()

    slowa_bledne = []
    for linia in dane:
        slowo, szyfrogram = linia.split()
        if znajdz_bledy(slowo, szyfrogram):
            slowa_bledne.append(slowo)

    with open("wyniki_6_3.txt", "w") as plik_wyjsciowy:
        for slowo_bledne in slowa_bledne:
            plik_wyjsciowy.write(slowo_bledne + "\n")

if __name__ == "__main__":
    main()








def szyfruj(slowo, klucz):
    zaszyfrowane_slowo = ""
    for litera in slowo:
        if litera.isalpha():
            kod_litery = ord(litera)
            nowy_kod = (kod_litery + klucz%26)
            if nowy_kod > ord("Z"):
                nowy_kod = nowy_kod - 26
            zaszyfrowana_litera = chr(nowy_kod)
            zaszyfrowane_slowo += zaszyfrowana_litera
        else:
            zaszyfrowane_slowo += litera
    return zaszyfrowane_slowo



klucz = 107

with open("dane_6_1.txt", "r") as plik_wejsciowy:
    slowa = plik_wejsciowy.readlines()

zaszyfrowane_slowa = [szyfruj(slowo.strip(), klucz) for slowo in slowa]

with open("wyniki_6_1.txt", "w") as plik_wyjsciowy:
    for zaszyfrowane_slowo in zaszyfrowane_slowa:
        print(zaszyfrowane_slowo)
        plik_wyjsciowy.write(zaszyfrowane_slowo + "\n")

