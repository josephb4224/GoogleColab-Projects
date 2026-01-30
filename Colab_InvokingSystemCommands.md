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

---

## Magics List

To get a complete list of supported magics, execute the following command −
```
%lsmagic
```

You will see the following output −
```
Available line magics:
%alias %alias_magic %autocall %automagic %autosave %bookmark %cat %cd %clear
%colors %config %connect_info %cp %debug %dhist %dirs %doctest_mode %ed %edit
%env %gui %hist %history %killbgscripts %ldir %less %lf %lk %ll %load %load_ext
%loadpy %logoff %logon %logstart %logstate %logstop %ls %lsmagic %lx %macro
%magic %man %matplotlib %mkdir %more %mv %notebook %page %pastebin %pdb %pdef
%pdoc %pfile %pinfo %pinfo2 %pip %popd %pprint %precision %profile %prun
%psearch %psource %pushd %pwd %pycat %pylab %qtconsole %quickref %recall
%rehashx %reload_ext %rep %rerun %reset %reset_selective %rm %rmdir %run %save
%sc %set_env %shell %store %sx %system %tb %tensorflow_version %time %timeit
%unalias %unload_ext %who %who_ls %whos %xdel %xmode

Available cell magics:
%%! %%HTML %%SVG %%bash %%bigquery %%capture %%debug %%file %%html %%javascript
%%js %%latex %%perl %%prun %%pypy %%python %%python2 %%python3 %%ruby %%script
%%sh %%shell %%svg %%sx %%system %%time %%timeit %%writefile
```
Automagic is `ON`, `%` prefix IS NOT needed for line magics.

Next, you will learn another powerful feature in Colab to set the program variables at runtime.

----

# Google Colab - Executing External Python Files

Suppose, you already have some Python code developed that is stored in your Google Drive. Now, you will like to load this code in Colab for further modifications. In this chapter, we will see how to load and run the code stored in your Google Drive.

## Mounting Drive
```
Tools / Command palette
```

Type a few letters like m in the search box to locate the mount command. Select `Mount Drive` command from the list. The following code would be inserted in your Code cell.
```
# Run this cell to mount your Google Drive.
from google.colab import drive
drive.mount('/content/drive')
```

If you run this code, you will be asked to enter the authentication code. The corresponding screen looks as shown below −
```
Go to this URL in a browser: https://accounts.google.com/o/oauth2/auth?client_id=94534236342k3r32rl1rnr3

Enter your authorization code:
```

Open the above URL in your browser. You will be asked to login to your Google account. Now, you will see the following screen −

Now, you are ready to use the contents of your drive in Colab.

## Listing Drive Contents

You can list the contents of the drive using the ls command as follows −
```
!ls "/content/drive/My Drive/Colab Notebooks"
```
This command will list the contents of your Colab Notebooks folder. The sample output of my drive contents are shown here −
```
Greeting.ipynb hello.py LogisticRegressionCensusData.ipynb LogisticRegressionDigitalOcean.ipynb MyFirstColabNotebook.ipynb SamplePlot.ipynb
```

## Running Python Code

Now, let us say that you want to run a Python file called hello.py stored in your Google Drive. Type the following command in the Code cell −
```
!python3 "/content/drive/My Drive/Colab Notebooks/hello.py"
```
The contents of hello.py are given here for your reference −
```
print("Welcome to TutorialsPoint!")
```
You will now see the following output −
```
Welcome to TutorialsPoint!
```
Besides the text output, Colab also supports the graphical outputs. We will see this in the next chapter.
