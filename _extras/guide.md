---
layout: page
title: "Instructor Notes"
permalink: /guide/
---

____
# Tips and Tricks

____
## Making a handout

Librarians like handouts. To make a handout for this lesson, adapt/print from [https://librarycarpentry.github.io/lc-shell/reference/](https://librarycarpentry.github.io/lc-shell/reference/).

______
## 02-counting-mining.md

This lesson notes that the `grep` flags `-o` and `-E` flag are not supported by Git Bash for Windows (see the callout 'Invalid option – o?'). Be prepared to manage these differences in shell behaviour between operating systems.
  
_____
# General notes on shell

-   Why do we learn to use the shell?
    -   Allows users to automate repetitive tasks
   -   And capture small data manipulation steps that are normally not recorded
        to make research reproducible
-   The Problem
    -   Running the same workflow on several samples can be unnecessarily labour intensive
    -   Manual manipulation of data files:
        -   is often not captured in documentation
        -   is hard to reproduce
        -   is hard to troubleshoot, review, or improve
-   The Shell
    -   Workflows can be automated through the use of shell scripts
    -   Built-in commands allow for easy data manipulation (e.g. sort, grep, etc.)
    -   Every step can be captured in the shell script and allow reproducibility and easy troubleshooting

## Overall

Many people have questioned whether we should still teach the shell.
After all,
anyone who wants to rename several thousand data files
can easily do so interactively in the Python interpreter,
and anyone who's doing serious data analysis
is probably going to do most of their work inside the iPython Notebook or RStudio.
So why teach the shell?

The first answer is,
"Because so much else depends on it."
Installing software,
configuring your default editor,
and controlling remote machines frequently assume a basic familiarity with the shell,
and with related ideas like standard input and output.
Many tools also use its terminology
(for example, the `%ls` and `%cd` magic commands in iPython).

The second answer is,
"Because it's an easy way to introduce some fundamental ideas about how to use computers."
As we teach people how to use the Unix shell,
we teach them that they should get the computer to repeat things
(via tab completion,
`!` followed by a command number,
and `for` loops)
rather than repeating things themselves.
We also teach them to take things they've discovered they do frequently
and save them for later re-use
(via shell scripts),
to give things sensible names,
and to write a little bit of documentation
(like comment at the top of shell scripts)
to make their future selves' lives better.

The third answer is,
"Because it enables use of many domain-specific tools and compute resources researchers cannot access otherwise."
Familiarity with the shell is very useful for remote accessing machines,
using high-performance computing infrastructure,
and running new specialist tools in many disciplines.
We do not teach HPC or domain-specific skills here
but lay the groundwork for further development of these skills.
In particular,
understanding the syntax of commands, flags, and help systems is useful for domain specific tools
and understanding the file system (and how to navigate it) is useful for remote access.

Finally,
and perhaps most importantly,
teaching people the shell lets us teach them
to think about programming in terms of function composition.
In the case of the shell,
this takes the form of pipelines rather than nested function calls,
but the core idea of "small pieces, loosely joined" is the same.

All of this material can be covered in three hours
as long as learners using Windows do not run into roadblocks such as:

-   not being able to figure out where their home directory is
    (particularly if they're using Cygwin);
-   not being able to run a plain text editor;
    and
-   the shell refusing to run scripts that include DOS line endings.

## Preparing to Teach

-   Use the `data` directory for in-workshop exercises and live coding examples.
     You can clone the shell-novice directory or use the `Download ZIP`
     button on the right to get the entire [repository](https://github.com/swcarpentry/shell-novice). We also now provide
     a zip file of the `data` directory that can be downloaded on its own
     from the repository by right-click + save or see the ["setup"]({{ page.root }}/setup/) page on the lesson website for more details.  

-   Website: various practices have been used.
    -   Option 1: Can give links to learners before the lesson so they can follow along,
        catch up,
	and see exercises (particularly if you're following the lesson content without many changes).
    -   Option 2: Don't show the website to the learners during the lesson, as it can be distracting:
        students may read instead of listen, and having another window open is an additional cognitive load.
	-   In any case, make sure to point to website as a post-workshop reference.

-   Content:
    Unless you have a truly generous amount of time (4+ hours),
    it is likely that you will not cover ALL the material in this lesson in a single half-day session.
    Plan ahead on what you might skip, what you really want to emphasize, etc.

-   Exercises:
    Think in advance about how you might want to handle exercises during the lesson.
    How are you assigning them (website, slide, handout)?
    Do you want everyone to try it and then you show the solution?
    Have a learner show the solution?
    Have groups each do a different exercise and present their solutions?

-   `reference.md` can be printed out and given to students as a reference, your choice.

-   Other preparation:
    Feel free to add your own examples or side comments,
    but know that it shouldn't be necessary:
    the topics and commands can be taught as given on the lesson pages.
    If you think there is a place where the lesson is lacking,
    feel free to file an issue or submit a pull request.

## Teaching Notes

-   Super cool online resource!
    <http://explainshell.com/> will dissect any shell command you type in
    and display help text for each piece. Additional nice manual tool could be <http://tldr-pages.github.io/> with short very descriptive manuals for shell commands, useful especially on Windows while using Git BASH where `man` could not work.

-   Another super cool online resource is <http://www.shellcheck.net>,
    which will check shell scripts (both uploaded and typed in) for common errors.

-   Running a text editor from the command line can be
    the biggest stumbling block during the entire lesson:
    many will try to run the same editor as the instructor
    (which may leave them trapped in the awful nether hell that is Vim),
    or will not know how to navigate to the right directory
    to save their file,
    or will run a word processor rather than a plain text editor.
    The quickest way past these problems is to have more knowledgeable learners
    help those who need it.

-   Introducing and navigating the filesystem in the shell (covered in
    [Navigating Files and Directories]({{ page.root }}/02-filedir/) section) can be confusing. You may have both terminal and GUI file explorer open side by side so learners can see the content and file structure while they're using terminal to navigate the system.

-   Tab completion sounds like a small thing: it isn't.
    Re-running old commands using `!123` or `!wc`
    isn't a small thing either,
    and neither are wildcard expansion and `for` loops.
    Each one is an opportunity to repeat one of the big ideas of Software Carpentry:
    if the computer *can* repeat it,
    some programmer somewhere will almost certainly have built
    some way for the computer *to* repeat it.

-   Building up a pipeline with four or five stages,
    then putting it in a shell script for re-use
    and calling that script inside a `for` loop,
    is a great opportunity to show how
    "seven plus or minus two"
    connects to programming.
    Once we have figured out how to do something moderately complicated,
    we make it re-usable and give it a name
    so that it only takes up one slot in working memory
    rather than several.
    It is also a good opportunity to talk about exploratory programming:
    rather than designing a program up front,
    we can do a few useful things
    and then retroactively decide which are worth encapsulating
    for future re-use.

-   If everything is going well, you can drive home the point that file
    extensions are essentially there to help computers (and human
    readers) understand file content and are not a requirement of files
    (covered briefly in [Navigating Files and Directories]({{ page.root }}/02-filedir/)).
    This can be done in the [Pipes and Filters]({{ page.root }}/04-pipefilter/) section by showing that you
    can redirect standard output to a file without the .txt extension
    (e.g., lengths), and that the resulting file is still a perfectly usable text file.
    Make the point that if double-clicked in the GUI, the computer will
    probably ask you what you want to do.

-   We have to leave out many important things because of time constraints,
    including file permissions, job control, and SSH.
    If learners already understand the basic material,
    this can be covered instead using the online lessons as guidelines.
    These limitations also have follow-on consequences:

-   It's hard to discuss `#!` (shebang) without first discussing
    permissions, which we don't do.  `#!` is also [pretty
    complicated][shebang], so even if we did discuss permissions, we
    probably still wouldn't want to discuss `#!`.

-   Installing Bash and a reasonable set of Unix commands on Windows
    always involves some fiddling and frustration.
    Please see the latest set of installation guidelines for advice,
    and try it out yourself *before* teaching a class.

-   On Windows machines
    if `nano` hasn't been properly installed with the
    [Software Carpentry Windows Installer][windows-installer]
    it is possible to use `notepad` as an alternative.  There will be a GUI
    interface and line endings are treated differently, but otherwise, for
    the purposes of this lesson, `notepad` and `nano` can be used almost interchangeably.

-   On Windows, it appears that:

    ~~~
    $ cd
    $ cd Desktop
    ~~~
    {: .bash}

    will always put someone on their desktop.
    Have them create the example directory for the shell exercises there
    so that they can find it easily
    and watch it evolve.

-  Stay within POSIX-compliant commands, as all the teaching materials do.
   Your particular shell may have extensions beyond POSIX that are not available
   on other machines, especially the default OSX bash and Windows bash emulators.
   For example, POSIX `ls` does not have an `--ignore=` or `-I` option, and POSIX
   `head` takes `-n 10` or `-10`, but not the long form of `--lines=10`.
   

## Windows

With the introduction of [GitforWindows](https://gitforwindows.org/), it is much easier to setup BASH in Windows. It is always important to test it out, though. 


## Setting up the Unix Environment

The **.bashrc** file is in your user folder (on Windows C:/Users/*Username*).
Make sure to [display hidden files](https://support.microsoft.com/en-us/help/14201/windows-show-hidden-files). 

### Simplify the Prompt
Note that the BASH prompt and window looks *very* different in the different operating systems. 
So, it can be useful to simplify your display. SWC uses a simple "$" prompt. 
See more information about [customizing your BASH prompt](https://www.howtogeek.com/307701/how-to-customize-and-colorize-your-bash-prompt/) .

Add a line starting with "PS1=" to **.bashrc**

*Examples*:
* A simple $ and space:\
	`PS1='\$ '`
* A $ with a blue background and line numbers:\
	`PS1='\! \[\e[1;37m\]\[\e[44m\]\$\[\e[1;40m\]\[\e[1;37m\] '`
* A unix-style prompt:\
	`PS1='\[\e[0;37m\]\[\e[44m\]user:\[\e[42m\]\w\[\e[40m\]\[\e[1;31m\]\$\[\e[1;37m\] '` 


### Display a Log
Learners may get behind and find it useful to see recent commands. 

**Option 1**: Install the split windows script from <https://github.com/rgaiacs/swc-shell-split-window>. 
* It requires tmux, which isn't natively supported in windows. But, there are options:
	* https://blog.pjsen.eu/?p=440
	* https://veerasundar.com/blog/2018/03/how-to-split-the-terminal-into-multiple-views-in-windows-10/

**Option 2**: Use a separate file viewer. A good cross-platform viewer is [glogg](http://glogg.bonnefon.org/). Atom can also be set up to do this. 
1. Add the following line to **.bashrc** so that it will update the history immediately:\
		`PROMPT_COMMAND="history -a;$PROMPT_COMMAND"`
1. In the file viewer, open the file **.bash_history** (in the same folder as .bashrc)
1. Set the viewer to automatically load file changes (in glogg, go to "View" then "Follow File") 
1. If you have the prompt display line numbers, you can show those too.  
