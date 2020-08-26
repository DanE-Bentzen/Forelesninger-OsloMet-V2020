

```python
import nbconvert
```


# Uke 3. 

Denne uken vil vi gå igjennom:
    - Python syntaks
    - Datatyper
    - Variabler og operatorer
    - Printformatering
    - Lese variabler inn fra terminalvinduet

# Hva er Python?

Python er et "høynivå" objektorientert dynamisk programeringsspråk. Laget av matematikkeren Guido van Rossum i 1989, og ga språket navnet "Python" fordi han var fan av Monthy python. Språket er i hovedsak bygget på C og er et av de mest brukte programeringsspråkene i dag.

# Hvorfor programmere i Python?
    - Det går fort å utføre store komplekse oppgaver
    - Veldig enkelt å bygge egne bibloteker
    - Enkelt lesbar kode. Nesten som å skrive pseudokode i C  
    - "Open source" og gratis
    - Uendelig mengder med bibloteker

# Noen ulemper
 - Ikke like effektivt som f.eks C eller Java
 - Stort minneforbruk
 - Ikke spesielt egnet for mobilløsninger eller databaser
 

# Første program "helloworld.py":
Print teksten 'hello world!' ut i terminalen


```python
print("hello world!") 
```

    hello world!
    

# Datatyper

Datatype strings


```python
minString = "abc"
minString1 = "3.14"
print(minString)
print(minString1)
```

    abc
    3.14
    

Datatype heltall/integer(int)


```python
tall1 = 2
tall2 = -1000
print(tall1 + tall2)# merk at du kan bruke operatorer inne i printfunksjonen 
float(2)
```

    -998
    




    2.0



Datatype decimaltall/flyttall(float)


```python
desimaltall1 = 1.11
desimaltall2 = 3.14
print(desimaltall1, desimaltall2) # Bruk komma i printfunksjonen for å print flere objekter i samme printfunksjon
int(desimaltall1)
```

    1.11 3.14
    




    1



Tips! Typesjekk:


```python
variabel1 = -10
print(type(variabel1)) # Printer hvilken klasse/datatype objektet tilhører
```

    <class 'int'>
    

Merk at Python autodefinerer datatype. 

F.eks:


```python
x = 2.1 # blir automatisk til en float siden punktum er benyttet
y = 32 # blir automatisk til en integer
z = x + y
w = x*y
print(w)
print(type(w))
print(z, type(z)) # float og integer blir automatisk til et flyttall

```

    67.2
    <class 'float'>
    34.1 <class 'float'>
    




    'heihei'



# Variabler 

Variabler er dynamiske, og trenger ikke å deklareres på forhånd


```python
a = 10
b = 1
c = b
print(c)
```

    1
    

Enkle matematiske operatorer:

| Operator | Navn |
| -------- | ---- |
| + | pluss |
| - | minus |
| * | gange |
| ** | eksponent |
| % | modulus |
| // | gulvdivison |


```python
print(a + b, a - b, a/10, a**2, b%a) #  Merk "^" fungerer ikke i python. 

# Lese inn variabler fra terminalen
```

    11 9 1.0 100 1
    


```python
innlest_variabel = input("Skriv inn variabel her ") # Teksten som blir satt i anførselstegn blir printet i terminalen.
```

    Skriv inn variabel her sdfsd
    

input() minner om scanf() fra C. Men det er en viktig forskjell

# Andre program "sirkel.py"

Vi skal lage et program som leser inn radius av en sirkel i terminalen. Programmet skal så printe ut både areal og omkrets av sirkelen


```python
pi = 3.14
radius = input("Skriv inn radius ")

areal = pi*radius**2
omkrets = pi*omkrets

print("areal =", areal)
print("omkrets =", omkrets)
```

Hva gikk galt?

Alt som leses inn fra terminalen ved hjelp av input() blir autodefinert til string, og string kan ikke summeres med float eller int. Her må vi typekonverte


```python
radius = input("Skriv inn radius ")
areal = pi*float(radius)**2
omkrets = pi*float(radius)
print("areal =", areal)
print("omkrets =", omkrets)
```

    Skriv inn radius 345345
    


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-3-23e1477fa37a> in <module>
          1 radius = input("Skriv inn radius ")
    ----> 2 areal = pi*float(radius)**2
          3 omkrets = pi*float(radius)
          4 print("areal =", areal)
          5 print("omkrets =", omkrets)
    

    NameError: name 'pi' is not defined


