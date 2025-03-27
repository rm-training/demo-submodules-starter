
- [Sample Project](https://github.com/rm-training/dummy-main-project)
- [Lab Starter](https://github.com/rm-training/lab-git-submodules-starter)

# Demo

```bash
git clone https://github.com/rm-training/demo-submodules-starter
cd demo-submodules-starter
rm -Rf .git
```

You'll be left with:

```bash
tree
.
├── main-project
│   ├── first
│   └── lib
│       └── module-a
│           ├── file3
│           ├── first
│           └── second
├── module-a
│   ├── first
│   └── second
├── module-b
│   ├── first
│   └── second
└── module-c
    └── first
```

# Module Project(s)

For each `module-{a}`:

```bash
cd module-a
git init
git add .
git commit -m 'A: First Commit'
git config --local receive.denyCurrentBranch warn

cd module-b
git init
git add .
git commit -m 'B: First Commit'
git config --local receive.denyCurrentBranch warn
```

# Main Project

```bash
cd main-project
git init
git add .
git commit -m 'Main: First Commit'
git config --local receive.denyCurrentBranch warn
```

Set the configs:
```bash
git config --local submodule.recurse true
git config --local diff.submodule log    
git config --local status.submoduleSummary true
```

You'll also need to allow `file` protocol:

```bash
# you could do this locally in each module & the main repo, too
# or go global:
git config --global protocol.file.allow always
```

More [info about file protocol](https://git-scm.com/docs/git-config#Documentation/git-config.txt-protocolallow)

Then add your submodule(s):
```bash
git submodule add ../external-remotes/module-a lib/module-a
```
