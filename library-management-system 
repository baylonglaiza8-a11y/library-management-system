from datetime import datetime

# === 1. CLASSES - ITO YUNG MGA BLUEPRINT ===
class Book:
    def __init__(self, book_id, title, author):
        self.book_id = book_id
        self.title = title
        self.author = author
        self.is_available = True

class Member:
    def __init__(self, member_id, name, email):
        self.member_id = member_id
        self.name = name
        self.email = email

class Loan:
    def __init__(self, loan_id, book, member):
        self.loan_id = loan_id
        self.book = book
        self.member = member
        self.date_borrowed = datetime.now()
        self.is_active = True
    
    def return_book(self):
        self.is_active = False
        self.book.is_available = True

# === 2. LIBRARY SYSTEM - DITO LAHAT NG FUNCTIONS ===
class Library:
    def __init__(self):
        self.books = []
        self.members = []
        self.loans = []
        self.next_loan_id = 1
        self.next_member_id = 3
        self.next_book_id = 3
        
        # Sample data para ma-test agad
        self.members.append(Member(1, "Juan Dela Cruz", "juan@email.com"))
        self.members.append(Member(2, "Maria Santos", "maria@email.com"))
        self.books.append(Book(1, "The Hobbit", "J.R.R. Tolkien"))
        self.books.append(Book(2, "Python 101", "John Doe"))

    # Helper functions
    def get_book(self, book_id):
        for book in self.books:
            if book.book_id == book_id:
                return book
        return None

    def get_member(self, member_id):
        for member in self.members:
            if member.member_id == member_id:
                return member
        return None
    
    def get_loan(self, loan_id):
        for loan in self.loans:
            if loan.loan_id == loan_id:
                return loan
        return None

    # FEATURE #1: Add Book
    def add_book(self):
        try:
            book_id = self.next_book_id
            title = input("Input: Book Title: ")
            author = input("Input: Book Author: ")
            new_book = Book(book_id, title, author)
            self.books.append(new_book)
            self.next_book_id += 1
            print(f"Book added successfully! ID: {book_id}")
        except Exception as e:
            print(f"Error: {e}")

    # FEATURE #2: Add Member
    def add_member(self):
        try:
            member_id = self.next_member_id
            name = input("Input: Member Name: ")
            email = input("Input: Member Email: ")
            new_member = Member(member_id, name, email)
            self.members.append(new_member)
            self.next_member_id += 1
            print(f"Member added successfully! ID: {member_id}")
        except Exception as e:
            print(f"Error: {e}")

    # FEATURE #3: Borrow Book
    def borrow_book(self):
        try:
            book_id = int(input("Input: Book ID: "))
            member_id = int(input("Input: Member ID: "))
            
            book = self.get_book(book_id)
            if book is None:
                raise Exception("Book not found.")
            
            member = self.get_member(member_id)
            if member is None:
                raise Exception("Member not found.")
            
            if book.is_available == False:
                raise Exception("Book is already borrowed.")
            
            book.is_available = False
            loan = Loan(self.next_loan_id, book, member)
            self.loans.append(loan)
            self.next_loan_id += 1
            print(f"{member.name} borrowed {book.title}")
            
        except ValueError:
            print("Error: Please enter valid numbers for IDs.")
        except Exception as e:
            print(f"Error: {e}")

    # FEATURE #4: Return Book
    def return_book(self):
        try:
            loan_id = int(input("Input: Loan ID: "))
            
            loan = self.get_loan(loan_id)
            if loan is None:
                raise Exception("Loan not found.")
            
            if loan.is_active == False:
                raise Exception("Loan is already closed.")
            
            loan.return_book()
            print(f"{loan.member.name} returned {loan.book.title}")
            
        except ValueError:
            print("Error: Please enter a valid number for Loan ID.")
        except Exception as e:
            print(f"Error: {e}")

    # FEATURE #5: View Books
    def view_books(self):
        books = self.books
        if len(books) == 0:
            print("No books found.")
        else:
            print("Books:")
            for book in books:
                status = "Available" if book.is_available else "Borrowed"
                print(f"{book.book_id} - {book.title} by {book.author} [{status}]")

    # FEATURE #6: View Members
    def view_members(self):
        members = self.members
        if len(members) == 0:
            print("No members found.")
        else:
            print("Members:")
            for member in members:
                print(f"{member.member_id} - {member.name} ({member.email})")

    # FEATURE #7: View Loans
    def view_loans(self):
        loans = self.loans
        if len(loans) == 0:
            print("No loans found.")
        else:
            print("Loans:")
            for loan in loans:
                status = "Active" if loan.is_active else "Closed"
                print(f"{loan.loan_id} - {loan.member.name} borrowed {loan.book.title} ({status})")

# === 3. MAIN PROGRAM - ITO YUNG MENU ===
def main():
    library = Library()
    
    while True:
        print("\n--- Library Management System ---")
        print("1. Add Book")
        print("2. Add Member")
        print("3. Borrow Book")
        print("4. Return Book")
        print("5. View Books")
        print("6. View Members")
        print("7. View Loans")
        print("8. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == "1":
            library.add_book()
        elif choice == "2":
            library.add_member()
        elif choice == "3":
            library.borrow_book()
        elif choice == "4":
            library.return_book()
        elif choice == "5":
            library.view_books()
        elif choice == "6":
            library.view_members()
        elif choice == "7":
            library.view_loans()
        elif choice == "8":
            print("Program closed.")
            break
        else:
            print("Invalid choice. Try again.")

# === 4. RUN THE PROGRAM ===
if __name__ == "__main__":
    main()