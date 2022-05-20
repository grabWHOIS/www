

![logo](http://logo.grabwhois.com/2/cover.png)

# [Website - www.grabwhois.com](http://www.grabwhois.com/) [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/MENU.md)

+ [Sourcecode - bash.grabwhois.com](http://bash.grabwhois.com/)
+ [Documentation - docs.grabwhois.com](http://docs.grabwhois.com/)
+ [News - blog.grabwhois.com](http://blog.grabwhois.com/)
+ [Logo - logo.grabwhois.com](https://logo.grabwhois.com/)




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


## Przykładowe statusy polskich domen we WHOIS [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/START.md)

Status domeny jest wykrywany poprzez wyszukiwanie charakterystycznej frazy w pliku wyniku WHOIS:

### Blocked - domena zablokowana przez rejestr NASK bez wyroku sądu
    "Trwa postępowanie wyjaśniające [REGISTERED, ze statusem clientHold/serverHold]"

### Expire - wygasająca
    "billing period had finished"
Zakończył się opłacony okres rozliczeniowy; w tym stanie domena przebywa do 30 dni.


### Free - wolna do rejestracji
    "No information available about domain name"
Domena nie istnieje w bazie Registry NASK.

+ ['clientHold/serverHold'. - Forum Di.pl Domeny Internetowe](https://di.pl/search/?q=clientHold/serverHold)
+ [STATUSY domen globalnych](STATUSY.md)


## Stan domeny [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/censura-pl/www/edit/main/DOCS/STAN_DOMENY.md)


Na stronie NASK napisano, że statusy domen nie są dostępne publicznie:

"Dozwolone operacje Uwaga! Właściwości domen mogą zostać zmodyfikowane poprzez nałożenie na nie statusów. 
Statusy powiązane z domenami nie są widoczne w bazie WHOIS."

+ [DNS - Krajowy Rejestr Domen](https://www.dns.pl/cykl_zycia_domeny_pl)

#### Stan domeny widoczny przy sprawdzaniu przez WHOIS to **"stan domeny"**

Przykładowy **stan domeny** to:

**"Trwa postępowanie wyjaśniające [REGISTERED, ze statusem clientHold/serverHold]"**


#### Wyjaśnienie stanu zablokowanej domeny przez NASK:

"Utrzymywanie domeny zostało wstrzymane do czasu wyjaśnienia wątpliwości dotyczących współpracy z jej abonentem, np. w przypadku zaległości płatniczych u rejestratora, braku aktualizacji danych abonenta (pomimo wezwania), wykorzystywania domeny do celów zagrażających bezpieczeństwu sieci."


#### Rodzą się niejasności i pytania:

+ Jak można odróżnić powód blokady z powodu płatności od blokady np. z powodu wyroku sądu?

+ Jak można odróżnić poszczególne przypadki blokady?

+ Jak rozumieć stwierdzenie: "wykorzystywania domeny do celów zagrażających bezpieczeństwu sieci." ?
 

NASK w ramach cenzury, czyli blokady bez wyroku sądu, nie tworzy nowego stanu/statusu dostępnego publicznie


#### Kto zna rzeczywisty powód blokady domeny?

Skąd mógłbym otrzymać precyzyjniejszą informację niż: "Trwa postępowanie wyjaśniające ..." ?

Trudno określić co konkretnie ma na myśli "instytut badawczy" NASK.
Ten ogólny opis stanu domeny może określać co najmniej te kilka poniższych możliwości: 

1. Utrzymywanie domeny zostało wstrzymane do czasu wyjaśnienia wątpliwości dotyczących współpracy z jej abonentem,
   + Wszystkie przypadki spoza listy poniżej

2. Zaległość płatnicza wynikająca z umowy (domeny nie jest opłacona mimo zawarcia umowy),

3. Blokada z powodu braku aktualizacji danych abonenta (pomimo wezwania),

4. Wykorzystywania domeny do celów zagrażających bezpieczeństwu sieci
   1. Sieci wewnętrznej konkretnej organizacji
   2. Wszystkim użytkownikom internetu
   3. Dystrybutorowi punktu dostępowego, zarządcy NASK

5. Złamanie prawa i zablokowanie na skutek wyroku sądowego
   + prawa autorskie, np. spór o nazwę domenę, wykorzystanie zarejestrowanej nazwy
   + patenty
   + działalność zabroniona w Polsce


Aktualnie to wszystko figuruje jako jeden status, dobrze by było znać kontekst blokady, dziś nie mamy pewności, kto złamał prawo, czy rejestrator, NASK, CERT, ABW, Exatel, itd...

Stan techniczny domeny można samemu sprawdzić, ale intencja blokady jest znana tylko organizacji NASK i organizacji zlecającej blokadę.

Druga istotna kwestia to data zdjęcia blokady o czym nie zawsze jesteśmy informowani, niektóre domeny mimo upłynięcia określonego czasu
nadal pozostają zablokowane do rejestracji.

Instytucja utrzymywana z pieniędzy podatników powinna być transparentna.

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



## TOOLS [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/TOOLS.md)

### WHOIS

Jak sprawdzić status domeny i dane abonenta?
+ [DNS - Krajowy Rejestr Domen](https://www.dns.pl/whois)

Jak sprawdzić hurtowo setki, tysiące domen?
+ [Domain Whois Search - Whois lookup - GetWhois.com](http://getwhois.com/)
+ [getWHOIS](https://getwhois.io/softreck.com#)


### DELETED DOMAINS

Globalna Lista usuniętych domen

+ [Deleted Domains (last 7 days) » ExpiredDomains.net](https://member.expireddomains.net/domains/combinedexpired/?o=statustld_registered&r=d&ftlds[]=196&flimit=200&fwordpl=1#listing)

+ [ WHOIS, DNS, & Domain Info - DomainTools](https://whois.domaintools.com/example.pl)


### Reverse IP

+ [ Reverse NS Lookup - DomainTools](https://reversens.domaintools.com/search/?q=)


### Check DNS, EN

There are two ways that a domain name =DNS server map can be constructed:

Zone file access: some registries grant access to their zone files to their registrars and other entities.
This makes it pretty easy to determine which domains in those zones are delegated to a given DNS server.
This is how DomainTools.com provides their Name Server Spy product.
This is the most reliable method, but is obviously limited to the zone files that they have access to.


Passive DNS. This involves examining traffic through recursive DNS servers at ISPs
and reconstructing zone data based on what's seen.
This method lets you discover information from the entire DNS space,
but is less reliable as changes take longer to appear in your database,
and won't recover information about domains that get little or no queries.

+ [Learn more about the team behind PerfOps](https://perfops.net/about-us)
+ [CDNPerf - CDN Benchmark - Worldwide multiple locations ping tool](https://www.cdnperf.com/tools/cdn-latency-benchmark)
+ [CDNPerf - CDN Performance and Uptime monitoring, comparison and analytics - RUM data](https://www.cdnperf.com/#!performance,Africa,2022-03-01)
+ [CDNPerf - CDN Performance and Uptime monitoring, comparison and analytics - RUM data](https://www.cdnperf.com/)
+ [Network tests and benchmarks on-demand](https://perfops.net/network-tests-on-demand)
+ [Raw Logs of CDN and DNS benchmarks](https://perfops.net/raw-logs)
+ [perfops API - Swagger UI](https://api.perfops.net/api-docs/)


## TODO [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/grabWHOIS/www/edit/main/DOCS/TODO.md)


Następny krok to aplikacja webowa z UI dla zarządzania i przyjmowania zgłoszeń, statyczne API z autoryzacją i limitami per client do 1000 zapytań dziennie.

2 metody dostępu do publicznego serwisu
+ token do zapytań generowany dla usera na rok
+ zapytania IP opóznianie do 1s/zapytanie
+ opcja hurtowego sprawdzania dla zarejestrowanych per email lub per token dla 1000 zapytań udostępniany dla wybranych, którzy nie chcą się rejestrować w systemie.
+ każdy kto zrobi donate, nawet bez rejestracji dostanie hash na 10k zapytań

Dzięki temu będzie szansa by więcej osób skorzystało i to nadal działało.
To część większego systemu, dlatego nie chcę zarabiać na dostępie do danych ogólnie dostępnych
a jedynie go ułatwić i też nawiązać współpracę z domainerami
Niestety to wszystko kosztuje czas i trwa miesiącami, kolejne usługi to będzie codzienna archiwizacja stron www w formacie HTML i zrzut ekranu


### Przykłady użycia

https://github.com/grabWHOIS/examples

na letWHOIS z opcją używania innnych agentów i przetwarzaniem formatu

z instalacją i przykładową listą input i output

### Lista wszystkich metod pozyskania whois

jako oddzielny projekt
do monitorowania zmian w rejestrach

### Aplikacje

portal do wyszukiwania zablokowanych stron

plugin do przeglądarki

## Statusy domen globalnych [<span style='font-size:20px;'>&#x270D;</span>](https://github.com/censura-pl/www/edit/main/DOCS/STATUSY.md)

Jak sprawdzić?

+ [RFC 3912: WHOIS Protocol Specification](https://www.rfc-editor.org/rfc/rfc3912)

Lista Serwerów:

+ [nirsoft.net/whois-servers.txt](http://www.nirsoft.net/whois-servers.txt)

clientHold https://icann.org/epp#clientHold

clientTransferProhibited https://icann.org/epp#clientTransferProhibited

pendingDelete https://icann.org/epp#pendingDelete

serverHold https://icann.org/epp#serverHold

autoRenewPeriod https://icann.org/epp#autoRenewPeriod

redemptionPeriod https://icann.org/epp#redemptionPeriod


## [EPP Status Codes | What Do They Mean, and Why Should I Know? - ICANN](https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en#clientHold)

### Server Status Codes are Set by Your Domain's Registry

+ RDAP Status Mapping
+ EPP Status Code
+ What does it mean?
+ Should you do something?

### add period

    addPeriod

This grace period is provided after the initial registration of a domain name. If the registrar deletes the domain name during this period, the registry may provide credit to the registrar for the cost of the registration.

This is an informative status set for the first several days of your domain's registration. There is no issue with your domain name.

### auto renew period

    autoRenewPeriod

This grace period is provided after a domain name registration period expires and is extended (renewed) automatically by the registry. If the registrar deletes the domain name during this period, the registry provides a credit to the registrar for the cost of the renewal.

This is an informative status set for a limited time after your domain's auto- renewal by the registry. If you do not want to keep it (i.e., pay the renewal fee) anymore, you should contact your registrar immediately to discuss what options are available.

### inactive

    inactive

This status code indicates that delegation information (name servers) has not been associated with your domain. Your domain is not activated in the DNS and will not resolve.

If your domain has remained in this status for several days, you may want to contact your registrar to request information about the delay in processing.

If the TLD requires documentation to be provided for registration, you may need to provide the required documentation.

### active

    ok

This is the standard status for a domain, meaning it has no pending operations or prohibitions.

Asking your registrar to enact status restrictions, like clientTransferProhibited, clientDeleteProhibited, and clientUpdateProhibited, can help to prevent unauthorized transfers, deletions, or updates to your domain.

### pending create

    pendingCreate

This status code indicates that a request to create your domain has been received and is being processed.

If the TLD is on a special registration period (e.g. sunrise), this may indicate that the domain name will be allocated at the end of such period.

If the TLD is not on a special registration period and you are NOT the listed Registrant, you should contact your registrar immediately to resolve the issue.

### pending delete

    pendingDelete

This status code may be mixed with redemptionPeriod or pendingRestore. In such case, depending on the status (i.e. redemptionPeriod or pendingRestore) set in the domain name, the corresponding description presented above applies. If this status is not combined with the redemptionPeriod or pendingRestore status, the pendingDelete status code indicates that your domain has been in redemptionPeriod status for 30 days and you have not restored it within that 30-day period. Your domain will remain in this status for several days, after which time your domain will be purged and dropped from the registry database.

Once deletion occurs, the domain is available for re-registration in accordance with the registry's policies.

If you want to keep your domain name, you must immediately contact your registrar to discuss what options are available.

### pending renew

    pendingRenew

This status code indicates that a request to renew your domain has been received and is being processed.

If you did not request to renew your domain and do not want to keep it (i.e., pay the renewal fee) anymore, you should contact your registrar immediately to discuss what options are available.

### pending restore

    pendingRestore

This status code indicates that your registrar has asked the registry to restore your domain that was in redemptionPeriod status. Your registry will hold the domain in this status while waiting for your registrar to provide required restoration documentation. If your registrar fails to provide documentation to the registry operator within a set time period to confirm the restoration request, the domain will revert to redemptionPeriod status.

Watch your domain's status codes within this frequently defined seven day period to ensure that your registrar has submitted the correct restoration documentation within the time window. If this period ended and your domain has reverted back to a redemptionPeriod status, contact your registrar to resolve whatever issues that may have halted the delivery of your domain's required restoration documentation.

### pending transfer

    pendingTransfer

This status code indicates that a request to transfer your domain to a new registrar has been received and is being processed.

If you did not request to transfer your domain, you should contact your registrar immediately to request that they deny the transfer request on your behalf.

### pending update

    pendingUpdate

This status code indicates that a request to update your domain has been received and is being processed.

If you did not request to update your domain, you should contact your registrar immediately to resolve the issue.

### redemption period

    redemptionPeriod

This status code indicates that your registrar has asked the registry to delete your domain. Your domain will be held in this status for 30 days. After five calendar days following the end of the redemptionPeriod, your domain is purged from the registry database and becomes available for registration.

If you want to keep your domain, you must immediately contact your registrar to resolve whatever issues resulted in your registrar requesting that your domain be deleted, which resulted in the redemptionPeriod status for your domain. Once any outstanding issues are resolved and the appropriate fee has been paid, your registrar should restore the domain on your behalf.

### renew period
    
    renewPeriod

This grace period is provided after a domain name registration period is explicitly extended (renewed) by the registrar. If the registrar deletes the domain name during this period, the registry provides a credit to the registrar for the cost of the renewal.

This is an informative status set for a limited period or your domain's renewal by your registrar. If you did not request to renew your domain and do not want to keep it (i.e., pay the renewal fee) anymore, you should contact your registrar immediately to discuss what options are available.

### server delete prohibited

    serverDeleteProhibited

This status code prevents your domain from being deleted. It is an uncommon status that is usually enacted during legal disputes, at your request, or when a redemptionPeriod status is in place.

This status may indicate an issue with your domain that needs resolution. If so, you should contact your registrar to request more information and to resolve the issue. If your domain does not have any issues, and you simply want to delete it, you must first contact your registrar and request that they work with the Registry Operator to remove this status code.

Alternatively, some Registry Operators offer a Registry Lock Service that allows registrants, through their registrars to set this status as an extra protection against unauthorized deletions. Removing this status can take longer than it does for clientDeleteProhibited because your registrar has to forward your request to your domain's registry and wait for them to lift the restriction.

### server hold
    
    serverHold

This status code is set by your domain's Registry Operator. Your domain is not activated in the DNS.

If you provided delegation information (name servers), this status may indicate an issue with your domain that needs resolution. If so, you should contact your registrar to request more information. If your domain does not have any issues, but you need it to resolve in the DNS, you must first contact your registrar in order to provide the necessary delegation information.

### server renew prohibited

    serverRenewProhibited

This status code indicates your domain's Registry Operator will not allow your registrar to renew your domain. It is an uncommon status that is usually enacted during legal disputes or when your domain is subject to deletion.

Often, this status indicates an issue with your domain that needs to be addressed promptly. You should contact your registrar to request more information and resolve the issue. If your domain does not have any issues, and you simply want to renew it, you must first contact your registrar and request that they work with the Registry Operator to remove this status code. This process can take longer than it does for clientRenewProhibited because your registrar has to forward your request to your domain's registry and wait for them to lift the restriction.


### server transfer prohibited

    serverTransferProhibited

This status code prevents your domain from being transferred from your current registrar to another. It is an uncommon status that is usually enacted during legal or other disputes, at your request, or when a redemptionPeriod status is in place.

This status may indicate an issue with your domain that needs to be addressed promptly. You should contact your registrar to request more information and resolve the issue. If your domain does not have any issues, and you simply want to transfer it to another registrar, you must first contact your registrar and request that they work with the Registry Operator to remove this status code.

Alternatively, some Registry Operators offer a Registry Lock Service that allows registrants, through their registrars to set this status as an extra protection against unauthorized transfers. Removing this status can take longer than it does for clientTransferProhibited because your registrar has to forward your request to your domain's registry and wait for them to lift the restriction.


### server update prohibited

    serverUpdateProhibited

This status code locks your domain preventing it from being updated. It is an uncommon status that is usually enacted during legal disputes, at your request, or when a redemptionPeriod status is in place.

This status may indicate an issue with your domain that needs resolution. If so, you should contact your registrar for more information or to resolve the issue. If your domain does not have any issues, and you simply want to update it, you must first contact your registrar and request that they work with the Registry Operator to remove this status code.

Alternatively, some Registry Operators offer a Registry Lock Service that allows registrants, through their registrars to set this status as an extra protection against unauthorized updates. Removing this status can take longer than it does for clientUpdateProhibited because your registrar has to forward your request to your domain's registry and wait for them to lift the restriction.


### transfer period

    transferPeriod

This grace period is provided after the successful transfer of a domain name from one registrar to another. If the new registrar deletes the domain name during this period, the registry provides a credit to the registrar for the cost of the transfer.

This is an informative status set for a limited period or your domain's transfer to a new registrar. If you did not request to transfer your domain, you should contact your original registrar.

### Client Status Codes are Set by Your Domain's Registrar


### client delete prohibited

    clientDeleteProhibited

This status code tells your domain's registry to reject requests to delete the domain.

This status indicates that it is not possible to delete the domain name registration, which can prevent unauthorized deletions resulting from hijacking and/or fraud. If you do want to delete your domain, you must first contact your registrar and request that they remove this status code.


### client hold

    clientHold

This status code tells your domain's registry to not activate your domain in the DNS and as a consequence, it will not resolve. It is an uncommon status that is usually enacted during legal disputes, non-payment, or when your domain is subject to deletion.

Often, this status indicates an issue with your domain that needs resolution. If so, you should contact your registrar to resolve the issue. If your domain does not have any issues, but you need it to resolve, you must first contact your registrar and request that they remove this status code.


### client renew prohibited

    clientRenewProhibited

This status code tells your domain's registry to reject requests to renew your domain. It is an uncommon status that is usually enacted during legal disputes or when your domain is subject to deletion.

Often, this status indicates an issue with your domain that needs resolution. If so, you should contact your registrar to resolve the issue. If your domain does not have any issues, and you simply want to renew it, you must first contact your registrar and request that they remove this status code.


### client transfer prohibited

    clientTransferProhibited

This status code tells your domain's registry to reject requests to transfer the domain from your current registrar to another.

This status indicates that it is not possible to transfer the domain name registration, which will help prevent unauthorized transfers resulting from hijacking and/or fraud. If you do want to transfer your domain, you must first contact your registrar and request that they remove this status code.


### client update prohibited
 
    clientUpdateProhibited

This status code tells your domain's registry to reject requests to update the domain.

This domain name status indicates that it is not possible to update the domain, which can help prevent unauthorized updates resulting from fraud. If you do want to update your domain, you must first contact your registrar and request that they remove this status code.



---

+ [edit](https://github.com/grabWHOIS/www/edit/main/README.md)
+ [grabWHOIS/www](https://github.com/grabWHOIS/www)
+ [LICENSE](LICENSE)

