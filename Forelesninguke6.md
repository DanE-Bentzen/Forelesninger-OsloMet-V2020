# Forelesning uke 6

##### Denne uken skal vi se på:
 - Filbehandling
 - moduler
 - lage moduler
 - installere moduler
 


### Filbehandling

Hvordan kan vi arbeide med filer i Python? Her har Python noen ferdige enkle verktøy som gjør dette enkelt for oss.


```python
fil_objekt = open('test.txt', 'r')
fil_objekt.close()
```

Funksjonen open burde minst få to argumenter: string-navn på fil og hva den skal gjøre med filen. __open(navn_paa_fil, modus)__. Her har vi brukt __'r'__ som modus som betyr å kun lese fil.

Når lager et fil-objekt på denne måten er det viktig at vi lukker etter på. Dette er det flere grunner til, blant annet at vi hindrer 'garbage-collector' i Python å gjøre jobben sin, at en evt aplikasjon vi har laget bruker mer RAM enn nødvendig. Det er også flere grunner.

Forsøker vi printe fil_objekt ser vi at dette har blitt et objekt

__print(fil_objekt)__

Metoder vi kan bruke på dette objekter har vi noen eksempler på her


```python
fil_objekt = open('test.txt', 'r')
print(fil_objekt.name) # navn på fil 
print(fil_objekt.mode) # i hvilken modus filen er i
print(fil_objekt.read(100)) # hvor mange elementer i filen vi skal lese av
fil_objekt.close()
```

    test.txt
    r
    
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque vulputate nisi sem, eu pharetra nu
    

Det finnes mange flere metoder vi kan bruke på et fil-objekt. Her er det bare å bruke dokumentasjonen https://docs.python.org/3/library/functions.html#open

Men det finnes finnes en tryggere og ryddigere metode å jobbe med filer Python. Her jobber vi med filbehandlingen mer som en blokk


```python
with open('test.txt', 'r+') as fil_objekt:
   innhold = fil_objekt.read() # read() uten input leser hele alt innholdet i filen 
   print(innhold) 
```

    
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque vulputate nisi sem, eu pharetra nunc pellentesque vel. Vestibulum auctor ex in consequat placerat. Nullam gravida ornare ipsum, et ullamcorper justo dignissim et. Vestibulum efficitur leo arcu, sit amet rhoncus nunc imperdiet vitae. Cras a ipsum cursus, dignissim risus hendrerit, efficitur odio. Maecenas tempus ante id est viverra tincidunt. Etiam maximus arcu quis libero pulvinar, ut auctor risus ultricies.
    

Her lukkes filen automatisk når vi går ut av blokken. Og vi kan fritt med filen inne i blokken. Vi har også brukt en annen modus enn forrige gang. Her er en oversikt over forskjellige moduser dere kan bruke med __open()__

<thead>
<tr class="row-odd"><th class="head"><p>Argument</p></th>
<th class="head"><p>Forklaring</p></th>
</tr>
</thead>
<tbody>
<tr class="row-even"><td><p><code class="docutils literal notranslate"><span class="pre">'r'</span></code></p></td>
<td><p> Kun avlesning(default)</p></td>
</tr>
<tr class="row-odd"><td><p><code class="docutils literal notranslate"><span class="pre">'w'</span></code></p></td>
<td><p>Åpne for å skrive</p></td>
</tr>
<tr class="row-even"><td><p><code class="docutils literal notranslate"><span class="pre">'x'</span></code></p></td>
<td><p>Åpne kun hvis lik fil ikke eksisterer, stopper hvis eksisterer</p></td>
</tr>
<tr class="row-odd"><td><p><code class="docutils literal notranslate"><span class="pre">'a'</span></code></p></td>
<td><p>Åpne for å skrive, hvis fil ekisisterer append til bunnen av filen</p></td>
</tr>
<tr class="row-even"><td><p><code class="docutils literal notranslate"><span class="pre">'b'</span></code></p></td>
<td><p>binær modus</p></td>
</tr>
<tr class="row-odd"><td><p><code class="docutils literal notranslate"><span class="pre">'t'</span></code></p></td>
<td><p>text modus (default)</p></td>
</tr>
<tr class="row-even"><td><p><code class="docutils literal notranslate"><span class="pre">'+'</span></code></p></td>
<td><p>Åpne for både avlesning og skrive (lese og skrive)</p></td>
</tr>
</tbody>
</table>




