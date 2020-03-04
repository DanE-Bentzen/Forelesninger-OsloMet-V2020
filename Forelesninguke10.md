# Forelesing uke 10

Denne uken skal vi se på:
 - Errorhåndtering
 - Teste programmer


### Error-håndtering

Vi ønsker noen ganger å "fakke" feil før de forekommer, slik at vi kan unngå fatale feil, eller andre ting som kan skape problemer i programmet vårt. Det er en innebygget funksjon i Python bibloteket som heter __assert__. La se på noen eksempler for hvordan __assert__ fungerer  


```python
def divisjon(a, b):
	assert b != 0, "Du kan ikke dele på null"
	return a/b


a = float(input("les inn tall: "))
b = float(input("les inn tall: "))

x = divisjon(a, b)
print(x)
```

    les inn tall:  1
    les inn tall:  0
    


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-1-47585c21e3da> in <module>
          7 b = float(input("les inn tall: "))
          8 
    ----> 9 x = divisjon(a, b)
         10 print(x)
    

    <ipython-input-1-47585c21e3da> in divisjon(a, b)
          1 def divisjon(a, b):
    ----> 2         assert b != 0, "Du kan ikke dele på null"
          3         return a/b
          4 
          5 
    

    AssertionError: Du kan ikke dele på null


Her legger vi merke til at __assert__ kun aktiveres hvis det logiske utsagnet er lik __False__. Som dere ser kan vi også lage egne feil meldinger, og få programmet til å stoppe for ting som normalt Python ikke vil stoppe for. 


```python
def gjennomsnittsalder(alders_liste):
	gjennomsnitt = 0
	for alder in alders_liste:
		gjennomsnitt += alder/len(alders_liste)
		assert alder >= 0, "Alder mindre enn null er ikke definert!"
	return gjennomsnittsalder

liste = []

for inp in range(5):
	liste.append(float(input("Alder: ")))
gjennomsnittsalder(liste)
```

    Alder:  1
    Alder:  2
    Alder:  3
    Alder:  4
    Alder:  -5
    


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-2-257407a6a140> in <module>
         10 for inp in range(5):
         11         liste.append(float(input("Alder: ")))
    ---> 12 gjennomsnittsalder(liste)
    

    <ipython-input-2-257407a6a140> in gjennomsnittsalder(alders_liste)
          3         for alder in alders_liste:
          4                 gjennomsnitt += alder/len(alders_liste)
    ----> 5                 assert alder >= 0, "Alder mindre enn null er ikke definert!"
          6         return gjennomsnittsalder
          7 
    

    AssertionError: Alder mindre enn null er ikke definert!


Noen ganger ønsker å vi fortelle Python nøyaktig hva den skal gjøre i enkelte situasjoner. Det er enten fordi det er en feil som Python ikke klarer å plukke opp, som gjør at programmet fortsetter med feil resultat. Eller noen ganger kommer vi utenfor feil som vi vet hvordan vi skal kode oss, men derfor trenger at fortsetter uten å kræsje. For dette introduserer vi noen kalles en __try-except__ blokk. Syntaksen er veldig lik en __if-else__ blokk 


```python
try:
    # forsøk å gjøre det som står i denne blokken
    x = str(y)
    
    # Forvent den type error som står etter except utsagnet
except Error: # Dette er en generell error plukker alle feil, MEN må brukes med varsomhet 
    
    # Hvis error forekommet, gjør det som står denne blokken
    print('Operasjonen du forsøkte å gjøre med y kan ikke gjøres')
    # Videre er det vanlig å fortelle hva programmet hvordan det skal fortsette
    pass # ikke gjøre noen ting, fortsette som programmet videre etter blokken
    break # Hvis try-except er en del av if-else eller loop kan denne brukes til å bryte ut av loopen
    continue # Hvis try-except er en del av if-else eller loop kan denne brukes til å fortesette loppen, men skippe denne iterasjonen
    close() # Hvis du ønsker å stenge en fil du har åpnet i try blokken   
    
```

