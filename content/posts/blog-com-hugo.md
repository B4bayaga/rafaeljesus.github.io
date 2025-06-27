+++ 
draft = false
date = 2025-06-27T10:21:35-03:00
title = "Dando Vida ao Meu Blog"
description = "Um Guia Prático com Hugo"
slug = "iniciando-meu-blog-com-hugo"
authors = ["Rafael Jesus"]
tags = []
categories = ["Tutoriais"]
externalLink = ""
series = []
#featuredImage = "/images/hugo_server.png"
+++
# <center>Dando Vida ao Meu Blog: Um Guia Prático com [Hugo](https://gohugo.io/)</center>

Hoje dou início a um projeto pessoal que visa registrar meu aprendizado na área de programação e, para isso, criei um blog pessoal. Ideia inovadora? Não! Mas o processo de escrever me ajuda a fixar o que aprendi e também serve como registro para consultas futuras, sem falar que pode vir a ajudar outras pessoas.

Para começar, qual tecnologia usar para construir e publicar o **Meu Blog**?

A resposta para essa pergunta foi francamente difícil devido à vasta quantidade de opções existentes. E logo de cara, pensei em construir com ferramentas que "domino" (na data em que escrevo este artigo), que são [Python](https://www.python.org/) com [Django](https://www.djangoproject.com/). Obviamente, depois pensei em [Wordpress](https://wordpress.org/), [Plone](https://plone.org/) entre outras. Passei uma semana inteira apenas para escolher que tecnologia usar, e foi quando vi um post do [Fabio Akita](https://github.com/akitaonrails), no post, ele descrevia como foi migrar o seu blog [AkitaOnRails](https://akitaonrails.com/), salvo engano, escrito em [Rails](https://rubyonrails.org/), para usar o **Hugo**.

Mas que diabos é **Hugo**? 🤔

Pois bem, fui pesquisar e descobri que **Hugo** é um software de código aberto escrito em [Go](https://go.dev/) utilizado para gerar **sites estáticos**, com a promessa de ser "extremamente rápido" e "eficiente". Ele é usado para construir diversos tipos de sites, mas é especialmente popular na criação de *blogs*, *sites de documentação*, *portfólios pessoais ou profissionais*, etc...

Entre as vantagens que o **Hugo** traz por padrão, como escrita em *Markdown* e uma vasta quantidade de ***temas***, o que mais me chamou atenção, foi a possibilidade de hospedar o **Meu Blog** no **Github Pages** totalmente **free**, o que para a natureza do projeto se encaixa como uma luva.

Mas, do que vou precisar? 🧐

Bom, para começar acessei a documentação do [**Hugo**](https://gohugo.io/documentation/), e descobri que não é tão simples quanto digitar um `sudo apt install hugo` e pronto, é só sair digitando loucamente, então resolvi fazer um checklist:

- [ ] 	Instalar a linguagem [Go](https://go.dev/).
- [ ] 	Instalar o [Hugo](https://gohugo.io/).
- [ ] 	Configurar o repositório no [GitHub](https://github.com/B4bayaga/rafaeljesus.github.io).
- [ ] 	Instalar o [Theme](https://themes.gohugo.io/themes/hugo-coder/).
- [ ] 	Configurar DNS do Domínio.
- [ ] 	Configurar o [GitHub Pages](https://pages.github.com/).
- [ ] 	Criar um [Workflow GitHub Actions](https://docs.github.com/en/actions/writing-workflows/quickstart).
- [ ] 	Indexar página com [Google Search Console](https://search.google.com/search-console/welcome?hl=pt-BR).
- [ ] 	Configurar rastreamento com [Google Analytics](https://developers.google.com/analytics?hl=pt-br).

## Instalando a linguagem [Go](https://go.dev/). 💽

Antes de seguir com a instalação da linguagem de programação **Go**, devo explicar que uso o sistema operacional [Linux](https://www.linux.org/) na distribuição [Pop!_OS](https://system76.com/), portanto, todo o processo de instalação e configuração se baseiam nessa configuração de sistema operacional.
Dito isso, vamos para a [documentação](https://go.dev/doc/install) oficial do **GO**, que pede para rodar o comando:

``` rm -rf /usr/local/go && tar -C /usr/local -xzf go1.24.4.linux-amd64.tar.gz ```

Esse comando remove qualquer instalação anterior do **GO**, excluindo a pasta ` /usr/local/go ` (caso exista), depois baixa e extrai o arquivo ` *.tar.gz `, na sequencia criando uma nova árvore de diretórios do Go em ` /usr/local/go `.

Agora adicionamos o caminho do binário na variável de ambiente do sistema com o comando:

` export PATH=$PATH:/usr/local/go/bin `

Ainda no terminal basta digitar:

 ` go version `

![Imagem Print go version](/images/um_guia_pratico_com_hugo/go_version.png)
 
A saída deverá conter a versão do **GO**, o que mostra que foi instalado com sucesso.

- [x] 	Instalar a linguagem [Go](https://go.dev/).

## Instalando o Hugo. 💾

Agora voltamos à documentação do [**Hugo**](https://gohugo.io/installation/linux/). Aqui um parêntese, a documentação orienta instalar via **snap**, porém, optei pela instalação via [GitHub](https://github.com/gohugoio/hugo?tab=readme-ov-file), mais precisamente a versão ***extended edition***. O primeiro motivo é que alguns temas do **Hugo** exigem versão **extended**, o outro é simplesmente porque eu quis. 😩

Continuando, no terminal rode o comando:

``` CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest ```

Para testar se tudo ocorreu bem rode:

``` hugo version ```

![Imagem Print hugo version](/images/um_guia_pratico_com_hugo/hugo_version.png)

Mais uma vez, a saída sendo a versão do **Hugo**, tudo ocorreu bem.

- [x] 	Instalar o [Hugo](https://gohugo.io/).

## Configurar o repositório no [GitHub](https://github.com/B4bayaga/rafaeljesus.github.io). 💻

Criei um repositório **público** no GitHub para configurar posteriormente o GitHub Pages e tornar o blog público para o mundo. O GitHub Pages exige que o repositório seja publico (na data dessa publicação), para publicar a página.

Com o repositório criado é hora ade clonar o projeto:

` git clone https://github.com/meu-id/meu-repositorio.git `

Agora, criamos o projeto com **Hugo** usando o comando abaixo:

` hugo new site meu-repositorio --force `

A *flag* ` --force ` força o **Hugo** a criar o site em um diretório existente, no meu caso o repositório privado que clonei anteriormente.

Com isso temos o repositório devidamente clonado para versionamento, publicação, etc... do projeto.

- [x] 	Configurar o repositório no [GitHub](https://github.com/B4bayaga/rafaeljesus.github.io).

## Instalar o [Theme](https://themes.gohugo.io/themes/hugo-coder/). 🎀

Outro ponto interessante do Hugo é a quantidade de **Temas ([Themes](https://themes.gohugo.io/))**, páginas prontas de fácil configuração, personalização e a grande maioria com boa documentação. Após escolha do **Tema** e ler a documentação do mesmo, seguimos no terminal para realizar a instalação.

Dentro do projeto, criarei um submódulo com **Git**, clonando o **Tema(Them)** dentro do diretório ` themes/ ` com o comando abaixo:

`  git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder `  

**Ok 👌**, agora vou configurar o **Theme** no arquivo ` hugo.toml ` no nosso diretório principal.

No **GitHub** do **Theme** que escolhi, tem um exemplo de arquivo ` hugo.toml `, são as [configurações mínimas](https://github.com/luizdepra/hugo-coder/blob/main/docs/configurations.md#complete-example) para que ele funcione, basta copiar e colar no arquivo ` hugo.toml ` do seu projeto, substituir metadados pessoas, como por exemplo ` baseURL,title `.

Pronto, com o arquivo ` hugo.toml ` configurado é hora de subir o **Hugo** localmente com o comando abaixo e verificar se tudo deu certo:

` hugo server `

![Print imagem terminal rodando comando hugo server](/images/um_guia_pratico_com_hugo/hugo_server.png)

- [x] 	Instalar o [Theme](https://themes.gohugo.io/themes/hugo-coder/).

## Configurar DNS do Domínio. 📝

Antes de configurar o **GitHub Pages** é muito importante configurar o **DNS**. Leve em consideração que tenho um **Domínio** hospedado, geralmente uso o **DNS** da [Cloudflare](https://www.cloudflare.com/), mas para esse projeto usarei o **DNS** do [registro.br](https://www.registro.br/), aqui estou assumindo que o **GitHub Pages** tem um mínimo de proteção contra ataques de negação de serviço [DoS attack](https://en.wikipedia.org/wiki/Denial-of-service_attack).

Dentro das configurações do meu **Domínio**, acesso "***configurar zona DNS***" e seguindo a [documentação](https://docs.github.com/pt/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages#using-an-apex-domain-for-your-github-pages-site) do **GitHub Pages** e crio 4 entradas do "**Tipo A**", deixo o segundo campo(nome) em branco e aponto para os **[IPs do GitHub Pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)**. Em seguida, criei outra entrada,desta vez do "**Tipo CNAME**". No campo "**name**", preenchi com "**www**" e, por último, apontei para o domínio do meu **GitHub**, esse domínio é formado pelo nome do seu usuário seguido de **.github.io**.

![Print imagem DNS](/images/um_guia_pratico_com_hugo/print_conf_dns.png)

Agora tenho que esperar as configurações se propagarem pelo mundo, esse tempo pode variar bastante.

- [x] 	Configurar DNS do Domínio.

## Configurar o [GitHub Pages](https://pages.github.com/). ⎘

Acessando o repositório publico no **GitHub**, segui com a configuração do **GitHub Pages**, clicando em **Settings**.

![Imagem Print menu Settings do GitHub](/images/um_guia_pratico_com_hugo/print_setings_github.png)

Na sequencia basta clicar em **Pages**.

<div style="text-align: center;">
  <img src="/images/um_guia_pratico_com_hugo/print_github_pages.png" alt="Imagem Print menu Pages do GitHub" width="auto">
</div>

No menu do **GitHub Pages** em ` Source ` selecione ` Deploy GitHub Actions `.

![Print menu deploy com Branch](/images/um_guia_pratico_com_hugo/print_deploy_actions.png)

Por fim, em ` Custom Domain ` digite o seu domínio, clique em ` Save ` e aguarde o **GitHub** checar e validar a configuração.

- [x] 	Configurar o [GitHub Pages](https://pages.github.com/).

## Criando [Workflow GitHub Actions](https://docs.github.com/en/actions/writing-workflows/quickstart). 🤖

Esta etapa será responsável por publicar **Meu Blog** usando automação do **GitHub Actions**, e para isso o **Hugo** disponibiliza um [Workflow](https://gohugo.io/host-and-deploy/host-on-github-pages/) pronto, basicamente basta da **copiar e colar** e pronto.

Seguindo a documentação do **Hugo**, depois das etapas anteriores finalizadas voltamos no nosso arquivo ``` hugo.toml ``` e realizamos as configuração de cache de imagens incluído o código abaixo:

```
[caches]
  [caches.images]
    dir = ':cacheDir/images' 
```

Agora tenho que criar o arquivo ``` hugo.yaml ``` em um diretório chamando ``` .github/workflows ```. Para isso usei o terminal:

```
mkdir -p .github/workflows
touch .github/workflows/hugo.yaml
```

Copiei e colei o YAML disponível na [documentação](https://gohugo.io/host-and-deploy/host-on-github-pages/) no arquivo que criei. Alterei apenas a versão do Hugo de acordo com a que estou usando e o nome do **Workflow**.

A ideia é que sempre que fizer um ``` push ``` na ``` main ``` as alterações serão publicadas no **GitHub Pages**.

Hora de testar!

```
git add -A
git commit -m "Cria hugo.yaml"
git push
```

Passou de primeira!! 😁😁

- [x] 	Criando [Workflow GitHub Actions](https://docs.github.com/en/actions/writing-workflows/quickstart).

## Indexando página com [Google Search Console](https://search.google.com/search-console/welcome?hl=pt-BR). ✍️

Neste ponto o **Meu Blog** esta online e acessível. Agora quero que seja listado no buscador do google, ou seja, indexado.

De acordo minha pesquisa existe opções para isso, escolhi usar a ferramenta [Google Search Console](https://search.google.com/search-console/welcome?hl=pt-BR) obviamente do [Google](google.com).

Aqui é simple, no **Google Search Console** realizei o login com minha conta google, escolhi a opção **DOMÍNIO** para o google verificar se realmente sou proprietário do domínio.

![Print página google search console](/images/um_guia_pratico_com_hugo/google_search_console.png)

Depois da primeira tela é hora de configurar no **DNS**. Seguindo orientação do **Google Search Console**, acesso novamente o [registro.br](https://www.registro.br/), depois "***configurar zona DNS***" e crio uma entrada do "**Tipo TXT**" e colo o registro que o google disponibiliza.

Na tela do **Google Search Console** clico em verificar para que o google valide minha propriedade sobre o Domínio.

![Print página google search console](/images/um_guia_pratico_com_hugo/txt_google_search_console.png)

Pronto! O google pede para aguardar 24 horas.

- [x] 	Indexa página com [Google Search Console](https://search.google.com/search-console/welcome?hl=pt-BR).

## Configurar rastreamento com [Google Analytics](https://developers.google.com/analytics?hl=pt-br). 📈

Por fim vamos realizar o cadastro no **Google Analytics**, isso irá me fornecer dados sobre o trafego do **Meu Blog**, esse tarefa como a anterior tam´bém é muito simples, basta realizar o cadastro no [Google Analytics](https://developers.google.com/analytics?hl=pt-br), no meu caso ainda não tinha cadastro, seguir o passo a passo no site e, por fim, basta copiar o ``` G-ID ``` que o google disponibiliza.

No arquivo ``` hugo.toml ```, temos que incluir o parâmetro ``` googleAnalyticsID ``` com o ``` G-ID ``` que copiamos no site do google:

```
[params.googleTagManager]
id = "G-ID" # Substituir pelo seu G-ID
```

Pronto! 🎉🎉🎉

Após todo o processo o [Google Analytics](https://developers.google.com/analytics?hl=pt-br) ira validar o G-ID e passara a fornecer dados de trafego do **Meu Blog**.

Com isso concluo o meu tutorial, [Dando Vida ao Meu Blog: Um Guia Prático com Hugo](https://rafaeljesus.dev.br/posts/iniciando-meu-blog-com-hugo/). Foi relativamente difícil pra mim, mesmo com experiência de aproximadamente 3 anos com programação, mas no fim, bastou segui a documentação oficial de cada tecnologia, então, leiam a documentação!