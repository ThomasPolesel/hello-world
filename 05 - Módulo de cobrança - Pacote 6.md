![](Aspose.Words.faf9efb4-d25a-4beb-96f9-53cbf9c68af1.001.png)
















||
| - |
|**EACetesb\_Padrão**|
|**Especificação de Caso de Uso**|
||









**Índice**


05 - Módulo de cobrança - Pacote 6	3**

**05.01 Manter Cálculo e Descontos	3**















**05 - Módulo de cobrança - Pacote 6**

**Diagrama de Casos de Uso: 05 - Módulo de Cobrança - Pacote 6**

![](Aspose.Words.faf9efb4-d25a-4beb-96f9-53cbf9c68af1.002.png)** 

**05.01 Manter Cálculo e Descontos**

**Descrição**: O objetivo do caso de uso é permitir a criação, visualização e atualização do valor da cobrança sobre a solicitação e também os descontos e condições de isenção do pagamento no sistema. Além de manter o valor da UFESP que auxiliará nos cálculos dos boletos.

@Regra001 - Dados de Consulta/Alteração/Cadastro

Objeto(obrigatório e do tipo autocomplete)

@Regra002 - O sistema permite que a cobrança sobre o objeto na solicitação seja feita, obrigatoriamente, por uma única opção:

Preço fixo(não obrigatório e tipo seleção)

Preço por finalidade(não obrigatório e tipo seleção)

Preço por tipologia(não obrigatório e tipo seleção)

Preço condicional(não obrigatório e tipo seleção)

Preço por tipo de Imóvel (não obrigatório e tipo seleção)

@Regra003 - Dados de Alteração/Cadastro terão os seguintes campos:

Preço da Solicitação[valor em UFESP ou fórmula] (obrigatório e do tipo preenchimento)

Preço anterior da Solicitação (obrigatório e editável), apresenta, se houver, um valor anterior já cadastrado

Preço máximo para Solicitação[Qualquer valor maior que 0](não obrigatório e do tipo preenchimento)

Prazo de Vencimento[Qualquer valor maior que 0](obrigatório e do tipo preenchimento)

Prazo de Vigência Pagamento[Qualquer valor maior ou igual a 0](obrigatório e do tipo preenchimento)

@Regra004 - O sistema permite que o valor total da cobrança do objeto na solicitação, seja definido por um valor fixo ou por uma fórmula, com exceção do Preço Condicional que só será aceito o valor fixo por intervalo

