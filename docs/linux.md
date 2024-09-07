---
layout: default
title: 🐧
category: Developer
tags: [Developer]
---

Root directory path is simply (/). Everything in file system is organized under this root directory. meaning: if I access say one Linux OS machine, then its default path is /

![image](https://github.com/user-attachments/assets/134ff627-5c7d-4115-b7a0-803542d68f34)

above dgm is not 100% accurate as I had 5yr old understanding but is not wrong either to del.
So, understanding more to how linux adds files - yes, its kind of fractal, look below:
![image](https://github.com/user-attachments/assets/788e629f-fdf9-4e86-aa36-02555f5a5e54)

![image](https://github.com/user-attachments/assets/b51f03f5-4c37-42fe-82ec-daf71d24d397) 

---
I must not had paid attention to kernel. otherwise how clear its to me now.
![image](https://user-images.githubusercontent.com/11883023/267250299-73389113-31e9-4af0-889c-23fad0118403.png)

kernel is middle tier which connects to hw resources. kernel doesnt always have to be terminal or bash CLI stuffs. It can be os (thanks to Linus who must have painstakingly written all those lines which lets you control w mouse). 

all those linux cmds like sudo, apt are recognized because Linus had written defined it as packages in C and assembly lang while writing Linux kernel. btw he didnt write it from scratch tho. he wrote on top of GNU framework, which was revolution against all proprietary locked Unix. [very related my next article](https://sbibek086.github.io/write-the-docs/2024-03-11-Understandg-Env-&-Engine-Files.html)

[Windows cant be said kernel but Linux is both kernel n os](https://www.youtube.com/watch?v=HbgzrKJvDRw) is both kernel and OS).

While Linux doesn't have a central registry, tools and utilities are available for managing system configuration. These include:

a) Package Managers: Tools like apt, yum, dnf, etc., often handle configuration files as part of package installation and removal.

b) Configuration Management Systems: Tools like Ansible, Puppet, Chef, and SaltStack provide ways to automate configuration management across multiple systems, enforcing desired states defined in configuration files.


Windows:
registry is centralized hierrachical database of windows os which stores config, settings etc configuration. jasto maile aaja taskbar vertical align gare vane tespachi kholda vertical nai vayera basira hunchh -ho yestai yestai vividh, yi sbae kura registry ma store hunchh.

HKLM= HKEY_LOCAL_MACHINE, is a Windows Registry tree that contains configuration data that is used by all users in Windows. This includes information about Windows services, drivers, programs that automatically run for every user, and general OS settings.

---
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/846e352f-12b6-4726-b505-d1c6e1b6e694)

---

![linuxx(1)](https://github.com/user-attachments/assets/d1cacb64-e777-4a2d-bdb3-17032b38d291)

---
Image Ka: 
![image](https://github.com/user-attachments/assets/b4882270-5bf3-472a-baf0-18607df00e14)

then, I wanted to install vscode as I had manually downloaded vscode from it official website
instead of 
```
sudo apt update

#1.Install dependencies
sudo apt install software-properties-common apt-transport-https wget

#2.Import Microsoft GPG key:
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -

#3.Enable vscode repository
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"

#4.install vscode
sudo apt update
sudo apt install code
```
n so had missed 4th step.

I faced this-> issue while doing 4th step manually
![image](https://github.com/user-attachments/assets/988fc413-3e30-4298-adcb-eb7d19b4e7e5)

So, I tried to make py app n connect to db. dhunga khojda deuta vane jasto py has already sqlite in it. So, 
I put all this below in Image Ka step:

```python
import sqlite3
from datetime import datetime

# Database connection
def connect_db():
    return sqlite3.connect('shop.db')

# Initialize the database and create tables
def initialize_db():
    conn = connect_db()
    cursor = conn.cursor()

    # Database Schema: now,We’ll define products table, customers table & sales table 1by1 in our SQLite database: 
    # Create products table
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS products (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL,
            price REAL NOT NULL,
            stock INTEGER NOT NULL
        )
    ''')

    # Create customers table
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS customers (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL,
            email TEXT UNIQUE NOT NULL
        )
    ''')

    # Create sales table
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS sales (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            customer_id INTEGER,
            product_id INTEGER,
            quantity INTEGER NOT NULL,
            sale_date TEXT NOT NULL,
            FOREIGN KEY (customer_id) REFERENCES customers(id),
            FOREIGN KEY (product_id) REFERENCES products(id)
        )
    ''')

    conn.commit()
    conn.close()

# Add a new product to the database
def add_product(name, price, stock):
    conn = connect_db()
    cursor = conn.cursor()
    cursor.execute('INSERT INTO products (name, price, stock) VALUES (?, ?, ?)', (name, price, stock))
    conn.commit()
    conn.close()
    print(f'Product "{name}" added successfully.')

# Add a new customer to the database
def add_customer(name, email):
    conn = connect_db()
    cursor = conn.cursor()
    cursor.execute('INSERT INTO customers (name, email) VALUES (?, ?)', (name, email))
    conn.commit()
    conn.close()
    print(f'Customer "{name}" added successfully.')

# Record a sale in the database
def record_sale(customer_id, product_id, quantity):
    conn = connect_db()
    cursor = conn.cursor()

    # Check if product is in stock
    cursor.execute('SELECT stock FROM products WHERE id = ?', (product_id,))
    stock = cursor.fetchone()
    
    if stock and stock[0] >= quantity:
        # Update product stock
        cursor.execute('UPDATE products SET stock = stock - ? WHERE id = ?', (quantity, product_id))

        # Record the sale
        sale_date = datetime.now().strftime('%Y-%m-%d %H:%M:%S')
        cursor.execute('INSERT INTO sales (customer_id, product_id, quantity, sale_date) VALUES (?, ?, ?, ?)',
                       (customer_id, product_id, quantity, sale_date))

        conn.commit()
        print(f'Sale recorded successfully.')
    else:
        print('Error: Not enough stock available.')

    conn.close()

# View all products
def view_products():
    conn = connect_db()
    cursor = conn.cursor()
    cursor.execute('SELECT * FROM products')
    products = cursor.fetchall()
    
    print("Product List:")
    for product in products:
        print(f'ID: {product[0]}, Name: {product[1]}, Price: {product[2]}, Stock: {product[3]}')

    conn.close()

# View all sales
def view_sales():
    conn = connect_db()
    cursor = conn.cursor()
    cursor.execute('''
        SELECT sales.id, customers.name, products.name, sales.quantity, sales.sale_date
        FROM sales
        JOIN customers ON sales.customer_id = customers.id
        JOIN products ON sales.product_id = products.id
    ''')
    sales = cursor.fetchall()
    
    print("Sales Records:")
    for sale in sales:
        print(f'Sale ID: {sale[0]}, Customer: {sale[1]}, Product: {sale[2]}, Quantity: {sale[3]}, Date: {sale[4]}')

    conn.close()

# Main menu for user interaction
def main_menu():
    while True:
        print("\n--- Shop Accounting System ---")
        print("1. Add Product")
        print("2. Add Customer")
        print("3. Record Sale")
        print("4. View Products")
        print("5. View Sales")
        print("6. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == '1':
            name = input("Enter product name: ")
            price = float(input("Enter product price: "))
            stock = int(input("Enter product stock: "))
            add_product(name, price, stock)
        
        elif choice == '2':
            name = input("Enter customer name: ")
            email = input("Enter customer email: ")
            add_customer(name, email)
        
        elif choice == '3':
            customer_id = int(input("Enter customer ID: "))
            product_id = int(input("Enter product ID: "))
            quantity = int(input("Enter quantity: "))
            record_sale(customer_id, product_id, quantity)
        
        elif choice == '4':
            view_products()
        
        elif choice == '5':
            view_sales()
        
        elif choice == '6':
            break
        
        else:
            print("Invalid choice. Please try again.")

# Initialize the database and run the main menu
if __name__ == "__main__":
    initialize_db()
    main_menu()
```

to bring kaamchalau app in bash itself. (bash mai ta aauchh ni, hello world ni bash mai athyo)
![image](https://github.com/user-attachments/assets/7964e025-de39-4f74-a349-775277eb8cf5)

Also, shop.db pani create vayera baseko chh tyo path ma ie. home/educare ma in my ubuntu

---
shortcuts for bash:
Ctrl Alt T to bring bash aka terminal
Ctrl Shift V to paste clipboard to terminal

---
![image](https://github.com/user-attachments/assets/82ea1ac9-98ee-491a-b187-306186a5fdb4)

these are ubuntu file manager called Nautilus symbols- others are:
- Gray X Icon: broken symlink, meaning target of symlink no longer exists.
- Lock Icon: Restricted access. file or folder is owned by another user (often root), n u don't have permissions to modify it unless you have superuser privileges.
- Orange or Yellow Exclamation Mark: Warning or attention reqd. Often used by cloud services or VCS to show that there is issue (e.g., sync error, or uncommitted changes in a repository).
- Padlock (for Encrypted Files): may appear if a file or folder is encrypted or has special protection mechanisms.
- Purple Folder: Specific directories, such as Documents, Downloads, etc., might have colored icons in some themes to distinguish them as system or special directories.
- Folder with a Person Icon: shared folders that are accessible to other users or systems on the network.
- Red Background with White Slash Symbol: folder that is not mounted (commonly used for external drives or partitions).
- Dot (.) in Front of File/Folder Name: hidden file or folder
- Green Checkmark: Commonly used by version control systems (VCS) or cloud sync services (e.g., Dropbox) to indicate that a file or folder is up-to-date or has been successfully synced with the cloud or repository.
- Blue Circle with Two Arrows: file or folder is synchronizing (e.g., syncing with a cloud service like Dropbox)
