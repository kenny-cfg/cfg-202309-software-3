# pipenv

`pipenv` is a widely used package management system. The major advantage of it is that requirements for your project are included in a file in the repository itself. The major disadvantage is that Pycharm doesn't deal with `pipenv` very well, and most likely you'll have to install packages from the command line.

More detailed instructions can be found [here](https://pipenv.pypa.io/en/latest/)

You'll have to install the `pipenv` program first. You can do this using `pip install --user pipenv`, or `pip3 install pipenv` if you have Python3 installed. Check that it has installed by typing `pipenv --version` in the command line. You might have to restart your terminal.

Some users (especially Windows, but also sometimes Mac) will experience difficulty getting `pipenv` to run. I haven't quite got to the bottom of why, but if you try this and it fails **you should pipe up immediately**. You should get this sorted out sooner rather than later: it will be quite a big blocker for later parts of the course.

For Mac users who are having difficult getting pipenv, you may need to set the path of pipenv on your machine, see this [video](https://www.youtube.com/watch?v=Bzn_MZ0tNXU) for the following:

* `python3 -m site --user-base` to find your user base directory of Python. Change `python3` to `python` if you have that version installed instead
* Copy the path printed in your terminal. It should look something like /Users/yourname/Libary/Python/3.11
* `code ~/.zshrc` to open your zshell file in VScode
* At the top of your zshell file, type `export PATH="$PATH:<paste your path here>/bin"` and save the file and close
* `pipenv --version` in a new terminal window. Your pipenv should now run

Then

* Navigate to the root folder of your new project
* `pipenv shell` to **activate** your virtual environment
* Install a library using `pipenv install requests`
* You'll notice a `Pipfile` that contains information about what libraries are installed, and a `Pipfile.lock` that specifies exactly what version of your libraries are installed, in your folder
* If you're interested, you can type `pipenv --venv` to find out where `pipenv` has put your virtual environment
* To **deactivate** your virtual environment, `exit`
* To delete your virtual environment, delete the folder pointed to by `pipenv --rm`
* To get the location of your virtual environment folder, `pipenv --venv`

## Under the bonnet

What `pipenv` does is quite clever.
* `pipenv shell` sets up your environment variable to point to a virtual environment folder
  * If no virtual environment folder exists, `pipenv shell` creates one
* `pipenv install <package_name>`
  * installs `<package_name>` into your virtual environment folder
  * adds this dependency to the `Pipfile`
  * adds the *exact* version number to the `Pipfile.lock`
* `pipenv install` (with no package name)
  * reads the `Pipfile.lock` and installs the *exact* versions specified
