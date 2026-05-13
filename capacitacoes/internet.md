---
layout: training
title: Internet
permalink: /capacitacoes/internet/
---
# Internet — Fundamentos Teóricos

> Material de apoio para aula. Cobre os conceitos essenciais da teoria por trás da Internet.

---

## 1. O que é a Internet?

A **Internet** é uma rede global de computadores interconectados que se comunicam por meio de um conjunto padronizado de protocolos. Ela não é uma rede única, mas sim uma **"rede de redes"**: milhares de redes autônomas — de universidades, empresas, governos e provedores — interligadas de forma descentralizada.

**Diferença importante:**
- **Internet** → infraestrutura física e lógica de comunicação entre máquinas.
- **Web (World Wide Web)** → serviço que roda *sobre* a Internet, baseado em páginas e hiperlinks.

---

## 2. Breve Histórico

| Período | Marco |
|--------|-------|
| 1969 | ARPANET — primeira rede de pacotes, financiada pelo Departamento de Defesa dos EUA |
| 1974 | Publicação do protocolo TCP por Cerf e Kahn |
| 1983 | Adoção do TCP/IP como protocolo padrão da ARPANET |
| 1991 | Tim Berners-Lee inventa a World Wide Web no CERN |
| 1993 | Mosaic — primeiro navegador gráfico popular |
| 1998 | Fundação da ICANN para gestão de domínios e IPs |
| 2000s | Expansão da banda larga e Internet móvel |
| 2010s | Cloud Computing, IoT e redes sociais como infraestrutura central |

---

## 3. Comutação de Pacotes

A Internet opera com **comutação de pacotes**, em oposição à comutação de circuitos (usada na telefonia tradicional).

### Como funciona
1. A mensagem é dividida em pequenos blocos chamados **pacotes**.
2. Cada pacote carrega o endereço de destino no seu cabeçalho.
3. Os pacotes trafegam de forma **independente** pela rede, podendo seguir rotas diferentes.
4. No destino, os pacotes são **reordenados e remontados**.

### Vantagens
- Uso eficiente da banda disponível.
- Tolerância a falhas: se um roteador cai, os pacotes são redirecionados.
- Compartilhamento do meio físico por múltiplos usuários simultaneamente.

---

## 4. Modelos de Referência

### 4.1 Modelo OSI (7 camadas)

| Camada | Nome | Função |
|--------|------|--------|
| 7 | Aplicação | Interface com o usuário (HTTP, FTP, DNS) |
| 6 | Apresentação | Codificação, criptografia, compressão |
| 5 | Sessão | Controle de sessões e diálogos |
| 4 | Transporte | Entrega confiável ponta a ponta (TCP/UDP) |
| 3 | Rede | Endereçamento e roteamento (IP) |
| 2 | Enlace | Transmissão entre nós adjacentes (Ethernet, Wi-Fi) |
| 1 | Física | Bits no meio físico (cabos, ondas de rádio) |

### 4.2 Modelo TCP/IP (4 camadas)

| Camada TCP/IP | Equivalente OSI |
|--------------|----------------|
| Aplicação | 5, 6, 7 |
| Transporte | 4 |
| Internet | 3 |
| Acesso à rede | 1, 2 |

> Na prática, a Internet é implementada seguindo o modelo TCP/IP. O OSI é usado como **referência conceitual**.

---

## 5. Protocolos Fundamentais

### 5.1 IP — Internet Protocol

- Responsável pelo **endereçamento** e **roteamento** dos pacotes.
- É um protocolo **não confiável** e **sem conexão**: não garante entrega, ordem ou integridade.

**IPv4:** endereços de 32 bits → ~4,3 bilhões de endereços (ex.: `192.168.0.1`)  
**IPv6:** endereços de 128 bits → 3,4 × 10³⁸ endereços (ex.: `2001:0db8::1`)

### 5.2 TCP — Transmission Control Protocol

- Protocolo **orientado a conexão** e **confiável**.
- Garante entrega, ordem dos pacotes e controle de fluxo.
- Usa o **three-way handshake** para estabelecer conexão:
  1. `SYN` (cliente → servidor)
  2. `SYN-ACK` (servidor → cliente)
  3. `ACK` (cliente → servidor)