@Regra005 - Para o tipo de cálculo por Tipologia, ao apresentar os registros já cadastrados na tabela de Tipologia [PRT047 - Fórmula por Tipologia.png](#BKM_736D6F57_8B8D_4D10_B200_B1DDBFFFACFA)  as linhas que já possuem descontos cadastrados devem aparecer em negrito.

@Regra006 - O sistema permite que a fórmula do preço da cobrança utilize cálculos com expressões matemáticas e a inclusão de variáveis conforme prótotipo [PRT051 - Modal Configurar Fórmulas.png](#BKM_0DCC8322_1B5F_463C_8C08_9E17AFAB6877)

@Regra007 - O sistema deve impedir que na construção da fórmula sejam inseridos operadores consecutivos e o mesmo vale para variáveis

@Regra008 - As variaveis apresentadas para construção das fórmulas são as mesmas utilizadas nos formulários dinâmicos no workflow da solicitação.

@Regra009 - O sistema permite que seja incluído uma ou mais finalidades(obrigatório e do tipo seleção autocomplete), quando escolhido o preço por finalidade. Somente as escolhidas serão apresentadas na solicitação, sendo obrigatório o valor específico de cada

@Regra010 - O sistema permite que somente as tipologias ativas sejam apresentadas(obrigatório e do tipo seleção autocomplete), quando escolhido o preço por tipologia, sendo obrigatório o cadastro do valor da cobrança individualmente em todas as tipologias existentes no sistema apresentando

os campos conforme @Regra003

@Regra011 - O sistema permite a cobrança por tipo de imóvel para as opções rural ou urbana, quando escolhido preço por tipo de imóvel, sendo obrigatório o valor específico de cada um

@Regra012 - O sistema permite que seja configuradas condições de cobrança utilizando operadores lógicos pré definidos pelo sistema afim de impedir erros de configurações por parte dos usuários, sendo assim os valores em UFESP que devem ser preenchidos são:

Variável (Obrigatório e do tipo seleção);

Valor Mínimo[Valor Maior que 0](obrigatório e do tipo preenchimento);

Valor Máximo[Valor Maior que 0](obrigatório e do tipo preenchimento);

Preço condicional 1 (obrigatório e do tipo preenchimento);

Preço condicional 2 (obrigatório e do tipo preenchimento);

Preço condicional 3 (obrigatório e do tipo preenchimento);

E o sistema irá gerar os seguintes ranges:

1. SE Váriavel <= {Valor Mínimo} ENTÃO Preço condicional 1
1. SE Variável > {Valor Mínimo} e Variável <= {Valor Máximo} ENTÃO Preço condicional 2
1. SE Variável > {Valor Máximo} ENTÃO Preço condicional 3

@Regra013 - O sistema não deve permitir que o valor de máximo seja menor ou igual que o valor de mínimo já inserido

@Regra014

Os campos Tipo do Imóvel; Finalidade; Tipologia são condicionais na tela de cópia e devem aparecer somente sobre os seguintes critérios:

- Objeto selecionado está cadastrado como "Preço por Tipo de Imóvel" - Apresenta o campo "Tipo de Imóvel
- Objeto selecionado está cadastrado como "Preço por Tipologia" - Apresenta o campo "Tipologia"
- Objeto selecionado está cadastrado como "Preço por Finalidade" - Apresenta o campo "Finalidade"

@Regra015 - O sistema permite o cadastro do número de dias do prazo de vencimento para pagamento de acordo com a necessidade de cada objeto

@Regar016 - O sistema permite o cadastro do número de dias do prazo de vigência para geração de um novo boleto, após o término do vencimento do boleto de acordo com a necessidade de cada objeto

@Regra017

Quando os campos Tipo do Imóvel; Finalidade e Tipologia forem apresentados na tela de cópia, devem apresentar uma lista de seleção apenas dos valores que apresentam algum valor ou fórmula configurada no objeto selecionado.

@Regra018 - O sistema deve permitir que o Preço da Solicitação juntamente com o Desconto e Isenção sejam copiados e utilizados em outro objeto, desde que os objetos tenham o mesmo modo de cálculo.

@Regra019 - O sistema deve permitir que seja configurado o desconto de 2 formas:

Um valor fixo[Valor Maior que 0](em UFESP) para a cobrança: este deve ser considerado o valor da cobrança

Um valor de porcentagem sobre o valor total do objeto: total - valor calculado do % de desconto [valor de 0 a 100%]

@Regra020 - O sistema permite a cobrança de desconto para os seguintes tipos de empresa: (Pelo menos um obrigatório e do tipo seleção)

ME

EPP

MEI

Associação/Cooperativa

Outros

@Regra021 - Quando selecionada a opção "Outros" será obrigatório selecionar também quais são as empresas que se enquadram como "Outros".

As opções de outros são:

- Administração pública direta, autarquias e fundações públicas da união, dos estados e dos municípios (não obrigatório e do tipo seleção)
- Entidades sem fins lucrativos(não obrigatório e do tipo seleção)
- Obras para proteção de recursos hídricos e para desocupação e recuperação de áreas degradadas e de áreas de risco(não obrigatório e do tipo seleção)
- Corte e queima de culturas agrícolas(não obrigatório e do tipo seleção)
- Construção, ampliação ou regularização de residência unifamiliar popular sem supressão de vegetação(não obrigatório e do tipo seleção)
- Construção, ampliação ou regularização de residência unifamiliar popular com supressão de vegetação(não obrigatório e do tipo seleção)
- Intervenção em recursos naturais por agricultores familiares ou assentamentos(não obrigatório e do tipo seleção)
- Projetos e planos habitacionais de interesse social(não obrigatório e do tipo seleção)

@Regra022 - O sistema permite que seja cadastrado um valor máximo de cobrança, para que este seja utilizado quando o preço da solicitação for definido por uma fórmula. Sendo assim, se o resultado da fórmula ultrapassar o valor de máximo definido, o valor da solicitação será o valor de máximo.

@Regra023 - O sistema permite que o valor da unidade UFESP seja cadastrado, e quando cadastrado o valor deve ser em Reais(R$) 

@Regra024- Dados de cadastro da UFESP

Data Início (tipo texto e obrigatório)

Valor UFESP(R$) [Valor maior que 0] (tipo texto e obrigatório)

@Regra025 - Sempre que for alterado o campo Data Início da UFESP, o sistema registra a nova Data de Início menos um dia, como final da vigência do período anterior. 

@Regra026 - Os campos de Autocomplete/Seleção para selecionar Tipologia e finalidades e Tipo de Empresa não devem apresentar os que já tenham sido selecionadas antes.

@Regra027 - Os campos para realizar a cópia são:

Objeto (Obrigatório e do tipo seleção);

Tipo do Imóvel (Obrigatório e do tipo seleção) ou Finalidade (Obrigatório e do tipo seleção) ou Tipologia (Obrigatório e do tipo seleção). Dependendo do tipo de cálculo solicitado

@Regra028 - Quando selecionado a opção Outros no cadastro de Descontos e Isenção, se torna obrigatório pelo menos o preenchimento de um dos checkbox apresentados em "Outros Tipos de Empresa"

@Regra029 - O sistema não permite que a data de Início da UFESP seja menor ou igual a data atual.

@Regra030 - Ao selecionar o botão excluir no cadastro de fórmulas por condicional, o sistema deve remover todos os registros da tabela

@Regra031 - Ao selecionar o botão Editar no cadastro de fórmulas por condicional, o sistema só deve permitir alterar os valores das solicitações. Os valores de máximo e mínimo não devem ser alterados.

Cenários 

|**Fluxo**:00 - Consultar/Alterar Cálculo|**Tipo**: Basic Path|
| :- | :- |
|**Ponto de Entrada**: Esse caso de uso se inicia quando o ator clica no menu esquerdo em "Configurar modo de cálculo"|
**Passo:** 00.01 - Apresenta a tela de consulta conforme o Protótipo PRT042 - Consulta de Formulas por Objeto.png - Sistema

**Passo:** 00.02 - Digita o objeto a ser pesquisado e seleciona a opção pelo autocomplete (FA12 - Atualizar Valor UFESP) - Ator

**Passo:** 00.03 - Apresenta a tela de Modo de Cálculo conforme o Protótipo PRT043 - Fórmula por Preço Fixo.png com os campos já preenchidos, se a configuração do objeto já estiver cadastrada (FA11 - Registro não encontrado)(FA01 - Cadastrar Cálculo) - Sistema

**Passo:** 00.04 - Altera os campos apresentados conforme @Regra002, @Regra003, @Regra004, @Regra006, @Regra007, @Regra015, @Regra016 (FA03 - Preço por Finalidade) (FA04 - Preço por Tipologia) (FA05 - Preço Condicional) (FA06 - Preço por Tipo de Imóvel) (FA02 - Copiar Configurações)(FA23 - Escrever Fórmula)(FA24 - Alterar modo de Cálculo) - Ator

**Passo:** 00.05 - Clica no botão <Salvar> (FA07 - Desconto e Isenção) (FA08 - Limpar dados)(FA15 - Voltar)(FA25 - Desabilita Descontos e Isenção) - Ator

**Passo:** 00.06 - Valida o preenchimento de acordo com a @Regra002, @Regra003 e apresenta a mensagem MSG005 - Dados salvos com sucesso (FA09 - Campo obrigatório) (FA10 - Valor inválido) - Sistema

**Passo:** 00.07 - Fim do caso de uso - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:01 - Cadastrar Cálculo|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona um objeto que ainda não tem nenhum registro de modo de cálculo cadastrado</p><p>no passo 03 do fluxo (00 - Consultar/Alterar Cálculo)</p>|
**Passo:** 01.01 - Apresenta a tela de Modo de Cálculo conforme o Protótipo PRT043 - Fórmula por Preço Fixo.png - Sistema

**Passo:** 01.02 - Preenche os campos apresentados conforme @Regra002, @Regra003, @Regra004, @Regra015, @Regra016 (FA03 - Preço por Finalidade) (FA04 - Preço por Tipologia) (FA05 - Preço Condicional) (FA06 - Preço por Tipo de Imóvel)(FA02 - Copiar Configurações)(FA23 - Escrever Fórmula) - Ator

**Passo:** 01.03 - Clica no botão <Salvar> (FA07 - Desconto e Isenção) (FA08 - Limpar dados)(FA15 - Voltar)(FA25 - Desabilita desconto e isenção) - Ator

**Passo:** 01.04 - Valida o preenchimento de acordo com a @Regra002, @Regra003 e apresenta a mensagem MSG005 - Dados salvos com sucesso (FA09 - Campo obrigatório) (FA10 - Valor inválido) - Sistema

**Passo:** 01.05 -  Fim do caso de uso - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:02 - Copiar Configurações|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator selecionar o ícone "Copiar Configurações" </p><p>no passo 04 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 02 no fluxo (01 - Cadastrar Cálculo),</p><p>no passo 02 no fluxo (03 - Preço por finalidade)</p><p>no passo 02 no fluxo (04 - Preço por Tipologia)</p><p>no passo 02 no fluxo (06 - Preço por Tipo de Imóvel)</p>|
**Passo:** 02.01 - Apresenta o modal conforme o protótipo PRT050 - Modal Copiar Fórmulas.png - Sistema

**Passo:** 02.02 - Seleciona o objeto e o campo complementar quando necessário, que será a base para a cópia da configuração da fórmula de acordo com a @Regra014, @Regra017, @Regra018, @Regra027 (FA22 - Fechar modal) - Ator

**Passo:** 02.03 - Retorna para o passo o passo 04 do fluxo 00 - Consultar/Alterar Cálculo 

passo 02 do fluxo 03 - Preço por Finalidade ou

para o passo 02 do fluxo 04 - Preço por Tipologia ou 

para o passo 02 do fluxo 05 - Preço condicional ou

para o passo 02 do fluxo 06 - Preço por Tipo de Imóvel - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:03 - Preço por Finalidade|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator clica na opção "Preço por Finalidade",</p><p>no passo 04 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 02 no fluxo (01 - Cadastrar Cálculo),</p>|
**Passo:** 03.01 - Apresenta a tela conforme o Protótipo PRT045 - Fórmula por Finalidade.png - Sistema

**Passo:** 03.02 - Seleciona a finalidade, preenche/Altera os campos conforme @Regra003, @Regra006, @Regra007, @Regra009, @Regra018 e @Regra026 e seleciona o botão Incluir (FA16 - Cancelar Inclusão)  (FA02 - Copiar Configurações)(FA23 - Escrever Fórmula)(FA08 - Limpar dados) - Ator

**Passo:** 03.03 - Adiciona o registro incluido na tabela  - Sistema

**Passo:** 03.04 - Retorna para o passo 05 no fluxo 00 - Consultar/Alterar Cálculo ou para o passo 03 do fluxo 01 - Cadastrar Cálculo (FA17 - Excluir registro)(FA18 - Editar Registro)(FA25 - Desabilita Descontos e Isenção) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:04 - Preço por Tipologia|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator clica na opção "Preço por Tipologia",</p><p>no passo 04 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 02 no fluxo (01 - Cadastrar Cálculo),</p>|
**Passo:** 04.01 - Apresenta a tela conforme o Protótipo PRT047 - Fórmula por Tipologia.png e a @Regra005 - Sistema

**Passo:** 04.02 - Seleciona a tipologia, preenche/altera os campos conforme @Regra003, @Regra006, @Regra007, @Regra010, @Regra018 e @Regra026 e seleciona o botão Incluir (FA16 - Cancelar Inclusão) (FA02 - Copiar Configurações)(FA23 - Escrever Fórmula)(FA08 - Limpar dados) - Ator

**Passo:** 04.03 - Adiciona o registro incluido na tabela  - Sistema

**Passo:** 04.04 - Retorna para o passo 05 no fluxo 00 - Consultar/Alterar Cálculo ou 

para o passo 03 do fluxo 01 - Cadastrar Cálculo (FA17 - Excluir Registro)(FA18 - Editar Registro)(FA07 - Desconto e Isenção) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:05 - Preço Condicional|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator clica na opção "Preço Condicional",</p><p>no passo 04 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 02 no fluxo (01 - Cadastrar Cálculo),</p>|
**Passo:** 05.01 - Apresenta a tela conforme o Protótipo PRT046 - Fórmula por Condicional.png - Sistema

**Passo:** 05.02 - Seleciona a variável, preenche/Altera os campos conforme @Regra003, @Regra006, @Regra007, @Regra008, @Regra012, @Regra013 @Regra030 e @Regra031 e seleciona o botão Incluir (FA16 - Cancelar Inclusão)(FA08 - Limpar dados) - Ator

**Passo:** 05.03 - Registra na tabela os ranges de acordo com os valores de máximo e mínimo que foram informados de acordo com a @Regra12  - Sistema

**Passo:** 05.04 - Retorna para o passo 05 no fluxo 00 - Consultar/Alterar Cálculo ou 

para o passo 03 do fluxo 01 - Cadastrar Cálculo (FA18 - Editar Registro) (FA17 - Excluir Registro)(FA25 - Desabilita Descontos e Isenção) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:06 - Preço por Tipo de Imóvel|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator clica na opção "Preço por Tipo de Imóvel",</p><p>no passo 04 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 02 no fluxo (01 - Cadastrar Cálculo),</p>|
**Passo:** 06.01 - Apresenta a tela conforme o Protótipo PRT044 - Fórmula por Tipo de Imóvel.png - Sistema

**Passo:** 06.02 - Seleciona o tipo de imóvel, preenche/altera os campos conforme @Regra003, @Regra006, @Regra007, @Regra011 e @Regra018 e seleciona o botão Incluir (FA16 - Cancelar Inclusão)  (FA02 - Copiar Configurações)(FA23 - Escrever Fórmula)(FA08 - Limpar dados) - Ator

**Passo:** 06.03 - Adiciona o registro incluido na tabela  - Sistema

**Passo:** 06.04 - Retorna para o passo 05 no fluxo 00 - Consultar/Alterar Cálculo ou

para o passo 03 do fluxo 01 - Cadastrar Cálculo (FA17 - Excluir Registro)(FA18 - Editar Registro)(FA25 - Desabilita Descontos e Isenção) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:07 - Desconto e Isenção|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator clica no checkbox "Permitir desconto ou isenção de pagamento",</p><p>no passo 05 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 03 no fluxo (01 - Cadastrar Cálculo)</p><p></p><p>Ou então quando o ator seleciona o ícone de "%"</p><p>no passo 04 no fluxo (04 - Preço por tipologia)</p>|
**Passo:** 07.01 - Apresenta a tela conforme o Protótipo PRT049 - Modal de Descontos e Isenções.png - Sistema

**Passo:** 07.02 - Seleciona o tipo de empresa, preenche/Altera os campos conforme @Regra019, @Regra020, @regra021 e @Regra026 e seleciona o botão Incluir (FA16 - Cancelar Inclusão)(FA08 - Limpar dados) - Ator

**Passo:** 07.03 - Adiciona o registro incluido na tabela  - Sistema

**Passo:** 07.04 - Verifica que o tipo de empresa é diferente de “Outros” (FA19 - Outros Tipos de Empresa) - 

**Passo:** 07.05 - Retorna para o passo 05 no fluxo 00 - Consultar/Alterar Cálculo ou

para o passo 01 do fluxo 03 - Cadastrar Cálculo  (FA17 - Excluir Registro)(FA18 - Editar Registro)(FA22 - Fechar modal) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:08 - Limpar dados|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator clica no botão <Limpar>,</p><p>no passo 05 no fluxo (00 - Consultar/Alterar Cálculo) ou</p><p>no passo 03 no fluxo (01 - Cadastrar Cálculo) ou </p><p>no passo 04 do fluxo (03 - Preço por Finalidade) ou</p><p>no passo 04 do fluxo (04 - Preço por Tipologia) ou</p><p>no passo 04 do fluxo (05 - Preço Condicional) ou</p><p>no passo 04 do fluxo (06 - Preço por Tipo de Imóvel) ou</p><p>no passo 04 do fluxo (07 - Desconto e Isenção)</p>|
**Passo:** 08.01 - Limpa os campos preenchidos - Sistema

**Passo:** 08.02 - Retorna  para o passo 03 no fluxo 00 - Consultar/Alterar Cálculo ou

para o passo 01 do fluxo 01 - Cadastrar Cálculo ou

para o passo 01 do fluxo 03 - Preço por Finalidade ou

para o passo 01 do fluxo 04 - Preço por Tipologia ou

para o passo 01 do fluxo 05 - Preço condicional ou

para o passo 01 do fluxo 06 - Preço por Tipo de imóvel ou - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:09 - Campo obrigatório|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o sistema localiza campos obrigatórios não preenchidos,</p><p>no passo 06 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 04 no fluxo (01 - Cadastrar Cálculo)</p><p>no passo 03 no fluxo (12 - Atualizar Valor UFESP)</p>|
**Passo:** 09.01 - Apresenta a mensagem  MSG004 - O campo é obrigatório - Sistema

**Passo:** 09.02 - Retorna  para o passo 04 no fluxo 00 - Consultar/Alterar Cálculo. Ou

para o passo 02 do fluxo - 01 Cadastrar Cálculo ou

para o passo 02 do fluxo 03 - Preço por Finalidade ou

para o passo 02 do fluxo 04 - Preço por Tipologia ou

para o passo 02 do fluxo 05 - Preço condicional ou

para o passo 02 do fluxo 06 - Preço por Tipo de imóvel ou

para o passo 02 do fluxo 07 - Descontos e Isenção ou

para o passo 01 no fluxo - 12 - Atualizar Valor UFESP - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:10 - Valor inválido|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o sistema verifica que há campos preenchidos com o valor incorreto,</p><p>no passo 06 no fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 04 no fluxo (01 - Cadastrar Cálculo)</p><p>no passo 03 no fluxo (12 - Atualizar Valor UFESP)</p>|
**Passo:** 10.01 - Apresenta a mensagem MSG042 - O valor é inválido - Sistema

**Passo:** 10.02 - Retorna  para o passo 04 no fluxo 00 - Consultar/Alterar Cálculo. Ou

para o passo 02 do fluxo - 01 Cadastrar Cálculo ou

para o passo 02 do fluxo 03 - Preço por Finalidade ou

para o passo 02 do fluxo 04 - Preço por Tipologia ou

para o passo 02 do fluxo 05 - Preço condicional ou

para o passo 02 do fluxo 06 - Preço por Tipo de imóvel ou

para o passo 02 do fluxo 07 - Descontos e Isenção ou

para o passo 01 no fluxo - 12 - Atualizar Valor UFESP - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:11 - Registro não encontrado|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o sistema não localiza na lista de campo autocomplete a opção preenchida,</p><p>no passo 03 do fluxo (00 - Consultar/Alterar Cálculo)</p>|
**Passo:** 11.01 - Apresenta na lista abaixo ao campo Objeto a informação de "Nenhum encontrado" sobre a pesquisa - Sistema

**Passo:** 11.02 - Retorna  para o passo 01 no fluxo 00 - Consultar/Alterar Cálculo - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:12 - Atualizar valor UFESP|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o botão "Valor UFESP" </p><p>no passo 02 do fluxo (00 - Consultar/Alterar Cálculo)</p>|
**Passo:** 12.01 - Apresenta o modal conforme o protótipo PRT048 - Cadastro de UFESP.png  com os valores preenchidos anteriormente - Sistema

**Passo:** 12.02 - Altera dos dados de acordo com a @Regra024 e @Regra029 e seleciona o botão <Salvar> (FA13 - Cancelar Atualização UFESP) - Ator

**Passo:** 12.03 - Valida as informações conforme a @Regra024, @Regra025 e @Regra029 e apresenta a mensagem MSG005 - Dados salvos com sucesso   (FA14 - Data inválida) (FA10 - Valor inválido) (FA09 - Campo obrigatório) - Sistema

**Passo:** 12.04 - Fim do caso de uso - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:13 - Cancelar Atualização UFESP|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o botão cancelar</p><p>no passo 02 do fluxo (12 - Atualizar Valor UFESP)</p>|
**Passo:** 13.01 - Retorna para o passo 01 do fluxo 00-Consultar/Alterar Cálculo - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:14 - Data Inválida|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator preenche uma data inválida</p><p>no passo 03 no fluxo (12 - Atualizar Valor UFESP)</p>|
**Passo:** 14.01 - Apresenta a mensagem MSG018 - Data inválida - Sistema

**Passo:** 14.02 - Retorna para o passo 01 do fluxo 12 - Atualizar Valor UFESP - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:15 - Voltar|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Este fluxo se inicia quando o ator seleciona o botão <Voltar> durante o Cadastro/Alteração do modo de cálculo</p><p>no passo 05 do fluxo (00 - Consultar/Alterar Cálculo);</p><p>no passo 03 do fluxo (01 - Cadastrar Cálculo)</p>|
**Passo:** 15.01 - Apresenta a mensagem MSG017 - Deseja Voltar? Você perderá todas as alterações não salvas. com as opções <Cancelar> e <Voltar> - Sistema

**Passo:** 15.02 - Seleciona o botão <Voltar> (FA21 - Cancelar Ação) - Ator

**Passo:** 15.03 - Retorna para o passo 01 do fluxo 00 - Consultar/Alterar Cálculo - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:16 - Cancelar Inclusão|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o botão Cancelar</p><p>no passo 02 do fluxo (03 - Preço por Finalidade)</p><p>no passo 02 do fluxo (04 - Preço por Tipologia)</p><p>no passo 02 do fluxo (05 - Preço Condicional)</p><p>no passo 02 do fluxo (06 - Preço por Tipo de Imóvel)</p><p>no passo 02 do fluxo (07 - Desconto e Isenção)</p>|
**Passo:** 16.01 - Retorna no passo 01 do fluxo (03 - Preço por Finalidade) ou

no passo 01 do fluxo (04 - Preço por Tipologia) ou

no passo 01 do fluxo (05 - Preço Condicional) ou

no passo 01 do fluxo (06 - Preço por tipo de imóvel) ou

no passo 01 do fluxo (07 - Desconto e Isenção) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:17 - Excluir Registro|**Tipo**: Basic Path|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o ícone de lixeira</p><p>no passo 04 do fluxo (03 - Preço por Finalidade)</p><p>no passo 04 do fluxo (04 - Preço por Tipologia)</p><p>no passo 04 do fluxo (05 - Preço condicional)</p><p>no passo 04 do fluxo (06 - Preço por Tipo de Imóvel)</p><p>no passo 04 do fluxo (07 - Desconto e Isenção)</p>|
**Passo:** 17.01 - Apresenta a mensagem MSG007 - Deseja remover o registo? com as opção <Cancelar> e <Remover> - Sistema

**Passo:** 17.02 - Seleciona o botão <Remover> (FA20 - Cancelar Exclusão) - Ator

**Passo:** 17.03 - Remove o(s) registro(s) - Sistema

**Passo:** 17.04 - Retorna no passo 01 do fluxo (03 - Preço por Finalidade) ou

no passo 01 do fluxo (04 - Preço por Tipologia) ou

no passo 01 do fluxo (05 - Preço Condicional) ou

no passo 01 do fluxo (06 - Preço por Tipo de Imóvel) ou

no passo 01 do fluxo (07 - Desconto e Isenção) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:18 - Editar Registro|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o ícone de Lápis </p><p>no passo 04 do fluxo (03 - Preço por Finalidade)</p><p>no passo 04 do fluxo (04 - Preço por Tipologia)</p><p>no passo 04 do fluxo (05 - Preço Condicional)</p><p>no passo 04 do fluxo (06 - Preço por Tipo de Imóvel)</p><p>no passo 04 do fluxo (07 - Desconto e Isenção)</p>|
**Passo:** 18.01 - Apresenta os campos preenchidos de acordo com a @Regra003 com os valores que estão na linha que está sendo feita a edição - Sistema

**Passo:** 18.02 - Retorna no passo 01 do fluxo (03 - Preço por Finalidade) ou

no passo 01 do fluxo (04 - Preço por Tipologia) ou

no passo 01 do fluxo (05 - Preço Condicional) ou

no passo 01 do fluxo (06 - Preço por tipo de Propriedade) ou

no passo 01 do fluxo (07 - Desconto e Isenção)

` `- Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:19 - Outros tipos de empresa|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator preenche o campo de desconto com o valor Outros</p><p>no passo 04 do fluxo (07 - Desconto e Isenção)</p>|
**Passo:** 19.01 - Apresenta os Checkbox com as opções dos Outros Tipos de empresa - Sistema

**Passo:** 19.02 - Seleciona as opções desejadas de acordo com a @Regra028 - Ator

**Passo:** 19.03 - Retorna  para o passo 05 no fluxo 07 - Desconto e isenção - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:20 - Cancelar Exclusão|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona a opção Cancelar</p><p>no passo 02 do fluxo (17 - Excluir Registro)</p>|
**Passo:** 20.01 - Retorna no passo 01 do fluxo 03 - Preço por Finalidade. Ou

no passo 01 do fluxo 04 - Preço por Tipologia Ou

no passo 01 do fluxo 06 - Preço por tipo de Propriedade Ou

no passo 01 do fluxo 07 - Desconto e Isenção - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:21 - Cancelar Ação|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona a opção cancelar</p><p>no passo 02 do fluxo (15 - Voltar) ou</p><p>no passo 02 do fluxo (24 - Alterar modo de cálculo)</p>|
**Passo:** 21.01 - Retorna para o passo 03 do fluxo 00 - Consultar/Alterar Cálculo ou 

para o passo 01 do fluxo 01 - Cadastrar Cálculo 

para o passo 01 do fluxo 03 - Preço por Finalidade ou

para o passo 01 do fluxo 04 - Preço por Tipologia ou

para o passo 01 do fluxo 05 - Preço condicional ou

para o passo 01 do fluxo 06 - Preço por Tipo de imóvel - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:22 - Fechar modal|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o botão Fechar</p><p>no passo 02 do fluxo (02 - Copiar Configurações) ou</p><p>no passo 02 do fluxo (07 - Desconto e Isenção) ou </p><p>no passo 02 do fluxo (23 - Escrever fórmulas)</p>|
**Passo:** 22.01 - Retorna para o passo 03 do fluxo 00 - Consultar/Alterar Cálculo ou 

para o passo 01 do fluxo 01 - Cadastrar Cálculo 

para o passo 01 do fluxo 03 - Preço por Finalidade ou

para o passo 01 do fluxo 04 - Preço por Tipologia ou

para o passo 01 do fluxo 05 - Preço condicional ou

para o passo 01 do fluxo 06 - Preço por Tipo de imóvel ou - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:23 - Escrever Fórmula|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator seleciona o ícone da calculadora</p><p>no passo 4 do fluxo (00 - Consultar/Alterar Cálculo) ou</p><p>no passo 02 no fluxo (01 - Cadastrar Cálculo) ou</p><p>no passo 2 do fluxo (03 - Preço por finalidade) ou</p><p>no passo 2 do fluxo (04 - Preço por tipologia) ou</p><p>no passo 2 do fluxo (06 - Preço por tipo de imóvel)</p>|
**Passo:** 23.01 - Apresenta o modal conforme Protótipo PRT051 - Modal Configurar Fórmulas.png - Sistema

**Passo:** 23.02 - Seleciona o campo "Preço da Solicitação" e cria a fórmula através do teclado e dos ícones auxiliares do modal, de acordo com a @Regra006, @Regra007 e @Regra008 (FA10 - Valor Inválido) - Ator

**Passo:** 23.03 - Seleciona o botão <Salvar>(FA22 - Fechar modal) - Ator

**Passo:** 23.04 - Retorna para o passo o passo 04 do fluxo 00 - Consultar/Alterar Cálculo 

passo 02 do fluxo 03 - Preço por Finalidade ou

para o passo 02 do fluxo 04 - Preço por Tipologia ou 

para o passo 02 do fluxo 06 - Preço por Tipo de Imóvel - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:24 - Alterar modo de Cálculo|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator está cadastrando ou editando um objeto e seleciona uma outra opção da @Regra002</p><p>no passo 04 do fluxo (00 - Consultar/Alterar Cálculo),</p><p>no passo 02 do fluxo (03 - Preço por Finalidade),</p><p>no passo 02 do fluxo (04 - Preço por Tipologia), </p><p>no passo 02 do fluxo (05 - Preço Condicional),</p><p>no passo 02 do fluxo (06 - Preço por Tipo de Imóvel)</p>|
**Passo:** 24.01 - Apresenta a Mensagem MSG047 - Deseja alterar o modo de cálculo? com as opções <Alterar> e <Cancelar> - Sistema

**Passo:** 24.02 - Seleciona a opção <Alterar>(FA21 - Cancelar ação) - Ator

**Passo:** 24.03 - Limpa as alterações feitas sem salva-las - Sistema

**Passo:** 24.04 - Retorna para o passo o passo 03 do fluxo 00 - Consultar/Alterar Cálculo ou

para o passo 01 do fluxo 03 - Preço por Finalidade ou

para o passo 01 do fluxo 04 - Preço por Tipologia ou 

para o passo 01 do fluxo 05 - Preço por condicional ou 

para o passo 01 do fluxo 06 - Preço por Tipo de Imóvel - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


|**Fluxo**:25 - Desabilita Desconto e Isenção|**Tipo**: Alternate|
| :- | :- |
|<p>**Ponto de Entrada**: Esse fluxo se inicia quando o ator desabilita a opção Desconto e Isenção, após o sistema já ter registrado algum tipo de valor aos campos de Desconto e Isenção,</p><p>no passo 05 do fluxo (00 - Consultar/Alterar Cálculo)</p><p>no passo 04 do fluxo (03 - Preço por Finalidade) ou</p><p>no passo 04 do fluxo (05 - Preço Condicional) ou</p><p>no passo 04 do fluxo (06 - Preço por tipo de imóvel)</p>|
**Passo:** 25.01 - Apresenta a mensagem MSG049 - Todos os descontos e isenções serão descartados, deseja continuar? com as opções <Descartar><Cancelar> - Sistema

**Passo:** 25.02 - Seleciona a opção <Descartar>(FA21 - Cancelar ação) - Ator

**Passo:** 25.03 -  Limpa as alterações feitas sem salva-las - Sistema

**Passo:** 25.04 - Retorna no passo 04 do fluxo (00 - Consultar/Alterar Cálculo)

no passo 01 do fluxo (03 - Preço por Finalidade) ou

no passo 01 do fluxo (05 - Preço Condicional) ou

no passo 01 do fluxo (06 - Preço por tipo de imóvel) - Sistema

\- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Pré e Pós Condições 

Requisitos Realizados pelo Caso de Uso 


`			`Página: 13 de 1
