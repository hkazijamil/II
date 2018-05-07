How to install and configure Python on a hosted server

By Steven Vaughan-Nichols June 1, 2015
Uncoiling the path to Python
Developers know that you can’t spell LAMP (Linux, Apache, MySQL, Perl/PHP/Python) on many systems without Python. And although, you are probably well aware that LAMP is the server stack powering today’s Internet, you might be wondering why you should pay attention to Python. Read on for more about the power of Python and how to install and configure this high-level programming language on a hosted server.

What is Python?

Among all three aforementioned programming languages, Python is king. Why? Clear programs, code readability and convenience (read: fewer lines of code). Python takes the bite out of a developer’s job in some ways because, once written, this general-purpose language can run pretty much on any computer without requiring you to change the program. Python is key to such Internet essential programs as the GNU Mailman, mailing-list manager; Yum, the Red Hat Enterprise Linux (RHEL) family’s package manager; and the Zope content-management system (CMS) application server.

How to check whether Python is already installed

Chances are Python is already installed on your hosted Linux server. If you’re unsure, follow these easy steps:

1. Run the following from your ssh terminal:

$ ls -la /usr/bin/python
Note: Keep in mind /usr/bin/python is the default location for the python executables.

2. Use the following command to see which version of Python you’re working with:

$ Python -V
How to check which version of Python you are running

Checking which version of Python you are running depends on which Linux you’re using and the patches that have been applied to it. With many hosted servers running the CentOS 6 distribution of Linux, the server uses Python 2.6.6. But again, it’s best to double check. Plus, if you’d rather use a newer version of Python, say Python 2.7.2, that never version might be already installed.

What you’ll need to install and configure Python

To get going with Python, you’ll need a server. We recommend a GoDaddy VPS or a full dedicated server if you’re ready to take total control. Additionally, various GoDaddy shared hosting plans — including Deluxe, Premium, Unlimited, or Ultimate Linux Web and Classic — support Python. (Note: It is not available on cPanel and Plesk Economy shared hosting accounts.) Now, you might be asking yourself, “What kind of hosting account do I have?” Simply log into your account, locate the Products tab, then expand your view of Servers by clicking the “+” button to the left. You should see which kind of server account you own.

Which version of Python to use

The vast majority of Python-based apps will run just fine with Python 2.6.x or 2.7.x. The latest version is up to Python 3.4.3 (as of May 2015), but updates to the Python 2.7 branch are still not ready. The Python community supports both Python 2.x and 3.x, because Python 2.x was, and remains, very popular. Many programs still rely on it. Furthermore, Python 3.x is not fully backwards-compatible with some Python 2.x features. If you prefer to use Python 3.x, refer to the step-by-step installation instructions below.

How to install Python 3

If you’re brave, you can install Python 3 yourself by taking the following steps:

1. Transfer the compression version of the files to your server.

$ wget https://www.python.org/ftp/python/3.4.3/Python-3.4.3.tgz
2. Decompress the files with the following command:

$ tar xvzf Python-3.4.3.tgz
Note: This will create the directory /home/user-name/Python-3.4.3 and automatically decompress all of Python’s files into their appropriate spots.

3. Go into that directory with:

$ cd Python-3.4.3
4. Once inside that directory, install your new version of Python.

$ ./configure --prefix=$HOME/.local
$ ./configure --prefix=$HOME/.local --enable-optimizations --enable-shared
Note: This step sets up your configuration and makes files.

5. Then run this command:

$ make
6. And follow that up with:

$ make install
if problem with zlib
$ apt-get install zlib1g-dev
The last command will install two of the most useful Python utilities:

pip: Python’s recommended tool for installing Python packages.
setuptools: Enables you to download, build, install, and uninstall Python packages.
Fairly easy, but you’re not done yet. Next, you must add the path to your environment. I use vi, the one true editor, for this but you can use Emacs, nano, or any other pure text editor. Never use a word processor, such as Microsoft Word or LibreOffice Writer. These add formatting codes to their documents, which make them worse than useless for coding purposes.

1. Go into your Bash profile configuration file:

$ cd $home
$ vi .bash_profile
2. With an editor, add the following lines, then save the file:

# Python 3 
export PATH="$HOME/.local/bin:$PATH"
3. Run the following to get your environment up to date:

$ source ~/.bash_profile
4. Then run the following from the shell and you should see Python 3.4.3:

$ python3 -V
You now have Python 3 installed. Congratulations!

Why not just run “python”?

If you just run “python,” the executable will show the version number for the default Python for your version of Linux — not your newly installed version of Python. Confusing, I know. You will now have two versions of one language on your server.

The best way to handle this is to use Python’s virtualenv module to create a virtual Python environment. Inside this container-like environment, you can use your newer version of Python — such as Python 3.4.3 or 2.7.2. — without interfering with the preexisting Python.

How to create a virtual Python environment

The easiest way to create a virtual Python environment is to use pip.

1. Install virtualenv for all users on your server with this basic command:

$ python3 -m pip install virtualenv
2. Or, if you’d rather keep this to the current user, use this command:

$ python -m pip install –user virtualenv
3. Then create a directory to use your new environment:

$ mkdir PythonTest
4. Enter the new directory:

$ cd PythonTest
5. And run the following to create a virtual Python environment, named PythonTest, in the PythonTest directory:

$ virtualenv PythonTest
6. Activate this new Python “container” with:

$ source PythonTest/bin/activate
Your shell prompt should now include PythonTest, or whatever you named your Python environment. Now, you’re ready to start programming with Python. Of course, you can always just use a default older Python as well.

For more on the basics of using virtualenv, see Python Guide’s Virtual Environments. Or, if you’re new to Python, refer to the Beginner’s Guide to Python. Got questions or comments on taming the beast we call Python? Connect with the dev community, and share your breakthroughs (or even your breakdowns) in the comments below.

Image by:	jurvetson via Compfight cc

#servers #development #hosting
Steven Vaughan-Nichols
Steven Vaughan-Nichols

Steven J. Vaughan-Nichols (aka sjvn) has been writing about technology and the business of technology since CP/M-80 was the cutting edge, PC operating system, 300bps was a fast Internet connection, WordStar was the state of the art word processor, and we liked it. His work has been published in everything from highly technical publications (IEEE Computer, ACM NetWorker, Byte) to business publications (eWEEK, InformationWeek, ZDNet) to popular technology (Computer Shopper, PC Magazine, PC World) to the mainstream press (Washington Post, San Francisco Chronicle, BusinessWeek).