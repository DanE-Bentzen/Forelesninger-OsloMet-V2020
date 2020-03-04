# Forelesning uke 5

##### Denne uken skal vi se på:
- Klasser og objekter
- Dunder/magiske-metoder

Forrige uke så vi på hvordan vi kunne bruke funksjoner
til å strukture og gjennbruke koden vi allerede har laget i samme program.
Hva om vi ønsker å gjennbruke andre programmer vi har laget?
Eller funksjoner vi har bygget i andre programmer? Det er her klasser kommer inn!

Det er 3 viktige uttrykk dere jeg kommer til å gjennta til det kjedsommelige:

1. objekter
2. instanser
3. metoder

Vi starter med en ganske så kjedelig klasse


```python
class Startup:
	pass

# Oppretter objekter
ansatt_1 = Startup() # Objektet "ansatt_1"
ansatt_2 = Startup() # Objektet "ansatt_2"

print(ansatt_1) # printer vi denne får vi kun ut minneadresse
print(ansatt_2) # Samme her

```

    <__main__.Startup object at 0x0000017DDA96CDC8>
    <__main__.Startup object at 0x0000017DDA96C048>
    

Men hva om vi ønsker å tillegge egenskaper til medlemene i klassen?
Det gjør vi ved å opprette instanser, eller egenskaper om vi vil.


```python
ansatt_1.fornavn = "Dan"
ansatt_1.etternavn = "Bentzen"
ansatt_1.epost = "dan.bentzen@jakobsenrakettstartup.no"


ansatt_2.fornavn = "John"
ansatt_2.etternavn = "Jakobsen"
ansatt_2.epost = "john.jakobsen@jakobsenrakettstartup.no"

# Her ser vi at instansen til objekt har lagret informasjonen
print(ansatt_1.fornavn) 
print(ansatt_1.etternavn)
print(ansatt_1.epost)


print(ansatt_2.fornavn)
print(ansatt_2.etternavn)
print(ansatt_2.epost)

```

    Dan
    Bentzen
    dan.bentzen@jakobsenrakettstartup.no
    John
    Jakobsen
    john.jakobsen@jakobsenrakettstartup.no
    

Men er dette noe mer effektivt enn å opprette variabler som lagrer
disse verdiene? Nei. La oss utvide klassen med noe som heter en konstruktør, også kalt init-metode

Vi starter klassen med å sette init-metode med argumentene som skal sendes til klassen.
Første argumentet har en spesiell plass, dette er instansevariablen. Denne må ikke hete self, men det
normen. Dette er som vi gjorde når vi satte "ansatt_1.etternavn", men nå har vi en variabel som tar med seg alle egenskaper 
som er lagret på variablen.


```python
class Startup:
	def __init__(self, fornavn, etternavn): 
		self.fornavn = fornavn
		self.etternavn = etternavn



ansatt_1 = Startup('John', 'Jakobsen')
ansatt_2 = Startup('Aleksander', 'Rømbøkk')


# Legg merke til ansatt_1 og ansatt_2 fremdeles er objekter
print(ansatt_1)
print(ansatt_2)

# Men vi kan hente ut enkelte instanser
print(ansatt_1.etternavn)
print(ansatt_2.fornavn)
```

    <__main__.Startup object at 0x0000017DDA9836C8>
    <__main__.Startup object at 0x0000017DDA9801C8>
    Jakobsen
    Aleksander
    

Ok, da har vi klart å effektivisere litt til. La oss effektivisere mer

Lager klassen med en metode


```python

class Startup:
	def __init__(self, fornavn, etternavn): 
		self.fornavn = fornavn
		self.etternavn = etternavn	
		# metoden epost

		"""Lag denne først uten self argumentet"""	
	def epost(self):
		return self.fornavn +'.'+ self.etternavn + '@jakobsenrakettstartup.no'


ansatt_1 = Startup('John', 'Rømbøkk')


print(ansatt_1.epost())
```

    John.Rømbøkk@jakobsenrakettstartup.no
    

Her må analysere feilmeldingen. Feilmeldingen sier at vi sendte en 
et argument feil til metoden vår. Men vi sendte ingen? Jo, dette skyldes at self blir autmatisk sendt til funksjoner.
Vi altså spesifisere at self skal inn i metoden!

Vi har nå opprettet en metode. Der metoden returnerer en string med standard formatet på en epost 

La oss opprette enda en metode: en som returnerer det fulle navnet til den ansatte


```python
class Startup:
	def __init__(self, fornavn, etternavn): 
		self.fornavn = fornavn
		self.etternavn = etternavn	

	def epost(self):
		return self.fornavn + self.etternavn + '@jakobsenrakettstartup.no'

	def fullt_navn(self):
		return self.fornavn + '.' + self.etternavn

```

Vi legger til enda en metode som returnerer årslønnen til hver ansatt, der vi også tar med årlig lønnsforhøsforhøyelse


