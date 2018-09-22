# janny-hexo

Post anywhere and Autosync everywhere.

Powered by hexo, Themed by jane, Controled by telcmd.

## What does Janny do?

1. Accept remote article: through open http API (i.e. `http://yourhost/telcmd?hexo`), and write it into `source/_post/${title}.md`. 

2. Run depoly script (i.e. `hexo generate && hexo deploy`), publish articles to Hexo Git pages.

3. Sync with your PC: run `git push` at Janny server, then telcmd send a command `git pull` to your PC. 


## Prepare

1. Your server

2. Create repositiry `yourname.github.io`

3. Fork repositiry `janny-hexo`

4. Install git & node, setup your git account

## Installation

```
git clone https://github.com/YourName/janny-hexo.git
cd janny-hexo
npm install
```

## Run

Server side:

```
// Start telcmd
forever start telcmd/server.js
```

PC side [optional]:

```
// Start telcmd
forever start telcmd/client.js
```

## Usage:

 - Post article by PC: 
 
     1. run command `new.bat` create a post
	 
	 2. run command `hx.bat` to review [optional]
	 
	 3. run command `sync.bat` to sync to server 
	 
 - Post article by http API: `http://yourhost:81/telcmd?hexo`