# Printformatering

Formatering av utskrift i terminalen fungerer på akkurat samme måte som printf() i C. Men syntaksen er noe annerledes


```python
mitt_navn = "Dan"
etternavn = "Bentzen"
print(f"Jeg heter {mitt_navn} {etternavn}") # f-string. Nytt av python 3.6

print("jeg heter {} {}".format(mitt_navn, etternavn)) # Eldre syntaks

pi = 3.14159265359

print(f"Pi avrundet til tre desimaler: {pi:.3f}") # Trunkering med f-string
```

# Lister
Det finnes flere typer. Vi skal se på de tre viktigste arrays, tuppel og ordbok

Arrays:


```python
myArray = [1, 2, 3, 100] # Liste av objekter
myArray1 = ["Dan", 3.14, 10] # Kan inneholde forksjellige datatyper 
myArray2 = [1, 2, [3, 4]] # Kan også inneholde arrays
```



Arrays er dynmiske og enkle å jobbe med


```python
sum_av_arrays = myArray + myArray1
print(sum_av_arrays) # Printer myArray forlenget med myArray1

print(myArray1[0]) # Elementene i arrayet nåes enkelt ved å indeksere elementet. Merk at Python nesten alltid indekser fra 0

print(myArray[-1]) # Negtive tall indekserer bakover i listen. Her printes siste element i myArray.


print(myArray2[2][-1]) # For å nå de indre elementene i liste inne i en liste legger man til en ekstra indeksering
```

    [1, 2, 3, 100, 'Dan', 3.14, 10]
    Dan
    100
    4
    


```python
myArray[1] = 10000 # For å bytte element lagerer vi verdien til den på indeksen vi ønsker verdi
myArray
```




    [1, 10000, 3, 100]



For legge til enkelt elementer bruker vi append() 


```python
myArray2.append(2) #Legger til elementet på siste plass i listen

print(myArray2)
```

    [1, 2, [3, 4], 'siste element', 2]
    

Array er hva vi kaller "mutable" objekt. Dvs. når objektet(arrayet) er opprettet så kan det endres


```python
Tuple:
```


```python
myTuple = (1, 2, 5)

myTuple = ("a", "b", "c")

myTuple[0]= "d" # Dette gir feimelding fordi tupler er hva vi kaller "immutable" objekter. En tuppel kan ikke endres etter den er opprettet
```

Fordelen med tupler er effektivitet og minneforbruk.

Ordbok/dictionaries


```python
handleliste = {
    "banan" : 4.90, # Viktig, husk komma mellom elementene
    "brød" : 17.90,
    "melk" : 15.90,
}
handleliste["melk"] = 16.9
print(handleliste["melk"])
```

    16.9
    

Dictonarie fungerer som en ordbok, du får ut hva som ligger lagret på akkurat dette variabel navnet. 

Legge til element


```python
myDict["sjokolade"] = 10.90 # Her ser vi at dict er et mutable objekt, objektet kan endres etter at det er lagt til
print(handleliste)
```

# Kontrolflyt if, else, or, and etc...

Logiske sjekker for uttrykk, dette fungerer akkurat som i C


```python
a = 10


if a <11: # Bruker kolon for å starte if-blokken
    print("a er mindre enn 11")
    
elif a > 11: # Betyr det samme som "if else" i C
    print("a er større enn 11")

else: 
    print("a er lik 11")
    

```

Viktig! Innrykk teller i Python. Lager vi et logisk uttrykk uten innrykk får vi feilmelding. Noen foretrekker å bruke "tab", andre bruker dobbel space. Ingen av delene er feil, men det er viktig å være konsistent i koden. Altså, bruke det samme gjennom hele koden.

Her er noen enkle logiske operatorer

| Operator | Navn |
| -------- | ---- |
| `==`     | Er lik |
| `!=` | Ikke lik |
| `>` | Større enn |
| `<` | Mindre enn |
| `>=` | Større eller lik |
| `<=` | Mindre eller lik|


```python

```
