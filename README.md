# 📋 Automação de Cadastros no SEI e SIP com macros do UI.Vision RPA

Este repositório contém diversas macros desenvolvidas com a ferramenta UI.Vision RPA para automatizar tarefas manuais e recorrentes relacionadas ao cadastro e configuração de usuários, unidades, assuntos e diversos outros itens de parametrização no Sistema Eletrônico de Informações - SEI (e no Sistema de Permissões - SIP). As automações foram desenhadas para facilitar cargas iniciais em massa de novos ambientes e agilizar manutenções periódicas.

As macros utilizam arquivos `.csv` como fonte de dados estruturada e realizam, de forma automatizada, a navegação e o preenchimento de campos nos sistemas SEI e SIP, interagindo diretamente com a interface de usuário (UI), sem qualquer manipulação de banco de dados, o que torna o processo extremamente seguro em termos de integridade do sistema. Cada macro trata um tipo específico de informação e obedece um padrão de repetição que apresenta mensagens de status e progresso, facilitando o acompanhamento em tempo real da execução.

## 👨‍🔧 A quem são destinadas estas macros?

Usuários com perfil de Administração do SEI, que tenham acesso ao SIP para cadastro de unidades, hierarquia, usuários, permissões e que tenham permissão para acessar e modificar configurações no menu `Administração` do SEI.

## 🚀 Objetivo

Automatizar processos administrativos repetitivos no SEI/SIP com segurança e eficiência, reduzindo o esforço manual de operadores e padronizando o carregamento de dados a partir de arquivos `.csv`.

## 🛠️ Pré-requisitos