```python

```

###### Oppgave "chopstick_data_effectivness.py"
Vi har fått servert et datasett som sier noe om effektiviteten ved av spisepinner ved forskjellige lengder. Forsøkene er utført på 31 personer.
Vi skal finne hvilken lengde som hadde høyest effektivitet, altså høyest score. Dataen er lagret i en .txt-fil med navn __chopstick-effectiveness.txt__. Vi ønsker å laste dataen direkte fra filen. 


```python
# siden vi ikke vet noe om strukturen på filen, starter vi med å lese den og printe innholdet
with open('chopstick-effectiveness.txt', 'r') as data:
    print(data.read())
```

    score,length
    19.55,180
    27.24,180
    28.76,180
    31.19,180
    21.91,180
    27.62,180
    29.46,180
    26.35,180
    26.69,180
    30.22,180
    27.81,180
    23.46,180
    23.64,180
    27.85,180
    20.62,180
    25.35,180
    28,17,180
    23.49,180
    27.77,180
    18.48,180
    23.01,180
    22.66,180
    23.24,180
    22.82,180
    17.94,180
    26.67,180
    28.98,180
    21.48,180
    14.47,180
    28.29,180
    27.97,180
    23.53,210
    26.39,210
    30.9,210
    26.05,210
    23.27,210
    29.17,210
    30.93,210
    17.55,210
    32.55,210
    28.87,210
    26.53,210
    25.26,210
    25.65,210
    29.39,210
    23.26,210
    24.77,210
    25.42,210
    23.65,210
    32.22,210
    18.86,210
    21.75,210
    23.07,210
    22.3,210
    27.04,210
    22.24,210
    24.87,210
    30.85,210
    21.15,210
    16.47,210
    29.05,210
    26.99,210
    21.34,240
    29.94,240
    32.95,240
    29.4,240
    22.32,240
    28.36,240
    28.49,240
    22.24,240
    36.15,240
    30.62,240
    26.53,240
    27.95,240
    31.49,240
    30.24,240
    24.8,240
    26.43,240
    29.35,240
    21.15,240
    29.18,240
    21.6,240
    25.39,240
    22.26,240
    24.85,240
    24.56,240
    16.35,240
    22.96,240
    25.82,240
    19.46,240
    23.6,240
    33.1,240
    27.13,240
    24.4,270
    25.88,270
    27.97,270
    24.54,270
    22.66,270
    28.94,270
    30.72,270
    16.7,270
    30.27,270
    26.29,270
    22.33,270
    24.85,270
    24.33,270
    24.5,270
    22.67,270
    22.28,270
    23.8,270
    25.36,270
    29.5,270
    20.19,270
    20.14,270
    21.09,270
    24.78,270
    24.74,270
    22.73,270
    21.08,270
    25.7,270
    19.79,270
    16.82,270
    31.15,270
    27.84,270
    22.5,300
    23.1,300
    28.26,300
    25.55,300
    16.71,300
    27.88,300
    31.07,300
    23.44,300
    28.82,300
    27.77,300
    24.54,300
    24.55,300
    27.78,300
    26.14,300
    23.44,300
    26.44,300
    27.47,300
    24.94,300
    29.68,300
    24.33,300
    25.42,300
    24.64,300
    22.78,300
    26.5,300
    18.71,300
    22.86,300
    25.09,300
    19.72,300
    17.05,300
    30.91,300
    25.92,300
    21.32,330
    26.18,330
    25.93,330
    28.61,330
    20.54,330
    26.44,330
    29.36,330
    19.77,330
    31.69,330
    24.64,330
    22.09,330
    23.42,330
    28.63,330
    26.3,330
    22.89,330
    22.68,330
    30.92,330
    20.74,330
    27.24,330
    17.12,330
    23.63,330
    20.91,330
    23.49,330
    24.86,330
    16.28,330
    21.52,330
    27.22,330
    17.41,330
    16.42,330
    28.22,330
    27.52,330
    
    


