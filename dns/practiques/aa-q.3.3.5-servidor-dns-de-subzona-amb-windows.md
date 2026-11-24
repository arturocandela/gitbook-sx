---
description: >-
  Delegació pública de subwin.nomcognom.netsx.es a una EC2 Windows Server amb
  DNS.
---

# 📎 AA-Q.3.3.5 - Servidor DNS de subzona amb Windows

## Objectiu

Després de crear la subzona Linux, es construeix una segona delegació real:

```
subwin.nomcognom.netsx.es
```

La zona pare `nomcognom.netsx.es` delega `subwin` a una EC2 Windows Server. Així es comprova que el mecanisme DNS de delegació, NS i _glue_ és el mateix encara que el servidor fill siga Windows DNS.

## Abans de començar

Han d'estar operatius el DNS públic pare i la subzona Linux. Es crea una EC2 amb Windows Server, una Elastic IP pròpia i un _Security Group_ que permeta entrada UDP/53 i TCP/53 des d'Internet. L'administració RDP s'ha de limitar a l'origen autoritzat.

S'utilitzen:

* `IP_PARE`: Elastic IP del DNS de `nomcognom.netsx.es`;
* `IP_SUBWIN`: Elastic IP de Windows Server;
* `nomcognom`: identificador assignat.

## 1. Delegar `subwin` en el DNS pare

En el fitxer de zona de `nomcognom.netsx.es`, s'afig:

```dns
subwin      IN NS dns1.subwin.nomcognom.netsx.es.
dns1.subwin IN A  IP_SUBWIN
```

L'A és el _glue_ de l'NS de Windows. S'incrementa la sèrie, es valida la zona i es recarrega BIND al pare.

## 2. Instal·lar i assegurar el servidor DNS de Windows

En Windows Server s'instal·la el rol **Servidor DNS** des de l'Administrador del servidor.

En el tallafoc de Windows s'han de permetre consultes DNS entrants per UDP/53 i TCP/53. El _Security Group_ d'AWS i el tallafoc de Windows són capes diferents: les dues han de permetre el trànsit.

En les propietats del servidor DNS:

* es desactiva la recursió, perquè no ha de ser un resolutor públic;
* es comprova que les transferències de zona estan desactivades;
* no es configuren reenviadors per donar servei públic;
* si hi ha una opció de DNSSEC que interfereix amb l'assaig, es deixa desactivada segons la instrucció de la pràctica.

## 3. Crear la zona filla

En **Administrador DNS → Zones de cerca directa → Zona nova**, es crea una **zona principal** basada en fitxer:

```
subwin.nomcognom.netsx.es
```

No es permeten actualitzacions dinàmiques. En les propietats de la zona:

* el SOA ha de tindre com a servidor primari `dns1.subwin.nomcognom.netsx.es.`;
* s'afig l'NS `dns1.subwin.nomcognom.netsx.es.`;
* l'A de `dns1` apunta a `IP_SUBWIN`;
* s'afig l'A de `www` amb `IP_SUBWIN`;
* s'afig un TXT a l'àpex: `Subzona Windows de NOM_COGNOM`.

L'A de `dns1` ha de ser idèntic al _glue_ del DNS pare.

## 4. Verificar la infraestructura

Des d'una EC2 Linux o una altra xarxa externa:

```bash
# Autoritat del fill Windows.
dig @IP_SUBWIN subwin.nomcognom.netsx.es. SOA +norecurse +notcp +ignore
dig @IP_SUBWIN subwin.nomcognom.netsx.es. SOA +norecurse +tcp
dig @IP_SUBWIN www.subwin.nomcognom.netsx.es. A +norecurse

# Delegació declarada pel pare.
dig @IP_PARE www.subwin.nomcognom.netsx.es. A +norecurse

# Resolució pública completa.
dig www.subwin.nomcognom.netsx.es. A
dig +trace www.subwin.nomcognom.netsx.es. A

# Transferència prohibida.
dig @IP_SUBWIN subwin.nomcognom.netsx.es. AXFR
```

Les respostes directes han de mostrar `aa`; la consulta al pare ha de mostrar l'NS i el _glue_; i l'AXFR ha de ser denegat.

## 5. Lliurament

S'entreguen:

* Elastic IP de la EC2 Windows;
* NS i _glue_ afegits a la zona pare;
* captures de la zona Windows, del Security Group i del tallafoc;
* proves de UDP, TCP, referència, resolució pública i transferència denegada;
* una explicació breu de la diferència entre el pare, el fill Linux `sublin` i el fill Windows `subwin`.

[Configuració inicial del DNS a AWS](<../README (1).md>) · [Pràctica de subzona amb Linux](ud02p03.-configuracio-dun-servidor-dns-de-subzona-amb-linux.md) · [Zones, delegació i glue](../fonaments/delegacio-i-glue.md)
