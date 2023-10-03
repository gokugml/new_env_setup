Over All Steps
===================

|index|          	|             	| content                                                                                             	|
|--- |----------	|-------------	|-----------------------------------------------------------------------------------------------------	|
| 1 | Must     	| Vpn         	| clash                                                                                               	|
| 2 | Must     	| Iterm2      	| [iterm2 Profile import](iterm2Profiles.json)<br>[oh my zsh](https://ohmyz.sh/)<br>`echo 'bindkey \^U backward-kill-line' >> ~/.zshrc`                         	|
| 3 | Must     	| ScreenSplit 	| [Rectangle](https://rectangleapp.com/) <br> [Other Suggest](https://www.v1tx.com/post/best-mac-split-screen-app/) 	|
| 4 | Must     	| Git&Python  	| [Miniconda](https://docs.conda.io/en/latest/miniconda.html) <br>[Pre-commit](https://pre-commit.com/)                                              	|
| 5 | Must     	| Develop     	| [Homebrew](https://brew.sh)<br> LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443  <br>[Vscode](https://code.visualstudio.com/)                                                                 	|
|6| Optional 	| SSH         	| Multiple SSH                                                                                        	|
| 7 | Suggest  	| Other       	| Alfred<br>![other useful](other_useful_app.png)                                                                                    	|



SSL_ERROR_SYSCALL
=====================

```bash
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```
https://stackoverflow.com/questions/48987512/ssl-connect-ssl-error-syscall-in-connection-to-github-com443




Multiple SSH Keys settings for different github account
=================================================================


create different public key
---------------------------------

create different ssh key according the article [Mac Set-Up Git](http://help.github.com/mac-set-up-git/)

	$ ssh-keygen -t rsa -C "your_email@youremail.com"

Please refer to [github ssh issues](http://help.github.com/ssh-issues/) for common problems.

for example, 2 keys created at:

	~/.ssh/id_rsa_github1
	~/.ssh/id_rsa_github2

then, add these two keys as following

	$ ssh-add ~/.ssh/id_rsa_github1
	$ ssh-add ~/.ssh/id_rsa_github2

you can delete all cached keys before

	$ ssh-add -D

finally, you can check your saved keys

	$ ssh-add -l


Modify the ssh config
---------------------------------

	$ cd ~/.ssh/
	$ touch config
	$ vi config

Then added

	#github1 account
	Host github.com-github1
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_github1

	#github2 account
	Host github.com-github2
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_github2


Clone you repo and modify your Git config
---------------------------------------------

clone your repo (change default git@github.com to git@github.com-github2)
	git clone git@github.com-github2:github2/gfs.git 

cd gfs_github2 and modify git config

	$ git config user.name "github2"
	$ git config user.email "github2@gmail.com" 
 

or you can have global git config
	$ git config --global user.name "github2"
	$ git config --global user.email "github2@gmail.com"


then use normal flow to push your code

	$ git add .
	$ git commit -m "your comments"
	$ git push


Pylint
=========

'''bash
pip install pylint-flask

pip install pylint-flask-sqlalchemy
'''


"python.linting.pylintArgs": ["--load-plugins", "pylint_flask_sqlalchemy", "pylint_flask"]
https://stackoverflow.com/questions/28193025/pylint-cant-find-sqlalchemy-query-member


https://stackoverflow.com/questions/42789666/pylint-error-message-on-cloud-9-cs50
