In your terminal, set the project to to sign: 
git config commit.gpgsign true
git config --global commit.gpgsign true
In the config file ~/.gnupg/gpg.conf add:
no-tty
use-agent