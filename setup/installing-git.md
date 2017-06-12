# Installing Git

## Tortoise Git

TortoiseGit is a windows shell extension that makes performing Git operations from the Windows File Explorer easy and intuitive.

* Install TortoiseGit from [https://tortoisegit.org/download/](https://tortoisegit.org/download/)

If you are unsure which version to install, install the 64-bit version.

## Git

During the installation of TortoiseGit it will probably ask you to install Git as well.

* Install Git for windows [https://git-for-windows.github.io/](https://git-for-windows.github.io/)

## \(Only\) if you have BlueCoat or other SSL Inspection Systems

If your network uses SSL Inspection, when you try to connect to a https git repository, your git client will receive an SSL certificate which does not match the destination. Git clients by default will attempt to validate the certificate and fail to connect if it detects that the certificate is not from the destination.

To overcome this _\(and you should only do this if this is a problem for you\)_:

* Open a CMD.EXE window and type the following
  `git config --global http.sslVerify false`



