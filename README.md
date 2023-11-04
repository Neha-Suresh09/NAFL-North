import mysql.connector
from mysql.connector import Error
import PyPDF2

db_host="localhost"
db_user="your_username"
db_password="your_password"
db_database="your_database"

def connect_to_mysql():
    try:
        connection = mysql.connector.connect(
            host=db_host,
            user=db_user,
            password=db_password,
            database=db_database)
        if connection.is_connected():
            return connection
    except Error as e:
        print("Error",e)
    return None

def read_pdf(file_path):
    try:
        with open(file_path, 'rb') as file:
            pdf_reader = PyPDF2.PdfFileReader(file)
            text = ''
            for page_num in range(pdf_reader.numPages):
                text += pdf_reader.getPage(page_num).extractText()
            return text
    except FileNotFoundError:
        print("File not found.")
    return None

cursor = connection.cursor()
# Replace with your query to retrieve the data
query = "SELECT category, value FROM graph_data"
cursor.execute(query)

# Fetch the data
data = cursor.fetchall()
categories = [row[0] for row in data]
values = [row[1] for row in data]
plt.bar(categories, values)
plt.xlabel("Categories")
plt.ylabel("Values")
plt.title("Bar Chart")
plt.xticks(rotation=45)  # Rotate x-axis labels for better readability

plt.show()
cursor.close()
connection.close()


import tkinter as tk
root=tk.Tk()
def button_click():
    label.config(text="Button Clicked")

button=tk.Button(root, text="Click Me",command=button_click)
root.geometry("800x500")
label=tk.Label(root,text="")
button.pack()
label.pack()
root.mainloop()


    
