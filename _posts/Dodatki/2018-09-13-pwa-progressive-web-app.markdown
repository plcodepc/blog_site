---
layout: post
title:  "PWA - Progressive Web Application"
date:   2018-09-13 05:35:33 +0200
category: dodatki
author: "Admin"
tags: [web ,service worker, aplikacja, pwa , manifest, service, worker, icon, offline]
snipped: "PWA - jak po co i dlaczego powinieneś wiedzieć co to."
image: https://res.cloudinary.com/codepc/image/upload/v1536840541/posts/pwa/progressive-web-app-co-to-jest-codepc.pl.png
full-image: https://res.cloudinary.com/codepc/image/upload/v1536841002/posts/pwa/progressive-web-app-co-to-jest-post-img-wiekszy-codepc.pl.png
comments: true
---

<h1> Progressive Web Apps </h1> - co to jest po co wgl się tym interesować. Czy powinieneś przerobić stronę na PWA?

W obecnych czasach coraz więcej osób korzysta z internetu a liczba użytkowników wyświetlających strony na urządzeniach mobilnych jest większa. Mimo że obecnie jest szeroki dostęp do internetu to nadal są użytkownicy którzy korzystają w wolniejszych łączy przez to strony które odwiedzają ładują się wolniej.

Jeżeli twoja aplikacja internetowa ładuje się długo nikt nie będzie czekał na jej załadowanie po prostu znajdzie inną. Podobnie sprawa się ma z wyglądem na urządzeniach mobilnych który jest bardzo ważny. Strona która nie wyświetli się poprawnie na urządzeniu będzie odebrana jako mało profesjonalna i zniechęci użytkownika do powrotu. Podobna sprawa ma się z bezpieczeństwem witryny.

Aplikacja progresywna to strona internetowa zachowująca się jak aplikacja natywna, która po zapisaniu nie będzie potrzebować internetu czyli będzie mogła nadal działać w trybie offline.
Po co stosować taki zabieg? Wszystko po to aby strona przeładowywała się szybciej, aby mogła działać gdy użytkownik straci połączenie z internetem, aby była bezpieczna.
Zamysł jest taki aby użytkownik nie był w stanie odróżnić aplikacji natywnej od Progressive Web App.

## Podsumujmy dlaczego: PWA?

Szybsze ładowanie strony. Poprzez cachowanie strona nie będzie musiała za każdym razem pobierać informacji z serwera.
Oszczędzamy czas i transfer użytkownika naszej aplikacji. A gdyby użytkownik stracił połączenie z internetem to nie będzie musiał przerywać korzystania z naszej strony.

Czyli powinniśmy przerobić stronę na PWA ale jak? Jak już wiemy PWA nie oznacza jakiejś nowej technologii ale zestaw dobrych praktyk które powinny zostać spełnione aby można było nazwać stronę progresywną.
1. Strona powinna działać dla każdego użytkownika niezależnie od wykorzystywanej przeglądarki.
2. Powinna być responsywna i wyświetlać się poprawnie na każdym urządzeniu.
3. Powinna wyświetlać się w trybie offline.
4. Kontent powinien być zawsze aktualny (aktualizacja servis workera).
5. Bezpieczeństwo - aplikacja musi wykorzystywać protokół HTTPS a nie zwykły HTTP aby kontent który widzi osoba w aplikacji nie mógł zostać podsłuchany, zmieniony przez kogoś innego.
6. Powinna być możliwość zainstalowania na urządzeniu mobilnym jak zwykła aplikacja natywna ale bez odwiedzania app-store jak ma miejsce z aplikacjami natywnymi.
7. Strona powinna być łatwo dostępna przez url - linkowalna.

Aby sprawdzić w jakim stopniu nasza strona spełnia powyższe wymagania wystarczy w Google Chrome uruchomić dev-tools <b>(CTRL+SHIFT+I )</b> i w zakładce Audits uruchomić test (Run Audits).
Jeżeli chcesz sprawdzić jakie strony które odwiedziłeś były PWA wystarczy wejść w zakładkę Application i rozwinąć listę Service Workers from other Application wyświetli się lista strona które zostały zarejestrowane. 

Na koniec krótko wymienię co trzeba zrobić aby nasza strona była PWA.
- Stworzyć manifest aplikacji w pliku json. Link do prostego generatora takiego pliku <a href="https://app-manifest.firebaseapp.com" > Manifest-json</a>
- Stworzenie serwis workera który będzie cachować naszą stronę w tle i zapisywał informacje w pamięci podręcznej. (Wielkość cachu - kilka procent dysku urządzenia w zależności od przeglądarki).
- Podpięcie ikony która będzie widoczna na urządzeniu użytkownika w bloku aplikacji po instalacji.
- Aplikacja musi być podpięta pod HTTPS oraz kontent z innych źródeł jak zdjęcia linkowane powinien być szyfrowany.


To podstawowe wymagania aby nasza aplikacja była szybka i wydajna oraz zachowywała się jak aplikacja natywna oraz mogła działać w trybie offline. Oczywiście istnieją sposoby na zdefiniowanie jak i kiedy powinna aplikacja korzystać z trybu offline a kiedy być online ale o tym może kiedy indziej.
Na koniec daję link do checklisty PWA - <a href="https://developers.google.com/web/progressive-web-apps/checklist" > PWA Checklist </a>




