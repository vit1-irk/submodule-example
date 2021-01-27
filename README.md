## Working with git submodules: howto

### Getting git for command line

<https://git-scm.com/>

### Setting up the directory for imported sources

This command will clone the dependency repo to some specified directory 
and setup it as a submodule. You need to do this just one time!

Let's assume you're in the root directory of your repo

```
git submodule add https://github.com/vit1-irk/top-dependency-test topdep
git commit -a -m "Added new submodule"
git push origin master
```

### Updating source code to pull the changes from submodules

Do it every time you want to make the dependencies fresh.

You also need to run these commands after git clone (on a new machine). Otherwise, 
the submodule directory will be empty

```
git submodule update --init --recursive --remote
git submodule foreach git pull origin master
```

You might also want to commit the changes if upstream dependency repo was updated, so your repo will point up to the latest changes.

```
git commit -a -m "new commits in dependency"
git push
```

### Moving submodule directory to another directory

Let's assume your submodule directory is called `topdep` and `newdirectory` folder already exists.

Make sure your repository and its submodules are in their latest freshness (previous section). After that run

```
git mv topdep newdirectory/topdep
git commit -a -m "moved submodule dir"
git push
```

You can move submodules in any path of your repository as you want. Nothing else is required, because Git automatically detects all paths where submodules are located. So, if you want to pull new changes from submodule, you just continue to do it the same way you did with same commands.