```python
class Startup:
	def __init__(self, fornavn, etternavn, loenn): 
		self.fornavn = fornavn
		self.etternavn = etternavn	
		self.loenn = loenn

		# metoden epost

		"""Lag denne først uten self argumentet"""	
	def epost(self):
		return self.fornavn + self.etternavn + '@jakobsenrakettstartup.no'

	def fullt_navn(self):
		return self.fornavn + ' ' + self.etternavn

	def forhoyelse(self): # Merk at det ikke er brukt et return-statement her
		self.loenn = self.loenn*1.05

```


```python
# Oppretter nytt objekter med nye parametere
ansatt_2 = Startup('John', 'Jakobsen', 300000)

print(ansatt_2.loenn)

"""Hva skjer om vi kaller på forhoyelse?"""

ansatt_2.forhoyelse()
# Her er forhøyelsen lagret til instansen "loenn" til objektet ansatt

print(ansatt_2.loenn)

# Her sere dere at forhøyelsen er lagt enda en gang

ansatt_2.forhoyelse()

# Loennen har blitt lagt til enda en gang
print(ansatt_2.loenn)
```

    300000
    315000.0
    330750.0
    

La introdusere enda et nytt konsept: Klassevariabler


```python
class Startup:
	forhoyelsesats = 1.05 # klassevaribler må legges på utisden av init-metoden
	def __init__(self, fornavn, etternavn, loenn): 
		self.fornavn = fornavn
		self.etternavn = etternavn	
		self.loenn = loenn


	def epost(self):
		return self.fornavn + self.etternavn + '@jakobsenrakettstartup.no'

	def fullt_navn(self):
		return self.fornavn + '.' + self.etternavn

	def forhoyelse(self): # Merk at det ikke er brukt et return-statement her
		self.loenn = self.loenn*self.forhoyelsesats



ansatt_1 = Startup('John', 'Jakobsen', 250000)




ansatt_1.forhoyelse()

print(ansatt_1.loenn)

```

    262500.0
    

Virker ikke dette noe mer tungvindt? Her er hvordan vi bruke klassevariabler


```python
ansatt_1.forhoyelsesats = 1.20
ansatt_1.forhoyelse()

print(ansatt_1.loenn)
```

    315000.0
    

Vi overlagrer verdien som ligger lagret på forhoyelse_sats=1.20

Vi kan også sjekke hvilken verdi som er lagret på forhoyelse_sats


```python
print(ansatt_1.forhoyelsesats)
ansatt_2 = Startup('John', 'Jakobsen', 300000)
print(ansatt_2.forhoyelsesats)
```

    1.2
    1.05
    

Her det en viktig detalje at endringen av klassevariablen kun blir lagret til den ansatte der vi brukte objektet.

Sett at vi hadde flere klassevariabler og mange ansatte, kunne vu ha fort mistet oversikten over hva som er lagret på hvem. Her får dere en "magisk"-metode som hjelper oss 


```python
print(ansatt_1.__dict__)
print(ansatt_2.__dict__)
```

    {'fornavn': 'John', 'etternavn': 'Jakobsen', 'loenn': 315000.0, 'forhoyelsesats': 1.2}
    {'fornavn': 'John', 'etternavn': 'Jakobsen', 'loenn': 300000}
    

Dette gir oss alle egenskapene/instanser som er lagret på objektet.

Vi kan også sende argumenter direkte til en metode uten å bruke "arv". 

La oss lage en ny metode "bonus" som også legger til en bonus, og tar argumentet "antall_solgt"


```python
class Startup:
	forhoyelsesats = 1.05
	def __init__(self, fornavn, etternavn, loenn): 
		self.fornavn = fornavn
		self.etternavn = etternavn	
		self.loenn = loenn


	def epost(self):
		return self.fornavn + self.etternavn + '@jakobsenrakettstartup.no'

	def fullt_navn(self):
		return self.fornavn + '.' + self.etternavn

	def forhoyelse(self): # Merk at det ikke er brukt et return-statement her
		self.loenn = self.loenn*self.forhoyelse_sats

	def bonus(self, antall_solgt):
		self.loenn = self.loenn + antall_solgt*1000
		return self.loenn 

ansatt_2 = Startup('John', 'Rune', 300000)
ansatt_2.forhoyelse_sats = 1.07
ansatt_2.forhoyelse()
ansatt_2.bonus(100)

print(ansatt_2.loenn)
```

    421000.0
    

I løpet av denne forelesningen ble introdusert et par spesielle metoder \_\_init\_\_ og \_\_dict\_\_. Dette er hva som kalles "double underscore methods", eller forkottet "dunder method" og "magic method". Dette er metoder som ligger lagret i pythonbibloteket med predefinert funksjonalitet. 

