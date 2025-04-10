# 📊 Coleta de Dados via API da Riot Games – Passo a Passo

Este projeto teve como objetivo a coleta e organização de dados de partidas ranqueadas de jogadores do servidor **coreano** de *League of Legends*, utilizando a **API pública da Riot Games**.

---

## 1. 📦 Importação das Bibliotecas

As seguintes bibliotecas foram utilizadas:

- `pandas`: manipulação de dados tabulares;
- `requests`: envio de requisições HTTP para a API da Riot.

---

## 2. 🔑 Definição da Chave de API

A chave de autenticação `api_key` foi definida, sendo fornecida pela Riot após registro no portal de desenvolvedores. Ela é obrigatória para autorizar o acesso à API.

---

## 3. 🎯 Coleta dos Jogadores do Elo Challenger

Foi feita uma requisição ao endpoint que retorna a lista de jogadores **Challenger** da fila ranqueada solo 5v5 no servidor da **Coreia**.

---

## 4. 🏆 Seleção dos 50 Melhores Jogadores

A lista foi ordenada por **League Points (LP)**, selecionando os 50 jogadores com maior pontuação.

---

## 5. 🧩 Recuperação dos PUUIDs

A partir dos nomes dos jogadores (summoner names), foram feitas requisições para obter os **PUUIDs**, identificadores únicos de cada jogador, via endpoint `summoner-v4`.

---

## 6. 🗂️ Coleta dos IDs das Partidas

Para cada PUUID, foram obtidos os **10 IDs das partidas mais recentes** usando o endpoint `match-v5`.

---

## 7. 🧹 Remoção de Duplicatas

Partidas duplicadas (casos em que dois jogadores selecionados jogaram a mesma partida) foram removidas para manter apenas IDs únicos.

---

## 8. 📄 Coleta dos Detalhes das Partidas

Com os match IDs únicos, foram feitas requisições para obter os **detalhes completos** de cada partida, incluindo estatísticas individuais e coletivas.

---

## 9. 🧮 Estruturação dos Dados

Para cada uma das partidas, foram extraídas as seguintes informações dos 10 jogadores:

- Campeão escolhido;
- Kills, deaths e assists;
- Dano causado, ouro acumulado, farm (CS);
- Resultado da partida (vitória ou derrota).

Esses dados foram organizados em um `DataFrame` com `pandas`.

---

## 10. 💾 Exportação dos Dados

Por fim, os dados foram salvos em um arquivo `.csv` para análises posteriores e/ou modelagem preditiva.

---

## 📂 Código Comentado

O código completo que implementa essas etapas está disponível no notebook:

📎 `Dados_viaAPI_RIOT_comentado.ipynb`