I python finnes det en rekke ferdige lagede feilmeldinger vi også kan bruke. Dere har nok allerede sett mange av de. Det er ofte de feilmeldingene vi får ut i terminalen når programmet kræsjer.

#### Python Built-in Exceptions 
__Exception	Cause of Error__ \
__AssertionErro__ rRaised when assert statement fails. \
__AttributeError__	Raised when attribute assignment or reference fails. \
__EOFError__	Raised when the input() functions hits end-of-file condition. \
__FloatingPointError__	Raised when a floating point operation fails. \
__GeneratorExit__	Raise when a generator's close() method is called.\
__ImportError__	Raised when the imported module is not found.\ 
__IndexError__ Raised when index of a sequence is out of range.\
__KeyError__	Raised when a key is not found in a dictionary. \
__KeyboardInterrupt__	Raised when the user hits interrupt key (Ctrl+c or delete). \
__MemoryError__	Raised when an operation runs out of memory. \
__NameError__	Raised when a variable is not found in local or global scope. \
__NotImplementedError__	Raised by abstract methods. \ 
__OSError__	Raised when system operation causes system related error. \
__OverflowError__	Raised when result of an arithmetic operation is too large to be represented. \
__ReferenceError__	Raised when a weak reference proxy is used to access a garbage collected referent. \
__RuntimeError__	Raised when an error does not fall under any other category. \
__StopIteration__	Raised by next() function to indicate that there is no further item to be returned by iterator. \
__SyntaxError__	Raised by parser when syntax error is encountered. \
__IndentationError__	Raised when there is incorrect indentation. \
__TabError__	Raised when indentation consists of inconsistent tabs and spaces. \
__SystemError__	Raised when interpreter detects internal error. \
__SystemExit__	Raised by sys.exit() function. \
__TypeError__	Raised when a function or operation is applied to an object of incorrect type. \
__UnboundLocalError__	Raised when a reference is made to a local variable in a function or method, but no value has been bound to that variable. \
__UnicodeError__	Raised when a Unicode-related encoding or decoding error occurs. \
__UnicodeEncodeError__	Raised when a Unicode-related error occurs during encoding. \
__UnicodeDecodeError__	Raised when a Unicode-related error occurs during decoding. \
__UnicodeTranslateError__	Raised when a Unicode-related error occurs during translating. \
__ValueError__	Raised when a function gets argument of correct type but improper value. \
__ZeroDivisionError__	Raised when second operand of division or modulo operation is zero. \

Eksempel:


```python
import numpy as np
import matplotlib.pyplot as plt
import itertools

y1_data = [1, 3, 4, 3, 2, '5', 1, 4, 5]
y2_data = [2, 3, 2, 4, 3, 4, 5, 6, 1]



y_data = []

i = 0

for y1, y2 in zip(y1_data, y2_data):
    i += 1
    try:
        y_data.append(y1+y2)
    except TypeError:
        print(f'Ved iterasjon {i} var ikke y1 = {type(y1)} og  y2 = {type(y2)} av samme datatype')
        continue

x_data = np.linspace(0, 10, len(y_data))


plt.plot(x_data, y_data)
plt.show()
    
```

    Ved iterasjon 6 var ikke y1 = <class 'str'> og  y2 = <class 'int'> av samme datatype
    


![png](output_12_1.png)


I eksempelet over har vi klart å behandle korrupt data, og gjennomføre det vi ønsket at programmet skulle utføre for oss.

Eksempel med filbehandling


```python
try:
    with open('text.txt', 'r') as f:
        x = load(f)
except FileNotFoundError:
    print("Filen eksisterer ikke!")
    exit() # stenger programmet
```

    Filen eksisterer ikke!
    

