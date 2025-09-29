📊 Documentação do Processo de ETL e Modelagem

Este documento descreve as etapas realizadas no processo de limpeza, transformação e modelagem de dados, utilizando **Power Query** e **Power BI**.

---

## ✅ 1. Verificação de Cabeçalhos e Tipos de Dados
Todos os cabeçalhos foram validados e os tipos de dados ajustados conforme a natureza de cada coluna, garantindo consistência para as etapas seguintes do processo.

---

## 💰 2. Ajuste de Valores Monetários
Os campos monetários foram convertidos para o tipo **Decimal (double preciso)**, garantindo maior acurácia nos cálculos e análises financeiras.

---

## 🔍 3. Análise de Valores Nulos
Avaliadas as colunas com valores nulos.  
Não houve necessidade de remoção, pois os nulos são esperados no contexto do negócio.

---

## 👔 4. Verificação de Colaboradores sem Gerente
Identificados:
- **3 colaboradores com papel de Gerente**  
- **1 Presidente** (sem `Super_ssn`, como esperado na hierarquia organizacional)

---

## 🏢 5. Verificação de Departamentos sem Gerente
Foi identificado que o departamento **Headquarters** não possui gerente definido no conjunto de dados.

---

## 👤 6. Tratamento de Departamentos sem Gerente
Embora não exista um gerente formalmente associado ao departamento **Headquarters**, foi assumido que o **Presidente** desempenha esse papel para fins de consistência do modelo.

---

## ⏳ 7. Análise das Horas por Projeto
A análise do número de horas alocadas aos projetos foi realizada utilizando **tabela e gráfico no Power BI**, permitindo visualizar rapidamente a distribuição de horas por projeto.

---

## 🏠 8. Separação de Colunas Complexas
A coluna de endereço dos colaboradores foi desmembrada em:
- Rua  
- Número  
- Estado  

Facilitando a limpeza e futuras análises geográficas.

---

## 🔗 9. Mesclagem de *Employee* e *Department*
Realizada a mesclagem na tabela **employee** utilizando o campo chave de relacionamento com **department**, garantindo a associação correta do nome do departamento a cada colaborador.  
A mescla foi feita como **Left Join**, preservando todos os registros de colaboradores.

---

## 🗑️ 10. Eliminação de Colunas Desnecessárias
Foram removidas as colunas irrelevantes para a análise, reduzindo o tamanho do modelo e otimizando a performance.

---

## 👥 11. Junção de Colaboradores com Gerentes
A junção foi feita no **Power Query**, criando uma **tabela dimensão de Gerente** e estabelecendo o relacionamento com a tabela **employee**, de modo a possibilitar análises hierárquicas entre gerente e colaborador.

---

## 🪪 12. Mescla de Nome e Sobrenome
Foi criada, no **Power Query**, uma **coluna personalizada** que concatena Nome e Sobrenome, resultando em um único campo **Nome Completo do Colaborador**.

---

## 🌎 13. Mescla de Nomes de Departamentos e Localizações
Na tabela **department**, foi criada uma coluna que combina **Nome do Departamento e Localização**, tornando cada par **Departamento-Local** único, conforme a necessidade para o modelo estrela.

---

## ⚙️ 14. Justificativa para Uso de Mesclar em vez de Atribuir
A operação **Atribuir (Append)** é adequada para **empilhar linhas de tabelas com a mesma estrutura**.  
Neste caso, foi necessário **Mesclar (Merge)**, pois a tarefa exigia **combinar informações complementares de tabelas distintas usando chaves de relacionamento**, enriquecendo cada linha da tabela base.

---

## 📈 16. Agrupamento de Colaboradores por Gerente
Criada uma **agregação no Power Query**, agrupando os colaboradores por gerente e gerando a contagem de subordinados de cada um.

---

## 🧹 17. Eliminação de Colunas e Tabelas Desnecessárias
Foi utilizado o **Measure Killer** para identificar e remover colunas e tabelas não utilizadas, evitando a exclusão de dependências ativas.  
Antes da exclusão, foi exportado um **arquivo TMDL** com o inventário do modelo, garantindo rastreabilidade e segurança nas futuras manutenções.

---
