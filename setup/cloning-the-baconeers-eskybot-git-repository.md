# Cloning the BaCoNeers EskyBot git repository with TortoiseGit

Choose the directory where you want to build the project from. Don't use a GoogleDrive or One Drive for this, use a local disk.

* Navigate to the directory in Windows Explorer \(Win+E\)

right-click and select "Git-Clone..."

![](/assets/gitclone.png)

* Enter `https://github.com/BaCoNeers/EskyBot.git` in the URL field

* And use a depth of 1[^1]

![](/assets/gitclone2.png)

* and click OK 

![](/assets/gitclone4.png)

* After it has finished you should see a directory called EskyBot with a green tick overlay. The green tick indicates that the git project has no uncommitted changes.



[^1]: We use a depth of 1 because the EskyBot repository is a clone of https://github.com/ftctechnh/ftc\_app.git and it has a large history. Using a Depth of 1 reduces the amount of data you need to download.

