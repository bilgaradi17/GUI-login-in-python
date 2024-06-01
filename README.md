# GUI-login-in-python

## Tkinter Registration and Login System
Welcome to the Tkinter Registration and Login System! This application is built using Python's Tkinter library and provides a simple user interface for user registration and login. Below, I'll guide you through the structure and functionality of the code, including explanations of the Python keywords used.

Code Overview
### Importing Modules
First, we import the necessary modules:

from tkinter import *
import os

from and import: These keywords are used to import specific modules or functions from modules. Here, we import everything (*) from the tkinter module and the os module for file system operations.


### Registration Window
The register function creates the registration window:

def register():
    global register_screen
    register_screen = Toplevel(main_screen)
    register_screen.title("Register")
    register_screen.geometry("800x600")   
    global username
    global password
    global username_entry
    global password_entry
    username = StringVar()
    password = StringVar()   
    Label(register_screen, text="Please enter details below", bg="blue").pack()
    Label(register_screen, text="").pack()
    username_label = Label(register_screen, text="Username * ")
    username_label.pack()
    username_entry = Entry(register_screen, textvariable=username)
    username_entry.pack()
    password_label = Label(register_screen, text="Password * ")
    password_label.pack()
    password_entry = Entry(register_screen, textvariable=password, show='*')
    password_entry.pack()
    Label(register_screen, text="").pack()
    Button(register_screen, text="Register", width=10, height=1, bg="blue", command=register_user).pack()

def: This keyword is used to define a new function.
global: Declares variables that can be accessed and modified outside the function.
Toplevel: Creates a new window that is a child of main_screen.
StringVar(): A Tkinter class for handling text variables.
Label, Entry, Button: Tkinter widgets for creating text labels, input fields, and buttons.
pack(): A method to manage the layout of widgets.


### Login Window
The login function creates the login window:

def login():
    global login_screen
    login_screen = Toplevel(main_screen)
    login_screen.title("Login")
    login_screen.geometry("800x600")
    Label(login_screen, text="Please enter details below to login").pack()
    Label(login_screen, text="").pack()
    global username_verify
    global password_verify
    username_verify = StringVar()
    password_verify = StringVar()
    global username_login_entry
    global password_login_entry
    Label(login_screen, text="Username * ").pack()
    username_login_entry = Entry(login_screen, textvariable=username_verify)
    username_login_entry.pack()
    Label(login_screen, text="").pack()
    Label(login_screen, text="Password * ").pack()
    password_login_entry = Entry(login_screen, textvariable=password_verify, show='*')
    password_login_entry.pack()
    Label(login_screen, text="").pack()
    Button(login_screen, text="Login", width=10, height=1, command=login_verify).pack()
    
command: A parameter that specifies the function to be called when the button is clicked.


### Register User
The register_user function handles the user registration logic:

def register_user():
    username_info = username.get()
    password_info = password.get()
    file = open(username_info, "w")
    file.write(username_info + "\n")
    file.write(password_info)
    file.close()
    username_entry.delete(0, END)
    password_entry.delete(0, END)
    Label(register_screen, text="Registration Success", fg="green", font=("calibri", 11)).pack()
    
open(): A built-in function to open a file.
write(): A method to write text to a file.
close(): A method to close a file.
delete(0, END): Deletes text from the entry field from the start (0) to the end (END).
fg: A parameter to set the text color.
font: A parameter to set the font style and size.


### Login Verification
The login_verify function verifies the login credentials:

def login_verify():
    username1 = username_verify.get()
    password1 = password_verify.get()
    username_login_entry.delete(0, END)
    password_login_entry.delete(0, END)  
    list_of_files = os.listdir()
    if username1 in list_of_files:
        file1 = open(username1, "r")
        verify = file1.read().splitlines()
        if password1 in verify:
            login_success()
        else:
            password_not_recognised()
    else:
        user_not_found()

if, else: Keywords used for conditional statements.
os.listdir(): A function to list files in the current directory.
read(): A method to read the content of a file.
splitlines(): A method to split the file content into a list of lines.


### Popup Messages
We define several functions to display popup messages for different login outcomes:

def login_success():
    global login_success_screen
    login_success_screen = Toplevel(login_screen)
    login_success_screen.title("Success")
    login_success_screen.geometry("400x250")
    Label(login_success_screen, text="Login Success").pack()
    Button(login_success_screen, text="OK", command=delete_login_success).pack()

def password_not_recognised():
    global password_not_recog_screen
    password_not_recog_screen = Toplevel(login_screen)
    password_not_recog_screen.title("Success")
    password_not_recog_screen.geometry("400x250")
    Label(password_not_recog_screen, text="Invalid Password").pack()
    Button(password_not_recog_screen, text="OK", command=delete_password_not_recognised).pack()

def user_not_found():
    global user_not_found_screen
    user_not_found_screen = Toplevel(login_screen)
    user_not_found_screen.title("Success")
    user_not_found_screen.geometry("400x250")
    Label(user_not_found_screen, text="User Not Found").pack()
    Button(user_not_found_screen, text="OK", command=delete_user_not_found_screen).pack()
    
These functions create popup windows to inform the user about the success or failure of their login attempt.


### Deleting Popup Screens
We also define functions to close the popup windows:

def delete_login_success():
    login_success_screen.destroy()

def delete_password_not_recognised():
    password_not_recog_screen.destroy()

def delete_user_not_found_screen():
    user_not_found_screen.destroy()
destroy(): A method to close the window.


### Main Window
Finally, we create the main window of the application:

def main_account_screen():
    global main_screen
    main_screen = Tk()
    main_screen.geometry("800x600")
    main_screen.title("Account Login")
    Label(text="Select Your Choice", bg="blue", width="800", height="2", font=("Calibri", 13)).pack()
    Label(text="").pack()
    Button(text="Login", height="2", width="30", command=login).pack()
    Label(text="").pack()
    Button(text="Register", height="2", width="30", command=register).pack()
    
    main_screen.mainloop()

Tk(): Initializes the main application window.
mainloop(): Starts the Tkinter event loop, waiting for user interaction.


### Running the Application
To run the application, simply execute the script. It will display the main window, allowing you to register a new user or log in with existing credentials.

main_account_screen()


Feel free to fork this repository, make improvements, and share your feedback!
