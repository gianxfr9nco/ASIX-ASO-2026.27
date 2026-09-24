# Fitxa 1 — Anàlisi inicial de MusicCloud

**Nom i cognoms:** Gian Franco Garcia Gonzales
**Data:** 17/09/2026

## 1. Conèixer MusicCloud

| Persona        | Departament       | Funció / responsabilitat                                                            | Necessita privilegis especials? Per què?                                                                   |
| -------------- | ----------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Aina Ciurans   | Direcció          | Gestió general de l'empresa                                                         | Sí, perquè necessita accedir als recursos de diferents departaments i consultar informació de l'empresa.   |
| Rut Tornil     | Direcció          | Gestió general de l'empresa                                                         | Sí, perquè forma part de Direcció i necessita accedir als recursos de l'empresa.                           |
| Dídac Gassó    | Administració     | Factures, contractes i documentació interna                                         | No, és un usuari estàndard del departament.                                                                |
| Laia Macias    | Administració     | Responsable d'Administració i gestió de factures, contractes i documentació interna | Sí, perquè és la cap del departament i necessita permisos complets sobre els recursos del seu departament. |
| Estel Birosta  | Suport tècnic     | Manteniment de sistemes i gestió d'incidències                                      | No, com a usuària estàndard utilitza els recursos del seu departament.                                     |
| Aina Zuriguel  | Suport tècnic     | Manteniment de sistemes i gestió d'incidències                                      | No, és una usuària estàndard del departament.                                                              |
| Lluïsa Richart | Suport tècnic     | Responsable de Suport tècnic i coordinació del departament                          | Sí, perquè és la cap del departament i necessita permisos complets sobre els seus recursos.                |
| Roser Alberch  | Producció musical | Gestió de continguts musicals                                                       | No, és una usuària estàndard del departament.                                                              |


### 1.1. Reflexió

**Quines diferències observes entre un treballador, un departament i una funció o responsabilitat?**

Un **treballador** és una persona que treballa a l'empresa.

Un **departament** és un grup de treballadors que realitza una determinada activitat dins de l'empresa.

Una **funció o responsabilitat** és la feina o les tasques que té assignades una persona dins de l'empresa.

**Hi ha persones que, pel seu càrrec o funció, necessiten accessos diferents dels altres membres del seu departament?**

☑ Sí
☐ No


---

# 2. Recursos de l'empresa

| Recurs                                                   | Qui creus que l'hauria d'utilitzar?                                  | Per a què?                                                   |
| -------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------ |
| `/empresa/comu/intercanvi`                               | Usuaris externs i treballadors que necessitin intercanviar documents | Per intercanviar temporalment documents amb usuaris externs. |
| `/empresa/comu/comunicats`                               | Treballadors de l'empresa                                            | Per consultar els comunicats interns de MusicCloud.          |
| `/empresa/departaments/administracio/compartida`         | Treballadors d'Administració                                         | Per compartir documents i informació del departament.        |
| `/empresa/departaments/administracio/gestio_departament` | La responsable d'Administració                                       | Per gestionar els recursos i la informació del departament.  |
| `/empresa/projectes/campanya_estiu`                      | Usuaris assignats al projecte                                        | Per treballar amb els fitxers del projecte Campanya Estiu.   |
| `/empresa/administracio_sistema/backups`                 | Administradors del sistema                                           | Per gestionar les còpies de seguretat del sistema.           |

L'estructura del PDF separa els espais comuns, els departaments, les carpetes personals, els projectes i l'administració del sistema.

---

# 3. Qui ha de poder fer què?

| Situació                                                             | Accés proposat | Justificació                                                                                                  |
| -------------------------------------------------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------- |
| Dídac accedeix a la carpeta compartida d'Administració               | L/E            | És treballador d'Administració i la carpeta compartida és per als usuaris del departament.                    |
| Laia accedeix a la gestió del departament d'Administració            | L/E            | És la responsable del departament i només ella ha de poder gestionar aquesta carpeta.                         |
| Pere, treballador extern, accedeix als comunicats interns            | NA             | Els usuaris externs només poden accedir a recursos públics o compartits específics i no a informació interna. |
| Talia accedeix als backups del sistema                               | ADM            | Talia és responsable d'Informàtica i els backups formen part de l'administració del sistema.                  |
| Un membre de Producció musical accedeix a la carpeta d'Administració | NA             | No necessita accedir als recursos propis d'Administració.                                                     |
| Un participant de `campanya_estiu` accedeix als fitxers del projecte | L/E            | Els usuaris assignats al projecte han de poder treballar amb els seus fitxers.                                |

---

# 4. Primer problema: com assignem els permisos?

### 4.1.

Si l'empresa tingués **100 treballadors**, hauríem de configurar els permisos de cada persona individualment. Això seria molt lent i difícil de gestionar.

