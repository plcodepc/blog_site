---
layout: post
title:  "Protokół HTTP  cz.1"
date:   2019-05-20 05:35:33 +0200
category: dodatki
description: "Metody http połączenie z serwerem przez http. REST api"
author: "Admin"
tags: [http, https, tts, tsl, js, post, get, rest, api, metody, axios, status, server]
snipped: "Metody http połączenie z serwerem przy użyciu protokołu http - odpowiedzi z serwera. Rest api omówienie."

comments: true
---

### Wstęp
Protokół HTTP (ang. Hypertext Transfer Protocol) to zasady wymiany informacji pomiędzy klientem (np. przeglądarka internetowa ) a serwerem miejscem gdzie znajduje się zasób. Http określa dokładnie format kompunikacji pomiędzy serwerem a klientem. Dzieki temu możemy wysłać zapytanie do pobrania danych z serwera lub wysłać zapytanie modyfikujące dany zasób na serwerze.

### HTTPS
Hyper Text Protocol Secure - jest to protokół http wzbogacony o szyfrowanie. Wcześniej używany był do szyfrowania protokół `SSL` a teraz `TLS` dzięki niemu uniemożliwiamy przechwytywanie i zniane przesyłanych danych. Obecnie https jest już standardem i jeżeli jakaś strona nie jest szyfrowana to wpłynie to negatywnie na jej SEO.

### Żądania HTTP
W specyfikacji HTTP występuje osiem metod które możemy wysłać do serwera aby otrzymać odpowiedz. W zależności której użyjemy wykonamy odpowiednią akcję modyfikacji, pobrania, usunięcia zasobu z serwera.

#### GET 
Jest to podstawowa metoda używana najczęściej. Użycie metody GET wyśle do serwera zapytanie o żądany zasób. Metoda GET jest dosyć bezpieczna ponieważ nie modyfikuje danych na serwerze a jedynie je pobiera i przesyła do np. przeglądarki. Zapytanie przy użyciu GET może zawierać dodatkowe parametry, które są przekazywane w adresie URL za pomocą tzw. query string. Dane pobrane tą metodą zostają zapisane w cache-u dzięki temu gdy wykonamy ponownie zapytanie pod ten sam adres przeglądarka sprawdzi czy nie ma takiego zasobu w cache. Jeżeli nie  znajdzie to wtedy wykona ponowne zapytanie do serwera.

#### HEAD 
Zapytanie tego typu jest używane do sprawdzenia czy nastąpiła modyfikacja danego zasobu. Metoda ta jest bardzo podobna do wspomnianej wyżej, z tym wyjątkiem że w HEAD nie otrzymujemy w wiadomości zawartości lecz tylko nagłówki. Dlatego też jeżeli zasób jest duży, a my chcemy tylko sprawdzić czy nastąpiła jakaś zmiana bez pobierania jej możemy użyć właśnie HEAD zamiast GET.

#### OPTIONS

Metoda ta wykorzystywana jest do określenia listy dostępnych metod HTTP w danym zasobie. Użycie options nie zwraca ciała odpowiedzi tylko sam nagłówek o nazwie `Allow` który zawiera listę dostępnych metod dla zasóbu.

#### POST

Ogólnie mówiąc metoda ta jest używana do przesyłania danych na serwer. Używając tej metody zawsze należy pamiętać o bezpieczeństwie i walidacji danych przesyłanych na serwer. W praktyce użycie metody post wykorzystujemy do przesyłania formularzy kontaktowych, dodawanie danych na serwer do istniejącego zasobu lub do utworzenia całkiem nowego. Dane przesyłane metodą post zawirają tzw ładunek, tam własnie znajdują się dane przesyłane do serwera.

#### PUT

PUT służy do aktualizacji danych we wskazanym zasobie a jeżeli zasób nie istnieje to do jego stworzenia. Aby zaaktualizować zasób na serwerze musimy znać dokładny adres url do tego zasobu aby nie zmodyfikować innego zasobu. Dodatkowo metoda ta podmienia wszystkie właściwości zasobu.                                                                 

#### PATCH 
Metoda ta również służy do aktualizacji zasobów na serwerze, ale patch podmienia tylko wyłącznie wybrane właściwości na podstawie przekazanej instrukcji. (patrz RFC 6902). 

#### DELETE
Jak sama nazwa wskazuje metoda ta służy do usuwania danych z serwera. Dzieki tej metodzie możemy usunąć pojedynczy zasób lub nawet całą kolekcję.


#### CONNECT

Służy do utworzenia połączenia pomiędzy klientem a serwerem.

#### TRACE

Metoda ta służy do testowania połączenia. Jeżeli wyślemy odpowiednie zapytanie do serwera w odpowiedzi powinniśmy otrzymać właśnie to zapytanie. Dzięki temu możemy testować czy serwer otrzymuje poprawnie nasze zapytania. Metoda trace zawiera tylko nagłówek bez ciała wiadomości.



## Statusy odpowiedzi z serwera

Każda odpowiedź z serwera zawiera między innymi informacje o statusie, czy żądanie zostało przetworzone prawidłowo czy nie. Kody statusów możemy podzielić na 5 grup i każda daje nam inne informacje dzięki którym możemy, określić ewentualny błąd czy też powodzenie wysłanej akcji.

- Statusy 1XX 

Zbiór statusów informujący clienta że zapytanie jest dostarczone i przetwarzane przez serwer, tzw kody informacyjne.

- Status 2XX

Informują nas że żądanie zostało prawidłowo przetworzone. W zależonści od numeru statusu dostaniemy odpowiedną informacje.
200 - zapytanie przetworzone prawidłowo, 201 - zapytanie powiodło się zasób został utworzony, 202 - przyjęte przez serwer zapytanie ale jego akcja nie została jeszcze ukończona, 204 - brak ciała wiadomości. Kody 2XX określają status powodzenia akcji.

- Status 3XX

Informują że wymagana jest dodatkowa akcja aby zapytanie zostało ukończone. Używane są do ustawiania przekierowań np. 301 Zasób zmienił swój URL. Kody 3XX odnoszą się do przekierowań.

- Status 4XX

Kody z tej grupy informują o błędzie ze strony klienta. Najczęstszy błąd to 404 - zasób nie został znaleziony, 400 - nieprawidłowe zapytanie, 401 - brak autoryzacji.

- Status 5XX

Kody błędu serwera http, informują że zapytanie nie może zostać przetworzone po stronie serwera. 500 - wewnętrzny błąd serwera, 504 - przekroczony czas oczekiwania.

## Podsumowanie

To narazie pierwsza część omawiania protokołu http i rest api wykorzystujący http. Zostały omówione metody kompunikacji klienta z serwerem oraz kody odpowiedzi. W następnych częściach omówię strukturę adresu url, tworzenie zasobów itp. Koniec.