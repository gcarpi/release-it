---
theme: unicorn
colorSchema: 'light'
logoHeader: '/logo.png'
---

# Release it! 
Versionamento e geração de releases automáticos

<div class="pt-12">
  <span @click="$slidev.nav.next" class="p-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Pressione <strong>Espaço</strong> para ir para a próxima página <carbon:arrow-right class="inline"/>
  </span>
</div>

---
logoHeader: '/logo.png'
---

# Introdução
Antes de falarmos sobre a ferramenta *Release It!* precisamos entender algumas coisas: O que é **versionamento** e o que são **releases**.

---
logoHeader: '/logo.png'
---

# Versionamento
Versionamento é uma metodologia de classificação adotada por programadores com o intuito de controlar e acompanhar o histórico de alterações em um software. Essa metodologia permite distinguir as mudanças realizadas, facilitando a identificação de cada uma delas. Atualmente uma metodologia muito utilizada é o __Versionamento Semântico__.

---
logoHeader: '/logo.png'
---

# Versionamento Semântico
O Versionamento Semântico é um conjunto simples de regras que ditam como os números de versão são atribuídos e incrementados.

---
logoHeader: '/logo.png'
---

# Regras do Versionamento Semântico
Diante do número de versão (ex: *1.0.0*) incremente-o utilizando as regras: __MAJOR__.__MINOR__.__PATCH__:

1. **MAJOR**:&nbsp;Quando há funcionalidades incompatíveis com as versões anteriores do sistema;
2. **MINOR**:&nbsp;&nbsp;Quando há funcionalidades adicionadas ao sistema porém com compatibilidade com as versões anteriores;
3. **PATCH**:&nbsp;&nbsp;Quando há uma ou mais correções em relação as funcionalidades existentes.

<br>

