
## Instalacja [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/INSTALL.md)

Rozwiązanie najlepiej uruchomić na zewnętrznym urządzeniu jak RPI, które może pracować całą noc pobierając mniej energii
a także resetować router jeśli taka opcja jest możliwa obecnie jest wspierane resetowanie routera marki fritz.

### Struktura plików

```bash    
|__LICENSE
|__.input
| |__2022-05-10_deleted_domains.txt
|__.output
| |__2022-05-10
| | |__free
| | |__expire
| | |__blocked
|__count.sh
|__data_clean.sh
|__data_create.sh
|__find.sh
|__find_input.sh
|__find_move.sh
|__find_output.sh
|__find_output_dns.sh
|__import_deleted_pl.sh
|__move.sh
|__nameserver.sh
|__README.md
|__registrar.sh
|__restart.bat
|__restart.sh
|__split.sh
|__whois.sh
|__whois_all.sh
|__whois_data.txt
|__whois_file_count.sh
|__whois_free.sh
|__whois_free.txt
|__whois_free_all.txt
|__whois_from_file.sh
```


Jak zainstalować na systemie linux: Debian, Ubuntu, ...

```bash
sudo apt update
sudo apt upgrade
sudo apt install whois
```

więcej informacji na bashfunc/www/whois: [How to Use the whois Command on Linux](https://www.howtogeek.com/680086/how-to-use-the-whois-command-on-linux/)

### Pobranie projektu

```bash
git clone https://github.com/grabWHOIS/bash.git grabWHOIS
```

```bash
cd grabWHOIS
```

## check WHOIS

Sprawdź domeny z plików tekstowych znajdujących się w folderze **input/**
```bash
./whois_all.sh 
```

Sprawdź listę domeny bezpośrednio z pliku tekstowego
```bash
./whois_from_file.sh strato.de
```

Stan liczebny domen w róznych statusach. Liczy osobno domeny zajęte, wolne, zablokowane.
```bash
./count.sh
```

Sprawdź różnice pomiędzy wczorajszym i dzisiejszym stanem domen
```bash
./diff.sh
```


## Check free domains

Check free domains in many extensions

whois domains .com .org .net

```bash
./whois_free.sh freedoman
```


