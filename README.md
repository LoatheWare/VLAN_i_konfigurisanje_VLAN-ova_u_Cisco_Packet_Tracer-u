# VLAN i konfigurisanje VLAN-ova u Cisco Packet Tracer-u
## Šta je ovo?
Ovo je vežba za administratore računarskih mreža koju sam radio tokom mog školovanja. Nalazi se jedan .pkt fajl koji se preuzme i to će Vam biti početno stanje. Zadak Vam je dat, kao i uputstvo za njegovo rešavanje. Ukoliko Vam nešto nije jasno tokom rešavanja ovih zadataka obratite mi se direktnom porukom na aplikaciji LinkedIn, www.linkedin.com/in/nikola-karanović-397185390

## Pitanja i odgovori — VLAN (Virtuelna lokalna mreža)

### 1. Šta je VLAN?
**VLAN** (Virtual Local Area Network) je tehnologija koja omogućava podelu jedne fizičke LAN mreže na više **logički odvojenih i međusobno izolovanih mreža**. Računari koji se nalaze u istom VLAN-u ponašaju se kao da su povezani na isti fizički svič, čak i kada su u stvarnosti povezani preko različitih svičeva. VLAN ne zavisi od fizičke topologije mreže i može se dinamički menjati rekonfiguracijom portova na uređajima. Tehnologiju VLAN-a definiše standard **IEEE 802.1Q** (poznat i kao *dot1q*).

---

### 2. Koje su tri osnovne prednosti VLAN tehnologije?
VLAN nam omogućava:
1. **Veću sigurnost** u LAN mreži (izolacija osetljivih grupa korisnika, npr. Uprave od ostalih).
2. **Bolje korišćenje propusnog opsega**, tj. smanjenje nepotrebnog mrežnog saobraćaja (brodkast poruke, ARP, STP okviri ne idu kroz celu mrežu, već samo unutar svog VLAN-a).
3. **Lakše upravljanje i nadgledanje LAN-om**.

---

### 3. Zašto je važno da računari u različitim VLAN-ovima imaju IP adrese iz različitih podmreža?
Svaki VLAN predstavlja **poseban brodkast domen**, pa je logično da svaki od njih ima i svoju IP podmrežu. Ukoliko bi računari iz različitih VLAN-ova bili u istoj IP mreži, ne bi mogli da komuniciraju jer su na **2. (data link) sloju** potpuno odvojeni — VLAN-ovi razdvajaju saobraćaj na nivou okvira (frame), pa IP paketi ne mogu "preskočiti" iz jednog VLAN-a u drugi bez posredovanja rutera. Korišćenjem različitih podmreža po VLAN-u obezbeđuje se ispravna logička organizacija i mogućnost rutiranja između njih.

---

### 4. Koje uređaje povezujemo na access portove?
Na **access portove** povezujemo **krajnje uređaje**, kao što su:
- računari
- serveri
- printeri
- IP kamere
- IP telefoni

Access port pripada samo **jednom VLAN-u** i prenosi okvire isključivo tog VLAN-a (bez VLAN tagova).

---

### 5. Koje uređaje povezujemo na trunk portove?
**Trunk portovi** se koriste za povezivanje **svičeva međusobno** (ili sviča i rutera), kada je potrebno da kroz jednu fizičku vezu putuju okviri **više različitih VLAN-ova** istovremeno.

---

### 6. U čemu se razlikuju access i trunk portovi?
| Tip porta | VLAN pripadnost | Šta prenosi |
|---|---|---|
| **Access** | Pripada jednom, tačno određenom VLAN-u | Prenosi okvire samo tog jednog VLAN-a, bez VLAN oznake (tag-a) |
| **Trunk** | Nije ograničen na jedan VLAN | Prenosi **tagovane** okvire više različitih VLAN-ova kroz jednu fizičku vezu |

---

### 7. Da li računari u različitim VLAN-ovima istog sviča mogu direktno da komuniciraju?
**Ne mogu.** Iako su fizički povezani na isti svič, VLAN-ovi ih razdvajaju i na **2. sloju** (data link layer), pa se ponašaju kao da su na potpuno odvojenim, nezavisnim mrežama. Da bi komunicirali, neophodno je da saobraćaj prođe kroz uređaj koji radi na **3. sloju** — odnosno kroz **ruter**.

---

### 8. Zašto se povezuje ruter u mrežu sa više VLAN-ova? Koja je njegova uloga?
Pošto su VLAN-ovi međusobno izolovani i imaju IP adrese iz različitih podmreža, računari iz različitih VLAN-ova **ne mogu komunicirati direktno**. Uloga rutera je da **poveže i rutira saobraćaj između tih VLAN-ova** (tzv. *inter-VLAN routing*), omogućavajući im da razmenjuju podatke uprkos tome što se nalaze u logički odvojenim mrežama. Ovo se može uraditi:
- preko **posebnih fizičkih interfejsa** rutera za svaki VLAN, ili
- preko **logičkih podinterfejsa** jednog fizičkog interfejsa (svaki podinterfejs ima svoju IP adresu za svoj VLAN), čime se štedi na broju fizičkih portova.

---

### 9. Koja je osnovna komanda za CISCO svič kojom vidimo konfiguraciju VLAN-ova?
