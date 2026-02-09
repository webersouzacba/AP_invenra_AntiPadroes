# Activity Provider – Inven!RA  
## Jogo Sopa de Letras — Antipadrões e Refatoração (Atividade 7)

### UC: Arquitetura e Padrões de Software (APSI) – MEIW – UAb/UTAD  
### Ano letivo 2025/2026  
### Autor/Aluno: Weber Marcelo Guirra de Souza  

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

Na versão anterior foram identificados e tratados:

- **Minefield**: responsabilidades implícitas e dispersas relacionadas com acesso a eventos persistidos  
- **Lava Flow / Boat Anchor**: módulos e código legado não utilizados, mantidos sem impacto funcional  

As refatorações aplicadas encontram-se documentadas no relatório da atividade e refletem-se diretamente na organização atual do código.

---

## Tecnologias Utilizadas

- Python 3.9+
- FastAPI
- Uvicorn (ASGI)
- Persistência simples em ficheiros JSON (mock)
- HTML/JS para páginas de teste manuais

---

## 🌐 Serviço em Produção (VPS)

A versão final refatorada encontra-se publicada numa VPS Linux (AlmaLinux), com execução persistente via **systemd**.

### Base URL

http://69.6.220.255:9012/

## 📡 Integração com a plataforma Inven!RA

JSON de registo do Activity Provider:

```json
{
  "name": "Sopa de Letras – APSI (Antipadrões e Refatoração)",
  "config_url": "http://69.6.220.255:9012/config",
  "json_params_url": "http://69.6.220.255:9012/params",
  "user_url": "http://69.6.220.255:9012/deploy",
  "analytics_url": "http://69.6.220.255:9012/analytics",
  "analytics_list_url": "http://69.6.220.255:9012/analytics/available"
}

Página de teste para o serviço POST / analytics disponível em:

http://69.6.220.255:9012/static/teste_analytics_POST.html

Repositório GitHub

O projeto encontra-se versionado no GitHub, com organização explícita por branches para evidenciar o processo de refatoração:

https://github.com/webersouzacba/AP_invenra_AntiPadroes/

main — estado pré-refatoração (baseline da atividade anterior), marcado pela tag v6-baseline.

refactor/atividade7 — versão refatorada, correspondente à Atividade 7 (antipadrões e refatoração).

Esta estrutura garante rastreabilidade entre o estado inicial e o resultado final da refatoração.


Estrutura ataul do Projeto:

AP_invenra_AntiPadroes/
│
├── main.py                     # App FastAPI (ponto de entrada)
├── requirements.txt
├── README.md
├── .gitignore
│
├── static/
│   ├── index.html
│   ├── teste_deploy_GET.html
│   └── teste_analytics_POST.html
│
└── ap/
    ├── facade.py               # Facade – coordenação dos casos de uso
    ├── persistence_proxy.py    # Proxy – acesso à persistência
    ├── store_json.py           # Persistência em JSON (mock)
    ├── builder.py              # Builder (apoio)
    ├── instance_manager.py     # Singleton (apoio)
    └── models.py               # DTOs e validação (Pydantic)

