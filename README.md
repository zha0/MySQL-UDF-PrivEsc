# MySQL-UDF-PrivEsc
Using MySQL UDF to excute system commands
<br/>Prerequisites:
- mysqld must run as root
- you must know know the credentials of a MySQL user that has the permission to create stored function on the DBMS

# How does it works?
The script use UDF shared library on MySQL to execute commands on a system, if mysqld run as root, so the passed (-c)ommand will be executed as root. On a 64bit *nix box you can pass the compiled .so included in this repo.<br/>
How to use the script: $0 -u <mysql user> -p <mysql user password> -s <path of the shared library> -c <command to execute> e.g.<br/>
# mysql_udf_exec_sys.sh -s lib_sys_udf.so -u root -p Secrete -c 'whoami > /tmp/whoM; chmod go+r /tmp/whoM;'
<br><b>Please have a look to the following resources to get specific information about the exploit: </b>
  - https://www.exploit-db.com/exploits/1518
  - MySQL UDF: https://mariadb.com/kb/en/library/create-functio-n-udf 
  - Shared library soname: https://en.wikipedia.org/wiki/Soname
