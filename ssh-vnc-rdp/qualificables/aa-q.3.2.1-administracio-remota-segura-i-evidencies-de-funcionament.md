---
hidden: true
---

# AA-Q.3.2.1 — Administració remota segura i evidències de funcionament

> **Activitat d’aula qualificable única de SA03 · Durada: 14 hores**
>
> **Tècnica d’avaluació:** activitats d’aula\
> **Instrument de qualificació:** rúbrica individual\
> **Resultat d’aprenentatge:** RA6 — Gestiona mètodes d’accés remot descrivint les seues característiques i instal·lant els servicis corresponents.

## Repte

Dissenya, desplega, configura de manera segura i comprova un escenari d’administració remota que combine laboratori local i núvol. El treball és individual encara que la xarxa de proves puga compartir-se.

L’escenari ha d’incloure:

* una màquina Linux en **VirtualBox** amb accés SSH;
* un equip **Windows** amb RDP habilitat i una màquina Linux amb servidor VNC;
* proves creuades Linux ↔ Windows;
* una instància Linux a **AWS Academy**, protegida amb un grup de seguretat restrictiu i accedida amb SSH mitjançant clau;
* documentació tècnica i evidències individuals de funcionament.

## Itinerari de treball

1. **Disseny i seguretat.** Dibuixa l’esquema d’equips, adreces, ports i fluxos. Justifica el protocol triat per a cada necessitat i aplica el principi de mínim accés: comptes autoritzats, claus SSH, tallafocs i grups de seguretat.
2. **Laboratori local.** Reinstal·la o instal·la OpenSSH a Linux i comprova el servei, el port, el tallafocs, els registres i l’accés amb clau. Desplega VNC a **GlaDOS** i comprova’l des d’**Alyx** i des de Windows.
3. **Interoperabilitat.** Connecta de Linux a Windows per RDP amb **Remmina** i de Windows a Linux amb un client VNC. En cada cas, crea o modifica un element i comprova’l al sistema destí. Registra origen, destinació, usuari, protocol, acció i resultat.
4. **Extensió a AWS.** Crea o utilitza la instància Linux prevista en AWS Academy, limita SSH/22 a l’origen autoritzat i accedix-hi amb clau. Des de Windows, configura en **PuTTY** un túnel local cap a Webmin (`127.0.0.1:10000`) i administra una opció no destructiva o un recurs de prova. Webmin no ha d’estar exposat a Internet. No publiques credencials, claus privades ni adreces reutilitzables.
5. **Documentació i defensa.** Entrega una memòria breu, clara i reproduïble, amb captures o registres propis, i explica les decisions de seguretat i la comprovació final.

## Materials vinculats

Per a la part de núvol, reutilitza les guies de [desplegament d’Ubuntu Server 24.04 a AWS Academy](https://cipfpbatoi.gitbook.io/serveis-en-xarxa/aws-academy/pindoles-formatives/udxx-03.-desplegament-duna-maquina-virtual-ubuntu-server-24.04-a-aws-academy) i de [configuració de grups de seguretat](https://cipfpbatoi.gitbook.io/serveis-en-xarxa/aws-academy/pindoles-formatives/udxx-02.-configuracio-dels-grups-de-seguretat). El material de bastió és ampliació voluntària: [configuració d’un bastion host a AWS](https://cipfpbatoi.gitbook.io/serveis-en-xarxa/aws-academy/practiques/udxxp01.-configuracio-dun-bastion-host-a-aws).

## Evidències mínimes

* esquema de l’escenari i taula d’adreces, ports i protocols;
* configuració aplicada i justificació de les mesures de seguretat;
* prova individual d’SSH reinstal·lat a Linux: servei, port/tallafocs, registre, clau i una ordre remota;
* prova VNC a GlaDOS des d’Alyx i des de Windows, amb una modificació comprovada al servidor;
* prova Linux → Windows per RDP amb Remmina, amb una modificació comprovada a Windows;
* prova Windows → Linux amb PuTTY i Webmin a través d’un túnel SSH local, amb una acció administrativa comprovada;
* prova d’accés SSH a AWS Academy amb el grup de seguretat ajustat;
* conclusió breu amb avantatges, limitacions i incidències resoltes.

## Rúbrica RA6

| Criteri                                                           | Evidència observable                                                                            | Assoliment |
| ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ---------- |
| **a)** Mètodes d’accés i administració remota                     | Descriu SSH, RDP i VNC i n’explica un ús adequat.                                               | 1 punt     |
| **b)** Servei d’accés remot en línia de comandos                  | Instal·la, configura i comprova SSH amb mesures bàsiques de seguretat.                          | 1,5 punts  |
| **c)** Servei d’accés remot en mode gràfic                        | Configura VNC funcional a Linux i RDP habilitat a Windows, amb accés gràfic verificat.          | 1,5 punts  |
| **d)** Comprovació de tots dos mètodes                            | Aporta evidències pròpies d’SSH, VNC i RDP amb una acció i comprovació final.                   | 1,5 punts  |
| **e)** Avantatges i deficiències                                  | Compara de manera raonada els protocols i les seues limitacions.                                | 1 punt     |
| **f)** Accés remot entre sistemes de diferent naturalesa          | Demostra Linux → Windows amb Remmina/RDP i Windows → Linux amb client VNC, documentades.        | 1,5 punts  |
| **g)** Administració remota entre sistemes de diferent naturalesa | Usa PuTTY i Webmin per túnel SSH per executar, verificar i documentar una acció administrativa. | 1,5 punts  |
| **Seguretat, documentació i autonomia**                           | Configuració restrictiva, evidències individuals, traçabilitat i respecte de les credencials.   | 0,5 punts  |

**Total: 10 punts.** Una evidència sense identificació individual, sense data/context o que expose credencials no es considera vàlida fins que es corregisca.

## Lliurament

Presenta un únic dossier tècnic individual en el format indicat a l’aula virtual. Inclou les evidències en l’ordre de la rúbrica i identifica què demostra cada una. Les claus privades, contrasenyes, fitxers `.pem` i dades sensibles no s’han d’entregar ni publicar.
