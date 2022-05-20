
## START [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/START.md)


### Zapraszam do testowania!

+ [Repozytorium plików git grabWHOIS/bash: bash.grabwhois.com](https://github.com/grabWHOIS/bash)


Program odpytuje WHOIS ze zmiennym IP poprzez router DSL
skrypt **restart.sh** resetuje go w momencie uzyskania limitu zapytań dla aktualnego adresu IP
W celu informowania o momencie resetowania wydaje dźwięk 1 raz
Skrypt odczekuje 1 minutę i ponawia dwukrotnie dźwięk by zasygnalizowąc powrót połączenia do sieci internet
```bash
./restart.sh
```

Skrypt **import_deleted_pl.sh** pobiera plik listy domen w trakcie wygasania ze strony
[https://www.dns.pl/deleted_domains.txt](https://www.dns.pl/deleted_domains.txt)
Plik z listą domen jest zapisywany folderze **input/** z nazwą zaczynającą się od daty utworzenia
```bash
./import_deleted_pl.sh
```

Uruchomienie pobierania danych z plików znajdujących się w folderze **input/**
```bash
./whois_all.sh 
```

Pobrane dane WHOIS domen są zapisywane do plików tekstowych, każda domena oddzielnie.
Skrypt **move.sh** przenosi pliki do folderów: **free**, **expire**, **blocked** na podstawie statusu WHOIS
```bash
./move.sh 
```
Domeny ze statusami: **wolne do rejestracji**, **wygasające po rejestracji** i **zablokowane** znajdują się w osobnych pod-folderach dla danej daty pobierania w folderze **output**
