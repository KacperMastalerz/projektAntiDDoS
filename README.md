Celem modułu powiadamiania o ataku w systemie anty-DDoS jest szybkie informowanie odpowiednich interesariuszy o wykryciu i charakterystyce ataków DDoS, umożliwiając im skuteczną reakcję i zarządzanie sytuacją.

Opis ogólny:
Moduł powiadamiania o ataku ma za zadanie monitorować i analizować zdarzenia związane z atakami DDoS, a następnie automatycznie lub ręcznie powiadamiać odpowiednie osoby lub systemy o wykrytych incydentach.

Wymagania funkcjonalne:

3.1 Wykrywanie ataków:

Moduł powinien być zintegrowany z modułem mitygacji, aby otrzymywać informacje na temat wykrytych ataków DDoS w czasie rzeczywistym.
System powinien rozpoznawać różne typy ataków i ich charakterystyki.
3.2 Powiadomienia:

Moduł powinien umożliwiać konfigurację różnych kanałów powiadamiania, takich jak e-maile, powiadomienia SMS, alerty systemowe itp.
System powinien dostarczać szczegółowe informacje na temat ataku, takie jak rodzaj ataku, źródło, cele i inne istotne dane.

3.3 Automatyczne powiadamianie:

W przypadku wykrycia ataku, moduł powinien automatycznie wysyłać powiadomienia do zdefiniowanych adresatów zgodnie z wcześniej skonfigurowanymi regułami.
System powinien umożliwiać dynamiczną konfigurację odbiorców powiadomień w zależności od rodzaju ataku.

3.4 Ręczne powiadamianie:

Administrator systemu powinien mieć możliwość ręcznego wysyłania powiadomień w sytuacjach wymagających interwencji lub komunikacji zespołowej.
Wymagania niefunkcjonalne:

4.1 Szybkość powiadamiania:

Moduł powinien dostarczać powiadomienia o atakach w czasie bliskim rzeczywistemu, aby umożliwić szybką reakcję na incydent.

4.2 Skalowalność:

System powinien obsługiwać duże ilości powiadomień jednocześnie, umożliwiając efektywne zarządzanie w przypadku masowych ataków.

4.3 Integracja:

Moduł powiadamiania powinien być zintegrowany z istniejącymi systemami monitoringu, zarządzania incydentami i mitygacji w ramach infrastruktury anty-DDoS.
