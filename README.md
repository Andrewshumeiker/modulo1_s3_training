# modulo1_s3_training
```python
books =[
   {"title":"","author":"","genre":"","year":"","quantity":"","price":""}
   {"title":"","author":"","genre":"","year":"","quantity":"","price":""}
   {"title":"","author":"","genre":"","year":"","quantity":"","price":""}
   {"title":"","author":"","genre":"","year":"","quantity":"","price":""}
   {"title":"","author":"","genre":"","year":"","quantity":"","price":""}
   ]
def register():
  print ("\n---Register a new book---")
  title = input("Enter title").strip()
  author = input("Enter author").strip()
  genre = input("Enter genre").strip()
  try:
     year = int(input("Enter a year of publication"))
     if year < 1800 or year > 2025:
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
def delete():
def generate():
  
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
        elif opcio == "6":
        print("Hasta luego! ")
        break
        else:
        print("Opción no válida, intenta de nuevo.\n")

main()
```