### 5.3 UDP — User Datagram Protocol

- Protocolo **sem conexão** e **não confiável**.
- Menor overhead, maior velocidade.
- Usado em streaming de vídeo, jogos online, VoIP e DNS.

### 5.4 HTTP / HTTPS

- **HTTP** (HyperText Transfer Protocol): protocolo da camada de aplicação para transferência de páginas web.
- **HTTPS**: versão segura com camada **TLS/SSL** para criptografia.
- Modelo **requisição/resposta**: cliente envia requisição, servidor responde.

**Métodos HTTP principais:**
- `GET` → solicitar recurso
- `POST` → enviar dados
- `PUT` / `PATCH` → atualizar recurso
- `DELETE` → remover recurso

**Evolução:**
- HTTP/1.1 → uma requisição por conexão
- HTTP/2 → multiplexação de requisições
- HTTP/3 → baseado em QUIC (UDP), menor latência

### 5.5 DNS — Domain Name System

- Sistema que traduz **nomes de domínio** (ex.: `google.com`) em **endereços IP**.
- Funciona como uma **"agenda telefônica"** distribuída e hierárquica.

**Hierarquia DNS:**
```
. (raiz)
└── .com / .br / .org (TLD — Top Level Domain)
    └── google.com / ufrn.br
        └── www.google.com / mail.google.com (subdomínios)
```

**Resolução de um domínio (passo a passo):**
1. Usuário digita `www.exemplo.com`
2. Navegador consulta o cache local
3. Consulta o **servidor DNS recursivo** do provedor
4. Esse servidor consulta os servidores **raiz**, depois o servidor **TLD**, depois o servidor **autoritativo**
5. Retorna o endereço IP ao cliente

---

## 6. Endereçamento IP e Sub-redes

### IPv4 — Classes e CIDR

Endereços privados (não roteáveis na Internet pública):
- `10.0.0.0/8`
- `172.16.0.0/12`
- `192.168.0.0/16`

**CIDR (Classless Inter-Domain Routing):** notação que define quantos bits pertencem à rede.  
Exemplo: `192.168.1.0/24` → 256 endereços, 254 utilizáveis para hosts.

### NAT — Network Address Translation
- Permite que múltiplos dispositivos compartilhem **um único IP público**.
- O roteador mapeia IPs privados para o IP público, mantendo uma tabela de tradução.

---

## 7. Roteamento

**Roteadores** são dispositivos responsáveis por encaminhar pacotes entre redes diferentes, baseando-se em **tabelas de roteamento**.

### Tipos de roteamento

| Tipo | Descrição |
|------|-----------|
| Estático | Rotas configuradas manualmente pelo administrador |
| Dinâmico | Rotas aprendidas automaticamente via protocolos |

### Protocolos de roteamento dinâmico
- **RIP** (Routing Information Protocol) — baseado em distância (saltos)
- **OSPF** (Open Shortest Path First) — baseado em estado de enlace
- **BGP** (Border Gateway Protocol) — protocolo da Internet pública entre ASes (Sistemas Autônomos)

> O **BGP** é o "protocolo que mantém a Internet unida", controlando como o tráfego é encaminhado entre os grandes provedores globais.

---

## 8. Infraestrutura Física

### Meios de transmissão
- **Par trançado (cabo UTP/STP):** redes locais (LAN), Ethernet
- **Cabo coaxial:** TV a cabo, algumas redes legadas
- **Fibra óptica:** backbone da Internet, alta velocidade, baixa latência
- **Wi-Fi (802.11):** transmissão sem fio por ondas de rádio
- **Satélite:** cobertura em áreas remotas (ex.: Starlink)

### Camadas da infraestrutura global
1. **Backbone** — cabos de fibra óptica submarinos e terrestres que interligam continentes
2. **ISPs (Provedores de Internet)** — Tier 1 (globais), Tier 2 (regionais), Tier 3 (locais)
3. **IXP (Internet Exchange Points)** — pontos físicos onde ISPs trocam tráfego diretamente
4. **Última milha** — conexão até o usuário final (fibra, cabo, DSL, 4G/5G)

