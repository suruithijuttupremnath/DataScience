# Documantation for Installing Apache Superset:

1. Download and install **miniconda or anaconda**.

2. Install python-geohash using cmd:
**conda install -c conda-forge python-geohash -y**
If install it with pip, you will face the following error:

error: Microsoft Visual C++ 14.0 is required. 
Get it with "Microsoft Visual C++ Build Tools": 
http://landinghub.visualstudio.com/visual-cpp-build-tools
and you have to install Windows Compiler(it is very big).

3. Downgrade OpenSSL version from 1.1.1e to 1.1.1d (latest stable and working), 
**conda install -c conda-forge openssl==1.1.1d -y**
Otherwise, you might face the following error:

[ERROR] Execution failed: [SSL: KRB5_S_TKT_NYV] unexpected eof 
while reading (_ssl.c:2555)

4. Install Apache Superset with pip
**pip install apache-superset**

If pip is not installed in anaconda or miniconda, reinstall it using the cmd:
**easy_install pip**

5. Create batch file superset.cmd in the same folder of python.exe
@set FLASK_APP=superset
@python "%~dp0Scripts\superset" %*
[type this in notepad and save then]
if you use powershell instead of command prompt, replace 

set FLASK_APP=superset
with 

$env:FLASK_APP = "superset"

6. Initialize the database
**superset db upgrade**

7. Create an admin user (you will be prompted to set a username, first and last name before setting a password)
**flask fab create-admin**

8. Load some data to play with
**superset load_examples**

9. Create default roles and permissions
**superset init**

10. To start a development web server on port 8088, use -p to bind to another port
**superset run -p 8088 --with-threads --reload --debugger**

11. open **http://localhost:8088** with the browser.