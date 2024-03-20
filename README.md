# Contact-info
import json

def load_contacts():
    try:
        with open('contacts.json', 'r') as file:
            contacts = json.load(file)
    except FileNotFoundError:
        contacts = {}
    return contacts

def save_contacts(contacts):
    with open('contacts.json', 'w') as file:
        json.dump(contacts, file, indent=4)

def add_contact(name, number, contacts):
    contacts[name] = number
    save_contacts(contacts)
    print(f"Contact '{name}' added successfully.")

def view_contacts(contacts):
    if not contacts:
        print("No contacts found.")
    else:
        print("Contacts:")
        for name, number in contacts.items():
            print(f"{name}: {number}")

def main():
    contacts = load_contacts()
    
    while True:
        print("\n1. Add Contact")
        print("2. View Contacts")
        print("3. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == '1':
            name = input("Enter contact name: ")
            number = input("Enter contact number: ")
            add_contact(name, number, contacts)
        elif choice == '2':
            view_contacts(contacts)
        elif choice == '3':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
