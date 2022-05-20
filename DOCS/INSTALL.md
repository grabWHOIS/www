
## Install [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/INSTALL.md)


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


