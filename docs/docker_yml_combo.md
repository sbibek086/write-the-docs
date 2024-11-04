---
layout: page
title: 🐳 + y(a)ml combo
category: Programming
tags: [Programming] 
---

hub.docker.com >>3.6.76. pw: 3..8 is My First GoTo when building app or sthg. Below shows WHY HOW :)
my words- yes, doing docker way is 10step to 5step thing but need to know port mapping etc concept expertly. so not recommended unless know these.
So, unless know, do localhost way primary way

[yo sab gareko WordpressCamp'sTut](https://www.facebook.com/mishra.aananta/videos/307497993616073)

![dockerWorkFlow](https://user-images.githubusercontent.com/11883023/209544204-48c30b20-48e6-47b5-972c-af4b98ddb45c.png)
![dockerWFlow](https://github.com/sbibek086/write-the-docs/assets/11883023/7b4b7003-e40b-4a67-9cb3-3d9e7e18b875)

![image](https://github.com/user-attachments/assets/efef7f6a-d0ba-496c-882b-ee6ed1803ecf)

```
docker run -d -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=mysite -e MYSQL_PASSWORD=password --name mysitedb -v "$PWD/database":/var/lib/mysql mysql
```

```
docker pull wordpress
docker run -d -e WORDPRESS_DB_NAME=mysite -e WORDPRESS_DB_USER=mysite -e WORDPRESS_DB_PASSWORD=password --name wordpress --link mysitedb -p 80:80 -v "$PWD/html":/var/www/html wordpress
```
IdontKnow why but while doing, mathi ko command rakhda athena tara tala ko
```
docker run -d --name wordpress --link mysitedb -p 81:80 -v "$PWD/html":/var/www/html wordpress
```
rakhda chai aathyo

Now, alternatively, lets do w docker-compose.yml way of what we tried to do CLI way of docker in github.com/sbibek086 

![image](https://github.com/user-attachments/assets/55f68371-31ac-4127-8606-5ab17f159a51)

[How does depends_on work?](https://stackoverflow.com/questions/73727944/when-depends-on-is-being-used-in-docker-compose-yml)

---
**Doing more Grand Project than earlier, using docker-compose**

So, docker-compose.yml is LHS-of-4th-pic-from-top and lets see how it compiles:
![image](https://github.com/user-attachments/assets/19211432-a5d3-4921-a5b7-71f4993ded67)

Then, how does app.py as client interacts w mysql server & also about how port expose is co-ordinated
```
from flask import Flask, request, jsonify
import mysql.connector
import os

app = Flask(__name__)

# Connect to MySQL
def get_db_connection():
    connection = mysql.connector.connect(
        host=os.getenv("MYSQL_HOST", "db"),
        user=os.getenv("MYSQL_USER", "root"),
        password=os.getenv("MYSQL_PASSWORD", "example"),
        database=os.getenv("MYSQL_DB", "test_db")
    )
    return connection

# Endpoint to add a new record
@app.route('/api/add', methods=['POST'])
def add_record():
    data = request.json
    name = data.get("name")
    
    connection = get_db_connection()
    cursor = connection.cursor()
    cursor.execute("INSERT INTO users (name) VALUES (%s)", (name,))
    connection.commit()
    cursor.close()
    connection.close()
    
    return jsonify({"message": "Record added successfully"}), 201

# Endpoint to retrieve all records
@app.route('/api/users', methods=['GET'])
def get_users():
    connection = get_db_connection()
    cursor = connection.cursor()
    cursor.execute("SELECT id, name FROM users")
    users = [{"id": row[0], "name": row[1]} for row in cursor.fetchall()]
    cursor.close()
    connection.close()
    
    return jsonify(users)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```
---
 ![image](https://github.com/user-attachments/assets/240d4d26-411d-46d4-8890-7d9f63a4109a)

B) Making docker image persistent on url no matter my dockerDektop is Off:
If I want such that -when I turn off docker, which I had to start app n run it. I mean that docker image of website always coming on URL no matter I switch off my machine, termed persistency.   If I want such, [then look here](https://developer.okta.com/blog/2018/09/27/test-your-github-repositories-with-docker-in-five-minutes)

---
But why is docker-compose.yml (can be said more Infrastructure as code) more seeked n practical efficient than docker way

![IaC](https://github.com/user-attachments/assets/00e53816-27cf-44e7-87a5-fea71ee8587d)

---
CI/CD aka devOps from Techworld with Nana YT not rel to above

![gitActions](https://user-images.githubusercontent.com/11883023/120933150-82a62080-c718-11eb-9667-0ede1aad1b33.jpg)
[thisYT](https://www.youtube.com/watch?v=R8_veQiYBjI) powerGist
Open source prj are mostly agile (means there is no such thing as 100% final; there's always improvement ,and there can be 1000+ contributors as it grows big.

So, its practically impossible to accept every pull req. (PR) code, edit with issues , check its validity(TEST), merge it etc etc. as written by Merged Code, Test, Build, Deploy in above pic. Every incoming PR to your open source repo is called EVENTS and things you do in its response (Mer., T, B, D is act of Continuous Integration/ Continuous Deployment = CI/CD) is called ACTIONS, which can be automated. Hence, the name Actions with CI/CD pipeline.

Though ci cd is superset of action.

1. Merged code (i will do it via git tools in Vstudio)
2. Test
3. Build (I will do 2, 3 in Vstudio)
4. Deploy (I will do it thru. XAMPP to localhost in my browser)
(amateur me understood, deploy to server is always thru xampp, which is true for php dev. But it can be facilitated entirely from packages which in turn is called by terminal scripts. Eg. Xxxxxx in create-react-app)
5. Then I will push to repo
These all can be automated writing few lines code in .YAML file (superset of json file)

Mind you! Github Actions run on github server itself.

---
