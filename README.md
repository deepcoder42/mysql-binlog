# Python project for maintaining binary logs in a MySQL database.
# Classification (U)

# Description:
  Program is used to maintain binary logs in a MySQL database to include flushing, backing up, and purging logs.


###  This README file is broken down into the following sections:
  * Features
  * Prerequisites
  * Installation
  * Configuration
  * Program Help Function
  * Testing
    - Unit


# Features:
  * Flush binary logs.
  * Backup missing binary logs.
  * Backup all binary logs.
  * Purge binary logs earlier than N days ago.
  * Purge binary logs before binary log file name.
  * Print missing backed up binary logs.


# Prerequisites:

  * List of Linux packages that need to be installed on the server.
    - git
    - python-pip

  * Local class/library dependencies within the program structure.
    - lib/cmds_gen
    - lib/arg_parser
    - lib/gen_libs
    - mysql_lib/mysql_libs
    - mysql_lib/mysql_class


# Installation:

Install the project using git.
  * Replace **{Python_Project}** with the baseline path of the python program.

```
umask 022
cd {Python_Project}
git clone git@github.com:deepcoder42/mysql-binlog.git
```

Install/upgrade system modules.

```
cd mysql-binlog
umask 022
pip install -r requirements.txt --upgrade --system
exit
```

Install supporting classes and libraries.

```
pip install -r requirements-python-lib.txt --target lib --system
pip install -r requirements-mysql-lib.txt --target mysql_lib --system
pip install -r requirements-python-lib.txt --target mysql_lib/lib --system
```

# Configuration:

Create MySQL configuration file and make the appropriate change to the environment.
  * Change these entries in the MySQL setup:
    - user = "USER"
    - japd = "PSWORD"
    - host = "SERVER_IP"
    - name = "HOST_NAME"
    - sid = SERVER_ID
    - extra_def_file = "PYTHON_PROJECT/config/mysql.cfg"
    - cfg_file = "MYSQL_DIRECTORY/my.cnf"

  * Change these entries only if required:
    - serv_os = "Linux"
    - port = 3306

```
cd config
cp mysql_cfg.py.TEMPLATE mysql_cfg.py
vim mysql_cfg.py
chmod 600 mysql_cfg.py
```

Create MySQL definition file and make the appropriate change to the environment.
  * Change these entries in the MySQL definition file:
    - password="PASSWORD"
    - socket=DIRECTORY_PATH/mysqld.sock

```
cp mysql.cfg.TEMPLATE mysql.cfg
vim mysql.cfg
chmod 600 mysql.cfg
```


# Program Help Function:

  The program has a -h (Help option) that will show display an usage message.  The help message will usually consist of a description, usage, arugments to the program, example, notes about the program, and any known bugs not yet fixed.  To run the help command:
  * Replace **{Python_Project}** with the baseline path of the python program.

```
{Python_Project}/mysql-binlog/mysql_binlog.py -h
```


# Testing:

# Unit Testing:

### Installation:

Install the project using git.
  * Replace **{Python_Project}** with the baseline path of the python program.
  * Replace **{Branch_Name}** with the name of the Git branch being tested.  See Git Merge Request.

```
umask 022
cd {Python_Project}
git clone --branch {Branch_Name} git@github.com:deepcoder42/mysql-binlog.git
```

Install/upgrade system modules.

```
cd mysql-binlog
sudo bash
umask 022
pip install -r requirements.txt --upgrade --system
exit
```

Install supporting classes and libraries.

```
pip install -r requirements-python-lib.txt --target lib --system
pip install -r requirements-mysql-lib.txt --target mysql_lib --system
pip install -r requirements-python-lib.txt --target mysql_lib/lib --system
```


### Testing:
  * Replace **{Python_Project}** with the baseline path of the python program.

```
cd {Python_Project}/mysql-binlog
test/unit/mysql_binlog/unit_test_run.sh
```

### Code Coverage:
```
cd {Python_Project}/mysql-binlog
test/unit/mysql_binlog/code_coverage.sh
```