Disse forteller også noe hvordan operasjoner er definert i python. Vi husker fra tidligere når vi type-sjekket datatyper får vi en utskrift som ser ut som dette: 


```python
variabel1 = 1
variabel2 = "hello"
print(type(variabel1))
print(type(variabel2))
```

    <class 'int'>
    <class 'str'>
    

Vi observerer at den forteller oss at den hører at variablene tilhører en spesiel klasse 'int', 'str' etc. La oss på en litt tungvindt måte summere to tall 


```python
a = 1
b = 2
c = int.__add__(a, b) # tenk på c nå er et objekt!
print(c)
```

    3
    

La oss gjøre det samme for to strings


```python
string_1 = 'abc'
string_2 = 'def'
print(str.__add__(string_1, string_2))
```

    abcdef
    

Metoden \_\_add\_\_ fungerer helt forskjellig om objektet er tilknyttet klassen str eller int. Her er hvordan jeg liker å tenke på dette: siden alle datayper er et objekt tilknyttet en klasse i Python, så er de tillatte operasjonene de som er definert i klassen objektet tilhører. 

Kanskje en litt vanskelig setning å svelge, vi prøver å illustrere dette med å definere noen operasjonen på objekter i klassen Startup.

Hva vil det si det å bruke operasjonen '+' på to objekter i klassen Startup?


```python
print(ansatt_1 + ansatt_2)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-16-f60e822ef4dd> in <module>
    ----> 1 print(ansatt_1 + ansatt_2)
    

    TypeError: unsupported operand type(s) for +: 'Startup' and 'Startup'


Som feilmeldingen forteller oss; operasjonen '+' er ikke definert på objekter tilhørerende klassen Startup. La oss definere at det å summere to objekter fra klassen Startup betyr å summere lønnen til de ansatte 


```python
class Startup:
    forhoyelsesats = 1.05
    def __init__(self, fornavn, etternavn, loenn): 
        self.fornavn = fornavn
        self.etternavn = etternavn	
        self.loenn = loenn
        
    # her lager vi oss en instanse variabel som tilhører det andre objektet vi prøver å summere
    def __add__(self, other): 
        return self.loenn + other.loenn

    def epost(self):
        return self.fornavn + self.etternavn + '@jakobsenrakettstartup.no'

    def fullt_navn(self):
        return self.fornavn + '.' + self.etternavn

    def forhoyelse(self): # Merk at det ikke er brukt et return-statement her
        self.loenn = self.loenn*self.forhoyelse_sats

    def bonus(self, antall_solgt):
        self.loenn = self.loenn + antall_solgt*1000
        return self.loenn 

ansatt_2 = Startup('John', 'Rune', 300000)
ansatt_2.forhoyelse_sats = 1.07
ansatt_2.forhoyelse()
ansatt_2.bonus(100)

print(ansatt_2.loenn)
```

    421000.0
    

Vi tester operasjoen


```python
ansatt_1 = Startup('Aleksander', 'Rømbøkk', 100000) # lager nytt objekt 

print(ansatt_1 + ansatt_2)
```

    521000.0
    

Det fungerte! La oss definere enda en operasjon. Vi så tidligere at det å printe ut et objekt var en ganske uinteressant affære


```python
print(ansatt_1)
print(ansatt_2)
```

    <__main__.Startup object at 0x0000017DDA7AB048>
    <__main__.Startup object at 0x0000017DDA995EC8>
    

La oss gjøre noe med det


```python
class Startup:
    forhoyelsesats = 1.05
    def __init__(self, fornavn, etternavn, loenn): 
        self.fornavn = fornavn
        self.etternavn = etternavn	
        self.loenn = loenn
        
    # her lager vi oss en instanse variabel som tilhører det andre objektet vi prøver å summere
    def __add__(self, other): 
        return self.loenn + other.loenn
    
    def __str__(self):
        return f"Ansattnavn: {self.fornavn} {self.etternavn}"

    def epost(self):
        return self.fornavn + self.etternavn + '@jakobsenrakettstartup.no'

    def fullt_navn(self):
        return self.fornavn + '.' + self.etternavn

    def forhoyelse(self): # Merk at det ikke er brukt et return-statement her
        self.loenn = self.loenn*self.forhoyelse_sats

    def bonus(self, antall_solgt):
        self.loenn = self.loenn + antall_solgt*1000
        return self.loenn 

ansatt_2 = Startup('John', 'Rune', 300000)
ansatt_2.forhoyelse_sats = 1.07
ansatt_2.forhoyelse()
ansatt_2.bonus(100)

print(ansatt_2.loenn)
```

    421000.0
    


```python
print(ansatt_2)
```

    Ansattnavn: John Rune
    

Det finnes en masse slike "dunder"-metoder. Og det er det som definerer operasjoner i Python. Her finnes det en oversikt over disse https://docs.python.org/3/reference/datamodel.html#special-method-names


```python

```
