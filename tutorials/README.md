# Tutorials #

This is a set of useful tutorials and resources to check out and/or work on before the Hackathon in September.

Take a look at them, some are really short!

## Documentation tools ##

- [Mastring markdown](https://guides.github.com/features/mastering-markdown/)
- [Sphinx](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html) is a documentation generator that has many features for writing technical documentation. You've probably seen software or bioinformatics tools documentation hosted in [read the docs](https://readthedocs.org/). Sphinx is how you create it.

## Modern coding practices ##

- [Git tutorial](https://git-scm.com/docs/gittutorial). Git is software (most likely experienced as a set of commands) to keep track of changes in a set of files (You can look at it as a wet lab logbook). It was created by Linus Torvalds (I mean, how many useful things can that guy create?). Anyway, learn how to use these and you're probably good:
  - `git init` to start a fresh git repository
  - `git add` to add or stage changes you've made to your repository
  - `git commit -m "commit message e.g. create script to plot volcano plot"` once you've made a set of related changes you want to commit them to safety or 'snapshot' your changes to the repository timeline (meaning, they'll live on forever)
  - You can use `git diff` to compare changes you've made against the current snapshot of the repository

Now, Git is really helpful to work as a team in coding projects because many people can work simultaneously on the same things. Meaning, we can use something like [GitHub](https://github.com), which is an internet service that hosts git repositories, to store our projects and work on them.

## single-cell analysis DOWNSTREAM of scTELESCOPE ##  

We want people to actually use scTELESCOPE and that means we need to consider "what do people do with single-cell RNA-seq data?"

Well, after aligning reads to the genome, peple use [Seurat](https://satijalab.org/seurat/) to QC, analyse and explore the single-cell RNA-seq data. So we really need to know what happens within Seurat, which data does it take as input and in which formats. 

So check out [Getting started with Seurat](https://satijalab.org/seurat/articles/get_started.html).










