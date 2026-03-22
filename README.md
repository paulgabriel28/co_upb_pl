# Proiect Final: Simplex - Programare Liniara

Aplicatia din `index.html` este un solver educational pentru probleme de Programare Liniara, construit integral in HTML, CSS si JavaScript. Proiectul ghideaza utilizatorul pas cu pas prin formularea problemei, transformarea in forma standard, construirea bazei initiale si aplicarea metodei Simplex cu tratamentul variabilelor artificiale prin Big-M.

Interfata este gandita pentru invatare si verificare, nu doar pentru calcul numeric. Utilizatorul poate introduce propria problema, poate urmari fiecare etapa a rezolvarii si poate salva exercitii local in browser.

## Functionalitati principale

- definirea unei probleme de tip `min` sau `max`
- introducerea unui numar variabil de variabile si restrictii
- suport pentru restrictii de tip `=`, `<=` si `>=`
- validarea structurii problemei de Programare Liniara
- transformarea automata din `PL` in `PLS`
- introducerea variabilelor de adaos/surplus si artificiale
- construirea bazei initiale `ASP`
- generarea tabelului Simplex cu iteratii complete
- evidentierea variabilei care intra in baza, a variabilei care iese si a pivotului
- afisarea indicatorilor specifici: `zj`, `Delta j`, `theta`
- verificarea solutiei finale in problema initiala
- exportul rezolvarii in format PDF
- salvarea exercitiilor in `IndexedDB`
- exportul si importul bazei de date locale in format JSON

## Etapele aplicatiei

Aplicatia este impartita in 5 pasi principali:

1. `Problema PL`
   Se introduc functia obiectiv, numarul de variabile, numarul de restrictii si coeficientii problemei.
2. `PL -> PLS`
   Problema este transformata in forma standard.
3. `ASP & Baza`
   Se construieste baza initiala si se afiseaza rezumatul variabilelor.
4. `Tabel Simplex`
   Sunt generate iteratiile algoritmului Simplex.
5. `Verificare`
   Solutia optima este verificata in problema initiala si poate fi exportata in PDF.

## Reguli de transformare folosite

Pentru fiecare restrictie, aplicatia foloseste urmatoarele reguli:

- `=` -> `+z_k`
- `<=` -> `+y_k`
- `>=` -> `-y_k + z_k`

Unde:

- `y_k` este variabila de adaos/surplus
- `z_k` este variabila artificiala

Variabilele artificiale primesc coeficient `+M` in functia obiectiv, conform metodei Big-M.

## Cum se foloseste

1. Deschide `index.html` intr-un browser modern.
2. Alege tipul problemei: `min` sau `max`.
3. Completeaza numarul de variabile si restrictii.
4. Introdu coeficientii functiei obiectiv.
5. Completeaza sistemul de restrictii.
6. Apasa `Validare`.
7. Parcurge etapele `PL -> PLS`, `ASP & Baza`, `Tabel Simplex` si `Verificare`.
8. Optional, salveaza exercitiul in baza locala sau exporta rezolvarea in PDF.

## Salvare si baza de date locala

Aplicatia foloseste `IndexedDB` pentru a salva exercitiile direct in browser. Din interfata pot fi facute urmatoarele operatii:

- salvare exercitiu curent
- cautare in exercitiile salvate
- sortare dupa recente, vechi sau rezolvate
- incarcare exercitiu salvat
- stergere exercitii
- export baza de date in fisier JSON
- import baza de date din fisier JSON

Fisierul `simplex_exercitii_db.json` este un exemplu de baza de date exportata.

## Fisierele proiectului

- `index.html` - aplicatia completa, implementata intr-un singur fisier
- `README.md` - documentatia proiectului
- `simplex_exercitii_db.json` - exemplu de exercitii exportate din baza de date locala

## Aspecte tehnice

- proiectul nu necesita build sau instalare
- ruleaza exclusiv client-side
- persistenta locala este realizata prin `IndexedDB`
- exportul PDF incarca biblioteci din CDN la runtime
- interfata este in limba romana

## Scopul proiectului

Acest proiect este potrivit pentru:

- laborator sau seminar la Cercetari Operationale
- invatarea metodei Simplex pas cu pas
- verificarea exercitiilor de Programare Liniara
- demonstratii didactice pentru forma standard, baza initiala si Big-M

## Limitari

- aplicatia presupune conditia de nenegativitate pentru variabile
- este orientata spre uz didactic, nu spre optimizare la scara mare
- exercitiile salvate raman locale in browser pana la export manual
- pentru export PDF este necesara conexiune la internet pentru incarcarea bibliotecilor externe
