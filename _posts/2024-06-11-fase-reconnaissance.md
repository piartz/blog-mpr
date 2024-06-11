---
layout: default
title: "Fase de recoñecemento: recoñecemento pasivo en DNS"
date: 2024-06-11
---

## Recoñecemento Pasivo en DNS

O recoñecemento (Reconnaissance) sitúase nas primeiras fases dunha interación ofensiva. Unha enumeración axeitada proporciona información útil, que máis tarde definirá as actividades a levar a cabo nas vindeiras fases (especialmente na de intrusión). 

O recoñecemento activo lévanos a obter información grazas á interación directa con sistemas e persoas. Este tipo de recoñecemento é valioso, pero tamén arriscado ao ser posible de detectar polo obxectivo. Por esa razón, o **recoñecemento pasivo** é unha tarea crucial. En moitas ocasións, será suficiente para continuar coas seguintes tarefas.

A intelixencia de fontes abertas (OSINT), xornais dixitais, notas de prensa, redes sociais e outros medios poden proporcionar unha información base, pero en moitas ocasións, o recoñecemento por DNS dun servizo exposto na Internet pode amosar resultados interesantes como adversario. Este tipo de recoñecemento, a pesares de requerir acción do atacante, pode considerarse pasivo, pois os servizos de DNS considéranse información pública e nunca se tería que interactuar directamente co obxectivo. 

### WHOIS

`whois <DOMINIO_OBXECTIVO>`

Amosa información relativa ao rexistro da entrada DNS. Entre outras: data de rexistro, última actualización, identidade do rexistrante, enderezos electrónicos ou teléfonos de contacto, xeolocalización... Moitos WHOIS están limitados, pero paga a pena ver qué información se atopa dispoñible. 

### NSLOOKUP

`nslookup <DOMINIO_OBXECTIVO>`

Ferramenta que amosa información relativa aos rexistros DNS dispoñibles nos NS (Servidor de Nomes). Normalmente, recupera información referente a qué IPs se atopan baixo ese dominio, e de que tipo é a entrada. 

- **A**:	Enderezo IPv4
- **AAAA**: Enderezo IPv6
- **CNAME**:	Nome canónico
- **MX**:	Servidor de correo
- **SOA**:	Principio de Autoridade (Start of Authority)
- **TXT**:	Texto

Podemos usar `nslookup -type=<TIPO> <DOMINIO_OBXECTIVO>` para amosar os datos referentes a un tipo específico de entrada. Importante: ás veces, un `nslookup` sen especificar a bandeira de tipo non amosa tódalas entradas. Na fase de enumeración, utlilizar a bandeira -type para verificar a existencia de tipos de rexistro. 

### DIG

`dig <DOMINIO_OBXECTIVO>`

Ferramenta similar a `nslookup`, con opcións máis avanzadas e información máis completa cando se fai uso das súas funcionalidades. Podemos especificar o servidor DNS ao que facer a consulta, xunto co dominio e o tipo de rexistros. Exemplo de uso para o DNS 1.1.1.1 (CloudFlare), dominio example.com e entradas de correo.
`dig @1.1.1.1 example.com MX`

### DNSDumpster.com

A web [DNSDumpster](https://dnsdumpster.com) permite opcións avanzadas de recoñecemento por DNS, como por exemplo o descubrimento de subdominios. Por exemplo, o dominio example.com podería ter subdominios coma blog.example.com, site.example.com, ou web.example.com. Tamén ten a opción de proxectar un grafo de relacións entre subdominios. 

### Shodan.io

Coa información recollida das anteriores ferramentas, poderiamos comprobar enderezos IP, servizos expostos e máis información no [Shodan](https://shodan.io). Ainda que funciona mellor cunha conta Premium, moita información está dispoñible de forma gratuíta. 
