# Uke 4

### Denne uken skal vi se på

#### Mer om kontrolflyt

- while og for

#### Funksjoner

- Prosedyrer
- Funksjoner med innput

## While-løkker

While løkken utfører alle instruksjoner inne i løkken, frem til det logiske utsagnet ikke lenger er sant. Dette er helt likt som i C. Kun litt annen syntaks


```python
n = 0

while n < 10: 
    print(f"n = {n}") # Husk indentering!
    n += 1 # Husk også å inkrementere n, ellers vil løkken gå til uendelig


```

## For-løkker 

Python for-løkker har noen andre egenskaper enn hva som er vanlig i en rekke andre programeringsspråk, blant annet C. Tellerverdien er ikke nødvendigvis et naturlig tall. Hva skjer om vi for eksempel teller over en liste med strings?


```python
list_of_animals = ["monkey", "rhino", "lion", "zebra"]

for animal in list_of_animals: # Tellervariablen "animal" kan vi gi hvilket navn vi vil
    print(animal) # Her printes verdien lagret i tellervariabelen.  
```

    monkey
    rhino
    lion
    zebra
    

Legg merke til valg av variabelnavn i forrige blokk. Leser vi koden som en setning ser vi at koden selv forklarer hva den gjør. Dette er hva kaller god "pythonic-code".

Legg også merke til Python selv finner lengden av listen. Noen ganger ønsker vi ikke å itere over en liste med elementer, da kan vi lage for-løkke i mer C-stil 


```python
sum_of_numbers = 0



for counter in range(0, 100, 1): # range() er en funskjon som tar følgende argumenter range(start, stop, steg størrelse)
    sum_of_numbers += counter # summen av alle tall mellom 0 og 99, husk at Python teller fra 0!
print(sum_of_numbers)

```

    4950
    

En nyttig funksjon når vi ikke skal bruke innholdet i en liste som inkrement, og vi ikke vet lengden av listen som vi skal iterere over er len().  

### largest_element.py
Find indeksen til det største tallet i listen list_of_numbers


```python
list_of_numbers = [6, 89, 19, 98, 99, 87, 18, 16, 32, 73, 14, 96, 64, 90, 28, 53, 69, 20, 29, 74, 94, 40, 26, 56, 8, 70, 35, 4, 5, 37, 15, 58, 83, 91, 78, 71, 86, 48, 62, 38, 79, 97, 59, 10, 92, 55, 47, 24, 44, 65, 50, 3, 57, 77, 33, 51, 21, 85, 93, 84, 81, 27, 75, 61, 95, 0, 63, 11, 43, 6, 39, 49, 1, 46, 67, 34, 82, 22]

print(len(list_of_numbers))

largest_number = 0
index_of_number = 0



for index in range(len(list_of_numbers)): 
    if list_of_numbers[index] > largest_number:
        index_of_number = index
        largest_number = list_of_numbers[index]

print(f"Det største tallet i listen lagret på indeks {index_of_number}")

```

    78
    Det største tallet i listen lagret på indeks 4
    

### Tre viktige utsagn for løkker
##### break 
Dette utsagnet får programmet til å "hoppe" ut av løkken, deretter fortsetter programmet

#### continue
Dette utsagnet får programmet til å "hoppe" over nåværende iterasjon av løkken, deretter fortsetter løkken på neste iterasjon

#### pass
Dette utsagnet får programmet til fortsette som før, dette er hva vi kaller et "null-statement". Og betyr helt enkelt; ingen tin skjer


```python
# break
for i in range(0, 50):
    if i == 25:
        break
    print(f"index = {i}")

print("Ute av loopen")
```

    index = 0
    index = 1
    index = 2
    index = 3
    index = 4
    index = 5
    index = 6
    index = 7
    index = 8
    index = 9
    index = 10
    index = 11
    index = 12
    index = 13
    index = 14
    index = 15
    index = 16
    index = 17
    index = 18
    index = 19
    index = 20
    index = 21
    index = 22
    index = 23
    index = 24
    Ute av loopen
    


```python
# continue
myList = [3, 9, 3, "4", 20, 5]
avarage = 0
number_of_elements = len(myList)

for element in myList:
    if type(element) != int:
        number_of_elements = number_of_elements - 1
        print(f"invalid type of element")
        continue
    avarage += element/number_of_elements

print(avarage)
```

    invalid type of element
    7.5
    


```python
for letter in 'Python': 
    if letter == "h":
        pass
        print ("This is pass block")
    print ("Current Letter :", letter)

print ("Good bye!")
```

    Current Letter : P
    Current Letter : y
    Current Letter : t
    This is pass block
    Current Letter : h
    Current Letter : o
    Current Letter : n
    Good bye!
    

### Nestede løkker(løkker i løkker)


compare_lists.py

