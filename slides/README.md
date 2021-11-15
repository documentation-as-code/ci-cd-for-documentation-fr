---
marp: true
theme: default
style: |
  footer {
    position: absolute;
    #left: 50%;
    bottom: 7px;
  }

  section header a { color: white;}

  video.inslide {
    position: absolute;
    width: 70%;
    height: 70%;
  }

  section.mainpage {
    color: white;
    background-image: url("https://scontent-cdt1-1.xx.fbcdn.net/v/t1.6435-9/fr/cp0/e15/q65/185239524_1166143223834007_3633212344109793893_n.jpg?_nc_cat=105&ccb=1-5&_nc_sid=ed5ff1&efg=eyJpIjoidCJ9&_nc_ohc=9WtvE4TuCLEAX_H1weY&tn=1JDryBYi5GcXQVIo&_nc_ht=scontent-cdt1-1.xx&oh=985709b12da6735a1d93a0dd6ec171de&oe=61AE7538");
    opacity: 1
  }

  section.mainpage h1 {
    color: white;
  }


footer: '[github/ojacques](https://github.com/ojacques) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; [github/angegar](https://github.com/angegar)'

---

<!-- paginate: false -->

<br/>
<br/>
<br/>
<br/>

<!-- _class: mainpage -->
# CI and CD

## Pour la documentation

<!-- 
speaker: Olivier

Thank you. Today, Laurent and I are going to talk about "Documentation as Code" and more specifically CI and CD for documentation.

But first, let us introduce ourselves:

Speakers: Olivier & Laurent
- Short intro

