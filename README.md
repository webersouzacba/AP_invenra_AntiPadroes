# Activity Provider – Inven!RA  
## Jogo Sopa de Letras — Antipadrões e Refatoração (Atividade 7)

**UC:** Arquitetura e Padrões de Software (APSI) – MEIW – UAb/UTAD  
**Ano letivo:** 2025/2026  
**Autor:** Weber Marcelo Guirra de Souza  

---

## Enquadramento

Este repositório contém a **versão refatorada** do *Activity Provider* **Sopa de Letras**, desenvolvida no âmbito da **Atividade 7 – Antipadrões e Refatoração** da UC **Arquitetura e Padrões de Software (APSI)**.

O projeto parte da implementação existente das atividades anteriores e realiza uma **refatoração incremental**, orientada pelas decisões registadas no relatório da atividade, com os seguintes objetivos:

- Identificar antipadrões presentes na versão anterior  
- Aplicar refatorações localizadas e justificadas  
- Preservar integralmente o comportamento observável do sistema  
- Manter compatibilidade com o contrato da plataforma **Inven!RA**  

---

## Antipadrões tratados (síntese)

Na versão anterior foram identificados e tratados os seguintes antipadrões:

### Minefield
Responsabilidades implícitas e dispersas relacionadas com o acesso a eventos persistidos.  
**Refatoração:** consolidação explícita dessa responsabilidade no `PersistenceProxy`, reduzindo dependências implícitas.

### Lava Flow / Boat Anchor
Módulos e código legado não utilizados, mantidos sem impacto funcional.  
**Refatoração:** remoção de módulos não utilizados, simplificando a base de código sem alterar o comportamento.

---

## 🌐 Serviço em Produção (VPS)

**Base URL:** http://69.6.220.255:9012/

---

## 🗂️ Repositório GitHub

- **main** – estado pré-refatoração (`v6-baseline`)  
- **refactor/atividade7** – versão final refatorada  

https://github.com/webersouzacba/AP_invenra_AntiPadroes/

