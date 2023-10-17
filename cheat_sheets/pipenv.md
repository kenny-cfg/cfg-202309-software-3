# pipenv

`pipenv` is a widely used package management system. The major advantage of it is that requirements for your project are included in a file in the repository itself. The major disadvantage is that Pycharm doesn't deal with `pipenv` very well, and most likely you'll have to install packages from the command line.

More detailed instructions can be found [here](https://pipenv.pypa.io/en/latest/)

You'll have to install the `pipenv` program first. You can do this using `pip install --user pipenv`. Check that it has installed by typing `pipenv --version` in the command line. You might have to restart your terminal.

Some users (especially Windows, but also sometimes Mac) will experience difficulty getting `pipenv` to run. I haven't quite got to the bottom of why, but if you try this and it fails **you should pipe up immediately**. You should get this sorted out sooner rather than later: it will be quite a big blocker for later parts of the course.

Then

* Navigate to the root folder of your new project
* `pipenv shell` to **activate** your virtual environment
* Install a library using `pipenv install requests`
* You'll notice a `Pipfile` that contains information about what libraries are installed, and a `Pipfile.lock` that specifies exactly what version of your libraries are installed, in your folder
* If you're interested, you can type `pipenv --venv` to find out where `pipenv` has put your virtual environment
* To **deactivate** your virtual environment, `exit`
* To delete your virtual environment, delete the folder pointed to by `pipenv --rm`

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
