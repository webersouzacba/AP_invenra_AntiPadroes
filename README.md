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

- **Minefield**  
  Responsabilidades implícitas e dispersas relacionadas com o acesso a eventos persistidos.

- **Lava Flow / Boat Anchor**  
  Módulos e código legado não utilizados, mantidos sem impacto funcional.

As refatorações aplicadas encontram-se documentadas no relatório da atividade e refletem-se diretamente na organização atual do código.

---

## Tecnologias Utilizadas

- Python 3.9+
- FastAPI
- Uvicorn (ASGI)
- Persistência simples em ficheiros JSON (mock)
- HTML/JavaScript para páginas de teste manuais

---

## 🌐 Serviço em Produção (VPS)

A versão final refatorada encontra-se publicada numa VPS Linux (AlmaLinux), com execução persistente via **systemd**.

### Base URL

http://69.6.220.255:9012/

yaml
Copiar código

---

## 📡 Integração com a plataforma Inven!RA

### JSON de registo do Activity Provider

```json
{
  "name": "Sopa de Letras – APSI (Antipadrões e Refatoração)",
  "config_url": "http://69.6.220.255:9012/config",
  "json_params_url": "http://69.6.220.255:9012/params",
  "user_url": "http://69.6.220.255:9012/deploy",
  "analytics_url": "http://69.6.220.255:9012/analytics",
  "analytics_list_url": "http://69.6.220.255:9012/analytics/available"
}
Página de teste (POST /analytics)
arduino
Copiar código
http://69.6.220.255:9012/static/teste_analytics_POST.html
🔌 Endpoints Principais
/config — Página de configuração da atividade

/params — Lista de parâmetros configuráveis

/deploy?activityID=XXXX — Instanciação da atividade

/game/{activityID} — Interface do jogo

/analytics — Receção de dados analíticos

/analytics/available — Lista de métricas disponíveis

📘 Documentação automática (Swagger)
arduino
Copiar código
http://69.6.220.255:9012/docs
🗂️ Repositório GitHub
O projeto encontra-se versionado no GitHub, com organização explícita por branches para evidenciar o processo de refatoração:

main
Estado pré-refatoração (baseline da atividade anterior), marcado pela tag v6-baseline.

refactor/atividade7
Versão refatorada, correspondente à Atividade 7 (antipadrões e refatoração).

Repositório:

ruby
Copiar código
https://github.com/webersouzacba/AP_invenra_AntiPadroes/
Esta estrutura garante rastreabilidade entre o estado inicial e o resultado final da refatoração.

📁 Estrutura Atual do Projeto
csharp
Copiar código
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
▶️ Execução Local
bash
Copiar código
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 9012 --reload
Aceder a:

http://127.0.0.1:9012/config

http://127.0.0.1:9012/docs

⚙️ Execução na VPS (systemd)
Serviço configurado em:

swift
Copiar código
/etc/systemd/system/ap-sopadeletras.service
Comandos principais:

bash
Copiar código
systemctl enable --now ap-sopadeletras
systemctl status ap-sopadeletras --no-pager
