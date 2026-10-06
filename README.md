# Twierdza — autoryzacja serwerów

Lista zezwoleń dla 25 modułów Twierdza: 14 klienckich i 11 serwerowych, w tym bridge reLife. Zatwierdzony publiczny adres wychodzący serwera: **37.28.155.66**.

## Aktualne wydanie
Wydanie `01OCT-GITHUB-1.0`, build `20261001-175110-603292`, zawiera integrację kodu i przebudowane PBO całego zestawu. SFP, TW_Terytorium, TW_AdminHammer i KulpaNameTags są poza zakresem.

Należy aktualizować cały zestaw razem: TwierdzaAdmin udostępnia wspólne API, a TwierdzaAdmin_Server wykonuje weryfikację. Prywatne PBO serwerowe pozostają wyłącznie w `-serverMod`. Peleryna nadal wymaga lokalnego prywatnego pliku licencji. Nie publikuj PBO serwerowych, źródeł prywatnych, kluczy licencji ani kluczy podpisujących w tym repozytorium.

## Zmiana zgody
Edytuj `server-allowlist.json`. Zgoda wymaga głównego `enabled: true`, IP na głównej liście oraz aktywnego wpisu danego modułu z tym IP w `mods`. Pary klient/serwer wymagają obu wpisów; cały zestaw wymaga TwierdzaAdmin i TwierdzaAdmin_Server. Nie zmieniaj identyfikatorów ani schematu. Główne `modId` pozostaje dla zgodności ze starszą peleryną.

Serwer odczytuje IP przez HTTPS z ipify i listę z GitHuba co 60 sekund. Cache GitHuba może opóźnić zmianę. Nowy start wymaga poprawnej odpowiedzi; przy awarii połączenia wcześniejsza zgoda wygasa najpóźniej 10 minut od ostatniej poprawnej weryfikacji. Usunięcie IP lub wyłączenie wpisu działa po odebraniu kolejnej poprawnej listy.

Brak zgody blokuje funkcje skryptowe Twierdzy i zapisuje informację w logu. Nie zamyka serwera, nie wyrzuca graczy i nie usuwa przedmiotów ani zapisów. Inicjalizacja i odtwarzanie danych pozostają dostępne. TwierdzaRdzen_Server jest adapterem konfiguracji, a jego zgoda jest wymagana przez mechaniki TwierdzaSkills_Rdzen.

## Sprawdzenie
W logu skryptów serwera szukaj:
```
[TW_MOD_LICENSE] ONLINE ACCEPTED: IP 37.28.155.66 modules=19
```
Przy obcym IP występuje `ONLINE DENIED` z informacją, że serwer nie jest autoryzowany. Liczy się adres wychodzący widziany przez ipify; NAT/VPN może go zmienić.

Dokładnie wydane 19 PBO przeszło 84 testy z wynikiem PASS, 0 FAIL; World i Mission skompilowały się. Odmowę dla obcego IP sprawdzono przez rzeczywiste HTTPS. Zgodę docelowego IP, cofnięcie zgody i awarie sprawdzono kontrolowanymi odpowiedziami w osobnym dodatku testowym, którego nie ma w wydaniu. Nie wykonano testu na produkcyjnym IP ani wizualnego testu klienta. Środowisko testowe zgłosiło osobny komunikat LBmaster Advanced Groups o braku autoryzowanej części serwerowej; jego licencji nie zmieniano.

## Kolejne mody i ograniczenia
Każdy kolejny moduł Twierdza należy dodać do `mods` dla tego IP, zintegrować z kontrolą w kodzie, przebudować i przetestować. Sam wpis na GitHubie nie zabezpiecza PBO.

To lista zezwoleń, nie rejestr wszystkich serwerów używających modów. GitHub nie wykrywa samodzielnie kopii. Kontrola nie uniemożliwia ekstrakcji modeli/tekstur ani nie wyłącza statycznej konfiguracji załadowanej przez klienta. Stare PBO bez kontroli online nie są objęte blokadą, a zmodyfikowane kopie mogą ją ominąć.
