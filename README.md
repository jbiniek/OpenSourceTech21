# OpenSourceTech2021

## Instrukcja uruchomienia środowiska laboratoryjnego

1. **Wymagane komponenty**

Komputer PC z systemem operacyjnym MS Windows 10, Apple macOS lub Linux o następujących minimalnych parametrach:
- procesor min. 4 rdzeniowy lub 2 rdzeniowy z technologią Hyper-Threading i włączoną opcją wirtualizacji w BIOS / UEFI
- minimum 12 GB pamięci RAM, zalecane 16GB (maszyna wirtualna zajmie 8GB)
- około 20 GB wolnej przestrzeni dyskowej

Dodatkowo należy pobrać i zainstalować następujące oprogramowanie:

- Vagrant - narzędzie do automatyzacji uruchamiania środowisk wirtualnych https://www.vagrantup.com/downloads
- VirtualBox - środowisko wirtualizacyjne https://www.virtualbox.org/wiki/Downloads

> Instalacja powyższych komponentów wymaga posiadania uprawnień Administratora systemu operacyjnego. 

2. **Uruchomienie środowiska laboratoryjnego**

Po instalacji wymaganego oprogramowania należy pobrać plik z definicją laboratoryjnego środowiska ("Vagrantfile") i zapisać go w lokalnym katalogu np. 'OpenSourceTech' na dysku C: (w sytemach MS Windows) lub w katalogu domowym użytkownika (w systemach Apple macOS i Linux). Bezpośredni link do pobrania: https://raw.githubusercontent.com/jbiniek/OpenSourceTech21/main/Vagrantfile

> **UWAGA**
> **Plik "Vagrantfile" należy pobrać i zapisać tak, jak jest udostępniony, bez dopisywania rozszerzeń typu .txt czy innych zmian.**

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
