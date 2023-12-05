---
description: Apache 2, instal·lat a Ubuntu Server 22.04, desplegat a AWS
---

# ⚒ Apache 2, instal·lat a Ubuntu Server 22.04, desplegat a AWS

## Introducció.

Apache 2 HTTP Server és un servidor web de codi obert, que ens permet allotjar llocs web, tant estàtics com dinàmics.&#x20;

Apache 2 destaca per la seva arquitectura modular, flexibilitat en la configuració, suport a la seguretat i rendiment, essent àmpliament utilitzat per a publicar contingut a la web.

## Configuració de la instància EC2.

Per a configurar el nostre servidor web Apache 2, haurem de:

* [Configurar un grup de seguretat internet](http://127.0.0.1:5000/s/dcAEDgX05ILtqXlw2HAH/pindoles-formatives/configuracio-dels-grups-de-seguretat/configuracio-del-grup-de-seguretat-internet.), que permetrà l'accés a internet de la nostra instància EC2, per a la instal·lació de paquets.
* [Configurar un grup de seguretat ssh-extern](http://127.0.0.1:5000/s/dcAEDgX05ILtqXlw2HAH/pindoles-formatives/configuracio-dels-grups-de-seguretat/configuracio-del-grup-de-seguretat-ssh-extern.), que permetrà l'accés SSH a la nostra instància EC2, des d'internet, per a efectuar les operacions de manteniment.
* [Configurar un grup de seguretat http-https](http://127.0.0.1:5000/s/dcAEDgX05ILtqXlw2HAH/pindoles-formatives/configuracio-dels-grups-de-seguretat/configuracio-del-grup-de-seguretat-http-https.), que permetrà l'accés als ports tcp/80 (http) i tcp/443 (https) a la nostra instància, per servir les webs allotjades al mateix.
* [Configurar una instància EC2](http://127.0.0.1:5000/s/dcAEDgX05ILtqXlw2HAH/pindoles-formatives/desplegament-duna-maquina-virtual-ubuntu-server-22.04-a-aws-academy) amb Ubuntu Server 2023, que apliqui els grups de seguretat configurats en els punts anteriors.
* Instal·lació i configuració del programari Apache 2.&#x20;

Els primers 4 punts podem fer-los seguint les instruccions dels enllaços de cada un dels paràgrafs.&#x20;

En les pàgines adients s'explicarà la instal·lació i configuració del servidor web Apache 2.

