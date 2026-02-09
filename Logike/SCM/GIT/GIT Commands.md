### Create a new repository on the command line

```
git init
git add *
git commit -m "first commit"
git remote add origin http://172.18.22.63:3000/BCO/sib-scheduled.git
git push -u origin master
```

### Push an existing repository from the command line

```
git remote add origin http://172.18.22.63:3000/BCO/sib-scheduled.git
git push -u origin master
```

### Set settings

```
git config --global user.name "javier.latorre"

git config --global user.email "javier.latorre@brueckner.co"

git config --list
```