```python
# Vi ser at første linje ikke er en del av dataen, forsøkene er skillt av ved linjeskifte. Samt at score og lengde er skillt av med comma. readline()

with open('chopstick-effectiveness.txt', 'r') as data_file:
    data_list = []
    data_file.readline()
    for line in data_file:
        data_inline = line.split(',')
        x = data_inline[0].strip('\n')
        y = data_inline[1].strip('\n')
        data_list.append([x, y])

sum_score_180 = 0
sum_score_210 = 0
sum_score_240 = 0
sum_score_270 = 0
sum_score_300 = 0
sum_score_330 = 0

number_of_attempts_180 = 0
number_of_attempts_210 = 0
number_of_attempts_240 = 0
number_of_attempts_270 = 0
number_of_attempts_300 = 0
number_of_attempts_330 = 0

for data in data_list:
    data[0]=float(data[0])

    if data[1]=='180':
        number_of_attempts_180 += 1
        sum_score_180 += data[0]
        
    elif data[1]=='210':    
        number_of_attempts_210 += 1
        sum_score_210 += data[0]
        
    elif data[1]=='240':    
        number_of_attempts_240 += 1
        sum_score_240 += data[0]
    
    elif data[1]=='270':    
        number_of_attempts_270 += 1
        sum_score_270 += data[0]
    
    elif data[1]=='300':    
        number_of_attempts_300 += 1
        sum_score_300 += data[0]
    
    elif data[1]=='330':    
        number_of_attempts_330 += 1
        sum_score_330 += data[0]

        


list_of_avarage_scores = [sum_score_180/number_of_attempts_180, 
                          sum_score_210/number_of_attempts_210, 
                          sum_score_240/number_of_attempts_240, 
                          sum_score_270/number_of_attempts_270, 
                          sum_score_300/number_of_attempts_300, 
                          sum_score_330/number_of_attempts_330]
        
print(list_of_avarage_scores)
        
        
```

    [24.833000000000006, 25.483870967741932, 26.32290322580646, 24.323870967741943, 24.968064516129033, 23.99967741935484]
    

### Moduler
Moduler er akkurat det samme som det vi kaller bibloteker i C. Altså ferdigskrevne programmer med verktøy vi kan importere inn i programmet vi lager 

For importe et biblotek skriver vi helt enkelt


```python
import os

print(os, type(os))
```

Når vi typesjekker en modul ser vi at dette er et klasse-objekt. Fra tidligere vet vi at klasser gjerne inneholder en rekke metoder. Metodene er vektøyene klassene gir oss. Ønsker vi å se hvilke verktøy en modul inneholder kan vi gjøre følgende utskrift   


```python
print(dir(os))
```

Siden modulene er objekter bruket dot-notasjon for å entre verktøyene.


```python
os.getcwd() # denne gir nåværende filbane
```

###### Litt mer os
__os__ er en viktig modul som medfølger Python. Dette er en pakke som lar oss samhandle med det underliggende operativsystem. Enkelt forklart er det samme som å operere i terminalvinduet. Her er noen eksempler på bruk av metoder som er i __os__ 


```python
os.getcwd() # nåværende filbane
os.chdir('C:\\Users\\danbe\\Systemintegrasjon\\uke6\\ny_mappe') # endre filbane
os.getcwd() # vi ser at filbanen har endret seg
```

Mange moduler kommer også med hjelpetekst, som kan gi oss mer informasjon om moduler og metoder. Et eksempel er hvis vi ønsker å lage en ny filbane. Vi ser fra forrige utskrift at 'mkdir' i listen, men vi er usikre på hvordan den fungerer. Da har vi funksjonen help()

