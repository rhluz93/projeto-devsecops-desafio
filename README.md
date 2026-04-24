# Desafio DevSecOps — Gerenciador de Tarefas

## Sobre o Projeto
O projeto consistia em fazer um aplicativo web que possuia vulnerabilidades propositais e uma pipeline incompleta.
O objetivo deste projeto foi implementar a pipeline de segurança e corrigir as vulnerabilidades, garantindo que nenhum código chegasse à produção sem passar pelos gates (portões) de segurança.

## Estado atual
A pipeline está completa e funcional. Todos os steps de segurança foram implementados e as vulnerabilidades do código foram corrigidas.

## Sua missão
1. Implementar os steps de segurança no `pipeline.yml`
2. Fazer a pipeline **quebrar** ao detectar os problemas
3. Corrigir as vulnerabilidades encontradas
4. Fazer a pipeline **passar** com tudo verde ✅
5. Documentar o funcionamento da pipeline neste README

## O que foi implementado
- [X] Secrets Scanning com **Gitleaks**
- [X] SAST com **Semgrep**
- [X] SCA com **Grype**
- [X] Deploy com **GitHub Pages**

## Como a pipeline funciona
Na pipeline implementada, o deploy para produção só ocorre se todos os steps de segurança passarem sem erros.

A pipeline inicia baixando o código do repositório para o ambiente de execução e realiza uma verificação básica, listando os arquivos da pasta `src/`. Isso garante que o ambiente tenha acesso aos arquivos mais recentes para análise.

O Gitleaks varre o código e o histórico de commits em busca de segredos expostos, como chaves de API, tokens de acesso, senhas e certificados. Isso é importate, pois credenciais vazadas em repositórios públicos ou privados podem ser rapidamente capturadas por atacantes para acessar sistemas, bancos de dados e serviços em nuvem, causando vazamentos de dados. O Gitleaks previne que esses segredos sejam desvendados ou cheguem à produção. Dessa forma realizamos o ajuste necessário, fazendo a alteração de comandos(`API_KEY` e `DB_PASSWORD`) do arquivo `script.js`.

O SAST(Static Application Security Testing) analisa o código estaticamente, sem executá-lo, em busca de padrões inseguros, bugs e vulnerabilidades clássicas. O SAST ajuda os desenvolvedores a escreverem códigos mais seguros desde o início.

O SCA Grype verifica todas as dependências e bibliotecas do projeto em busca de vulnerabilidades conhecidas. A pipeline foi configurada para falhar caso encontrasse vulnerabilidades de severidade média ou superior.

Após todos os steps de segurança passarem com sucesso (o "sinal verde"), a pipeline empacota a pasta `src/` e realiza o deploy automático da aplicação utilizando o GitHub Pages. Apresentando mensagem final "Conectado ao Banco de Dados", mostrando que o job foi feito e concluido de forma correta.



## URL de Produção
https://github.com/rhluz93/projeto-devsecops-desafio
https://rhluz93.github.io/projeto-devsecops-desafio/
