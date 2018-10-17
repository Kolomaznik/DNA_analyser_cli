# DNA Analyser CLI preparation

Předpříprava projektu CLI pro platformu DNA analyzátoru pro Mendelu IBP.

## Zadání

Projekt musí být schopen dávkového zadávání jednotlivých DNA sekvencí do REST API. Tzn. uživatel se musí příhlásit na svůj uživatelksý účet tzn. získat JWT token [nutný pro další cally = nutné vyřešit jeho ukládání a případný update v případě expirace].

> Běh programu obecně

1. Uživatel zadá uživatelské jméno a heslo
2. Server odpovídá v případě správného zadání JWT tokenem, který ukládám případně vyhazuji chybovou hlášku
3. Dalším příkazem zobrazuji nabídku možností volby/nahrání DNA sekvence
   1. Nahrání nové sekvence
      1. ze souboru / ze složky = více souborů najednou (kontrola obsahu filu případně koncovky filu !!!)
      2. zadáním krátké sekvece? (na zvážení jestli je vhodné)
      3. NCIB import
      4. NCIB multiple import
   2. Zobrazení již nahraných sekvencí (sdílené mezi účty takže mohu vybírat)
4. Vybrání vhodné sekvence případně skupiny sekvencí pro spuštění analýzi
   1. Nabídka jednotlivých spustitelných metod
      1. pro jednu sekvenci
      2. pro skupinu sekvencí
   2. Nastavení jednotlivých parametrů metody
5. Jiným příkazem zobrazení seznamu hotových analýz
   1. Stažení výsledků a výpis pro jednu metodu dle výběru
   2. Stažení + překrytí výsledů z několika metod

> Zadání uživatelských informací

```
dna-cli -n user@user.com -p useruser
dna-cli --name user@user.com --password useruser
```

> Nahrání nové sekvence

```
dna-cli -u [file_path, folder/*]
dna-cli --upload [file_path, folder/*]
dna-cli -l [link NCIB]
dna-cli --link [link NCIB]
```

> Zobrazení nahraných sekvencí (buď všech nebo možná filtrace? na zvážení)

```
dna-cli -s --all
dna-cli --show --all
```

> Vybrání sekvence pro analýzu

```
dna-cli -c -i [id sekvence]
dna-cli --choose --id [id sekvence]
```

> Volba analyz jestě na zvážení jak určit metodu

```
dna-cli -a [metoda id?] -i [id sekvence nebo sekvencí]
dna-cli --analyze [metoda id?] --id [id sekvence nebo sekvencí]
```

> Vypsání sekvencí které již analýzu mají zpracovanou

```
dna-cli -s --analyze-complete
dna-cli --show --analyze-complete
```
