How to set up your git and walk through some frustrating git problem:
Follow all instruction displayed on GitHub, if everything fine with you, congratz.


git push origin master.

ERROR: Please make sure you have the correct access rights and the repository exists.

Here is about your ssh key:
1. reset your git information.

git config --global user.name "yourname"

git config --global user.email“your@email.com"

2. search .ssh folder you will find
  id_rsa
  id_rsa.pu
  known_hosts

  this is how does GitHub do verification
  you can delete all of them because they will be regenerate later or if you want you can only delete known_hosts,and  id_rsa and id_rsa.pu will be overwitted later

3.ssh-keygen -t rsa -C "your@email.com"

you will see :

Generating public/private rsa key pair.

Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):  

press Enter
it will also ask you for passphrases, press Enter

4. it will generate id_rsa and id_rsa.pub you can open id_rsa.pub by notebook copy all the information and paste on (GitHub->Profile->SSH and GPG keys->New SSH Key)

add ssh key

5. ssh -T git@github.com
If you see the greeting words from GitHub. everything works fine right now.

6. try git push origin master again
if sth like:
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 337 bytes | 337.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:Username/TQR.git

it works right now

or maybe
fatal: unable to access 'https://github.com/username/someTitle.git/': error:1407742E:SSL routines:SSL23_GET_SERVER_HELLO:tlsv1 alert protocol version

the reason why we saw this is that GitHub did not support tlsv1 protocol anymore after 2018-02-22. Because tlsv1 is weak.

7. check TLS version
git config --global --list

8. git config --global --unset http.sslVersion
   git config --global --add http.sslVersion tlsv1.2

9. try git push origin master again, always make sure update your git and reopen cmd or bash terminal after you uninstall or install sth.

10. git clone git@github.com:Username/somerepo.git

11. after update
    git add.  (add all things you change)
    git commit -m "description" (description about your change)
    git push origin master


requirements.txt installment

pip freeze > requirements.txt
pip install -r requirements.txt
