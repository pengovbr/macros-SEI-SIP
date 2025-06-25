# 📋 Automação de Cadastros no SEI e SIP com UI.Vision RPA

Este repositório contém um conjunto de macros desenvolvido com a ferramenta UI.Vision RPA para automatizar tarefas recorrentes e manuais relacionadas à configuração e gestão de usuários e unidades organizacionais no Sistema Eletrônico de Informações - SEI. As automações foram desenhadas para facilitar cargas iniciais em massa, bem como agilizar manutenções periódicas.

As macros utilizam arquivos `.csv` como fonte de dados estruturada e realizam, de forma automatizada, a navegação e o preenchimento de campos nos sistemas, interagindo diretamente com a interface. Cada macro trata um tipo específico de informação e segue uma lógica de repetição com mensagens de status e progresso, facilitando o acompanhamento em tempo real da execução.


## 🚀 Objetivo

Automatizar processos administrativos repetitivos no SEI/SIP com segurança e eficiência, reduzindo o esforço manual de operadores e padronizando o carregamento de dados a partir de arquivos CSV.

## 🛠️ Pré-requisitos

- Navegador com extensão UiVision RPA instalada ([Google Chrome](https://chrome.google.com/webstore/detail/uivision-rpa/ljdobmomdgdljniojadhoplhkpialdid) ou [Mozilla Firefox](https://addons.mozilla.org/en-US/firefox/addon/uivision-rpa/)). As macros foram criadas no Google Chrome, mas não deve haver conflito.
- Arquivo(s) CSV de entrada preenchidos conforme estrutura apresentada nos arquivos exemplo.
- Acesso de Administrador aos ambientes do SEI e SIP.

## 📂 Estrutura do Repositório

📁 macros/  
├─ 1.cargaUnidades.json  
├─ 2.hierarquia.json  
├─ 3.dadosUnidadesSEI.json  
├─ 4.cargaUsuarios.json  
├─ 5.permissoes.json  
├─ 6.cargaAssuntos.json  
└📁 csv/  
&nbsp;&nbsp; ├─ exemploUnidades.csv  
&nbsp;&nbsp; ├─ exemploUnidades.csv  
&nbsp;&nbsp; └─ exemploAssuntos.csv  

### Sobre as macros incluídas:

1.	Cadastro de Unidades: Automatiza o registro de unidades administrativas no sistema, com base em sua sigla, descrição e órgão vinculado.
2.	Cadastro das Unidades na Hierarquia: Realiza o vínculo entre as unidades cadastradas, definindo sua posição na estrutura hierárquica.
3.	Cadastro de Dados Complementares das Unidades: Preenche informações adicionais relacionadas às unidades, como tipo, endereço ou outros campos auxiliares.
4.	Cadastro de Usuários: Cria contas de usuários no sistema, utilizando dados como CPF, nome, login e e-mail institucional
5.	Cadastro de Permissões: Atribui as permissões adequadas aos usuários conforme o perfil a ser concedido e a unidade de atuação no sistema.
6.	Cadastro de Assuntos: Preenche as informações referentes aos assuntos que constam das Tabelas de Assunto do SEI, para fins de classificação de processos e documentos e controle da temporalidade.


## ▶️ Como usar

1. Instale a extensão UiVision RPA no seu navegador.
2. Importe os arquivos `.json` para o UiVision via menu `Manage Macros > Import`.
3. Importe o arquivo `.csv` correspondente para utilização na macro.
4. Caso tenha renomeado o arquivo, altere também o valor do campo `Target` da linha onde consta o comando `csvReadArray` na macro, para que corresponda ao arquivo que irá utilizar.
6. Abra o SEI ou SIP no navegador e acesse o menu correspondente à macro (Por exemplo: a macro `4.cargaUsuarios` se inicia no sistema `SIP`, menu `Usuários` > `Listar`). Estes caminhos estão indicados sempre na primeira linha de cada macro.
7. A página  em que a macro será executada deve estar aberta na tela para iniciar sua execução.
8. Execute a macro desejada, clicando em `Play Macro`.
9. Acompanhe o log da execução e valide o resultado no sistema. As macros apresentam quantas linhas foram cadastradas com sucesso ou com falha. Valide a execução por meio de batimento as quantidades de valores cadastrados diante da quantidade de valores existentes no arquivo de referência.

## 📝 Outras orientações e observações

- Os arquivos CSV devem estar no formato esperado por cada macro. Consulte os comentários internos de cada script para detalhes.
- Caso algum termo utilizado no arquivo `.csv` contenha vírgulas, coloque o valor inteiro entre aspas (por exemplo: A `Divisão de Obras, Contratos e Serviços Gerais` deve ser grafada no arquivo `.csv` como `"Divisão de Obras, Contratos e Serviços Gerais"` (com aspas). 
- Certifique-se de que os dados de entrada (nomes, e-mails, CPF etc.) estejam validados antes da execução, para evitar retrabalho posterior.
- Embora bastante incomum, alterações na interface do SEI ou SIP podem impactar os seletores usados (IDs, nomes, posições). Verifique e atualize conforme necessário.

### ⏯️ Linha de Início (Retomada após erro ou pausa)
Todas as macros permitem retomar a execução a partir de uma linha específica do CSV, bastando ajustar a variável de início `i`, logo no início de cada macro no comando `store | 1 | i`. Este valor `1` indica que a macro deve iniciar sua execução pela 1ª linha do CSV. Basta alterar para a linha da qual se deseja retomar, em caso de necessidade. Isso é útil para continuidade após interrupções.

### 💾 Armazenamento das macros
No canto inferior esquerdo de sua interface, o UI.Vision permite que você defina se irá salvar as macros no armazenamento da própria extensão `Local Storage (In Browser)` ou em uma pasta de seu computador `Fyle system (on hard drive)`. Se você utilizar a opção `Local Storage (In Browser)`, você precisará sempre importar novamente o CSV a cada nova alteração ou correção. Se salvas no computador, basta atualizar os arquivos normalmente e clicar em 🗘 _(Reload all resources on hard drive)_ para que as alterações se reflitam na execução das macros.

### 🧾 Visualizando os logs
Recomenda-se que a visualização dos logs (no canto inferior direito da tela, ao lado do botão `Clear`) seja definida com a opção `Echo & Status`, para que as mensagens exibidas sejam apenas aquelas configuradas na criação das macros. As macros foram desenvolvidas para exibir informações de progresso e estimativa de tempo restante, conforme são executadas. A exibição completa (`All`) traz a execução linha a linha de cada macro e pode gerar confusão para usuários não familizarizados com o tema. Neste sentido, sua utilização é recomendada apenas em caso de necessidade de depuração de erros, por usuários experientes.  

> [!TIP]
> **A execução exibe mensagens claras de progresso no log, como, por exemplo:**
> - 📈 Progresso e ⏳ Tempo restante estimado
> - 🔁 Processando item
> - ✅ Sucesso no cadastro
> - ❌ Falha, com a mensagem de erro capturada
> - 🏁 Resumo final com total de registros e número de erros


### 🪪 Macro 5.permissões
A macro de permissões trata o uso de * para unidade global e faz uma conversão interna para evitar falhas, trocando o asterisco, que gera erro de comportamento da macro pelo termo index=1. Foi uma solução adotada para evitar erros de permissionamento no caso de acesso à unidade global.

## 📄 Licença

Este repositório é disponibilizado sob a [Licença Creative Commons (CC BY-NC-SA 4.0)](LICENSE).

## 📫 Contato

Dúvidas ou sugestões? Abra uma [Issue](https://github.com/pengovbr/pen-docs/issues) ou entre em contato conosco por meio da [Central de Atendimento do PEN](https://portaldeservicos.gestao.gov.br).

