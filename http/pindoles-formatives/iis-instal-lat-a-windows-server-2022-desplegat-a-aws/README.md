---
description: Desplegament i configuració d'un bastion host.
---

# ⚒ IIS, instal·lat a Windows Server 2022, desplegat a AWS

En primer lloc, accedim a la consola d'administració de serveis d'AWS.

<figure><img src="../../.gitbook/assets/image (97).png" alt=""><figcaption><p>Consola d'administració d'AWS</p></figcaption></figure>

Al buscador, a la part superior de la web, Introduïm el text 'EC2' i seleccionem el servei 'EC2 - servidors virtuals al núvol'.

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption><p>Buscador de serveis</p></figcaption></figure>

Ens mostrarà el panel del servei EC2, amb una graella que mostra els serveis en execució.&#x20;

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption><p>Panel del servei EC2</p></figcaption></figure>

Per a crear el nostre host bastió, haurem de polsar sobre l'opció instàncies:

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption><p>Menú instancies</p></figcaption></figure>