Finn ut hvor mange tall som er i både list1 og list2


```python
list1 = [20, 27, 3, 18, 23, 30, 22, 10, 24, 17]
list2 =[16, 10, 29, 10, 19, 27, 29, 16, 24, 21]

counter = 0

for number1 in list1:
    for number2 in list2:
        if number1 == number2:
            counter += 1

            
            
print(counter)
```

    4
    

## Generere lister med løkker
harmonic_series_list.py

Lag en liste som består av de 20 første elementene i den harmoniske tallfølgen:
$\sum_{i = 0}^{20} \frac{1}{i+1}=\{1, \frac{1}{2},\dots ,\frac{1}{20}\}$


```python
harmonicSeries = []
element = 0

for n in range(20): # Hvis vi kun sender et tall som argument til range(), antar python start = 0 og step = 1
    element += 1/(n + 1)
    harmonicSeries.append(element)

print(harmonicSeries)
```

    [1.0, 1.5, 1.8333333333333333, 2.083333333333333, 2.283333333333333, 2.4499999999999997, 2.5928571428571425, 2.7178571428571425, 2.8289682539682537, 2.9289682539682538, 3.0198773448773446, 3.103210678210678, 3.180133755133755, 3.251562326562327, 3.3182289932289937, 3.3807289932289937, 3.439552522640758, 3.4951080781963135, 3.547739657143682, 3.597739657143682]
    

square_numbers_list_comprehension.py
Lag en liste med de 20 første kvadrattallene større enn 0 ved hjelp av "list comprehension" 
$\sum_{i=1}^{20} i*i = \{1, 4,\dots, 400\}$


```python
squareNumbers = [n*n for n in range(21) if n > 0]
print(squareNumbers)
```

    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
    

Formen listen over er laget på er \["formel";     "iterasjon med while eller for";      "filter med logisk utsagn"\]. Hva er fordelen med metoden som er brukt over? 
 - Den regnes som mer "pythonic". Altså mer lesbar
 - Er mer regneffektiv og bruker mindre minne

"List comprehensions" er nært beslektet til det som kalles lambda funksjoner og funksjonell programmering. Dette regnes som et programmeringsparadigme på lik linje med sekvensiel og objektorientert programmering. Men krever dessverre en del mer teori enn det vi rekker å dekke her.  

# Funksjoner
Ofte ender vi med å bruke samme kode/verktøy vi flere ganger i samme program. Her det naturlig at funksjoner kommer inn. Funksjoner i Python er enkle å bruke og minner om matematiske funksjoner. Funksjoner er også en god måte å strukturere kode på.

### Prosedyrer
Dette er egentlig en helt vanlig funksjon, men mentalt kan vi tenke annerledes på den. En funksjon uten innput kaller vi gjerne en prosedyre. 


```python
def print_prosedyre(): # prosedyren returnerer emn utskrift hver gang vi kaller på den
    a = 1
    return print("Printer hver gang du kaller på meg", a)

for i in range(10):
    print_prosedyre() # kall på prosedyren
```

    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    Printer hver gang du kaller på meg 1
    

Som vi ser, for å kalle på en prosedyre trenger vi kun å skrive navnet med paranteser () bak. Siden Python-tolkeren leser linje for linje når vi kjører programmet, ligger koden i funksjonen/prosedyren "død" frem til vi kaller på den. Men vi må selvfølgelig bygge den før vi kaller på den. 

# Funksjoner med Input

Input til en Python funksjon kan være hva som helst type object. For eksempel float, int, string, lister etc. Når vi sender input til en funksjon vil variablen være definert lokalt inne i funksjon. Funksjoner kan kun tolke variabler på utsiden av funksjoner hvis de er deklarert globalt.


```python
def sum_av_tall(x, y):
    return x + y

x_1 = 4

y_1 = 5

z = sum_av_tall(x_1, y_1)
print(z, type(z))
```

    9 <class 'int'>
    

Som dere ser i eksempelet under, er det mulig bruke globale variabler i Python. Men unngå dette størst mulig grad, da dette gir dårlig kontroll over koden. Koden blir også mindre lesbar. 


```python
global fornavn # Må deklareres på forhånd  
fornavn = "Dan" 

def mitt_navn(etternavn):
    return f"Mitt navn er {fornavn} {etternavn}"

mitt_navn("Bentzen")
```




    'Mitt navn er Dan Bentzen'



Du kan ha flere inputs til samme funksjon, og flere outputs


```python
def multiplikasjon_og_division(a, b):
    produkt = a*b
    divisjon = a/b
    return produkt, divisjon
c = multiplikasjon_og_division(3, 7)
print(c, type(c[1]))
```

    (21, 0.42857142857142855) <class 'float'>
    

Merk at et return med flere outputs returnerer en tuple med de forskjellige outputverdiene.
