# OpenSourceTech2021

## Instrukcja uruchomienia środowiska laboratoryjnego

1. **Wymagania systemowe**

Komputer/laptop z systemem operacyjnym MS Windows 10, Apple macOS lub Linux, o następujących minimalnych parametrach:
- procesor min. 4 rdzeniowy (lub 2 rdzeniowy z technologią Hyper-Threading) i włączoną wirtualizacją w BIOS / UEFI
- minimum 16 GB pamięci RAM (maszyny wirtualne zajmą 12GB)
- około 20 GB wolnej przestrzeni dyskowej

Dodatkowo należy pobrać i zainstalować następujące oprogramowanie:

- Vagrant - narzędzie do automatyzacji uruchamiania środowisk wirtualnych https://www.vagrantup.com/downloads
- VirtualBox - środowisko wirtualizacyjne https://www.virtualbox.org/wiki/Downloads

> Instalacja powyższych komponentów wymaga posiadania uprawnień Administratora systemu operacyjnego. 

2. **Uruchomienie środowiska laboratoryjnego**

Po instalacji wymaganego oprogramowania należy pobrać plik z definicją laboratoryjnego środowiska ("Vagrantfile") i zapisać go w lokalnym katalogu np. 'OpenSourceTech' na dysku C: (w sytemach MS Windows) lub w katalogu domowym użytkownika (w systemach Apple macOS i Linux). Bezpośredni link do pobrania: https://raw.githubusercontent.com/jbiniek/OpenSourceTech21/main/Vagrantfile

> **UWAGA**
> **Plik "Vagrantfile" należy pobrać i zapisać tak, jak jest udostępniony, bez dopisywania rozszerzeń typu .txt czy innych zmian. Najlepiej kliknąć prawym przyciskiem w powyższy link, wybrać "Zapisz jako.." i upewnić się, że nazwa pliku to samo "Vagrantfile" bez rozszerzeń.**

Po pobraniu pliku Vagrantfile należy uruchomić terminal i wykonać następujące polecenia: 
- w systemie MS Windows
```bash
cd c:\OpenSourceTech
vagrant up
```
- w systemach Apple macOS i Linux
```bash
cd ~/OpenSourceTech
vagrant up
```
Poprawne inicjalizowanie środowiska laboratoryjnego powinno zakończyć się uruchomieniem maszyny wirtualnej, która posłuży nam do instalacji Ranchera.

Kolejnym krokiem będzie wywołanie polecenia 
```bash
docker run -d --restart=unless-stopped \
  -p 80:80 -p 443:443 \
  --privileged \
  rancher/rancher:latest
```
które pobierze obrazy kontenerów składających się na serwer Ranchera i je uruchomi. Szerszy opis procedury instalacyjnej znajduje się w dokumentacji: https://rancher.com/docs/rancher/v2.x/en/installation/other-installation-methods/single-node-docker/

Po zakończeniu tego polecenia Rancher będzie potrzebował kilku minut na pełne wystartowanie usług. Po tym czasie będzie go można wywołać wpisując w przeglądarce adres https://127.0.0.1 

Używamy w tej instalacji certyfikatu "self-signed" dlatego przeglądarka może nas ostrzegać przed niebezpieczną stroną. W takim wypadku należy wybrać "Zaawansowane" i potwierdzić, że chce się wejść na tę stronę.

Ekran powitalny poprosi nas o ustanowienie hasła administratora, trzeba też zaznaczyć zgodę na warunki korzystania. Następnie zostaniemy poproszeni o adres serwera, należy podać:

> 192.168.10.10 

Można już zacząć przygodę z Rancherem!
