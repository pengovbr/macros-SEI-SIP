# 📋 Macros UiVision para Cadastramento no SEI/SIP

Este repositório contém um conjunto de macros desenvolvidas para automatizar tarefas recorrentes no Sistema de Informações do Processo Eletrônico Nacional (SEI/SIP), como o cadastramento de usuários, perfis e unidades, utilizando a ferramenta UiVision RPA.

## 🚀 Objetivo

Automatizar processos administrativos repetitivos no SEI/SIP com segurança e eficiência, reduzindo o esforço manual de operadores e padronizando o carregamento de dados a partir de arquivos CSV.

## 🛠️ Pré-requisitos

- Navegador com extensão UiVision RPA instalada ([Chrome](https://chrome.google.com/webstore/detail/uivision-rpa/ljdobmomdgdljniojadhoplhkpialdid) ou [Firefox](https://addons.mozilla.org/en-US/firefox/addon/uivision-rpa/))
- Arquivo(s) CSV de entrada estruturados conforme instruções específicas de cada macro
- Acesso ao ambiente do SEI/SIP com permissões compatíveis com a operação automatizada

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

## ▶️ Como usar

1. Instale a extensão UiVision RPA no seu navegador.
2. Importe os arquivos `.json` para o UiVision via menu `Manage Macros > Import`.
3. Abra o SEI/SIP no navegador e acesse o menu correspondente à macro (ex: "Usuários" > "Listar").
4. Execute a macro desejada.
5. Acompanhe o log da execução e valide o resultado no sistema.

## 📝 Observações

- Os arquivos CSV devem estar no formato esperado por cada macro. Consulte os comentários internos de cada script para detalhes.
- Certifique-se de que os dados de entrada (nomes, e-mails, CPF etc.) estejam validados antes da execução.
- Algumas macros assumem layout e elementos específicos da interface do SEI/SIP. Adapte conforme necessário em caso de alterações na versão do sistema.

## 📄 Licença

Este repositório é disponibilizado sob a [Licença MIT](LICENSE).

## 📫 Contato

Dúvidas ou sugestões? Abra uma [Issue](https://github.com/pengovbr/pen-docs/issues) ou entre em contato conosco por meio da [Central de Atendimento do PEN](https://portaldeservicos.gestao.gov.br).

