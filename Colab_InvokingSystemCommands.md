# Google Colab - Invoking System Commands
[tutorialspoint](https://www.tutorialspoint.com/google_colab/google_colab_invoking_system_commands.htm)

Jupyter includes shortcuts for many common system operations. Colab Code cell supports this feature.

## Simple Commands

Enter the following code in the Code cell that uses the system command echo.
```
message = 'A Great Tutorial on Colab by Tutorialspoint!'
greeting = !echo -e '$message\n$message'
greeting
```
Now, if you run the cell, you will see the following output −

['A Great Tutorial on Colab by Tutorialspoint!', 'A Great Tutorial on Colab by Tutorialspoint!']

## Getting Remote Data

Let us look into another example that loads the dataset from a remote server. Type in the following command in your Code cell −
```
!wget http://mlr.cs.umass.edu/ml/machine-learning-databases/adult/adult.data -P "/content/drive/My Drive/app"
```
If you run the code, you would see the following output −
```
--2019-06-20 10:09:53-- http://mlr.cs.umass.edu/ml/machine-learning-databases/adult/adult.data
Resolving mlr.cs.umass.edu (mlr.cs.umass.edu)... 128.119.246.96
Connecting to mlr.cs.umass.edu (mlr.cs.umass.edu)|128.119.246.96|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 3974305 (3.8M) [text/plain] 
Saving to: /content/drive/My Drive/app/adult.data.1

adult.data.1 100%[===================>] 3.79M 1.74MB/s in 2.2s

2019-06-20 10:09:56 (1.74 MB/s) - /content/drive/My Drive/app/adult.data.1 saved [3974305/3974305]
```

As the message says, the `adult.data.1` file is now added to your drive. You can verify this by examining the folder contents of your drive. Alternatively, type in the following code in a new Code cell −
```
import pandas as pd
data = pd.read_csv("/content/drive/My Drive/app/adult.data.1")
data.head(5)
```

Run the code now and you will see the following output −

Likewise, most of the system commands can be invoked in your code cell by prepending the command with an Exclamation Mark (!). Let us look into another example before giving out the complete list of commands that you can invoke.

## Cloning Git Repository

You can clone the entire GitHub repository into Colab using the gitcommand. For example, to clone the keras tutorial, type the following command in the Code cell −
```
!git clone https://github.com/wxs/keras-mnist-tutorial.git
```

After a successful run of the command, you would see the following output −
```
Cloning into 'keras-mnist-tutorial'...
remote: Enumerating objects: 26, done.
remote: Total 26 (delta 0), reused 0 (delta 0), pack-reused 26
Unpacking objects: 100% (26/26), done.
```

Once the repo is cloned, locate a Jupyter project (e.g. MINST in keras.ipyab) in it, right-click on the file name and select Open With / Colaboratory menu option to open the project in Colab.

## System Aliases

To get a list of shortcuts for common operations, execute the following command −
```
!ls /bin
```

You will see the list in the output window as shown below −
```
bash*             journalctl*       sync*
bunzip2*          kill*             systemctl*
bzcat*            kmod*             systemd@
bzcmp@            less*             systemd-ask-password*
bzdiff*           lessecho*         systemd-escape*
bzegrep@          lessfile@         systemd-hwdb*
bzexe*            lesskey*          systemd-inhibit*
bzfgrep@          lesspipe*         systemd-machine-id-setup*
bzgrep*           ln*               systemd-notify*
bzip2*            login*            systemd-sysusers*
bzip2recover*     loginctl*         systemd-tmpfiles*
bzless@           ls*               systemd-tty-ask-password-agent*
bzmore*           lsblk*            tar*
cat*              lsmod@            tempfile*
chgrp*            mkdir*            touch*
chmod*            mknod*            true*
chown*            mktemp*           udevadm*
cp*               more*             ulockmgr_server*
dash*             mount*            umount*
date*             mountpoint*       uname*
dd*               mv*               uncompress*
df*               networkctl*       vdir*
dir*              nisdomainname@    wdctl*
dmesg*            pidof@            which*
dnsdomainname@    ps*               ypdomainname@
domainname@       pwd*              zcat*
echo*             rbash@            zcmp*
egrep*            readlink*         zdiff*
false*            rm*               zegrep*
fgrep*            rmdir*            zfgrep*
findmnt*          run-parts*        zforce*
fusermount*       sed*              zgrep*
grep*             sh@               zless*
gunzip*           sh.distrib@       zmore*
gzexe*            sleep*            znew*
gzip*             stty*
hostname*         su*
```

Execute any of these commands as we have done for echo and wget. In the next chapter, we shall see how to execute your previously created Python code.