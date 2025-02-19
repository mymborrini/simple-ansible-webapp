# Simple Web Application

This is a simple web application using [Python Flask](http://flask.pocoo.org/) and [MySQL](https://www.mysql.com/) database. 
This is used in the demonstration of development of Ansible Playbooks.
  
  Below are the steps required to get this working on a base linux system.
  
  - Install all required dependencies
  - Install and Configure Database
  - Start Database Service
  - Install and Configure Web Server
  - Start Web Server
   
## 1. Install all required dependencies
  
  Python and its dependencies

    sudo apt install -y python3-venv
    python3 -m venv .venv
    . .vevn/bin/activate
    pip install -r requirements.txt


   
## 2. Install and Configure Database
    
 Install MySQL database
    
    apt install -y mysql-server mysql-client

## 3. Start Database Service
  - Start the database service
    
        service mysql start

  - Create database and database users
        
        # mysql -u root -p
        
        mysql> CREATE DATABASE employee_db;
        mysql> USE employee_db;
        mysql> CREATE TABLE employees (name VARCHAR(20));
        
  - Insert some test data
        
        mysql> INSERT INTO employees VALUES ('JOHN');
    

## 4. Start Web Server

Start web server

    FLASK_APP=app.py flask run --host=0.0.0.0
    
## 5. Test

Open a browser and go to URL

    http://<IP>:5000                            => Welcome
    http://<IP>:5000/how%20are%20you            => I am good, how about you?
    http://<IP>:5000/read%20from%20database     => JOHN