- Navegador com extensão UiVision RPA instalada ([Google Chrome](https://chrome.google.com/webstore/detail/uivision-rpa/ljdobmomdgdljniojadhoplhkpialdid) ou [Mozilla Firefox](https://addons.mozilla.org/en-US/firefox/addon/uivision-rpa/)). As macros foram criadas no Google Chrome, mas não deve haver conflito.
- Arquivo(s) `.csv` de entrada preenchidos conforme estrutura apresentada nos arquivos exemplo.
- Acesso de Administrador aos ambientes do SEI e SIP.

## 📂 Estrutura do Repositório

Você pode baixar todo o conjunto de macros e arquivos `.csv` em um único arquivo `.zip`, no link abaixo: 

(macros-SEI-SIP.zip)(https://github.com/pengovbr/macros-SEI-SIP/blob/main/macros-SEI-SIP.zip)

Alternativamente, você pode baixar cada arquivo individualmente na listagem abaixo.

> Clique com o botão direito e escolha “Salvar link como...”

📁 macros-SEI-SIP/  
├─ [1.cargaUnidades.json](https://github.com/pengovbr/macros-SEI-SIP/raw/main/1.cargaUnidades.json)  
├─ [2.hierarquia.json](https://github.com/pengovbr/macros-SEI-SIP/raw/main/2.hierarquia.json)  
├─ [3.dadosUnidadesSEI.json](https://github.com/pengovbr/macros-SEI-SIP/raw/main/3.dadosUnidadesSEI.json)  
├─ [4.cargaUsuarios.json](https://github.com/pengovbr/macros-SEI-SIP/raw/main/4.cargaUsuarios.json)  
├─ [5.permissoes.json](https://github.com/pengovbr/macros-SEI-SIP/raw/main/5.permissoes.json)  
├─ [6.cargaAssuntos.json](https://github.com/pengovbr/macros-SEI-SIP/raw/main/6.cargaAssuntos.json)  
└📁 csv/  
&nbsp;&nbsp; ├─ [exemploAssuntos.csv](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploAssuntos.csv)  
&nbsp;&nbsp; ├─ [exemploUnidades.csv](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploUnidades.csv)  
&nbsp;&nbsp; └─ [exemploUsuarios.csv](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploUsuarios.csv)  

### Sobre as macros incluídas:

1.	**Cadastro de Unidades no SIP**: Automatiza o registro de unidades administrativas no sistema, com base em sua sigla, descrição e órgão vinculado;
2.	**Cadastro das Unidades na Hierarquia no SIP**: Realiza o vínculo entre as unidades cadastradas, definindo sua posição na estrutura hierárquica;
3.	**Cadastro de Dados Complementares das Unidades no SEI**: Preenche informações adicionais relacionadas às unidades, como tipo, endereço ou outros campos auxiliares;
4.	**Cadastro de Usuários no SIP**: Cria contas de usuários no sistema, utilizando dados como CPF, nome, login e e-mail institucional etc.;
5.	**Cadastro de Permissões no SIP**: Atribui as permissões adequadas aos usuários conforme o perfil a ser concedido e a unidade de atuação no sistema; e
6.	**Cadastro de Assuntos no SEI**: Preenche as informações referentes aos assuntos que constam das Tabelas de Assunto do SEI, para fins de classificação de processos e documentos e controle da temporalidade.

> [!IMPORTANT]
> Além destas, estão disponíveis 03 (três) arquivos em formato `.csv` para servir de modelo para preenchimento pelo administrador: 
> 1. **exemploUnidades**: que traz a estrutura de dados referentes a unidades, para execução das macros `1.cargaUnidades.json`, `2.hierarquia.json ` e `3.dadosUnidadesSEI.json`;
> 2. **exemploUsuarios**: que traz a estrutura de dados referentes a usuários,  para execução das macros `4.cargaUsuarios.json` e `5.permissoes.json `; e
> 3. **exemploAssuntos**: que traz a estrutura de dados referentes aos assuntos da tabela, para servir de modelo para preenchimento pelo administrador, para execução da macro `6.cargaAssuntos.json `;


## ▶️ Como usar

1. Instale a extensão UiVision RPA no seu navegador.
2. Importe os arquivos `.json` para o UiVision via menu `Manage Macros > Import`.
3. Importe o arquivo `.csv` correspondente para utilização na macro.
4. Caso tenha renomeado o arquivo, altere também o valor do campo `Target` da linha onde consta o comando `csvReadArray` na macro, para que corresponda ao arquivo que irá utilizar.
6. Abra o SEI ou SIP no navegador e acesse o menu correspondente à macro (Por exemplo: a macro `4.cargaUsuarios` se inicia no sistema `SIP`, menu `Usuários` > `Listar`). Estes caminhos estão indicados abaixo, nas instruções Macro a Macro, e também são exibidos sempre na primeira linha de cada macro.
7. A página  em que a macro será executada deve estar aberta na tela para iniciar sua execução.
8. Execute a macro desejada, clicando no botão `Play Macro`.
9. Acompanhe o log da execução e valide o resultado no sistema. As macros apresentam quantas linhas foram cadastradas com sucesso ou com falha. Valide a execução por meio de batimento entre as quantidades de valores cadastrados e a quantidade de valores existentes no arquivo de referência.

## 📝 Orientações gerais e observações

- Há dois tipos de erros possíveis na reprodução das macros: os erros que ocorrem no SEI ou SIP, que são exibidos pelas macros no `echo`, como parte do resultado da execução (erros previstos), e os erros que ocorrem por falha de execução da própria macro, que são exibidos como **"Error"** e interrompem a execução das macros. Nestes casos, é importante investigar para ver o que causou o erro e o que pode ser feito para sanar o reportado. Alguns erros, como o **"Lost connection to site"** (conexão perdida com o site), por exemplo, podem ser resolvidos com uma reexecução da macro. Outros podem exigir uma revisão do arquivo `.csv` ou revisão das configurações de execução do UI.Vision (botão ⚙️ - Settings).
- Os arquivos `.csv` devem estar no formato esperado por cada macro. A primeira linha de cada arquivo exemplo traz um cabeçalho indicando a estrutura de cada `.csv`.
- Caso algum termo utilizado no arquivo `.csv` contenha vírgulas, coloque o valor inteiro entre aspas (por exemplo: A `Divisão de Obras, Contratos e Serviços Gerais` deve ser grafada no arquivo `.csv` como `"Divisão de Obras, Contratos e Serviços Gerais"` (com aspas). 
- Certifique-se de que os dados de entrada (nomes, e-mails, CPF etc.) estejam devidamente validados antes da execução, para evitar retrabalho por inconsistência.
- Embora bastante incomuns, alterações na interface do SEI ou SIP podem impactar os seletores usados (IDs, nomes, posições). Verifique e atualize conforme necessário.

### 𝄜 Como gerar o arquivo `.csv`?
Elaborar um arquivo `.csv` manualmente pode ser **muito** complicado. Se você tiver grandes quantidades de linhas ou colunas, os valores ficam muito próximos e o risco de você se confundir aumenta consideravelmente. Assim, a maneira mais fácil de gerar um `.csv` é a partir de uma planilha. Recomendamos, neste caso, utilizar o [editor de planilhas da Google](https://docs.google.com/spreadsheets), porque ele oferece a opção de gerar um arquivo `.csv` com  facilidade. Basta clicar, após gerar a lista de dados a serem cadastrados, em `Arquivo` > `Baixar` > `Valores separados por vírgulas (.csv)` e fazer o download do arquivo para a pasta que você escolher.

### ⏯️ Linha de Início (Retomada após erro ou pausa)
- Todas as macros permitem retomar a execução a partir de uma linha específica do `.csv`, bastando ajustar a variável de início `i`, logo no início de cada macro no comando `store | 1 | i`. Este valor `1` indica que a macro deve iniciar sua execução pela 1ª linha do `.csv`. Basta alterar para a linha da qual se deseja retomar, em caso de necessidade. Isso é útil para continuidade após interrupções.

### 💾 Armazenamento das macros
- No canto inferior esquerdo de sua interface, o UI.Vision permite que você defina se irá salvar as macros no armazenamento da própria extensão `Local Storage (In Browser)` ou em uma pasta de seu computador `Fyle system (on hard drive)`. Se você utilizar a opção `Local Storage (In Browser)`, você precisará sempre importar novamente o `.csv` a cada nova alteração ou correção. Se salvas no computador, basta atualizar os arquivos normalmente e clicar em 🔄 _(Reload all resources on hard drive)_ para que as alterações se reflitam na execução das macros. Neste caso (`Local Storage (In Browser)`), as macros devem ser salvas dentro da pasta do UI.Vision, subpasta `macros` e os arquivos `.csv` devem ser salvos na subpasta `datasources`.

### 🧾 Visualizando os logs
- Recomenda-se que a visualização dos logs (no canto inferior direito da tela, ao lado do botão `Clear`) seja definida com a opção `Echo & Status`, para que as mensagens exibidas sejam apenas aquelas configuradas na criação das macros. As macros foram desenvolvidas para exibir informações de progresso e estimativa de tempo restante, conforme são executadas. A exibição completa (`All`) traz a execução linha a linha de cada macro e pode gerar confusão para usuários não familizarizados com o tema. Neste sentido, sua utilização é recomendada apenas em caso de necessidade de depuração de erros, por usuários experientes.  

> [!TIP]
> **A execução exibe mensagens claras de progresso no log, como, por exemplo:**
> - 📈 Progresso e ⏳ Tempo restante estimado ( visível a partir da 4ª execução, para evitar grandes distorções na estimativa)
> - 🔁 Processando item
> - ✅ Sucesso no cadastro
> - ❌ Falha, com a mensagem de erro capturada
> - 🏁 Resumo final com total de registros e número de erros


## 🏢 Macros sobre unidades
As macros que tratam de informações sobre unidades (`1.cargaUnidades`, `2.hierarquia` e `3.dadosUnidadesSEI`) usam como referência o arquivo `exemploUnidades.csv`, cuja estrutura está indicada abaixo:

As colunas são:  
**0-Seq.**: Número sequencial (ajuda na orientação linha a linha);  
**1-ORGAO**: Sigla do órgão em que a unidade será cadastrada (deve estar idêntica à sigla do órgão no SIP) - **Campo obrigatório**;  
**2-SIGLA**: Sigla da Unidade a ser cadastrada - **Campo obrigatório**;  
**3-DESCRICAO**: Nome da Unidade a ser cadastrada - **Campo obrigatório**;  
**4-PAI**: Unidade imediatamente superior na hierarquia - **Campo obrigatório** (no caso de unidade "raiz", que não possui unidade acima, deve ser deixado em branco);  
**5-EMAIL**: Endereço de e-mail corporativo da unidade;  
**6-TELEFONE**: Telefone da unidade; e  
**7-SITE**: sítio web da unidade.  

Confira abaixo um exemplo de montagem da lista de unidades:

| 0-Seq. | 1-ORGAO | 2-SIGLA | 3-DESCRICAO | 4-PAI | 5-EMAIL | 6-TELEFONE | 7-SITE
|---|---|---|---|---|---|---|---|
| 1 | ORGAO1 | UNI1 | Nome da Unidade 1 | | uni1@orgao1.gov | (99) 2233-4455 | gov.br/orgao1
| 2 | ORGAO1 | SUBUNI1.1 | Nome da Subunidade 1.1 | UNI1 | subuni1.1@orgao1.gov | (99) 2233-5566 | gov.br/orgao1
| 3 | ORGAO1 | SUBUNI1.2 | Nome da Subunidade 1.2 | UNI1 | subuni1.2@orgao1.gov | (99) 2233-5566 | gov.br/orgao1/tema-xpto
| 4 | ORGAO1 | SUBUNI1.2.1 | Nome da Subunidade 1.2.1, antiga 1.3  | SUBUNI1.2 | subuni1.2.1@orgao1.gov | (99) 2233-6677 | gov.br/orgao1/tema-xpto
| 5 | ORGAO1 | UNI2 | Nome da Unidade 2 | | uni2@orgao1.gov | (99) 2233-3344 | gov.br/orgao1/tema-xyz
| ... | | | | | | | |

Em formato `.csv`, esta lista ficará visível desta forma:
> 0-Seq.,1-ORGAO,2-SIGLA,3-DESCRICAO,4-PAI,5-EMAIL,6-TELEFONE,7-SITE  
> 1,ORGAO1,UNI1,Nome da Unidade 1,,uni1@orgao1.gov,(99) 2233-4455,gov.br/orgao1  
> 2,ORGAO1,SUBUNI1.1,Nome da Subunidade 1.1,UNI1,subuni1.1@orgao1.gov,(99) 2233-5566,gov.br/orgao1  
> 3,ORGAO1,SUBUNI1.2,Nome da Subunidade 1.2,UNI1,subuni1.2@orgao1.gov,(99) 2233-5566,gov.br/orgao1/tema-xpto  
> 4,ORGAO1,SUBUNI1.2.1,"Nome da Subunidade 1.2.1, antiga 1.3",SUBUNI1.2,subuni1.2.1@orgao1.gov,(99) 2233-6677,gov.br/orgao1/xpto  
> 5,ORGAO1,UNI2,Nome da Unidade 2,,uni2@orgao1.gov,(99) 2233-3344,gov.br/orgao1/tema-xyz  

> [!NOTE]
> Repare o uso das aspas para isolar conteúdo que tenha vírgulas originalmente.  
> Repare também que as unidades `UNI1` e `UNI2` são unidades "raiz", e portanto nada foi inserido na coluna `Pai`. O arquivo `.csv` traz duas vírgulas seguidas para mostrar que o campo foi deixado em branco.

### Vamos falar destas três macros abaixo: 

### 🏤 Macro `1.cargaUnidades`
- O ponto de partida dessa macro é o sistema SIP, menu `Unidades` > `Listar`;
- O arquivo de referência é o `exemploUnidades.csv`, acima;
- As colunas `1-ORGÃO`,`2-SIGLA` e `3-DESCRICAO` são utilizadas por esta macro. As demais são usadas pelas macros posteriores; e 
- Na linha 3 da macro, onde consta `store | 1 | i`, o valor `1` indica que a macro será executada a partir da 1ª linha. Caso deseje executar a partir de outro ponto, altere este valor para a linha que desejar.

### 🖧 Macro `2.hierarquia`
- O ponto de partida dessa macro é o sistema SIP, menu `Unidades` > `Listar`;
- O arquivo de referência é o `exemploUnidades.csv`, cuja estrutura está detalhada acima.
- As colunas `1-ORGÃO`,`2-SIGLA` e `4-PAI` são utilizadas por esta macro. As demais são usadas pelas macros posteriores.
> [!IMPORTANT]
> - As linhas que trazem a coluna `4-PAI` em branco indicam que se trata de uma unidade _"Raiz"_, ou seja, que não possui nenhuma unidade acima de si na hierarquia. As demais linhas devem trazer a unidade imediatamente superior a elas para cadastramento na hierarquia.
> - Por isso, é importante ter em mente que a hierarquia deve ser cadastrada <ins>**de cima para baixo**</ins>. Ou seja, primeiro devem ser inseridos na planilha os níveis mais altos da estrutura organizacional e depois os que vierem abaixo destes. Isso evita que o SIP retorne mensagem de erro informando que a unidade superior não foi encontrada ou travamento da macro.
- Esta macro executa um script para atribuir ao campo "Data de Início" da unidade na hierarquia com a data atual (dia em que a macro está sendo executada). Caso opte por utilizar outra data, "comente" a linha 32 da macro (clicando em `//`) e altere o teor do campo `value` da linha 33, em que consta `${dataHoje}` para a data que deseja fazer constar.

### 🎛️ Macro `3.dadosUnidadesSEI`
- O ponto de partida dessa macro é o sistema SEI, menu `Administração` > `Unidades` > `Listar`;
- O arquivo de referência é o `exemploUnidades.csv`, cuja estrutura está detalhada acima.

## 🙋🏻‍♀️ Macros sobre usuários

### 👩🏻‍💻 4.cargaUsuarios
- O ponto de partida dessa macro é o sistema SIP, menu `Usuários` > `Listar`;
- O arquivo de referência é o `exemploUsuários.csv`, cuja estrutura está detalhada acima, nas informações sobre a macro `1.cargaUnidades`.


### 🪪 Macro 5.permissões
- A macro de permissões trata o uso de * para unidade global e faz uma conversão interna para evitar falhas, trocando o asterisco, que gera erro de comportamento da macro pelo termo index=1. Foi uma solução adotada para evitar erros de permissionamento no caso de acesso à unidade global.

## 📄 Licença

Este repositório é disponibilizado sob a [Licença Creative Commons (CC BY-NC-SA 4.0)](LICENSE).

## 📫 Contato

Dúvidas ou sugestões? Abra uma [Issue](https://github.com/pengovbr/pen-docs/issues) ou entre em contato conosco por meio da [Central de Atendimento do PEN](https://portaldeservicos.gestao.gov.br).