Para mais informações consulte a documentação oficial: [https://semver.org/](https://semver.org/lang/pt-BR/)

---
logoHeader: '/logo.png'
---

# Releases

Releases são versões de um software que podem ser disponibilizados para um público em geral. Geralmente é disponibilizado por plataformas de hospedagem de código, como: *GitHub*, *GitLab* ou *Bitbucket*. Aqui nessa apresentação vamos abordar o __GitHub Releases__.

---
logoHeader: '/logo.png'
---

# GitHub Releases
A página de releases nos projetos hospedados no GitHub é um local que contém todo o histórico do projeto, com todas as suas versões e notas de lançamento.

---
layout: image-center
image: './releases.jpg'
imageWidth: '400'
imageHeight: '900'
class: 'text-center'
---

# GitHub Releases

---
logoHeader: '/logo.png'
---

# Quais são as propriedades de um release?

- Título
- Notas de lançamento
- Assets (arquivos binários)
- Git Tag
- Autor

---
layout: image-center
image: './release-title.jpg'
imageWidth: '450'
imageHeight: '950'
class: 'text-center'
---

# Título
Utilizado como um identificador do release

---
layout: image-center
image: './release-notes.jpg'
imageWidth: '450'
imageHeight: '950'
class: 'text-center'
---

# Notas de lançamento
Abrange todas as alterações realizadas naquela versão

---
layout: image-center
image: './release-assets.jpg'
imageWidth: '450'
imageHeight: '950'
class: 'text-center'
---

# Assets
Qualquer arquivo que pode ser disponibilizado para download

---
layout: image-center
image: './release-author.jpg'
imageWidth: '450'
imageHeight: '950'
class: 'text-center'
---

# Autor
Usuário que criou o release

---
layout: image-center
image: './release-tag.jpg'
imageWidth: '450'
imageHeight: '950'
class: 'text-center'
---

# Tag do Git
Uma tag do Git é vinculada ao release

---
logoHeader: '/logo.png'
---

# Ok... mas por quê criar um release?
Um release informa por meio das notas de lançamento mudanças significativas realizadas em cada versão de um projeto, ou seja, facilitando que usuários e contribuidores vejam precisamente quais mudanças foram realizadas entre cada versão publicada. 

---
logoHeader: '/logo.png'
---

# e mais...
Para os contribuidores do projeto, o vínculo entre o release e a tag do Git pode auxiliar em muitos casos. A tag indica um determinado estado do código e esse estado sempre pode ser recuperado, não importa quantos commits e branches seguem, esse estado é definitivo. 

---
logoHeader: '/logo.png'
---

# Uma tag do Git pode ser utilizada para: 
- Obter uma versão específica do projeto;
- Distribuir essa versão como um pacote;
- Realizar deploy dessa versão em um servidor;
- Reverter uma versão com falha.

---
logoHeader: '/logo.png'
---

# Sabendo de tudo isso, já podemos criar nosso release...

---
logoHeader: '/logo.png'
---

# Criando um novo release
Criar um novo release manualmente pode ser um pouco tedioso pois envolve um número considerável de etapas:

- Realizar a atualização da versão em alguns arquivos (ex: *package.json*, *composer.json*, entre outros...);
- Realizar tarefas pré-release, como o lint do projeto e/ou testes automatizados antes da publicação;
- Realizar a compilação/build do código;
- Criar uma tag no Git;
- Dar commit e realizar o push de todas essas modificações para finalmente gerar o release...

---
logoHeader: '/logo.png'
---

# Aí que entra o Release It! 
Essa ferramenta nos auxilia a automatizar as etapas chatas para criar um release. Ele executa as etapas ditas anteriormente por meio de uma CLI com a sua intervenção em cada etapa ou de forma completamente automatizada.

---
logoHeader: '/logo.png'
---

# Alguns recursos do Release It! são:

- Atualização de versão em arquivos específicos (ex: *package.json* ou em qualquer arquivo utilizando o plugin [@release-it/bumper](https://github.com/release-it/bumper));
- Criação de tags no Git utilizando o Versionamento Semântico;
- Criação de releases automáticos no GitHub ou GitLab;
- Criação das notas de lançamento automaticamente com base nos commits ou seguindo o padrão *Keep A Changelog*;
- Publicação automática de pacotes no *NPM*;
- Possibilidade de criar *hooks* para automação de tarefas pré-release ou pós-release;
- e muito mais…

---
logoHeader: '/logo.png'
---

# Instalação

1. Certifique-se de ter instalado o Node ≥ 14 em sua máquina:

```shell
$ node -v
> v14.20.0
```

<br>

2. Adicione as dependências ao projeto:
```shell
$ npm install release-it @release-it/keep-a-changelog -D
```

<br>

3. Pronto! Prossiga agora para a etapa de __Configuração <carbon-arrow-right />__ 

---
logoHeader: '/logo.png'
---

# Configuração
1. Dentro do arquivo *package.json* procure pela propriedade *scripts* e adicione o script:
```json
"scripts": {
  "release": "release-it"
}
```

<br>

2. Após, vamos criar um arquivo *.release-it.json* na raiz do projeto e preencher o conteúdo do arquivo com as [configurações](https://github.com/release-it/release-it/blob/master/config/release-it.json) da ferramenta.

<br>

3.  Para demonstração vamos utilizar algumas [configurações básicas](https://gist.github.com/gcarpi/7e6716342b354746c0d61b3d214b81e6). Veja mais informações sobre essas configurações <carbon-arrow-right />

---
logoHeader: '/logo.png'
---

# Configuração para o Git

```json{all|2|3|4-5|6-8|all}
"git": {
  "requireBranch": "release",
  "requireCleanWorkingDir": true,
  "commitMessage": "Release v${version}",
  "commitArgs": [],
  "tag": true,
  "tagName": "${version}",
  "tagAnnotation": "Release v${version}"
}
```

---
logoHeader: '/logo.png'
---

# Configuração para o GitHub

```json{all|2|3|all}
"github": {
  "release": true,
  "releaseName": "v${version}"
}
```

---
logoHeader: '/logo.png'
---

<br>
<br>

# Configuração dos hooks

```json{all|2|3-17|all}
"hooks": {
  "before:init": ["npm run lint"],
  "after:release": [
    "echo Updating and pushing changes to main...",
    "git checkout main",
    "git fetch origin main",
    "git merge --no-ff release",
    "git push origin main",

    "echo Updating and pushing changes to develop...",
    "git checkout develop",
    "git fetch origin develop",
    "git merge --no-ff release",
    "git push origin develop",

    "echo Successfully released ${name} v${version} to ${repo.repository}!"
  ]
}
```

---
logoHeader: '/logo.png'
---

<br>

# Configuração das notas de lançamento

```json
"plugins": {
  "@release-it/keep-a-changelog": {
    "filename": "CHANGELOG.md"
  }
}
```

<br>

**Atenção:** Na raiz do projeto crie um arquivo *CHANGELOG.md* e preencha o conteúdo deste arquivo seguindo o padrão do [Keep A Changelog](https://keepachangelog.com/pt-BR/1.0.0/). Para criar um novo release é __obrigatório__ ter uma seção *[Unreleased]* com as notas de lançamento da nova versão. 

<br>
Veja um exemplo <carbon-arrow-right />

---
logoHeader: '/logo.png'
---
# CHANGELOG.md

```md
# Changelog
Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
### Adicionado
- Adicionada biblioteca `release-it` e plugin `@release-it/keep-a-changelog`.

## [1.0.0] - 2022-09-20
### Adicionado
- Primeira versão do projeto.
```

---
logoHeader: '/logo.png'
---

# Pronto! Agora já podemos gerar o release.
<br>

Execute o comando abaixo para executar a CLI com intervenção em cada etapa:
```bash
$ npm run release
```

<br>

Ou execute o comando abaixo para executar de forma completamente automatizada:
```bash
$ npm run release -- minor --ci
```

---
layout: image-center
image: 'https://raw.githubusercontent.com/release-it/release-it/master/docs/assets/release-it-interactive.gif'
imageWidth: '350'
imageHeight: '800'
class: 'text-center'
---
# Se tudo der certo...
Você irá ver algo parecido com:

---
logoHeader: '/logo.png'
---

# Agora seu projeto está pronto para gerar releases automáticos!

---
layout: center
logoHeader: '/logo.png'
---

# Obrigado!

[Documentação](https://github.com/release-it/release-it) <carbon-logo-github />