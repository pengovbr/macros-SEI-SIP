<img width="1080" height="146" alt="header github macros pen mgi" src="https://github.com/user-attachments/assets/fa151c3a-3073-4c93-bb9d-d179413f7695" />

# Automação de Cadastros no SEI e SIP com macros do UI.Vision RPA

## 📚 Sumário

- [Introdução](#introducao)
- [A quem são destinadas estas macros?](#-a-quem-são-destinadas-estas-macros)
- [Objetivo](#-objetivo)
- [Pré-requisitos](#️-pré-requisitos)
- [Download dos Arquivos](#-download-dos-arquivos)
- [Como usar](#como-usar)
- [Orientações gerais e observações](#-orientações-gerais-e-observações)
- [Cadastramento de Unidades](#unidades)
- [Cadastramento de Usuários](#usuarios)
- [Cadastramento de Assuntos](#assuntos)
- [Cadastramento de Tipos de Processo](#tiposDeProcesso)
- [Demonstração em vídeo](#demo-video)
- [Licença](#-licença)
- [Contato](#contato)

---

<a name="introducao"></a>
## ℹ️ Introdução

Este repositório contém diversas macros desenvolvidas com a ferramenta UI.Vision RPA para automatizar tarefas manuais e recorrentes relacionadas ao cadastro e configuração de usuários, unidades, assuntos e diversos outros itens de parametrização no Sistema Eletrônico de Informações - SEI (e no Sistema de Permissões - SIP). As automações foram desenhadas para facilitar cargas iniciais em massa de novos ambientes e agilizar cenários de mudança, como revisão da estrutura organizacional, admissão de grande quantidade de novos usuários (concursos, mudanças de carreira etc.) ou de entrada em vigor de nova tabela de assuntos etc.

As macros utilizam arquivos `.csv` como fonte de dados estruturada e realizam, de forma automatizada, a navegação e o preenchimento de campos nos sistemas SEI e SIP, interagindo diretamente com a interface de usuário (UI), sem qualquer manipulação de banco de dados, o que torna o processo extremamente seguro em termos de integridade do sistema. Cada macro trata um tipo específico de informação e obedece um padrão de repetição que apresenta mensagens de status e progresso, facilitando o acompanhamento em tempo real da execução.

## 👨‍🔧 A quem são destinadas estas macros? 

Usuários com perfil de Administração do SEI, que tenham acesso ao SIP para cadastro de unidades, hierarquia, usuários, permissões e que tenham permissão para acessar e modificar configurações no menu `Administração` do SEI.

<br/>

## 🎯 Objetivo

### Automatizar processos administrativos repetitivos no SEI/SIP com segurança e eficiência, reduzindo o esforço manual de operadores e padronizando o carregamento de dados a partir de arquivos `.csv`.

> [!WARNING]
> **ATENÇÃO!** As macros disponibilizadas neste repositório foram desenvolvidas para facilitar atividades administrativas repetitivas nos sistemas SEI e SIP, mas devem ser utilizadas com cautela e sob responsabilidade do usuário.
>
> Tenha em mente que **é o seu usuário** (administrador do sistema) que estará logado, realizando todas as operações.
>
> Antes de executar qualquer macro:
> 
> - Verifique cuidadosamente os dados inseridos nos arquivos `.csv`;
> - É **<ins>extremamente recomendado testar as macros em ambiente de homologação</ins>**, para avaliar se estão se comportando como esperado ou se é necessária alguma correção;
> - Certifique-se de que possui perfil adequado e permissões suficientes nos sistemas;
> - Avalie se o comportamento da macro está compatível com a versão do sistema utilizada.
>
> _Os mantenedores deste repositório não se responsabilizam por perdas, inconsistências, danos ou qualquer consequência decorrente do uso incorreto ou não supervisionado destas automações. Ao utilizar os arquivos aqui disponibilizados, você declara estar ciente desses riscos e de que é integralmente responsável pelos dados inseridos e pelas ações executadas._

<br/>

## 🛠️ Pré-requisitos

- Navegador com extensão UiVision RPA instalada ([Google Chrome](https://chrome.google.com/webstore/detail/uivision-rpa/ljdobmomdgdljniojadhoplhkpialdid) ou [Mozilla Firefox](https://addons.mozilla.org/en-US/firefox/addon/uivision-rpa/)). As macros foram criadas no Google Chrome, mas não deve haver conflito.
  - Na lista de extensões do navegador, é recomendável "fixar" o UI.Vision para facilitar o acesso à extensão, clicando no ícone ![image](https://github.com/user-attachments/assets/fae6c779-4018-4558-9180-4277218f15ce) (Fixar) ao lado da extensão. Uma vez fixada, o botão "fixar" fica azul e o ícone da extensão fica visível ao lado da Barra de Endereços.
- Arquivo(s) `.csv` de entrada, preenchidos conforme estrutura apresentada nos arquivos exemplo.
- Acesso de **Administrador** aos ambientes do SEI e SIP.

<br/>

## 📥 Download dos arquivos

Aqui, você pode baixar todos os arquivos do repositório.

> Clique com o botão direito e escolha “Salvar link como...”

Você pode baixar este [📦 arquivo `.zip` com todas as macros e exemplos `.csv`](https://github.com/pengovbr/macros-SEI-SIP/raw/refs/heads/main/macros-SEI-SIP.zip)  

Ou baixar cada um, individualmente, de acordo com sua necessidade:

### 🔧 Macros UI.Vision

📁 `macros-SEI-SIP/`  
├─ [`1.cargaUnidades.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/1.cargaUnidades.json)  
├─ [`2.hierarquia.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/2.hierarquia.json)  
├─ [`3.dadosUnidadesSEI.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/3.dadosUnidadesSEI.json)  
├─ [`4.cargaUsuarios.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/4.cargaUsuarios.json)  
├─ [`5.primeirasPermissoes.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/5.permissoes.json)  
├─ [`6.cargaAssuntos.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/6.cargaAssuntos.json)  
└─[`7.cargaTiposDeProcesso.json`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/7.cargaTiposDeProcesso.json)

### 📑 Arquivos de exemplo `.csv`
└📁 `csv/`  
&nbsp;&nbsp; ├─ [`exemploAssuntos.csv`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploAssuntos.csv)  
&nbsp;&nbsp; ├─ [`exemploUnidades.csv`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploUnidades.csv)  
&nbsp;&nbsp; └─ [`exemploUsuarios.csv`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploUsuarios.csv)  
&nbsp;&nbsp; └─ [`exemploTiposDeProcesso.csv`](https://github.com/pengovbr/macros-SEI-SIP/raw/main/csv/exemploTiposDeProcesso.csv)  

### 🔧 Sobre as macros incluídas:
São 06 (seis) macros, que executam diferentes operações nos sistemas SEI e SIP, conforme detalhado abaixo:
1.	**Cadastro de Unidades no SIP**: Automatiza o registro de unidades administrativas no sistema, com base em sua sigla, descrição e órgão vinculado;
2.	**Cadastro das Unidades na Hierarquia no SIP**: Realiza o vínculo entre as unidades cadastradas, definindo sua posição na estrutura hierárquica;
3.	**Cadastro de Dados Complementares das Unidades no SEI**: Preenche informações adicionais relacionadas às unidades, como tipo, endereço ou outros campos auxiliares;
4.	**Cadastro de Usuários no SIP**: Cria contas de usuários no sistema, utilizando dados como CPF, nome, login e e-mail institucional etc.;
5.	**Cadastro das Primeiras Permissões no SIP**: Atribui as primeiras permissões dos usuários, conforme o perfil a ser concedido e a unidade de atuação no sistema; 
6.	**Cadastro de Assuntos no SEI**: Preenche as informações referentes aos assuntos que constam das Tabelas de Assunto do SEI, para fins de classificação de processos e documentos e controle da temporalidade; e
7.	**Cadastro de Tipos de Processo no SEI**: Preenche as informações dos Tipos de Processo a serm cadastrados no sistema, parametrizando-os com classificação por assunto sugerida, restrição a órgãos e unidades para gerar o Tipo de Processo, níveis de acesso etc.

### 📑 Sobre os arquivos de exemplo em `.csv`:
Estão disponíveis 03 (três) arquivos em formato `.csv` para servir de modelo para preenchimento pelo administrador: 
1. **exemploUnidades**: que traz a estrutura de dados referentes a unidades, para execução das macros `1.cargaUnidades.json`, `2.hierarquia.json ` e `3.dadosUnidadesSEI.json`;
2. **exemploUsuarios**: que traz a estrutura de dados referentes a usuários,  para execução das macros `4.cargaUsuarios.json` e `5.primeirasPermissoes.json `; 
3. **exemploAssuntos**: que traz a estrutura de dados referentes aos assuntos da tabela, para servir de modelo para preenchimento pelo administrador, para execução da macro `6.cargaAssuntos.json `; e
4. **exemploTiposDeProcesso**: que traz a estrutura de dados referente aos Tipos de Processo, para execução da macro `7.cargaTiposDeProcesso.json`

<br/>


<a name="como-usar"></a>
## ▶️ Como usar

### 𝄜 Gerar um arquivo `.csv` de referência
- A primeira etapa de uma atividade de cadastro de um volume grande de dados no SEI ou no SIP é, certamente, gerar um arquivo de referência que tenha todos os dados a serem cadastrados. Normalmente, se utiliza um editor de planilhas para compilar - linha a linha - as informações que serão cadastradas. O arquivo em formato `.csv` nada mais é do que uma conversão da planilha original em um formato compatível com outros sistemas. Partindo dessa lógica, foram gerados os arquivos de exemplo disponíveis neste repositório, que contêm todos os dados necessários aos cadastros e parametrizações do sistema.
- Por outro lado, elaborar um arquivo `.csv` manualmente, no layout do formato, também pode ser **muito** complicado. Se você tiver grandes quantidades de dados nas linhas e colunas, os valores ficam muito próximos e o risco de você se confundir aumenta consideravelmente. Assim, a maneira mais fácil de gerar um `.csv` é a partir da conversão de uma planilha. Recomenda-se, neste caso, utilizar o [editor de planilhas da Google](https://docs.google.com/spreadsheets), porque ele oferece a opção de gerar um arquivo `.csv` com  facilidade. Basta clicar, após gerar a lista de dados a serem cadastrados, em `Arquivo` > `Baixar` > `Valores separados por vírgulas (.csv)` e fazer o download do arquivo para a pasta que você escolher.  

  ![image](https://github.com/user-attachments/assets/be8474d6-c5f5-4c63-9b29-9e0692c86108)

> [!NOTE]
>- _Por que não usar o Microsoft Excel?_ Porque, infelizmente, o Excel usa um padrão de configurações de regionalização no Brasil que:
>    - Usa ponto e vírgula (`;`) ao invés de vírgula (`,`) para separar os valores. Isso quebra por completo a capacidade de leitura do UI.Vision;
>    - Usa a codificação `ISO 8859-1` ao invés da `UTF8` (amplamente mais compatível com diferentes idiomas e símbolos), o que resulta em geração de caracteres desconfigurados, como acentos, cedilhas etc. 

- Os arquivos `.csv` devem estar no formato esperado por cada macro. A primeira linha de cada arquivo exemplo traz um cabeçalho indicando a estrutura de cada `.csv`.
    - Independente do editor utilizado, é recomendável fazer o download do arquivo exemplo que deseja utilizar e modificar (apenas) seu conteúdo, **preservando sua estrutura original**.
  - Caso opte por gerar um arquivo novo, este arquivo deverá ter a **mesma quantidade** de colunas e estas devem estar na **mesma posição** (com relação aos exemplos, descritos [aqui](#unidades), [aqui](#usuarios) e [aqui](#assuntos)) para que as macros funcionem corretamente.

- Caso algum termo utilizado no arquivo `.csv` contenha vírgulas, coloque o valor inteiro entre aspas (por exemplo: A `Divisão de Obras, Contratos e Serviços Gerais` deve ser grafada no arquivo `.csv` como `"Divisão de Obras, Contratos e Serviços Gerais"` (com aspas).

### ↻ Rodar a macro no UI.Vision
1. Acesse o UI.Vision a partir do ícone ![image](https://github.com/user-attachments/assets/3147ce13-d273-4844-9153-07a4bbc1d3c6) ao lado da Barra de Endereços, ou clicando no ícone ![image](https://github.com/user-attachments/assets/c0bdfd3c-d946-4fd8-a879-6a3636d7322f) (Extensões).

2. Uma dica útil para a primeira vez que utilizar o UI.Vision (além de explorar a interface para se familiarizar com os campos e botões) é clicar no botão ![image](https://github.com/user-attachments/assets/709f50d0-f3d3-42b4-af20-a9358aba9601) (_Settings_) e alterar algumas configurações. A opção `Command Interval` pode ser configurada para `Fast (no delay)`. As macros testadas funcionaram bem nessa velocidade. Caso tenha problemas de execução, retorne para uma velocidade mais lenta.  
  ![image](https://github.com/user-attachments/assets/5f3784e7-3687-45de-80d5-7371b0c6c706)
  

 
3. Na tela inicial do Ui.Vision, importe o arquivo `.zip` (para importar todas as macros) ou `.json` (para importar uma macro específica) para o UiVision, clicando no botão ![image](https://github.com/user-attachments/assets/86fd9e48-84ae-4e0a-a97c-4e5e10161b95). Este passo só precisa ser executado uma vez (não é necessário "re-importar" as macros).  
   ![UI Vision-Import-Json](https://github.com/user-attachments/assets/32dc93eb-7c19-4fc4-8112-21ce2396f05a).  
<br/>

  - A(s) macro(s) importada(s) deve(m) aparecer na lista à esquerda da tela.  
![image](https://github.com/user-attachments/assets/903496f3-1dee-40e9-8f75-7c9dd4246482)
3. Importe o arquivo `.csv` correspondente para utilização na macro, clicando em `CSV` e depois em `Import CSV`.
![image](https://github.com/user-attachments/assets/d23265df-eaae-4439-98fe-39ec912c0c59)
 
4. As macros fazem referência aos arquivos de exemplo específicos (`exemploUnidades.csv`, `exemploUsuarios.csv` ou `exemploAssuntos.csv`). Portanto, caso tenha gerado um arquivo com outro nome para servir de referência, **altere também** o valor do campo `Target` da linha onde consta o comando `csvReadArray` na macro, para que corresponda ao arquivo que irá utilizar.
![image](https://github.com/user-attachments/assets/fdbce9bd-2316-4df7-b6b7-0c7c691862bb)

5. Abra o SEI ou SIP no navegador e acesse o menu correspondente à macro (Por exemplo: a macro `4.cargaUsuarios` se inicia no sistema `SIP`, menu `Usuários` > `Listar`). Estes caminhos estão indicados abaixo, nas instruções Macro a Macro, e também são exibidos sempre na primeira linha de cada macro.
6. A página  em que a macro será executada deve estar aberta na tela para iniciar sua execução.
![image](https://github.com/user-attachments/assets/ab4e37dc-bf4a-46d6-86b4-b22a6eccea23)


7. Execute a macro desejada, clicando no botão `Play Macro`.  
![image](https://github.com/user-attachments/assets/7f11b577-351a-480f-8ef2-f8d88aebb805)

8. Acompanhe o log da execução e valide o resultado no sistema. As macros apresentam quantas linhas foram cadastradas com sucesso ou com falha. Valide a execução por meio de batimento entre as quantidades de valores cadastrados e a quantidade de valores existentes no arquivo de referência.  
![image](https://github.com/user-attachments/assets/ab4efc74-33fd-438b-80fe-0281a844a3a6)


<br/>

## 📝 Orientações gerais e observações

### 🧾 Visualizando os logs
- Recomenda-se que a visualização dos logs (no canto inferior direito da tela, ao lado do botão `Clear`) seja definida com a opção `Echo & Status`, para que as mensagens exibidas sejam apenas aquelas configuradas na criação das macros. As macros foram desenvolvidas para exibir informações de progresso e estimativa de tempo restante, conforme são executadas. A exibição completa (`All`) traz a execução linha a linha de cada macro e pode gerar confusão para usuários não familizarizados com o tema. Neste sentido, sua utilização é recomendada apenas em caso de necessidade de depuração de erros, por usuários experientes.  

> [!TIP]
> **O log exibe mensagens claras de progresso, como, por exemplo:**
> - 📈 Progresso e ⏳ Tempo restante estimado ( visível a partir da 4ª execução, para evitar grandes distorções na estimativa)
> - 🔁 Processando item
> - ✅ Sucesso no cadastro
> - ❌ Falha, com a mensagem de erro capturada
> - 🏁 Resumo final com total de registros e número de erros

- Há dois tipos de erros possíveis na reprodução das macros:
  - os erros que ocorrem no SEI ou SIP, que são exibidos pelas macros no `echo`, como parte do resultado da execução (erros previstos);
  - e os erros que ocorrem por falha de execução da própria macro, que são exibidos como **"Error"** e interrompem a execução das macros. Nestes casos, é importante investigar para ver o que causou o erro e o que pode ser feito para sanar o reportado. Alguns erros, como o **"Lost connection to site"** (conexão perdida com o site), por exemplo, podem ser resolvidos com uma reexecução da macro. Outros podem exigir uma revisão do arquivo `.csv` ou revisão das configurações de execução do UI.Vision (botão ![image](https://github.com/user-attachments/assets/38802f7c-b5b1-4766-9cc1-e90fca974597) _Settings_).
- Certifique-se de que os dados de entrada (nomes, siglas, e-mails, CPF etc.) estejam devidamente validados antes da execução, para evitar retrabalho por inconsistência.
- Embora bastante incomuns, alterações na interface do SEI ou SIP podem impactar os seletores usados (IDs, nomes, posições). Verifique e atualize conforme necessário.

### ⬇️ Campos `ID Origem` 
- Estas macros não incluem as informações de `ID Origem` para cadastro de unidades ou de usuários. **Caso faça uso  de informações de ID Origem (<ins>e somente nesse caso</ins>)** - como, por exemplo, em casos de importação de sistemas legados ou importação usuários de sistema de RH -, acrescente uma coluna adicional aos arquivos da seguinte maneira:
  - Para unidades, acrescente a coluna `8.idOrigemUnidade` ao arquivo que você criar com base no `exemploUnidades.csv` e, na macro `1.cargaUnidades`, inclua uma linha abaixo da linha 24 com as seguintes especificações: `Command: type | Target: id=txtIdOrigem |Value: ${unidades[${i}][8]}`.
  - Para usuários, acrescente a coluna `9.idOrigemUsuario` ao arquivo que você criar com base no `exemploUsuarios.csv` e, na macro `4.cargaUsuarios` inclua uma linha abaixo da linha 25 com as seguintes especificações: `Command: type | Target: id=txtIdOrigem |Value: ${usuarios[${i}][9]}`.

### ⏯️ Linha de Início (Retomada após erro ou pausa)
- Todas as macros permitem retomar a execução a partir de uma linha específica do `.csv`, bastando ajustar a variável de início `i`, logo no início de cada macro no comando `store | 1 | i`. Este valor `1` indica que a macro deve iniciar sua execução pela 1ª linha do `.csv`. Basta alterar para a linha da qual se deseja retomar, em caso de necessidade. Isso é útil para continuidade após interrupções.

### 💾 Armazenamento das macros
- No canto inferior esquerdo de sua interface, o UI.Vision permite que você defina se irá salvar as macros no armazenamento da própria extensão `Local Storage (In Browser)` ou em uma pasta de seu computador `Fyle system (on hard drive)`. Se você utilizar a opção `Local Storage (In Browser)`, você precisará sempre importar novamente o `.csv` a cada nova alteração ou correção. Se salvas no computador, basta atualizar os arquivos normalmente e clicar em 🔄 _(Reload all resources on hard drive)_ para que as alterações se reflitam na execução das macros. Neste caso (`Local Storage (In Browser)`), as macros devem ser salvas dentro da pasta do UI.Vision, subpasta `macros` e os arquivos `.csv` devem ser salvos na subpasta `datasources`.
![image](https://github.com/user-attachments/assets/efff66cf-9b8b-40f8-8485-10500e4a8f23) ![image](https://github.com/user-attachments/assets/b04e1201-04b8-45a4-a7a8-8b5057536c86)

<br/>

> [!TIP]
> ### Confira, no final deste **Readme**, uma demonstração em vídeo do uso da macro `1.cargaUnidades`.

<br/>

#### Em seguida, serão abordados os três grandes temas tratados por estas ferramentas: Unidades, usuários e assuntos.  
<br/>

<a name="unidades"></a>
## 🏢 CADASTRAMENTO DE UNIDADES

O arquivo exemploUnidades.csv é utilizado para alimentar as macros `1.cargaUnidades`, `2.hierarquia` e `3.dadosUnidadesSEI`, responsáveis pelo cadastro da estrutura organizacional no SIP/SEI. Ele contém os dados básicos de cada unidade administrativa, sua posição na hierarquia e informações complementares opcionais.

#### Suas colunas são:
0. **Seq.**: Número sequencial (ajuda na orientação linha a linha);  
1. **ORGAO**: Sigla do órgão em que a unidade será cadastrada (deve estar idêntica à sigla do órgão no SIP) - **Campo obrigatório**;  
2. **SIGLA**: Sigla da Unidade a ser cadastrada - **Campo obrigatório**;  
3. **DESCRICAO**: Nome da Unidade a ser cadastrada - **Campo obrigatório**;  
4. **SUPERIOR NA HIERARQUIA**: Unidade imediatamente superior na hierarquia - **Campo obrigatório** (no caso de unidade "raiz", que não possui unidade acima, deve ser deixado em branco);  
5. **EMAIL**: Endereço de e-mail corporativo da unidade;  
6. **USA ENDEREÇO DO ÓRGÃO?**: Campo S/N (Sim ou não) que permite ao administrador utilizar os mesmos dados de contato do órgão para a unidade ou preencher as informações de cada unidade individualmente (útil para órgãos com unidades descentralizadas);
7. **ENDEREÇO DA UNIDADE:** Campo para informar a primeira linha do endereço da unidade, caso informado que esta não usa o mesmo endereço do órgão.
8. **COMPLEMENTO DO ENDEREÇO:** Campo para informar a segunda linha (complemento) do endereço da unidade, caso informado que esta não usa o mesmo endereço do órgão.
9. **BAIRRO DA UNIDADE:** Campo para informar o bairro da unidade, caso informado que esta não usa o mesmo endereço do órgão.
10. **UF DA UNIDADE:** Campo para informar a UF em que está localizada unidade, caso informado que esta não usa o mesmo endereço do órgão.
11. **CIDADE DA UNIDADE:** Campo para informar a Cidade em que está localizada unidade, caso informado que esta não usa o mesmo endereço do órgão.
12. **CEP DA UNIDADE:** Campo para informar o CEP do local da unidade, caso informado que esta não usa o mesmo endereço do órgão.
13. **CNPJ DA UNIDADE:** Campo para informar o CNPJ da unidade;.
14. **TELEFONE DA UNIDADE**: Campo para informar o Telefone da unidade; e  
15. **SITE DA UNIDADE**: Campo para informar o sítio web da unidade.  

#### Exemplo de arquivo `exemploUnidades.csv` em formato de tabela:

| 0-Seq. | 1-orgaoUnidade | 2-siglaUnidade | 3-descricaoUnidade                           | 4-superiorNaHierarquia | 5-emailUnidade                | 6-usaEndereçoDoÓrgao? | 7-endereçoUnidade                                  | 8-complementoEndereco     | 9-bairroUnidade | 10-UFUnidade | 11-cidadeUnidade | 12-CEPUnidade | 13-CNPJUnidade | 14-telefoneUnidade | 15-siteUnidade                              |
|--------|----------------|----------------|----------------------------------------------|-------------------------|-------------------------------|------------------------|-----------------------------------------------------|----------------------------|------------------|---------------|-------------------|----------------|----------------|---------------------|---------------------------------------------|
| 1      | GOV-CR         | GABIN          | gabinete                                     |                         | governador@cariris.gov.br     | S                      |                                                     |                            |                  |               |                   |                |                | (61)2345-6789       | https://governo.cr.gov.br/                 |
| 2      | GOV-CR         | ASIMP          | Assessoria de Imprensa                       | GABIN                   | imprensa@cariris.gov.br       | S                      |                                                     |                            |                  |               |                   |                |                | (61)2345-6789       | https://governo.cr.gov.br/                 |
| 3      | GOV-CR         | PROJUR         | Procuradoria Estadual                        | GABIN                   | procuradoria@cariris.gov.br   | S                      |                                                     |                            |                  |               |                   |                |                | (61)2345-6789       | https://governo.cr.gov.br/                 |
| 4      | GOV-CR         | ESPRE          | Escritório de Projetos estratégicos          |                         | projetos@cariris.gov.br       | S                      |                                                     |                            |                  |               |                   |                |                | (61)2345-6789       | https://governo.cr.gov.br/                 |
| 5      | GOV-CR         | SETIN          | Secretaria de Transformação Digital e Inovação |                         | setin@cariris.gov.br          | N                      | Avenida 123, Área Especial 456, Palácio de Governo  | Bloco C, Sala 253-A       | Centro           | CR            | Esperança         | 59900-000      |                | (61)2345-6543       | https://governo.cr.gov.br/inovacao         |
| 6      | GOV-CR         | SUTEC          | Subsecretaria de Tecnologia e Infraestrutura | SETIN                   | sutec@cariris.gov.br          | N                      | Avenida 123, Área Especial 456, Palácio de Governo  | Bloco C, Sala 253         | Centro           | CR            | Esperança         | 59900-000      |                | (61)2345-6543       | https://governo.cr.gov.br/inovacao         |
| 7      | GOV-CR         | SUINV          | Subsecretaria de Inovação                    | SETIN                   | suinv@cariris.gov.br          | N                      | Avenida 123, Área Especial 456, Palácio de Governo  | Bloco C, Sala 255         | Centro           | CR            | Esperança         | 59900-000      |                | (61)2345-6543       | https://governo.cr.gov.br/inovacao         |


#### Formato `.csv` correspondente:

> 0-Seq.,1-orgaoUnidade,2-siglaUnidade,3-descricaoUnidade,4-superiorNaHierarquia,5-emailUnidade,6-usaEndereçoDoÓrgao?,7-endereçoUnidade,8-complementoEndereco,9-bairroUnidade,10-UFUnidade,11-cidadeUnidade,12-CEPUnidade,13-CNPJUnidade,14-telefoneUnidade,15-siteUnidade
> 1,GOV-CR,GABIN,gabinete,,governador@cariris.gov.br,S,,,,,,,,(61)2345-6789,https://governo.cr.gov.br/
> 2,GOV-CR,ASIMP,Assessoria de Imprensa,GABIN,imprensa@cariris.gov.br,S,,,,,,,,(61)2345-6789,https://governo.cr.gov.br/
> 3,GOV-CR,PROJUR,Procuradoria Estadual,GABIN,procuradoria@cariris.gov.br,S,,,,,,,,(61)2345-6789,https://governo.cr.gov.br/
> 4,GOV-CR,ESPRE,Escritório de Projetos estratégicos,,projetos@cariris.gov.br,S,,,,,,,,(61)2345-6789,https://governo.cr.gov.br/
> 5,GOV-CR,SETIN,Secretaria de Transformação Digital e Inovação,,setin@cariris.gov.br,N,"Avenida 123, Área Especial 456, Palácio de Governo","Bloco C, Sala 253-A",Centro,CR,Esperança,59900-000,,(61)2345-6543,https://governo.cr.gov.br/inovacao
> 6,GOV-CR,SUTEC,Subsecretaria de Tecnologia e Infraestrutura,SETIN,sutec@cariris.gov.br,N,"Avenida 123, Área Especial 456, Palácio de Governo","Bloco C, Sala 253",Centro,CR,Esperança,59900-000,,(61)2345-6543,https://governo.cr.gov.br/inovacao
> 7,GOV-CR,SUINV,Subsecretaria de Inovação,SETIN,suinv@cariris.gov.br,N,"Avenida 123, Área Especial 456, Palácio de Governo","Bloco C, Sala 255",Centro,CR,Esperança,59900-000,,(61)2345-6543,https://governo.cr.gov.br/inovacao


> [!NOTE]
> Veja como são usadas aspas para isolar conteúdo que tenha vírgulas originalmente.  
> Repare também que as unidades `UNI1` e `UNI2` são unidades "raiz", e portanto nada foi inserido na coluna `SUPERIOR.NA.HIERARQUIA`. O arquivo `.csv` traz duas vírgulas seguidas para mostrar que o campo foi deixado em branco.

### Pontos de atenção sobre as macros referentes a Unidades: 

### 🏤 Macro `1.cargaUnidades`
- O ponto de partida dessa macro é o sistema SIP, menu `Unidades` > `Listar`;
- O arquivo de referência é o `exemploUnidades.csv`, cuja estrutura está detalhada acima;
- As colunas `1-ORGÃO`,`2-SIGLA` e `3-DESCRICAO` são utilizadas por esta macro. As demais são usadas pelas macros posteriores; 

### 🖧 Macro `2.hierarquia`
- O ponto de partida dessa macro é o sistema SIP, menu `Hierarquias` > `Montar` > Hierarquia `SEI` > `Pesquisar`;
- O arquivo de referência é o `exemploUnidades.csv`, cuja estrutura está detalhada acima.
- As colunas `1-ORGÃO`,`2-SIGLA` e `4-SUPERIOR.NA.HIERARQUIA` são utilizadas por esta macro. As demais são usadas pelas macros posteriores.

> [!IMPORTANT]
> - As linhas que trazem a coluna `4-SUPERIOR.NA.HIERARQUIA` em branco indicam que se trata de uma unidade _"Raiz"_, ou seja, que não possui nenhuma unidade acima de si na hierarquia. As demais linhas devem trazer a unidade imediatamente superior a elas para cadastramento na hierarquia.
> - Por isso, é importante ter em mente que a hierarquia deve ser cadastrada <ins>**de cima para baixo**</ins>. Ou seja, primeiro devem ser inseridos na planilha os níveis mais altos da estrutura organizacional e depois os que vierem abaixo destes. Isso evita que o SIP retorne mensagem de erro informando que a unidade superior não foi encontrada ou travamento da macro.
- Esta macro executa um script para atribuir ao campo "Data de Início" da unidade na hierarquia com a data atual (dia em que a macro está sendo executada). Caso opte por utilizar outra data, "comente" a linha 32 da macro (clicando em `//`) e altere o teor do campo `value` da linha 33, em que consta `${dataHoje}` para a data que deseja fazer constar.

### 🎛️ Macro `3.dadosUnidadesSEI`
- O ponto de partida dessa macro é o sistema SEI, menu `Administração` > `Unidades` > `Listar`;
- O arquivo de referência é o `exemploUnidades.csv`, cuja estrutura está detalhada acima.
- Esta macro utiliza a funcionalidade `Usar endereço associado` da Administração do SEI, que faz com que o  endereço do órgão seja adotado para suas unidades. Caso tenha necessidade de cadastrar dados individualizados por unidade, [registre uma issue](https://github.com/pengovbr/macros-SEI-SIP/issues/new/choose) sugerindo esta melhoria.

<br/>


<a name="usuarios"></a>
## 🙋🏻‍♀️ CADASTRAMENTO DE USUÁRIOS
O arquivo `exemploUsuarios.csv` é utilizado para alimentar as macros `4.cargaUsuarios` e `5.primeirasPermissoes`, responsáveis pelo cadastro de usuários e concessão de suas permissões iniciais no SIP/SEI. Ele contempla dados de identificação, CPF, e-mail e dados das primeiras permissões para viabilizar acesso ao SEI para os usuários.

#### Suas colunas são:
0. **Index**: Número sequencial (ajuda na orientação linha a linha);  
1. **Orgao**: Sigla do órgão em que o usuário será cadastrado (deve estar idêntica à sigla do órgão no SIP) - Campo obrigatório;  
2. **Sigla**: Sigla do Usuário a ser cadastrado - Campo obrigatório;  
3. **Nome**: Nome do Usuário a ser cadastrado - Campo obrigatório;  
4. **Nome Social**: Nome pelo qual a pessoa transgênero ou não-binária deseja ser reconhecida e tratada;  
5. **CPF**: Cadastro de Pessoa Física do Usuário - embora _não obrigatório_, pode ser usado para autenticação GOV.BR;
6. **E-mail Institucional**: E-mail institucional do usuário - embora _não obrigatório_, pode ser usado para autenticação via SSO;
7. **unidadePrimeiraPermissao**: Unidade na qual o usuário deve receber a primeira permissão, viabilizando seu acesso ao SEI; e
8. **perfilPrimeiraPermissao**: perfil a ser dado ao usuário na unidade da primeira permissão.

#### Exemplo de arquivo `exemploUsuarios.csv` em formato de tabela:

|0.Index|1.Orgao | 2.Sigla                | 3.Nome                      | 4.Nome Social              | 5.CPF          | 6.E-mail institucional                | 7.unidadePrimeiraPermissao| 8.perfilPrimeiraPermissao               |
|-------|--------|------------------------|-----------------------------|----------------------------|----------------|---------------------------------------|---------------------------|-----------------------------------------|
| 1     | ORGAO1 | leocadio.macambira     | Leocádio Macambira          |                            | 118.229.998-98 | leocadio.macambira@orgao1.gov         | UNI1                      | Básico                                  |
| 2     | ORGAO1 | tertuliano.gongora     | "Tertuliano Gongora, Msc."  |                            | 124.039.082-31 | tertuliano.gongora@orgao1.gov         | UNI1.1                    | Básico                                  |
| 3     | ORGAO1 | belarmina.batatinha    | Belarmina Batatinha         |                            | 147.551.240-69 | belarmina.batatinha@orgao1.gov        | UNI2                      | Colaborador (Básico sem Assinatura)     |
| 4     | ORGAO1 | zildette.brazil        | Raimundo Nonato da Silva    |   Zildette Brazil          | 836.508.748-06 | zildette.brazil@orgao1.gov            | UNI1.2                    | Colaborador (Básico sem Assinatura)     |
| 5     | ORGAO1 | ursula.trigueirinho    | Úrsula Trigueirinho         |                            | 065.697.139-81 | ursula.trigueirinho@orgao1.govr       | UNI1.2.1                  | Básico                                  |
| ...   |||||||  

#### Formato `.csv` correspondente:
> 0Index,1Orgao,2Sigla,3Nome,4Nome Social,5CPF,6E-mail institucional,7unidadePrimeiraPermissao,8perfilPrimeiraPermissao  
> 1,ORGAO1,leocadio.macambira,Leocádio Macambira,,118.229.998-98,leocadio.macambira@orgao1.gov,UNI1,Básico  
> 2,ORGAO1,tertuliano.gongora,"Tertuliano Gongora, Msc.",,124.039.082-31,tertuliano.gongora@orgao1.gov,UNI1.1,Básico  
> 3,ORGAO1,belarmina.batatinha,Belarmina Batatinha,,147.551.240-69,belarmina.batatinha@orgao1.gov,UNI21,Colaborador (Básico sem Assinatura)  
> 4,ORGAO1,zildette.brazil,Raimundo Nonato da Silva,Zildette Brazil,836.508.748-06,zildette.brazil@orgao1.gov,UNI1.2,Colaborador (Básico sem Assinatura)  
> 5,ORGAO1,ursula.trigueirinho,Úrsula Trigueirinho,,065.697.139-81,ursula.trigueirinho@orgao1.gov,UNI1.2.1,Básico  

> [!NOTE]
> - A coluna `Nome Social` diz respeito ao nome pelo qual a pessoa transgênero ou não-binária deseja ser reconhecida e tratada, em vez do nome registrado oficialmente, com base no Decreto nº 8.727/2016 ou legislação correlata. **Não deve** ser utilizada para cadastro de nome artístico, pseudônimo, nome político ou nome de fantasia de empresa representada.  
> - A ideia das colunas 7 e 8 é viabilizar o acesso dos usuários ao SEI, cadastrando as **primeiras** permissões. Outras permissões devem ser cadastradas posteriormente pelo administrador (Recomenda-se, a título de agilidade, utilizar a funcionalidade `Atribuição em Bloco` no menu `Permissões` do SIP).

### Pontos de atenção sobre as macros referentes a Usuários:

### <img width="24" height="24" alt="image" src="https://github.com/user-attachments/assets/cb5a8743-27fc-4a5a-9423-a9e3a12a6a2b" /> Macro `4.cargaUsuarios`
- O ponto de partida dessa macro é o sistema SIP, menu `Usuários` > `Listar`;
- O arquivo de referência é o `exemploUsuários.csv`, cuja estrutura está detalhada acima.


### <img width="24" height="24" alt="image" src="https://github.com/user-attachments/assets/50e5b32b-cd6c-415e-b62f-2735f2fc5ad3" /> Macro `5.permissões`
- O ponto de partida dessa macro é o sistema SIP, menu `Permissões` > `Atribuição em Bloco`;
- A macro de permissões trata o uso de `*` para a Unidade Global por meio de uma conversão interna para evitar falhas, trocando o asterisco (que gera erro de comportamento na macro) pelo termo `index=1`. Foi uma solução adotada para evitar erros de permissionamento no caso de acesso à unidade global.
- Como dito anteriormente, a proposta, neste caso, é apenas cadastrar uma **primeira permissão** para viabilizar o acesso ao SEI para o usuário cadastrado, e não esgotar todas as suas permissões. Estas podem ser cadastradas posteriormente, com o sistema já em uso pelos usuários.
- Esta macro utiliza comandos `pause` para gerar pequenos tempos de espera - gravados em `ms` (milissegundos), necessários ao carregamento de informações em listas "dependentes" (ou seja, situações em que os itens da lista de um nível abaixo variam de acordo com a escolha no nível superior). Se necessário, edite estes valores para mais ou para menos para otimizar seu funcionamento.

<br/>


<a name="assuntos"></a>
## 🗄️CADASTRAMENTO DE ASSUNTOS
O arquivo `exemploAssuntos.csv` é utilizado para alimentar a macro `6.cargaAssuntos`, responsável pelo cadastro dos assuntos da Tabela de Assuntos do SEI, com base no Código de Classificação de Documentos (CCD) e na Tabela de Temporalidade e Destinação (TTD).

#### Suas colunas são:
0. **Index:** Número sequencial (auxilia na identificação linha a linha durante a execução da macro).  
1. **CodigoEstruturado:** Código de Classificação de Documentos (CCD), que estrutura os assuntos conforme as funções da instituição. A hierarquia é implícita no código, sem necessidade de definir assunto hierarquicamente superior.  
2. **NomeAssunto:** Nome do assunto conforme o CCD.  
3. **chkEstrutural:** Indica se o item é apenas estrutural (valor S). Assuntos estruturais não são selecionáveis na hora de classificar documentos, servindo apenas como agrupadores.  
4. **PrazoCorrente:** Prazo em anos de guarda na fase corrente, conforme a TTD.  
5. **PrazoIntermed:** Prazo em anos de guarda na fase intermediária.  
6. **Destinacao:** Destinação final do documento: Guarda Permanente ou Eliminação.  
7. **Obs:** Campo livre para observações manuais.  

#### Exemplo de arquivo `exemploAssuntos.csv` em formato de tabela:

| 0.Index | 1.CodigoEstruturado  | 2.NomeAssunto                 | 3.chkEstrutural  | 4.PrazoCorrente  | 5.PrazoIntermed  | 6.Destinacao      | 7.Obs                        |
|---------|----------------------|-------------------------------|------------------|------------------|------------------|-------------------|------------------------------|
| 1       | 020.01               | Atividades Acadêmicas         | S                |                  |                  |                   | Exemplo de observação        |
| 2       | 020.01.01            | Projetos de Pesquisa          |                  | 5                | 10               | Guarda            | Pendente validação           |
| 3       | 020.01.02            | Eventos Acadêmicos            |                  | 3                | 2                | Eliminação        |                              |
| 4       | 020.02               | Ensino                        | S                |                  |                  |                   | Pendente validação           |
| 5       | 020.02.01            | Planos de Ensino              |                  | 2                | 3                | Eliminação        |                              |


#### Formato `.csv` correspondente:
> 0.Index,1.CodigoEstruturado,2.NomeAssunto,3.chkEstrutural,4.PrazoCorrente,5.PrazoIntermed,6.Destinacao,7.Obs  
> 1,020.01,Atividades Acadêmicas,S,,,,Exemplo de observação  
> 2,020.01.01,Projetos de Pesquisa,,5,10,Guarda Permanente,Pendente validação  
> 3,020.01.02,Eventos Acadêmicos,,3,2,Eliminação,  
> 4,020.02,Ensino,S,,,,Pendente validação  
> 5,020.02.01,Planos de Ensino,,2,3,Eliminação,  
  
### Pontos de atenção sobre a macro referentes a Assuntos:

### 🗃️ Macro `6.assuntos`
- O ponto de partida dessa macro é o sistema SEI, menu `Administração` > `Tabelas de Assunto` > [Escolher a tabela desejada] >`Assuntos da Tabela`;
- O arquivo de referência é o `exemploAssuntos.csv`, cuja estrutura está detalhada acima.
- O log desta macro traz informações de progresso e detalha cada assunto carregado (informa se é apenas estrutural ou, se não, quais os prazos e qual a destinação associada a este assunto).
<br/>
<br/>

<a name="tiposDeProcesso"></a>
## 🗂️ CADASTRAMENTO DE TIPOS DE PROCESSO  

O arquivo `exemploTiposDeProcesso.csv` é utilizado para alimentar a macro `7.cargaTiposDeProcesso`, responsável pelo cadastro dos Tipos de Processo no SEI. Ele inclui informações diversas, como a Classificação por Assunto sugerida, os órgãos e unidades a que se deseja restringir a criação de processos desse tipo, os níveis de acesso permitidos e sugeridos (os sugeridos se aplicam a sistemas integrados via Webservice e módulos), dentre outras funcionalidades.

#### Suas colunas são:
0. **Seq:** Número sequencial (auxilia na identificação linha a linha na execução da macro).  
1. **Nome:** Nome do tipo de processo a ser criado.
2. **descricao:** Descrição complementar do tipo de processo (campo opcional).  
3. **sugestaoDeAssuntos:** Lista de códigos de assuntos sugeridos para este tipo (separados por ponto e vírgula).  
4. **restringirAosOrgaos:** Lista de siglas de órgãos autorizados a utilizar o tipo (separados por ponto e vírgula). **Deixe em branco** para liberar para todos.  
5. **restringirAsUnidades:** Lista de siglas de unidades de cada órgão, autorizadas a utilizar o tipo (separadas da seguinte maneira ORGAO-A:UNIDADE1|UNIDADE2|UNIDADE3;ORGAO-B:UNIDADE4|UNIDADE5|UNIDADE6). **Deixe em branco** para liberar para todas.  
6. **niveisDeAcessoPermitidos:** Lista dos níveis de acesso permitidos, sendo **"RES"** para Restrito, **"SIG"** para Sigiloso e **"PUB"** para Público.  
7. **nivelDeAcessoSugerido:** Nível de acesso sugerido (obrigatório ser um dos valores da lista anterior).  
8. **grauSigilo:** É o grau de sigilo sugerido para este Tipo de Processo, quando sigiloso, podendo ser **"U"** para Ultrassecreto, **"S"** para Secreto e **"R"** para Reservado.  
9. **sugestaoHipoteseLegal:** Hipótese legal sugerida (O ).  
10. **exclusivoOuvidoria:** Indica se o tipo será exclusivo da Ouvidoria (S ou deixe em branco).  
11. **permiteContatoAnonimo:** Se marcado como S, permite abertura de processo sem identificação (só se for exclusivo da ouvidoria).  
12. **ProcessoUnicoPorInteressado:** Indica se só poderá existir um processo desse tipo por interessado (S ou em branco).  
13. **InternoDoSistema:** Indica se o tipo de processo será usado apenas internamente, sem visibilidade para usuários comuns (S ou em branco).  


#### Visão do arquivo `exemplo.csv` em formato de tabela:

| 0.Seq | 1.Nome                                                                                      | 2.descricao                                                              | 3.sugestaoDeAssuntos | 4.restringirAosOrgaos | 5.restringirAsUnidades                    | 6.NiveisDeAcessoPermitidos | 7.NivelDeAcessoSugerido | 8.GrauSigilo | 9.sugestaoHipoteseLegal                                                                                       | 10.exclusivoOuvidoria | 11.permiteContatoAnonimo(ouvidoria) | 12.ProcessoUnicoPorInteressado | 13.InternoDoSistema |
|-------|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|----------------------|-----------------------|--------------------------------------------|---------------------------|------------------------|--------------|--------------------------------------------------------------------------------------------------------------|-----------------------|-------------------------------------|---------------------------------|---------------------|
| 1     | Comunicação: Serviço De Transmissão De Dados, Voz E Imagem                                 | Processo relacionado a serviço de transmissão de dados, voz e imagem.    | 073.4                | PEN;SBM               | PEN:ADMIN&#124;NEG;SBM:GABPREF&#124;SEDUC  | PUB;RES                   | RES                    |              | Protocolo Pendente de Análise de Restrição (Art. 6º, III, da Lei nº 12.527/2011)                              |                       |                                     |                                 |                     |
| 2     | Gestão de Contrato: Cadastramento De Fornecedores E De Prestadores De Serviços              | Processo relacionado a cadastramento de fornecedores e de prestadores.   | 030.02               | PEN;SBM               |                                            | PUB;RES;SIG               | SIG                    | R            | Informação Pessoal Sensível (Art. 31 da Lei nº 12.527/2011)                                                   |                       |                                     |                                 |                     |
| 3     | Capacitação: Contratação de curso com ônus à Instituição                                   | Processo relacionado a com ônus.                                          | 028.21               |                       |                                            | PUB                       | PUB                    |              |                                                                                                              |                       |                                     |                                 |                     |
| 4     | Pessoal: Avaliação de Desempenho                                                            | Processo relacionado a desempenho.                                       | 23.155               | SBM;PEN               | SBM:GABPREF;PEN:ADMIN                      | PUB;RES                   | RES                    |              | Investigação/Prevenção de Acidentes Aeronáuticos (Art. 88-I, § 3º, da Lei nº 7.565/1986)                      | SIM                   | SIM                                 |                                 |                     |
| 5     | Pessoal: Emissão De Certificados                                                            | Processo relacionado a emissão de certificados.                          | 914                  |                       |                                            | PUB;RES                   | RES                    |              | Sigilo de Empresa em Situação Falimentar (Art. 169 da Lei nº 11.101/2005)                                     | SIM                   |                                     |                                 |                     |



#### Formato `.csv` correspondente:
> 0.Seq,1.Nome,2.descricao,3.sugestaoDeAssuntos,4.restringirAosOrgaos,5.restringirAsUnidades,6.NiveisDeAcessoPermitidos,7.NivelDeAcessoSugerido,8.GrauSigilo,9.sugestaoHipoteseLegal,10.exclusivoOuvidoria,11.permiteContatoAnonimo(ouvidoria),12.ProcessoUnicoPorInteressado,13.InternoDoSistema  
> 1,"Comunicação: Serviço De Transmissão De Dados, Voz E Imagem","Processo relacionado a serviço de transmissão de dados, voz e imagem.",073.4,PEN;SBM,"PEN:ADMIN|NEG;SBM:GABPREF|SEDUC","PUB;RES",RES,,"Protocolo Pendente de Análise de Restrição (Art. 6º, III, da Lei nº > 12.527/2011)",,,,  
> 2,"Gestão de Contrato: Cadastramento De Fornecedores E De Prestadores De Serviços","Processo relacionado a cadastramento de fornecedores e de prestadores de serviços.",030.02,PEN;SBM,,"PUB;RES;SIG",SIG,R,"Informação Pessoal Sensível (Art. 31 da Lei nº 12.527/2011)",,,,  
> 3,"Capacitação: Contratação de curso com ônus à Instituição","Processo relacionado a com ônus.",028.21,,,PUB,PUB,,,,,,  
> 4,"Pessoal: Avaliação de Desempenho","Processo relacionado a desempenho.",23.155,SBM;PEN,"SBM:GABPREF;PEN:ADMIN","PUB;RES",RES,,"Investigação/Prevenção de Acidentes Aeronáuticos (Art. 88-I, § 3º, da Lei nº 7.565/1986)",SIM,SIM,,  
> 5,"Pessoal: Emissão De Certificados","Processo relacionado a emissão de certificados.",914,,,PUB;RES,RES,,"Sigilo de Empresa em Situação Falimentar (Art. 169 da Lei nº 11.101/2005)",SIM,,,  

  
### Pontos de atenção sobre a macro referentes a Tipos de Processo:

### <img width="24" height="24" alt="image" src="https://github.com/user-attachments/assets/9544de43-9ff6-4d5b-a530-eb5500e9bf47" /> Macro `6.assuntos`
- O ponto de partida dessa macro é o sistema SEI, menu `Administração` > `Tipos de Processo`;
- O arquivo de referência é o `exemploTiposDePRocesso.csv`, cuja estrutura está detalhada acima.
- O log desta macro traz informações de progresso e detalha cada Tipo de Processo carregado (informando se a criação de processos desse tipo está limitada a determinado órgão ou unidade).
> [!NOTE]
> - Por se tratar de uma macro que alterna bastante entre diferentes modais (janelas auxiliares de seleção), há um risco maior de falha de execução. Neste caso, basta retomar a execução da macro da linha em que ela foi interrompida, alterando o valor na linha 3 `store|1|i`, alterando o valor `1` pelo número da linha da qual deseja retomar.
> - Os campos de limitação a órgãos e unidades são de uso facultativo. Caso deseje que os Tipos de Processo estejam disponíveis para todas as unidades de todos os órgãos de sua instalação, deixe-os em branco.
<br/>
<br/>


---


<a name="demo-video"></a>
### 🎬 Vídeo com contextualização e demonstração de uso da macro `1.cargaUnidades`

_Clique na imagem com o botão direito e abra o link em nova aba, caso precise manter esta aberta._

[![video-macros-mini](https://github.com/user-attachments/assets/591f5eec-712d-4373-a385-70e9672a1f9d)](https://youtu.be/uYujObEl0RY)



---


<a name="contato"></a>
## 📫 Contato

Dificuldades, dúvidas ou sugestões? [Abra uma Issue](https://github.com/pengovbr/macros-SEI-SIP/issues/new/choose) ou entre em contato conosco por meio da [Central de Atendimento do PEN](https://portaldeservicos.gestao.gov.br).

## 📄 Licença

Este repositório é disponibilizado sob a [Licença Creative Commons CC BY-NC-SA 4.0](https://github.com/pengovbr/macros-SEI-SIP/blob/main/LICENSE.md).