(NOTE: embed Olivier & Laurent's faces / OBS)

Laurent:
Hello I am Laurent, I also work for DXC Technology where I am acting internally as a DevOps Coach and externally as a CI and CD expert. I hope we will manage to show you the benefits of the CI and CD practices for documentation as code, as well as how easy it is to do it.
-->

---
<!--backgroundImage: url('https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/dxc.jpg')-->

<!--
speaker: Olivier

Laurent and I both work for DXC technology customers. DXC technology is a global IT services leader.

With 19.6B$ of revenues, 6000 customers and 138000 employees across 70 countries, we are - in many dimensions - big.

-->

---
<!--backgroundImage: url('https://github.com/documentation-as-code/ci-cd-for-documentation-fr/raw/master/slides/slide-background.png')-->

Documentation : La quête de la perfection

# 🏰🦄🤴👸🐴👻⚔🗡🏴‍☠️

<!-- 

Back to this presentation. 

This presentation is an experience report, because we have learned so much from others through this format.

This presentation is about our quest: the quest for great documentation.

Previously, 
- our documentation was the last thing we would do,
- it had spelling and syntax mistakes,
- we were using the passive voice, but sometimes the active voice
- it was often inaccurate,
- a few were able to fix it and we had to contact them through email,
- several authors could not work on the same piece of documentation without going through lengthy merges,
- and links would break very often without us even knowing.

Today, it's a very different situation
- we have one service catalog and 174 services documented
- documentation readers can contribute to the documentation using a Pull Request
- we can report bugs and fix them
- documentation changes go through a series of tests and gates
- it's bigger yet more thorough and precise than ever
- It has the same look & feel
- it's written in the same style

-->

---

# Nous avons beaucoup docummenté

## (avec du code)

- 1 catalogue de service: contenant différents points d'entrée
- 174 services: Documentation technique
- 630 contributeurs

<!--

The context for the experience report is our own company (but we do that with our customers too):
- A platform which provides intelligence, orchestration, and automation capabilities to our managed service offerings
- 630 contributors (developers, testers, scrum masters)
- 1 "service catalog" site
- 174 services documented

-->

---

![bg 95% right:62%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/service-catalog-hugo.gif)

# Catalogue de service
Avec [Hugo](https://gohugo.io/)

<!--
Speaker: Olivier

We have 2 types of documentation: 
- Service catalog
- Service documentation

Service catalog:
- Marketing / catalog site: mix of text, benefits, highlights, videos
-->
---

![bg 95% right:62%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/service-documentation-mkdocs.gif)

# Documentation de service
Avec [MkDocs](https://www.mkdocs.org/) +
[material theme](https://squidfunk.github.io/mkdocs-material/)

<!--
Speaker: Olivier

The documentation for each service leverages Mkdocs which we love because it's very close to markdown and does not require a separate git repository.

-->

---

![bg center 60%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/doc-site.jpg)

<!--
Speaker: Olivier

-->
---
# 🤯

## DXC, Microsoft, GitHub, GitLab, AWS tous utilisent "Documentation comme du code"

Pour de bonnes raisons:

- C'est rapide, sécurisé pas cher (sites statiques)
- Il est facile de contribuer et donc de garder la documentation à jour
- Cette solution a été éprouvée à plus d'un titre
- Cela peut être monitoré (pensons analytiques)

<!--
Fast, secure and cheap (static sites)
  - Comparing to WordPress/Drupal/Confluence type solutions
  - More secure (no DB to hack)
  - Portable (even offline)
Easier to contribute to / keep up-to-date
  - The pull request / merge request workflow fully applies
Battle test documentation
Monitoring:
  - "Is this page useful?"
  - Analytics: like Google Analytics or Open Source alternative: Matomo
  - Reader journey, what is useful
-->

---

# Nos challenges

- Une apparence commune
- Une "voix" commune
- DRY: Don't Repeat Yourself
- Schémas: qu'est-ce qui change ?
- Liens hypertexte
- Publications

<!--
speaker: Olivier

-->
---
<video loop class="inslide" src="https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/gource.mp4" autoplay muted />

<!--
speaker: Olivier

This video is a visualization of our service catalog repository documentation, as it evolves.

In summary, we needed to build great documentation, at scale, battle tested and ensure it would not break over time.

Looks like code to us!

-->

---

![bg right 80%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/ci-cd-for-doc.gif)


# CI and CD for documentation

CI

- Correction orthographique
- Acronymes approuvés / dictionnaire personnalisé
- Une seule voix
- Contrôle périodique des liens morts

CD

- Publication automatique

<!--
Speaker: Olivier

-->

---

![bg](https://github.com/documentation-as-code/ci-cd-for-documentation-fr/raw/master/slides/title.png)
<br/>
<br/>

# En pratique

<!--
Speaker: Laurent

Hi, during the second part of the talk, I will give you a brief overview of the state of the art about CI/CD tools for documentation as code.

Let's start with the development environment, which environment is required ?
-->

---
![bg right 90%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/vscode.jpg)
# Création de contenu

Utilisation de [`Markdown`](https://guides.github.com/features/mastering-markdown/)

Avec votre éditeur préféré :

- [IntelliJ](https://www.jetbrains.com/help/idea/markdown.html#navigation)
- [Eclipse](https://marketplace.eclipse.org/content/markdown-text-editor)
- [VSCode](https://code.visualstudio.com/docs/languages/markdown) 👈

<!--
Speaker: Laurent

To write the documentation we use the Markdown language. Yes, I said language. Indeed, you write your documentation in your native language then you surround it with decorators which will modify the format.

There is no need to have developer skills, the Markdown syntax is easy to use.

-->

---
![bg right 90%](https://github.com/hediet/vscode-drawio/raw/master/docs/drawio-png.gif)
# Création (1)

## Rajouter des extensions

- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) (pour la syntaxe)
- [Draw.io](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) (pour les schémas)
- [PlantUML](https://github.com/qjebbs/vscode-plantuml) (pour les schémas comme du code)
- [Marp](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) (pour les transparents)

<!--
Speaker: Laurent

Most of the integrated development environments (IDE) can be enhanced with multiple plugins. Here is a short list of what we used to use.
-->
---
![bg right 90%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/codespaces.jpg)

# Création (2)

## GitHub [Codespaces](https://github.com/features/codespaces) ou GitPod

- Édition directe dans le navigateur
- Plus facile pour les éditeurs techniques:
  pas de `git clone/branch/push`
  `git reset origin/main --hard`
- Une liste d'extension propre au projet

<!--
Speaker: Laurent

GitHub offers an online VSCode instance attached to your GitHub repository. The Codespaces feature allows all the developer to share the same set of extensions as this configuration is automatically shared across the development environment attached to the project.
-->
---
# Création (3)

## Faîtes votre choix

- [Jekyll](https://jekyllrb.com/) 🤐
- [Hugo](https://gohugo.io/): puissant, léger, rapide 👈
- [Marp](https://marp.app/): transparents / présentations
- [MkDocs](https://www.mkdocs.org/) + [material theme](https://squidfunk.github.io/mkdocs-material/) 👈

<!--

- Jekyll : Based on Ruby, it's hard to configure for a non developer users especially under windows => hard to contribute
- Hugo:
  - HTML + go template for documentation
  - Far from standard markdown => hard for non dev users
  - shortcodes: like macro, for documentation. Ensures uniformity
  - Recommended if you need to have multiple page template in your web site

- Marp:
  - Excellent to generate slide deck
  - Follow Markdown syntax
  - Presenter view
  - Template with CSS
  - Extensible
  - Output PPTX, PDF, PNG, JPEG
- MkDocs:
  - Follow Markdown syntax
  - Closest to plain markdown, great for tech docs
  - Can integrate native HTML web page => Can integrate Marp outputs
-->
---
# Orchestration

- GitHub Actions
- GitLab CI
- Jenkins (`Jenkinsfile`) 👈
- AWS code pipeline
- Azure DevOps

<!--
Speaker: Laurent

Use your favorite orchestration tool to deploy your documentation.
Those tools now offer predefined features to ease your pipeline;

We will see a set of GitHub Market Actions used in this documentation pipeline.
-->
---
# CI: Linter

## CLI linter

- [github super-linter](https://github.com/github/super-linter)
- [markdownlint](https://github.com/DavidAnson/markdownlint)
![bg right 80%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/linter.png)

## Linter dans l'éditeur

- [VS Code markdownlint extension](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)

<!--
We use linters to check code "doc" quality.

2 types of linters
- CLI: to be integrated in the pipeline 
- Editor: check syntax as you type, before commit and push

-->

---

# CI: Orthographe

## En ligne de commande

![bg 90% right](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/spellcheck_code.png)

- [spellcheck-github-actions](https://github.com/rojopolis/spellcheck-github-actions)
- [spellchecker-cli](https://github.com/tbroadley/spellchecker-cli)

## Dans l'éditeur

- [VS Code code-spell-checker extension](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

<!-- 
Identically, we can find CLI spell checker and Editor one

Work with direction of exception and custom dictionary
-->

---
# CI: Vérification liens hypertexte

![bg right:62% 95%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/markdown-link-check.jpg)

## Liens morts

[markdown-link-check](https://github.com/tcort/markdown-link-check)

<!-- 
Links must be checked regularly (cron) as they break without you doing any change.

-->
---

![bg right:65% 95%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/style-vale.jpg)

# CI: Tester (4)

## Style / voix

[Vale](https://github.com/errata-ai/vale)

<!--

Used to ensure your a vocabulary style guide.
-->
---
# Publication (CD)

![bg right 95%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/github_actions.png)

## Hébergement GIT

GitHub, GitLab, Bitbucket

## Hébergement web

- [GitHub pages](https://pages.github.com/) 👈
- [GitLab pages](https://docs.gitlab.com/ee/user/project/pages/)
- [Netlify](https://www.netlify.com/)
- Un bucket AWS S3 👈

<!--

You don't have to spin up a virtual machine or server to host your documentation site. Major Source Code Management applications already host web pages.
-->
---
![bg right:58% 72%](https://github.com/documentation-as-code/ci-cd-for-documentation/raw/main/slides/github_template.png)
# Démarrage rapide

Facilitez vous la vie avec les :

- [GitHub templates](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/creating-a-template-repository)
- [GitLab project templates](https://docs.gitlab.com/ee/gitlab-basics/create-project.html#project-templates)

<!--
Speaker: Laurent

We have been using GitHub template to ease the creation of Documentation As Code

-->
---
# Merci 🙏
