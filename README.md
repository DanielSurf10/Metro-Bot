# 🚇 MetrôBot SP — Assistente de Navegação do Metrô de São Paulo

O **MetrôBot SP** é um assistente inteligente desenvolvido para auxiliar passageiros no planejamento de rotas pela malha do Metrô de São Paulo (cobrindo a Linha 1-Azul e a Linha 2-Verde). O projeto integra algoritmos clássicos de busca em grafos, motor de inferência em lógica proposicional e de primeira ordem (para tratamento de regras de acessibilidade, bloqueios e pontos de interesse) e modelos de linguagem (LLMs) para interpretação de pedidos e geração de explicações em linguagem natural.

> **Regra de Ouro:** *O LLM conversa, o algoritmo decide.*

---

## 👥 Autores

* **Daniel Barbosa Alves** — RA: 1845274
* **Allan Reis da Conceição** — RA: 153960
* **Giovana Alves Duarte de Sena** — RA: 2594141
* **Gabriel Noriler Souza** — RA: 1642714

---

## ⚙️ Pré-requisitos e Modos de IA

O sistema possui suporte para execução via nuvem, local ou modo de segurança offline:

1. **IA na Nuvem (Groq API):**
   * Para utilizar os modelos na nuvem via Groq, é **obrigatório gerar uma API Key** no painel da [Groq](https://console.groq.com/).
   * A chave pode ser disponibilizada via variáveis de ambiente, arquivo `.env` (`GROQ_API_KEY=...`) ou pelo recurso de Secrets do Google Colab.

2. **IA Local (Ollama):**
   * Se optar por não utilizar a API na nuvem, o sistema utilizará a IA localmente via **Ollama**, utilizando por padrão o modelo `qwen2.5:3b`.
   * **Requisito de Hardware:** Para a execução local do modelo, é necessária uma placa de vídeo (GPU dedicada) com pelo menos **4 GB de VRAM**.

3. **Modo Offline (Fallback):**
   * Caso não haja conexão com a nuvem ou suporte a GPU local, o sistema ativa um modo offline baseado em expressões regulares e templates estruturados, garantindo o funcionamento contínuo do planejador.

---

## 📦 Dependências do Projeto

As dependências de software do projeto incluem:

* **Python 3.x**
* **Bibliotecas Python:** `groq`, `ollama`, `ipywidgets`, `python-dotenv`
* **Utilitários do sistema (para execução no Colab/Linux):** `zstd`, `lspci`, `lshw`, `ollama`

---

## 🚀 Como Executar

### Método 1: Google Colab (Recomendado)

1. Faça o upload do arquivo do notebook (`.ipynb`) no [Google Colab](https://colab.research.google.com/).
2. Se deseja utilizar a IA via nuvem, adicione sua chave `GROQ_API_KEY` nos **Secrets** (ícone de chave no menu lateral) e conceda acesso ao notebook.
3. Execute todas as células em sequência.
4. Na última célula, o painel interativo renderizado via `ipywidgets` estará disponível para interações em tempo real.

### Método 2: Ambiente Local (Jupyter / VS Code)

1. Clone o repositório ou baixe o código-fonte.
2. Execute os seguintes comandos:
   ```bash
   pip install -q groq ollama ipywidgets python-dotenv
   apt-get install -y zstd
   apt-get install -y lspci
   apt-get install -y lshw
   curl -fsSL https://ollama.com/install.sh | sh
   (ollama serve &) &
   ollama pull qwen2.5:3b
   ```
3. Crie um arquivo .env contendo:
    ```
    GROQ_API_KEY=sua_chave_aqui
    ```
4. Rode o script com:
   ```
   python aula_pratica01_metrobot.py
   ```
