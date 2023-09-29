# Contents

## Lesson 1:
[1. Set up repository + README.md](#1.1)
[2. Set up new environment (venv)](#1.2)
[3. Create necessary files](#1.3)
&emsp;&emsp;.gitignore / setup.[]()py / requirements.txt / src folder
[4. Create the package](#1.4)

Lesson 1 link: https://www.youtube.com/watch?v=Rv6UFGNmNZg&ab_channel=KrishNaik

## Lesson 2:
[1. Create project module structure](#2.1)
[2. Setup custom exception handling](#2.2)

Lesson 2 link: https://www.youtube.com/watch?v=sDWL30CzJT8&list=PLZoTAELRMXVPS-dOaVbAux22vzqdgoGhG&index=3&ab_channel=KrishNaik




[Tips & notes](#25)



# Lesson 1
Steps:
<a id="1.1"></a>
## 1.1. Set up repository and README[]().md

-    1. Create new repository in github
-    2. Create folder to be synced with repo
-    3. Initialize git & commit
        (git should be installed)
        - "git init"
        </br>
-    4. Create README.md & commit
        - After creatind README.txt:
        - git add README.md
        - git commit -m 'First commit'
        </br>
-    5. sync with github:
        *git should be configured with same email id & username as github, search git global config for instructions
        "git branch -M main"
        "git remote add origin https://github.com/UserName/RepositoryName.git"

<a id="1.2"></a>
## 1.2. Set up new environment:

    Create and activate virtual environment
        with conda (miniconda, on windows): 
        1. Navigate to the folder you want to create the venv through the command prompt
        2. Create environment by typing:
            conda create -p venv python==3.8 -y
            note: venv is the name of the virtual environment. it can be anything, but venv is what is usually used
        3. Activate virtual environment:
            conda activate venv/

        *conda venv tips & troubleshooting
        </br>
        </br>
<a id="1.3"></a>
## 1.3. Create gitignore / requirements.txt / setup.[]()py: 

    - create .gitignore file
        create in github, choosing .gitignore template: python
    'git pull' to sync with local folder
    - create setup.py & requirements.txt 
    *tips & best practices for setup.py & requirements.txt
    </br>
    </br>

<a id="1.4"></a>
## 1.4. create src folder, define it as package
    To define it as a module add a '__init__.py' file inside
- Install requirements (and run setup.py):

    - Install from the given requirements file:
    - "pip install -r requirements.txt"
    - Commit / pull / push



# Lesson 2
Steps:
<a id="2.1"></a>
## 2.1. Create project module structure

- Creating the following (standard) structure for the project in the src module:

    |-components/
    |&emsp;&emsp;|--\_\_init__.py
    |&emsp;&emsp;|--data\_ingestion.py 
    |&emsp;&emsp;|--data_transformation.py 
    |&emsp;&emsp;|--model_trainer.py
    |     
    |--pipeline/
    |&emsp;&emsp;|--\_\_init__.py
    |&emsp;&emsp;|--train_pipeline.py
    |&emsp;&emsp;|--predict_pipeline.py
    |     
    |--logger.py
    |--exception.py
    |--utils.py         
     
Steps:
<a id="2.2"></a>
## 2.2. Setup custom exception handling (in the exceptions.py):
- 2.2.1 Define function to extract error details from a given error and its associated traceback. Function also Constructs and returns a detailed error message using the file name, line number, and error message.
- 2.2.2 Define a CustomExceptionClass to handle all exceptions, inheriting from Exceptions
- Test code (will make sense after logging setup)














<a id="25"></a>
## Notes & Tips 

### Contents

#### 1. conda venv tips & troubleshooting
- In order for conda to run from command line, conda should be added to the path. If not,un-install and re-install conda (using mini-conda) 
and when installing, click the add to path option when it appears

- Delete a virtual environment with conda:
       conda env remove -p C:\this\is\the\path\of\venv
</br>
#### 2. tips for setup.()[]py

- Why setup.py?
    - setup.py serves as a build script for packaging and distributing Python projects. Helps in creating a package that can be installed with PyPI (pip install pck_name)
    - Defines metadata, dependencies, scripts, and modules of a package.
    - Includes package name, version, description, author, etc
    - Lists required packages in install_requires.
    </br>

- 2.1. Follow semantic versioning for verion:
    "Given a version number MAJOR.MINOR.PATCH, increment the:
        MAJOR version when you make incompatible API changes
        MINOR version when you add functionality in a backward compatible manner
        PATCH version when you make backward compatible bug fixes
    Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format."
    (source: https://semver.org/)
    </br>

- 2.2. Initially in requirements add "-e .". What this does is that when the install requirements.txt is used, it also runs the setup.py, that sets up the package.
   It is used only the first time, then when the pckg is created, it is removed
    </br>
- 2.3. use the find_packages:
    "from setuptools import find_packages, ..
    ...
    setup (...
    ...
    packages = find_packages()," 
    "..."
    

    this will finds all packages in directory 
    package: define a folder as a package by adding a "__init__.py" file inside 

- 2.4. Pin dependency versions for reproducible builds.
