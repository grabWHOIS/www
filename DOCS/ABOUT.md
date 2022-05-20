
## ABOUT grabWHOIS [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/ABOUT.md)


Skrypty bash'a odpytujące whois ze zmiennym IP z resetowaniem routera DSL przez API

+ [Repozytorium plików git grabWHOIS/bash: bash.grabwhois.com](https://github.com/grabWHOIS/bash)
+ [Projekt grabWHOIS](https://github.com/grabWHOIS)


Poniżej kilka informacji:

+ Jak to działa
+ Do czego służy
+ Jak zainstalować

### Użycie programu

Rozwiązanie najlepiej uruchomić na zewnętrznym urządzeniu jak RPI, które może pracować całą noc pobierając mniej energii
a także resetować router jeśli taka opcja jest możliwa obecnie jest wspierane resetowanie routera marki fritz.

Struktura plików

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
