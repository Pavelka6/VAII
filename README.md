# Portál pre zdieľanie receptov

Erik Pavelka

5ZYI33

## Stručný opis projektu
Aplikácia slúži na zdieľanie, prezeranie a hodnotenie receptov. Je určená pre ľudí, ktorí sa chcu inšpirovať inými receptami alebo chcú ukázať ostaným ľuďom svoj vlastný recept. 
Účelom aplikácie je poskynúť platformu, kde použivateľia si vedia najsť recepty rôznych kategórii a zároveň môžu zdieľať tie vlastné poprípade hodnotiť iné recepty.

## Role v projekte
návštevník (neregistrovaný používateľ) - má základný prístup na portál. vie si pozrieť ostatné recepty, no nevie s nimi nijak interagovať. Nemôže zdieľať svoje vlastné recepty a ani hodnotiť.

registrovaný používateľ - vie si vytvoriť svoje vlastné recepty a zdieľať ich s ostatnáými. vie svoje recepty editovať a mazať. vie reagovať na ostatné recepty.

administrátor - dohliada na poriadok a kvalitu obsahu. má rovnaké oprávnenia ako registrovaný používateľ, ale môže upravovať a mazať recepty ostatných.


## Prípady použitia podľa rolí
návštevník (neregistrovaný používateľ) - vyhľadáva recepty pomocou filtrovania. Vie si pozrieť detailny postup receptu. A vie sa registrovať.

registrovaný používateľ - vie si vytvoriť svoje vlastné recepty a zdieľať ich s ostatnými. Taktiež vie ohodnocovať ostatné recepty.

administrátor - zmaže nevhodný komentár pod receptom alebo recept ak je potreba. 

## Plánované entity
USER - evidencia osôb v systéme a zabezpečenie prihlasovania
    atribúty: id, meno, email, heslo, rola
    vzťahy: táto entita bude viazaná s entitami RECEPT, HODNOTENIE

RECEPT - reprezentuje konkrétne jedlo. 
    atribúty_ id, názov, postup_pripravy, cesta_k_obrazku (upload img), id_kategorie, id_autora
    vzťahy: patrí jednému USER a jednej KATEGORIA a obsahuje viacero HODNOTENIE

KATEGORIA - na triedenie receptov
    atribúty: id, nazov, popis
    vzťahy: obsahuje viac receptov

HODNOTENIE - slúži na ukladanie spätnej väzby od komunity.
    atribúty: id, nazov, popis
    vzťahy: obsahuje viacero RECEPTov a jednému USERovi


## Vzťahy medzi entitami
USER a RECEPT (1:N) - jeden používateľ môže mať viac RECEPTov ale konkrétny RECEPT ma práve jedného USERa

KATEGORIA a RECEPT (1:N) - do jednej kategórie patrí viacero receptov ale každý recept má iba jednú kategóriu

RECEPT a HODNOTENIE (1:N) - jeden recept má viacero hodnotení od rôzných uživateľov.

USER a HODNOTENIE (1:N) - jeden USER môže mať viac hodnotení. 

## Hlavné stránky aplikácie
DOMOVSKA STRANKA (ZOZNAM RECEPTOV) - na hlavnej stranke sa objavia vsetky recepty s filtrovanim podla kategorii

DETAIL RECEPTU - slúži na zobrazenie konkretného receptu a jeho ingrediencii a postupom varenia. je tam aj sekcia pre komentáre.

PRIHLASOVACIA/REGISTROVACIA STRANKA - stránka obsahuje okna na prihlasenie alebo registrovanie uživateľa.

MANAZMENT VLASTNYCH RECEPTOV - užívateľ si vie pozrieť všetky svoje nahrané recepty a editovať ich. popripade nahrať nové.

ADMINISTRATIVNY PANEL - stránka určená pre administrátora za účelom mazať cudzie komentáre alebo recepty.

## Rozdelenie funkcionality
ZAKLADNE FUNKCIE 
praca s frameworkom, registrovanie alebo prihlasenie užívateľa, CRUD operácie nad entitami, upload obrazkov pre recepty a podobne

ROZSIRUJUCE FUNKCIE
nahratie avatarov (pre uzivatela), napojenie na API pre zobrazenie nutričných hodnôt ingrediencii.  
