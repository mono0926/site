Source of http://mono0926.com

- Deployed to: https://github.com/mono0926/mono0926.github.io
- Created by [Hugo :: A fast and modern static website engine](http://gohugo.io/)

## Structure

- [Theme repositories](https://github.com/mono0926/site/tree/master/themes) are added by Git Submodule
- [Public directory's repository](https://github.com/mono0926/mono0926.github.io) is added by Git Submodule

## Workflow

- Executing by [Alfred Workflows](http://support.alfredapp.com/workflows) is recommended.
- These scripts should be improved...

### Post a new article

```sh
SOURTH_PATH='/Documents/Git/Private/site'
cd ~/$SOURTH_PATH
git pull
POST_PATH=$(hugo new post/$1.md)
POST_PATH=$(echo $POST_PATH | sed -e "s/ created//")
open $POST_PATH
```

### Preview

```sh
SOURCE_PATH='/Documents/Git/Private/site'
cd ~/$SOURCE_PATH
open http://localhost:1313/
hugo server --buildDrafts --watch
```

### Deploy

```sh
push_changes() {
    git add -A
    git commit -m "Deployed via workflow."
    git pull
    git push origin master
}

SOURCE_PATH='/Documents/Git/Private/site'
cd ~/$SOURCE_PATH
hugo
cd public
push_changes
cd -
cd themes/hugo-mono
push_changes
cd -
push_changes
```