### 4.2.

Cada vegada que s'incorporés una persona nova hauríem de configurar manualment tots els seus permisos.

### 4.3.

Hauríem de treure manualment els permisos del departament anterior i donar-li els permisos del nou departament.

### 4.4.

Crearia **conjunts de persones que tinguessin les mateixes necessitats d'accés** i assignaria els permisos al conjunt en lloc de fer-ho persona per persona.

---

# 5. Canvis a MusicCloud

### Cas A

**Dídac deixa Administració i passa a Producció musical.**

**Quins accessos hauria de perdre?**

Hauria de perdre els accessos als recursos específics d'Administració, com la carpeta compartida, la documentació interna i la gestió del departament.

**Quins accessos hauria d'obtenir?**

Hauria d'obtenir els accessos corresponents a Producció musical.

---

### Cas B

**S'incorpora una nova treballadora al departament d'Administració.**

Caldria afegir-la al conjunt d'usuaris d'Administració i donar-li accés als recursos compartits i a la documentació interna del departament.

---

### Cas C

**Pere Espinalt deixa de col·laborar amb MusicCloud.**

Caldria eliminar o desactivar el seu usuari i retirar els seus accessos als recursos de l'empresa.

---

# 6. Busquem una solució millor

### 6.1.

L'avantatge és que els permisos es poden gestionar per conjunt de persones i no cal configurar-los un per un. Això facilita molt l'administració.

### 6.2.

Caldria treure Dídac del conjunt d'Administració i afegir-lo al conjunt de Producció musical.

### 6.3.

Aquests conjunts de persones s'anomenarien **grups**.

---

# 7. Primera proposta per a MusicCloud

| Nom proposat      | Qui hi pertanyeria?                                                                              | Per què existeix aquest conjunt?                          |
| ----------------- | ------------------------------------------------------------------------------------------------ | --------------------------------------------------------- |
| Administració     | Dídac Gassó i Laia Macias                                                                        | Per gestionar els recursos d'Administració.               |
| Suport tècnic     | Estel Birosta, Aina Zuriguel i Lluïsa Richart                                                    | Per gestionar els recursos de Suport tècnic.              |
| Producció musical | Roser Alberch, Guillem Adella, Meritxell Reglat, Alícia Monclús, Carles Molins i Eulàlia Galcera | Per gestionar els recursos de Producció musical.          |
| Informàtica       | Talia Costas i Alex Soriano                                                                      | Per gestionar els recursos d'Informàtica.                 |
| Externs           | Pere Espinalt i Neus Bages                                                                       | Per gestionar els accessos limitats dels usuaris externs. |

El document defineix explícitament el departament d'externs per als usuaris temporals o externs.

---

# 8. Cas que complica el model

**És suficient que pertanyi només al conjunt `Administració`?**

☐ Sí
☑ No

**Per què?**

Perquè Laia és treballadora d'Administració però també és la responsable del departament. Necessita permisos diferents dels altres membres.

**Quina possible solució proposes?**

Que Laia pertanyi al grup `Administració` i també a un grup específic de responsables, amb permisos addicionals.

---

# 9. Un altre cas

**Creus que hauríem de canviar-les de departament?**

☐ Sí
☑ No

**Si no, com podríem donar-los accés als recursos del projecte?**

Podem crear un grup específic per al projecte `Campanya Estiu` i afegir-hi temporalment les persones que hi participen. Així poden accedir als recursos del projecte sense canviar de departament.

## El PDF indica que els projectes transversals tenen les seves pròpies carpetes i que l'accés als projectes correspon als usuaris assignats.

# 10. Conclusions

### Usuari

Un usuari representa **una persona que utilitza els recursos i serveis informàtics de l'empresa**.

### Recurs

Un recurs és **una carpeta, fitxer o servei al qual un usuari pot tenir accés**.

### Permís

Un permís determina **què pot fer un usuari sobre un recurs**.

### Grup

Un grup serveix per **agrupar usuaris amb necessitats d'accés semblants i facilitar la gestió dels permisos**.

---

# 11. Regla de mínim privilegi

La regla significa que **cada usuari només ha de tenir els permisos necessaris per poder fer la seva feina i no més**.

**Exemple relacionat amb MusicCloud:**

Un treballador de Producció musical no necessita tenir accés als backups del sistema, perquè aquesta informació correspon a l'administració del sistema.

---

# 12. Pregunta final

☐ Assignar permisos individualment a cada usuari.

☑ Organitzar els usuaris segons les seves necessitats i assignar permisos a aquests conjunts.

**Justificació:**

La segona opció és més fàcil de gestionar quan l'empresa creix. Si entra un treballador nou, només cal afegir-lo al grup corresponent. Si canvia de departament, es pot canviar de grup i els seus permisos s'adapten als del nou departament.

