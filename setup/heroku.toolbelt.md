

# Setting Up Heroku Toolbelt on CSIL

There are various tutorials for Heroku such as the following that contain a step where you "Install the Heroku Toolbelt".  It is important to know that *the instructions as given do not work on CSIL*.   These alternative instructions are what you should do instead.

Here is a partial list of the tutorials that includes a "Install Heroku Toolbelt" step that you should SKIP and do the instructions on this page instead:

* [Getting Started on Heroku with Python](https://devcenter.heroku.com/articles/getting-started-with-python)
* [Getting Started on Heroku with Java](https://devcenter.heroku.com/articles/getting-started-with-java)
* etc.

So when you get to the step that says "In this step you will install the Heroku Toolbelt", know that:

**This instructions for this step, as written, absolutely will not work from a non-privileged account on CSIL.**

If you are working on a CSIL machine—that is, a machine in Phelps 3525, the CSIL lab, or ssh'ing into CSIL—as opposed to working completely on your own computer, without using CSIL resources at all—you will need to make significant modifications to the instructions for this step.

Read and follow the instructions in this step carefully, and you should have no trouble.

The following steps "mirror" what the automatic "Set Up the Heroku Toolbelt" procedure does, but in a way that will work on your CSIL account:

(1) Create a directory ${HOME}/heroku/bin

    mkdir -p ${HOME}/heroku/bin

(2) cd into that directory

    cd ${HOME}/heroku/bin

Use `ls` to verify that this is an empty directory. If not, empty it out before proceeding. (If you aren't sure how, get some Unix help from a knowledgeable person.)

(3a) Download the tarball for the Heroku client. This URL comes from the install script that was in the "install.sh" that the Heroku "Standalone" option wanted us to download and execute directly. 

Using a browser, navigate to this file.  You don't need to download it or execute it: just want to look inside it.

* https://toolbelt.heroku.com/install.sh

Near the top, there should be a line such as this one:

```
 HEROKU_CLIENT_URL="https://s3.amazonaws.com/assets.heroku.com/heroku-client/heroku-client.tgz"
```

That URL, i.e. https://s3.amazonaws.com/assets.heroku.com/heroku-client/heroku-client.tgz is the URL for a file that we are going to download directly.    We need to download it directly rather than using the install.sh script provided by Heroku, because installation on CSIL has to be slightly "adjusted" for our local environment.

The command you are going to type on CSIL is this one.  Make sure the URL matches the one in the file online (just in case they moved it or renamed it.)

    wget https://s3.amazonaws.com/assets.heroku.com/heroku-client/heroku-client.tgz


Now that you've downloaded this file, are are going to "unpack it".   That's called "untar-ing the tarball", and its similar to opening up a "zip" file (i.e. a compressed file containing lots of stuff inside.)

(3b) Untar the tarball.

    tar -xvf heroku-client.tgz

(4) You should now have a subdirectory called `heroku-client`.

And, you should now be able to run the heroku toolbelt client by typing the following. Give it a try:

    ${HOME}/heroku/bin/heroku-client/bin/heroku

(5) Optional: If you want to add this into your path, you should be able to do so by putting the following in your ${HOME}/.profile file (assuming you are using bash as your shell)

    export PATH=${PATH}:${HOME}/heroku/bin/heroku-client/bin

That should allow you to just type "heroku" to run the heroku-client. Note that like any change to your .profile file, you either have to reload it to your shell, or open a new login shell to see the effect take place.

Try typing `heroku` at the shell prompt when logged into CSIL.

What do you see?

<table style="border: 1px solid black;">
<tr>
<td style="width:50%">
<b>This is what you want to see:</b>

</td>
<td style="width:50%">
<b>This is what you do NOT want to see:</b>

</td>
</tr>
<tr>
<td style="vertical-align:top;">
    -bash-4.3$ heroku
    -bash-4.3$ heroku
    Updating Heroku v4 CLI to 4.27.9-cce0260 (master)... done
    Updating plugins... done
    rebuilding plugins cache... done
    Usage: heroku COMMAND [--app APP] [command-specific-options]

    Primary help topics, type "heroku help TOPIC" for more details:

<em>\[Many lines of output omitted\]</em>

      twofactor    #  manage two-factor authentication settings
      update       #  update the heroku client
      version      #  display version
    -bash-4.3$ 

In this case, click on the button on the Heroku tutorial web page, and continue:

<http://www.cs.ucsb.edu/~pconrad/images/heroku/50/IHaveDownloadedTheToolbelt.png>

</td>
<td style="vertical-align:top;">
    -bash-4.3$ heroku
    bash: heroku: command not found...
    Install package 'rubygem-heroku' to provide command 'heroku'? [N/y] 

In this case, type N and hit enter, and then read through this step again.

</td>
</tr>
</table>



