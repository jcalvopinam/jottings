# Manage projects :aws

## Create a virtual environment
You create a virtual environment by calling the `venv` module. The module expects a name as an argument.
Take the following steps:
- Go to the directory where you want to keep your project.
- Use the following command to call the `venv` module.
```shell
python -m venv env
```

At this point, some directories are created for you. The directory names differ slightly depending on your operating system.
- For `Windows`:
```shell
/env
/include
/lib
/Scripts
```

- For  `Linux` and `macOS`:
```shell
/env
/bin
/include
/lib
```

- Your environment needs the `env` directory to keep track of details like which version of Python and which libraries you're using. Don't put your program files in the `env` directory. We suggest that you put your files in a directory called `src` or something similar. The project structure might then look like this:
```shell
/env
/src
program.py  
```


## Activate the virtual environment
- At this point, you have a virtual environment, but you haven't started using it. To use it, you need to activate it by calling an `activate` script.
- On `Windows:`
```shell
C:\ .. \env\Scripts\activate
```

- On `Linux` and `macOS`:
```shell
source env/bin/activate
```

- Calling `activate` changes your prompt. It's now preceded with `(env)` and looks something like this example:
```shell
(env) -> path/to/project
```

## Install a package
- If you run `pip freeze`, you'll see a much longer list of dependencies. This list indicates that you see all the packages installed on your machine rather than just what's installed in your virtual environment.

- Run `pip freeze` to see installed libraries in your environment:
```shell
pip freeze
```
You should get no response. Next, let's see how the output of `pip freeze` changes when you add a library (a package).

- To install a package, run `pip install` from the `env` directory, like in this example:
```shell
pip install python-dateutil
```

- To install a specific version, use `===` between the package name and the version number. Here's an example command:
```shell
pip install python-dateutil===1.4
```

- A large output of text says it's installing your library, and it should end with the following sentence:
```shell
Successfully installed python-dateutil-2.8.2 six-1.16.0 
```

- Rerun `pip freeze` to see how your list of libraries has changed:
```shell
pip freeze
```

- Now you should see the following list:
```shell
python-dateutil==2.8.2
six==1.16.0
```

- If you run the preceding command, you'll download and install `dateutil`, a package for parsing the .yml file format. After you install the package, you can see it listed if you expand the _lib_ directory under _env_, like this:
```shell
/env
  /lib
    /dateutil
```

- To see what packages are now installed in your virtual environment, you can run `pip freeze`. This command produces a list of installed packages in the terminal:
```shell
python-dateutil==2.8.2
six==1.16.0
```

**Note**
- The reason that the preceding list contains more than just `pipdate` is that `pipdate` itself relies on other libraries that are also fetched.
- To ensure that these packages exist only in your virtual environment, try stepping out of that environment by calling `deactivate`:
```shell
deactivate
```

- Notice how the terminal prompt changes. It's no longer preceded by `(env)` and has reverted to this appearance:
```python
path/to/project
```


## Deactivate a virtual environment
- So far, you've created a virtual environment and added a package to it. However, you might be working on several Python projects and need to change between them. To do that, you need step out of (_deactivate_) your virtual environment.
- Run the `deactivate` command:
```shell
deactivate
```
Note how your terminal prompt changes from `(env)` to how it looked before.

## More ways to install a package
-   Have a set of files on your machine and install from that source:
```shell
cd <to where the package is on your machine>
python3 -m pip install .
```

-   Install from a GitHub repository that provides version control:
```shell
git+https://github.com/your-repo.git
```

-   Install from a compressed archive file:
```shell
python3 -m pip install package.tar.gz
```

## Use an installed package
- You now have a package installed. How do you use it in code?
- Ensure that you have a directory for your files. We suggest that you call the directory _src_ and add an entry-point Python file called _app.py_. Now add some code to call `dateutil`:
```python
from datetime import *
from dateutil.relativedelta import *
now = datetime.now()
print(now)

now = now + relativedelta(months=1, weeks=1, hour=10)

print(now)
```

- Run the app:
```shell
python newapp.py
```

- The output should look something like this:
```shell
2023-01-30 17:04:24.799976
2023-03-07 10:04:24.799976
```

## Upgrade a package
- Packages change over time, as previously stated. You can upgrade to the latest package without specifying what the exact version number is. Use this command:
```shell
pip install <name of package> --upgrade
```

- If you want to  specify that you want to upgrade only if there are new patch versions that use the "2.7.\*" pattern.
```shell
pip install "python-dateutil==2.7.*" --upgrade
```

## Clean up unused packages
- Sometimes, you might realize that you no longer need a certain Python package and you want to remove it. For such a case, you can use `pip uninstall`:
```shell
pip uninstall python-dateutil
```

- However, if you run `pip freeze`, you see how the preceding command removed only the `python-dateutil` library.
```shell
six==1.16.0
```

- This can be problematic, because your project now might contain many unused libraries that take up space. To clear out everything that this package depended on, you can write all installed packages to a _requirements.txt_ list, like this:
```python
pip freeze > requirements.txt
```

Then remove all the packages in that list, like this:
```python
pip uninstall -r requirements.txt -y
```

# Reference
- [python-create-manage-projects](https://learn.microsoft.com/en-us/training/modules/python-create-manage-projects/2-set-up-project)