__help(os.mkdir)__

Her får vi forklart at første argument er 'path', og at denne er relativ til hvor vi står i filsystemet.


```python
os.mkdir('/ny_bane_1')
os.mkdir('/ny_bane_2')
os.mkdir('/ny_bane_3')
```


```python
os.listdir() # vi ser at de tre mappene ble lager
```

Vi kan også lage våre egne moduler, og det har vi allere gjort forrige uke. Moduler er som nevnt kun klasser. La oss forsøke å importe modulen laget forrige uke


```python
import startup
```

Som vi ser finner den ingen modul med navn __Startup__. Dette vil gjelde for alle moduler som ikke ligger i samme filbane som programmet importerer det til, eller som ligger i filbanen til en global miljøvaribel på datamaskinen. Hvordan kan vi løse dette uten flytte filer osv? Jo, med en modul som heter __sys__


```python
import sys
path_to_startup = 'C:/Users/danbe/Systemintegrasjon/uke5' # filbane-variabel
sys.path.insert(0, path_to_startup) 
import startup
```

Suksess! 

###### Litt om sys
__sys__ har endel verktøy som ligner på sitt __os__, men er laget for dynamisk interaksjon med Python. Veldig enkelt forklart vet sys hvordan den skal håndtere Python filer.  

Men vi må snakke om en ting før vi fritt begynner å bygge og bruke våre egne module, og det er __if \_\_main\_\_=='\_\_name\_\_':


Når vi importer og deretter bruker verktøy fra andre moduler - så kjører Python hele koden i programmet vi importerer. Men koden vi importerer kan inneholde print-kommandoer og andre outputs som vi ikke ønsker i hovedprogrammet som vi importerer til, før vi faktisk bruker modulen. 

Hver gang vi kjører et Python program starter den med å sette hovedprogrammet programmet som main, hvis ikke dette allerede er satt i et annet hovedprogram den importerer.  


```python
# foo.py
"""
def bar():
    pass

print(__main__)
"""


```


```python
"""
Terminal: python foo.py
>> foo
"""
```

Her har allerede Python utført if __\_\_main\_\_=='\_\_name\_\_'__, altså satt filnavnet foo til __\_\_main\_\___ + strippet foo.py for .py. 

Enkelt sagt: __det er god praksis å starte alle programmer vi kun ønsker skal være moduler med__  ___if: \_\_name\_\_=='\_\_main\_\_':___


```python
"""
if __name__ == '__main__':
    class Startup:
        forhoyelse_sats = 1.05
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

ansatt = Startup('Dan','Bavian', 100000) 
print(ansatt)

"""
```

### Installere moduler med pip

_pip_ er et pakkeinstalleringsverktøy som hjelper med oss med: laste ned pakker(moduler), sikre avhengigheter og installere de på riktig sted på maskinen. De alle de vanlige pakkene kan installeres med pip. For pakker som ikke er en del av det tilgjengelige bibloteker til pip(som oftest ting som andre har lagt ut på GitHub), anbefaler jeg verktøyet Git :https://git-scm.com/.


For Windows:
skriv i terminalen: _python get-pip.py_

For Mac:
skriv terminalen: _curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py_
Når den er ferdig å laste ned skriv: _python3 get-pip.py_

Linux-systemer(Rasberry Pi):
skriv i terminal: _sudo apt install python3-pip_



For installere en pakke med pip trenger du kun navnet på pakken.  

#### Viktig! For de som har både Python2 og Python3 installert, må det spesifiseres _pip3_ instede for _pip_


```python
pip install numpy
```

_pip_ har flere funksjoner enn å bare installere pakker. For å se alle funksjoner pip har, skriv: _pip help_


```python
pip help
```

__Tips!__ Rasberry Pi 3(+) har et begrenset cache-minne, dere kan fort oppleve at minnet blir brukt opp når dere installerer større pakker som maplotlib eller numpy. Bruk commandoen no-cache-dir. Nedlastning går endel saktere, men er ofte nødvendig.
