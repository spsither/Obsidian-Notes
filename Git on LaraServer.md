On LaraServer /srv/git/ there are bare git repositories 
To add a bare repository do the following
>git clone --bare /var/www/html/react-tibet-museum /src/git/react-tibet-museum.git

To clone a repository from the bare 
>git clone git@172.28.13.45:/srv/git/react-tibet-museum.git

Push to all the remote
>git remote | xargs -L1 git push --all

I created an alias **grp** for the above command in ~/.zshrc


To add remote lara to local repositories
> git remote add lara git@172.28.13.45:/srv/git/react-tibet-museum.git

To give /usr/bin/bash shell access to git do the following.
>sudo chsh git

I had to give bash shell to user git so I could add ssh key to the LaraServer
> ssh-copy-id -i .ssh/id_rsa.pub git@172.28.13.45


