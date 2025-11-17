# Recomendador de Campeões de League of Legends — Similaridade do Cosseno

![[Dentre os 167 campeões qual escolher.png]]

Projeto de análise de dados que utiliza **Similaridade do Cosseno** para recomendar campeões semelhantes no _League of Legends_.  
A proposta é transformar atributos do jogo como **rotas¹**, **tipo de recurso²**, entre outros, em vetores e calcular quais campeões possuem o perfil mais próximo do escolhido pelo usuário.

---

## Objetivo do Projeto

O objetivo é auxiliar novos jogadores a encontrarem campeões com estilos de jogo parecidos com aqueles que já experimentaram e aprovaram, ajudando na construção de uma **pool³** consistente.

O usuário final é qualquer pessoa que gostou da gameplay de um campeão e deseja descobrir alternativas similares para treinar e expandir seu repertório dentro do jogo.

---

## Base de Dados

Os dados utilizados foram obtidos no Kaggle, através do dataset:  
**“League of Legends Champions”**

link: "[https://www.kaggle.com/datasets/cutedango/league-of-legends-champions](https://www.kaggle.com/datasets/cutedango/league-of-legends-champions)"

Durante a análise inicial, foram identificadas e tratadas algumas inconsistências, como:

- valores nulos na coluna de tipo de recurso²;
    
- campos contendo mais de um valor.
    

Após os ajustes, foi possível obter um dataset estável para desenvolvimento do projeto.

---

## Preparação dos Dados

Para aplicar a Similaridade do Cosseno, foi necessário identificar quais variáveis realmente impactariam a similaridade entre campeões.  
As variáveis mais relevantes para esta etapa foram:

- **Rotas¹**
    
- **Tipo de recurso²**
    

A partir disso, foi construída uma tabela binária utilizando `pd.get_dummies()`, onde cada atributo é representado por:

- **0** = o campeão não possui o atributo
    
- **1** = o campeão possui o atributo
    

Esse processo resultou em um vetor representando cada campeão de maneira estruturada.

Exemplo da tabela transformada:  
![[Pasted image 20251117152657.png]]

---

## Cálculo de Similaridade

Com os vetores preparados, foi implementado o cálculo de Similaridade do Cosseno utilizando **scikit-learn** com a função `cosine_similarity()`.  
A função desenvolvida permite que o usuário digite o nome de um campeão e receba:

- a lista de campeões mais similares;
    
- os valores de similaridade;
    
- os atributos binários responsáveis pela proximidade.
    

Exemplo da saída do sistema:  
![[Pasted image 20251117153456.png]]

---

## Próximos Passos

Algumas evoluções planejadas para as próximas versões do projeto incluem:

- **Adicionar novas variáveis**, como dificuldade do campeão e tipo de dano;
    
- **Criar uma interface visual**, tornando o sistema mais acessível ao público geral;
    
- **Aplicar técnicas de clusterização** (ex.: K-Means) para agrupar campeões por estilo de jogo;

---

## Dicionário de Termos

**1. Rotas (lanes)** — Posições do mapa onde cada campeão costuma jogar. Ex.: Top, Mid, Jungle, ADC, Suporte.

**2. Tipo de recurso** — Mecânica usada para lançar habilidades. Ex.: Mana, Energia, Ferocidade, Sem recurso.

**3. Pool (champion pool)** — Conjunto de campeões que um jogador domina ou joga com frequência.

**4. Dataset** — Conjunto de dados utilizado para análise.

**5. Feature** — Atributo usado para representar um objeto em análise.

**6. Vetor** — Representação numérica dos atributos de um campeão.

**7. Similaridade do Cosseno** — Métrica que mede o quão parecidos dois vetores são.

**8. One-hot encoding** — Processo que transforma categorias em colunas binárias.

**9. Kaggle** — Plataforma de datasets para projetos de dados.

**10. `pd.get_dummies()`** — Função do Pandas que aplica one-hot encoding.

**11. `cosine_similarity()`** — Função do scikit-learn que calcula a similaridade cosseno.

---

Readme/PDF feito e salvo no software Obsidian.

**Criador:** _Matheus José Pereira de Souza — Main Qiyana e Ekko, Estudante do 2° semestre de Ciências da Computação._  
_Projeto desenvolvido como parte da **Trilha de Análise de Dados em Python** (aulas aos sábados)._