Ved å kombinere __try-except__ og __assert__ kan vi lage våre egne feilmeldinger, og bestemme hvordan Python håndterer feilmeldingene


```python
alders_liste = [2, 3, 4, 5, -3, 2]
teller = 0
gjennomsnitt = 0
for alder in alders_liste:	
    try:		
        gjennomsnitt += alder		
        assert alder >= 0 	
    except AssertionError:		
        print("Alder mindre enn null er ikke definert!")		
        continue	
    else:		
        teller += 1


print(gjennomsnitt/teller)
```

    Alder mindre enn null er ikke definert!
    2.6
    

### Testing av programmer

Dette er en viktig del av det å programmere. Men hva vil det si å teste et program? Jo, det har vi gjort mange ganger! Hver gang vi gjør en utskrift i terminalen for å sjekke at resultatet stemmer, type-sjekker eller at har riktig logisk verdi. Men som alt når vi programmerer så ønsker vi å automatisere prosessen. Vi velger i dette kurset å skrive alle testene manuelt. Det finnes integrerte systemer i Python som unit-testing, men det er et godt stykke forbi hva vi skal snakke om i dette kurset.  

En god filosofi når tester et program er:
 - Hva forventer brukeren at programmet skal levere(output), dette må testes!
 - Hvilke funksjonaliteter(f.eks metoder) finnes i programmet, dette må testes!


Vi lager gjerne et eget testprogram men navn _test\_<navn på program som testes>.py_. Her kan vi benytte oss av __try-except__ og __assert__ for å teste programmet. 

La oss se på eksempelet der vi denne klassen

_fil: geometri.py_


```python
import math

class Geometri:
	def __init__(self, radius, lengde):
		self.radius = radius 
		self.lengde = lengde


	def areal(self):
		areal_sirkel = math.pi*self.radius**2
		areal_kvadrat = self.lengde**2
		return areal_sirkel, areal_kvadrat

	def volum(self):
		volum_sirkel = (4/3)*math.pi*self.radius**3
		volum_kube = self.lengde**3
		return volum_sirkel, volum_kube

```

Vi lager så et testprogram

_fil: test\_geometri.py_


```python
from geometri import Geometri
import math

def test_areal():
	radius = 3.0
	lengde = 10.0
	forv_sirk = math.pi*radius**2  # forventet areal av en sirkel med radius 3
	forv_kvad = lengde**2  # forventet areal av et kvadrat med lengde 10
	
	areal_objekt = Geometri(radius, lengde)
	berg_sirk, berg_kvad =  areal_objekt.areal() # metoden returner en tuppel, derfor "unpacker" vi

	epsilon = 1E-15 # lager en svært liten verdi som feilmargin, dette skyldes flyttalls estimering 
	try:
		assert abs(forv_sirk - berg_sirk) < epsilon, "funket dette?" # dette er selve testen
	except AssertionError:
		 print("Areal av sirkel ble beregnet feil")
	try:
		assert abs(forv_kvad - berg_kvad) < epsilon
	except AssertionError:
		print("Areal av kvadrat ble beregnet feil")

test_areal()



def test_volum():
	radius = 3.0
	lengde = 10.0
	forv_kule = (4/3)*math.pi*radius**3 # forventet volum av en kule med radius 3 
	forv_kube = lengde**2 # forventet volum av en kube med sider av lengde 10
	
	volum_objekt = Geometri(radius, lengde)
	volum_kule, volum_kube = volum_objekt.volum() # "unpacker"
	epsilon = 1E-15

	try:
		assert abs(forv_kule - volum_kule) < epsilon, "funket dette?" # dette er selve testen
	except AssertionError:
		 print("Volumet av kulen ble beregnet feil")
	try:
		assert abs(forv_kube - volum_kube) < epsilon
	except AssertionError:
		print("Volumet av kuben ble beregnet feil")

test_volum()
```

Vi har nå testet all funksjonalitet vi ønsker fra programmet. 
