# Relatório — Encurtador de URL

## Viabilidade

- Grupo: Dupla 01
- Integrantes: Wellington Menezes e Lucas Gonçalves Amaral
- Repositório: https://github.com/wellingtonfpo/url-short
- Stack: TypeScript, NestJS, React, PostgreSQL e Visual Studio Code.
- Veredito: Viável

O fluxo cabe no prazo: colar uma URL longa, receber um código curto e redirecionar. Login e histórico são um segundo corte, não a primeira spec. A justificativa ainda não explica por que NestJS, React e PostgreSQL juntos.

## SWOT

### Forças

Problema e resultado cabem em uma frase. O domínio tem regras testáveis: código único, redirecionamento e recusa de URL inválida. A stack é uma só linguagem.

### Fraquezas

A justificativa fala em “problema real para usar SDD” e não amarra a arquitetura. Login, histórico e banco entram antes do redirecionamento existir.

### Oportunidades

Entregar primeiro o encurtamento anônimo e o redirect. Histórico por usuário fica para depois, se a spec do núcleo estiver estável. Claude Code serve como agente da disciplina sem fazer parte do produto.

### Ameaças

Autenticação consome as semanas de spec e implementação. Códigos previsíveis e URLs maliciosas precisam de regra explícita, senão o projeto vira discussão de segurança sem produto.

## Stack técnica

**Parecer: Adequada.** A stack TypeScript com NestJS, React e PostgreSQL serve ao encurtador; se a dupla quiser menos peças para operar, Next.js com um banco leve cobre o mesmo fluxo.

A combinação proposta é coerente: uma linguagem só, uma API no NestJS, uma tela em React e um banco que guarda o par código-endereço. Isso consegue implementar o redirecionamento, recusar URL inválida e impedir código repetido. Não há motivo para trocar a stack.

O custo está na quantidade de processos. NestJS e React são dois projetos para subir, configurar e manter em dupla. Para este domínio, o PostgreSQL também é mais do que o volume de dados pede. Se a constitution ficar pesada, a alternativa mais simples, ainda em TypeScript, é Next.js: a tela e a rota de redirect ficam no mesmo projeto, e SQLite ou o próprio PostgreSQL guarda os códigos. Claude Code continua como agente de desenvolvimento, não como componente do produto.

## Recomendação

**Especifiquem primeiro só o encurtamento e o redirecionamento, e deixem login e histórico para quando esse caminho já funcionar.**

A ideia do encurtador já é suficiente para a disciplina, desde que a dupla trate o login como uma etapa posterior. Na constitution, o sistema precisa fazer uma coisa de ponta a ponta: a pessoa cola um endereço longo, recebe um código curto e, ao abrir esse código, chega no endereço original. Histórico por usuário e autenticação só entram depois que esse caminho estiver especificado e funcionando. Se login vier agora, a dupla passa as próximas semanas discutindo conta e senha e deixa o redirecionamento para o fim. A justificativa técnica também precisa explicar a stack com esse fluxo em mente. O NestJS existe para expor a criação do código e o redirecionamento; o React existe para o formulário; o PostgreSQL existe para guardar o par código-endereço e impedir código repetido. Vale escrever na spec o que acontece com um endereço inválido, com um código que já existe e com um código que ninguém cadastrou. O repositório público ainda está vazio, então o primeiro commit, com essa descrição, vem antes de detalhar tarefas.