---

## 9. Segurança na Internet

### Principais ameaças
- **Phishing:** engenharia social para roubar credenciais
- **Malware:** vírus, ransomware, spyware
- **DDoS:** sobrecarga de servidores com tráfego falso
- **Man-in-the-Middle (MitM):** interceptação de comunicações
- **SQL Injection / XSS:** ataques a aplicações web

### Mecanismos de proteção
- **TLS/SSL:** criptografia das comunicações (HTTPS)
- **Firewall:** filtragem de tráfego por regras
- **VPN:** túnel criptografado entre cliente e servidor
- **Certificados digitais e PKI:** autenticação de identidade na web
- **2FA:** autenticação em dois fatores

---

## 10. Web — Camada de Aplicação

### Componentes da Web
- **URL** (Uniform Resource Locator): endereço de um recurso na web
  - Estrutura: `protocolo://domínio:porta/caminho?parâmetros`
- **HTML:** linguagem de marcação para estrutura das páginas
- **CSS:** estilização visual
- **JavaScript:** comportamento e interatividade
- **Servidor Web:** processa requisições HTTP (ex.: Apache, Nginx)

### Arquiteturas
- **Cliente-Servidor:** modelo clássico da web
- **APIs REST:** comunicação entre sistemas via HTTP
- **WebSockets:** comunicação bidirecional e em tempo real
- **CDN (Content Delivery Network):** distribuição de conteúdo em servidores geograficamente próximos ao usuário

---

## 11. Cloud Computing e Internet Moderna

A nuvem é a extensão natural da Internet, onde recursos computacionais (servidores, armazenamento, bancos de dados) são disponibilizados como serviço.

| Modelo | Descrição | Exemplos |
|--------|-----------|---------|
| IaaS | Infraestrutura como serviço | AWS EC2, Azure VMs |
| PaaS | Plataforma como serviço | Heroku, Google App Engine |
| SaaS | Software como serviço | Gmail, Google Docs, Notion |

### Tendências atuais
- **IoT (Internet of Things):** bilhões de dispositivos conectados
- **Edge Computing:** processamento próximo à fonte de dados, reduzindo latência
- **5G:** nova geração de redes móveis com altíssima velocidade e baixíssima latência
- **IPv6:** adoção crescente para suportar o número de dispositivos

---

## 12. Governança da Internet

A Internet não tem um único dono, mas há organismos de coordenação:

| Organização | Função |
|-------------|--------|
| **IETF** | Define os padrões técnicos (RFCs) |
| **ICANN** | Gerencia domínios e endereços IP globalmente |
| **W3C** | Define padrões da Web (HTML, CSS) |
| **NIC.br / CGI.br** | Governança da Internet no Brasil |
| **IANA** | Alocação de endereços IP e números de protocolos |

---

## 13. Resumo Conceitual

```
Usuário
  │
  ▼
Dispositivo (IP privado via NAT)
  │
  ▼
Roteador doméstico
  │
  ▼
ISP (provedor local — Tier 3)
  │
  ▼
ISP regional (Tier 2) → IXP
  │
  ▼
Backbone global (Tier 1 / Fibra submarina)
  │
  ▼
Servidor de destino (data center / cloud)
```

---

## 14. Conceitos-chave para Revisão

- [ ] O que diferencia Internet de Web?
- [ ] Por que a comutação de pacotes é superior à comutação de circuitos para dados?
- [ ] Qual a diferença entre TCP e UDP? Quando usar cada um?
- [ ] Como funciona a resolução DNS passo a passo?
- [ ] O que é NAT e por que ele existe?
- [ ] Qual a função do BGP na Internet pública?
- [ ] O que garante a segurança em uma conexão HTTPS?
- [ ] Quais são os três modelos de cloud computing?

---

> **Referências recomendadas**
> - Tanenbaum, A. S. — *Redes de Computadores* (5ª ed.)
> - Kurose & Ross — *Redes de Computadores e a Internet: Uma Abordagem Top-Down*
> - RFC 791 (IP), RFC 793 (TCP), RFC 1034/1035 (DNS)
> - [How the Internet Works — Stanford CS](https://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm)
