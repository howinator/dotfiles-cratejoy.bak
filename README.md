Used forked macOS guide and this gist

I like to manage dotfiles without having to mess with silly symlinks or having
to install/configure specific dotfile managament tools. So here's what I did:
```
$ cd ~
$ git init .
$ echo '*' > .gitignore                   # ignore all files by default
$ echo '!.bashrc' >> .gitignore           # ...and then tell git what files not to *not* ignore
$         # ...add other files you may want to track to *not* ignore
$ git add .bashrc                         # now actually add the files to git
$ git add .gitignore                      # add the .gitignore to git
$ git submodule add -f git@github.com:lonetwin/lonetvim.git .vim
$         # ...and any other remote repos you may want to track
$ git commit                              # ..and you're done !!

# import into github if you prefer
# Create different 'profiles' as branches (eg: work_profile, home_profile, dev_box ...)

Now, on the next system you want to recreate the dot files:
$ git init .
$ git remote add origin <url to your repo>
$ git fetch
$ # rm .bashrc ... # any files that are present by OS default
$ git checkout <branch name>    # ...and you're done !!
```
