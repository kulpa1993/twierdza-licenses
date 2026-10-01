# Twierdza — autoryzacja serwerów

Lista publicznych adresów IPv4 uprawnionych do korzystania z peleryny Twierdza.

## Zmiana zgody
Otwórz `server-allowlist.json`, kliknij ołówek i edytuj `allowedPublicIPv4`. Zapisz przez Commit changes. Adresy wpisuj jako tekst, oddzielone przecinkami. `enabled: false` wyłącza zgodę dla wszystkich serwerów.

Mod serwerowy sprawdza listę co 60 sekund przez HTTPS. Po zmianie może wystąpić dodatkowe opóźnienie cache GitHuba. Publiczny adres wychodzący serwera jest odczytywany przez ipify, a nie z edytowalnego pliku IP. Przy NAT może różnić się od adresu dołączania do gry.

Po starcie wymagana jest poprawna odpowiedź obu usług. Przy błędzie połączenia wcześniej uzyskana zgoda pozostaje ważna maksymalnie 10 minut od ostatniej poprawnej weryfikacji. Usunięcie IP z poprawnej listy lub `enabled: false` wyłącza ochronę przy następnym skutecznym sprawdzeniu. Gracze pozostają na serwerze, ale kamuflaż nie działa.

## Zakres
W repozytorium jest tylko publiczna lista IP. Nie umieszczaj tutaj PBO serwerowego, klucza licencji ani kluczy podpisujących.

To lista zezwoleń, nie rejestr wszystkich serwerów używających moda. GitHub nie wykrywa samodzielnie skopiowanych modów. Zmodyfikowane kopie mogą ominąć kontrolę; starsze wersje bez kontroli online nie są nią objęte.

## Zakres rejestru — 1 października 2026
Lista zawiera 19 modułów z `Twierdza` w nazwie (11 klienckich, 8 serwerowych), w tym bridge reLife. SFP, TW_Terytorium, TW_AdminHammer i KulpaNameTags nie są objęte tym zakresem.

Pole `mods` jest rejestrem zezwoleń dla obecnych i kolejnych integracji. Samo dopisanie modułu nie modyfikuje jego PBO. Obecnie wydaną i przetestowaną kontrolę online ma peleryna; pozostali konsumenci wymagają integracji kodu i testu przed uznaniem ich za zabezpieczone. Zachowano pola główne dla zgodności z peleryną 1.5.0.
