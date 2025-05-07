# modulo1_s3_training
```python
books =[
   {"title":"Pride and Prejudice","author":"Jane Austen","genre":"Romance","year":"1813","quantity":"5","price":"12.99"},
   {"title":"Harry Potter and the Goblet of Fire","author":" J.K Rowling","genre":"Fantasy","year":"2000","quantity":"8","price":"15.50"},
   {"title":"To Kill a Mockingbird","author":"Harper Lee","genre":"Fiction","year":"1960","quantity":"4","price":"10.75"},
   {"title":"Dracula","author":"Bram Stoker","genre":"Horror","year":"1897","quantity":"3","price":"9.60"},
   {"title":"Jane Eyre","author":"Charlotte Bronte","genre":"Romance","year":"1847","quantity":"6","price":"11.80"}
]
def register():
  print ("\n---Register a new book---")
  title = input("Enter title ").strip()
  author = input("Enter author ").strip()
  genre = input("Enter genre ").strip()
  try:
     year = int(input("Enter a year of publication"))
     if year < 800 or year > 2025:
        print("Invalid year. Please enter a year between 1800 - 2025")
        return
  except ValueError:
     print("Invalid input. Year must be a number. ")
  try:
     quantity = int(input("Enter the quantity of books"))
     if quantity < 0:
        print("Invalid quantity. Please enter a valid quantity")
        return
  except ValueError:
     print("Invalid input. quantity must be a number. ")
  try:
     price = float(input("Enter replacement price: "))
     if price <= 0:
        print("Invalid price. Price must be a positive number")
        return
  except ValueError:
     print("Invalid input. price must be a number. ")
  for book in books:
     if book['title'].lower() == title.lower():
        print("Book already exist in the catalog.")
        return
  new_book = {
     "title": title,
     "author": author,
     "genre": genre,
     "year": year,
     "quantity": quantity,
     "price": round(price,2)
  }
  books.append(new_book)
  print(f"\nBook'{title}' registered successfully. ")
def search():
   print("\n---Search Book---")
   ask = input("Enter book title or author to search: ").strip().lower()
   found = False
   for book in books:
      if ask in book['title'].lower() or ask in book['author'].lower():
         print(f"\nBook found: \n"
               f"Title: {book['title']}\n"
               f"Author:{book['author']}\n"
               f"Genre:{book['genre']}\n"
               f"Year:{book['year']}\n"
               f"Quantity available: {book['quantity']}\n"
               f"Replacement Price: ${book['price']}\n")
         found = True
   if not found:
      print("Book not found. Do you want to register it? (yes/No)")
      answer = input().strip().lower()
      if answer == "yes":
         register()
      
def update():
   print("\n---Update Book---")
   ask = input("Enter book title or author to search: ").strip().lower()
   found = False
   for book in books:
      if ask in book['title'].lower() or ask in book['author'].lower():
         print(f"\nBook found: \n"
               f"Title: {book['title']}\n"
               f"Author:{book['author']}\n"
               f"Genre:{book['genre']}\n"
               f"Year:{book['year']}\n"
               f"Quantity available: {book['quantity']}\n"
               f"Replacement Price: ${book['price']}\n")
         found = True
         data_change = input("Which value you want to change: ")
         if data_change in books.keys():
            new_value = input("What value do you want to change it to?").strip()
            if data_change in ['year','quantity']:
               try:
                  new_value = int(new_value)
               except ValueError:
                  print("Error: value must be a number")
                  return
            elif data_change == 'price':
               try:
                  new_value = float(new_value)
               except ValueError:
                  print("Error: value must be a decimal number.")
                  return
            book[data_change] = new_value
            print(f"{data_change.capitalize()} has been updated successfully.\n")
         else:
            print("This value cant be changed!")
         break
   if not found:
      print("Book not found. Do you want to register it? (yes/No)")
      answer = input().strip().lower()
      if answer == "yes":
         register()        
def delete():
   print("\n---Delete Book---")
   delete = input("Enter book title to delete: ").strip().lower()
   found = False
   if delete in books:
      answer = print("Re ypu sure to delete this book? (yes/no) \n")
      if answer =="yes":
         del books[delete]
         print("Book successfully deleted.")
      else:
         print("Deletion cancelled")
   else:
      print("Book not found.")       
def generate():
   try:
     action = str(input("Which report want to see?: (invetory/antique)\n"))
     if action != "inventory" or action != "antique":
        print("Invalid option")
        return
     if action =="inventory":
        print("\n---Report inventory---")
        total_cost = 0
        for book in books.values():
           cost = book['quantity'] * book['price']
           total_cost += cost
           print(f"{book['title']} - {book['quantity']} units - $ {cost}")
        print(f"Total restock cost: ${total_cost}")
     elif action == "antique":
        print("\n---Antique report by genre---")
        genre_dictionary = []
        for book in book.values():
           genre = book['genre']
           year = int(book ['year'])
           if genre not in genre_dictionary:
              genre_dictionary[genre] = {'oldest': book, 'newest': book}
           else:
              if year  < int(genre_dictionary[genre]['oldest']['year']):
                 genre_dictionary[genre]['oldest'] = book
              if year > int(genre_dictionary[genre]['newest']['year']):
                 genre_dictionary[genre]['newest'] = book
        for genre, data in genre_dictionary.items():
           print(f"\n Genre : {genre}")
           print(f" Oldest : {data ['oldest']['title']} ({data ['oldest']['year']})")
           print(f"Newest : {data ['newest']['title']} ({data ['newest']['year']})")
   except ValueError:
     print("invalid value, must be (inventory/antique)")
def main ():
    while True:
        print("\n menú de opciones")
        print("1. Registrar nuevos libros")
        print("2. Buscar libros")
        print("3. Actualizar información")
        print("4. Eliminar libros")
        print("5. Generar reporte")
        print("6. Salir")
    
        opcion = input("Elige una opción (1-6): ")
    
        if opcion == "1":
            register()
        elif opcion == "2":
            search()
        elif opcion == "3":
            update()
        elif opcion == "4":
            delete()
        elif opcion == "5":
            generate()    
        elif opcion == "6":
            print("Hasta luego! ")
        break
    else:
        print("Opción no válida, intenta de nuevo.\n")

main()
```
