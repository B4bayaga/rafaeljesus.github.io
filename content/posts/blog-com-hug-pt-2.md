+++ 
draft = false
date = 2025-06-21T09:57:04-03:00
title = "Dando Vida ao Meu Blog [Pt-2]"
description = "Um Guia Prático com Hugo"
slug = "iniciando-meu-blog-com-hugo-pt-2"
authors = ["Rafael Jesus"]
tags = []
categories = ["Tutoriais"]
externalLink = ""
series = ["Dando Vida ao Meu Blog"]
+++


# <center>Dando Vida ao Meu Blog: Um Guia Prático com [Hugo](https://gohugo.io/) [Pt-2]</center>

Dando continuidade ao post [anterior](https://rafaeljesus.dev.br/posts/iniciando-meu-blog-com-hugo), vamos finalizar as configurações que implementam o **Meu Blog**

Em resumo o que fizemos no **post** anterior foi:

- [x] 	Instalar a linguagem [Go](https://go.dev/).
- [x] 	Instalar o [Hugo](https://gohugo.io/).
- [x] 	Configurar o repositório no [GitHub](https://github.com/B4bayaga/rafaeljesus.github.io).
- [x] 	Instalar o [Theme](https://themes.gohugo.io/themes/hugo-coder/).
- [x] 	Configurar DNS do Domínio.
- [x] 	Configurar o [GitHub Pages](https://pages.github.com/).

Com isso o **blog** está no ar e disponível para todo o planeta.

E seguindo a mesma ideia do post anterior, vou fazer um checklist do que ainda falta:

- [ ] 	Criando [Workflow GitHub Actions](https://docs.github.com/en/actions/writing-workflows/quickstart).
- [ ] 	Indexa página com [Google Search Console](https://search.google.com/search-console/welcome?hl=pt-BR).
- [ ] 	Configurar rastreamento com [Google Analytics](https://developers.google.com/analytics?hl=pt-br).

Mas como vimos anteriormente, toda ves que preciso publicar um novo post, atualiza-lo, etc... , tenho que primeiro editar o código fonte no repositório principal, depois no terminal executar o comando ``` hugo build ``` para gerar o site, ainda no repositório principal realizar o ``` git commit ``` e ``` git push  ```. Por fim, entrar no **submodule** que criei no diretório ``` public/ ``` e novamente realizar o ``` git commit ``` e ``` git push  ```, etc... para publicar as atualizações do **blog**. Muito **chato** 🥱.

Para resolver esse "problema" o **Hugo** disponibiliza um **Workflow** do **GitHub Actions**.

Mas para que serve o **Workflow GitHub Actions**? 🤔

