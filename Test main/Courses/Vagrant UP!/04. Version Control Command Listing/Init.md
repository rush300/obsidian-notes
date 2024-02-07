cd ~
which git
git version
cd projects/demo
ls -al
git init
git add Vagrantfile
git commit -m "Adding vagrantfile"
vi .gitignore
>.vagrant
>:wq!
git add .gitignore
git commit -m "Add gitignore file"
git log --oneline

vi Vagrantfile
>#Hello from Version Control
>:wq!

git status
git commit -a -m "updated vagrant config"
git log --oneline


