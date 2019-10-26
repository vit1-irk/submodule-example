### Working with git submodules: howto
#### Setting up the directory for imported sources

This command will clone the dependency repo to some specified directory 
and setup it as a submodule. You need to do this just one time!

Let's assume you're in the root directory of your repo

```
git submodule add https://github.com/Sergey-Anfinogentov/clean_lib clean-lib-dir
git commit -a -m "Added new submodule"
git push origin master
```

#### Updating source code to pull the changes from submodules

Do it every time you want to make the dependencies fresh.

You also need to run these commands after git clone (on a new machine). Otherwise, 
the submodule directory will be empty

```
git submodule update --init --recursive
git submodule foreach git pull origin master
```

