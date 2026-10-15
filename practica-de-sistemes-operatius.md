---
description: >-
  Pràctiques guiades per instal·lar, configurar i administrar sistemes
  operatius.
icon: terminal
---

# Pràctica de sistemes operatius

En aquesta pàgina trobaràs una guia pràctica per aplicar els conceptes de teoria mitjançant màquines virtuals i exercicis d’administració de sistemes.

## Objectius

* Crear i configurar màquines virtuals.
* Instal·lar sistemes operatius Windows i Linux.
* Configurar xarxa, adreçament IP i DNS.
* Administrar usuaris, permisos, serveis i actualitzacions.
* Comprovar el funcionament amb ordres i proves bàsiques.

## 1. Preparar la màquina virtual

1. Obre VirtualBox o el programa de virtualització indicat a classe.
2. Crea una màquina virtual amb un nom identificable.
3. Assigna la memòria RAM, els processadors i el disc segons els requisits del sistema operatiu.
4. Selecciona la imatge ISO d’instal·lació.
5. Configura l’adaptador de xarxa segons les indicacions de la pràctica.

## 2. Instal·lar el sistema operatiu

1. Inicia la màquina virtual des de la ISO.
2. Segueix l’assistent d’instal·lació.
3. Configura idioma, teclat, disc i usuari.
4. Reinicia la màquina i retira la ISO si cal.
5. Comprova que el sistema arrenqui correctament.

## 3. Configurar i verificar la xarxa

A Linux, consulta la configuració amb:

```bash
ip addr
ip route
```

Per comprovar la connectivitat:

```bash
ping -c 4 8.8.8.8
```

Per comprovar la resolució DNS:

```bash
nslookup example.com
```

A Windows, utilitza aquestes ordres al terminal:

```powershell
ipconfig /all
ping 8.8.8.8
nslookup example.com
```

## 4. Tasques d’administració

* Crear un usuari de prova i comprovar-ne l’accés.
* Revisar les actualitzacions disponibles.
* Consultar els processos i serveis en execució.
* Revisar l’espai de disc i l’ús de memòria.
* Aplicar permisos a una carpeta de prova i verificar-ne el resultat.

## 5. Comprovar els resultats

* [ ] El sistema operatiu s’instal·la i arrenca correctament.
* [ ] La configuració IP és l’esperada.
* [ ] Les proves de connectivitat i DNS funcionen quan la xarxa ho permet.
* [ ] Les tasques d’administració s’han completat.
* [ ] Has guardat captures de pantalla i les ordres utilitzades.

## 6. Documentació de la pràctica

Per entregar l’activitat, inclou l’objectiu, la configuració de la màquina virtual, els passos realitzats, les ordres executades, les captures de pantalla i una breu conclusió amb els problemes trobats i la seva solució.

> **Important:** adapta els recursos, les adreces IP i les ordres als requisits concrets que indiqui el professor. No canviïs la configuració de xarxa d’altres màquines sense comprovar abans l’esquema de la pràctica.
