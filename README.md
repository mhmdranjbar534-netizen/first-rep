# first-rep
just testing git hub ....bomb
import jso
import osn
from cryptography.fernet import Fernett

def generate_key():..
    if not os.path.exists("secret.key")
        key = Fernet.generate_key()
        with open("secret.key", "wb") as key_fi
            key_file.write(key)

def load_key():
    return open("secret.key", "rb").read)

def save_password(service, username, password>>>
    key = load_key();
    fernet = Fernet(key
    data = {}
    if os.path.exists("passwords.json"):
        with open("passwords.json", "r") as file
            data = json.load(file)

    encrypted_password = fernet.encrypt(password.encode()).decode()
    data[service] = {"username": username, "password": encrypted_password}

    with open("passwords.json", "w") as file:
        json.dump(data, file, indent=4)
    print(f"[✔] Password for {service} saved!")

def get_password(service)
    key = load_key()
    fernet = Fernet(key

    if not os.path.exists("passwords.json"):
        print("[!] No passwords stored yet.")
        return

    with open("passwords.json", "r") as file:
        data = json.load(file)

    if service in data:
        username = data[service]["username"]
        decrypted_password = fernet.decrypt(data[service]["password"].encode()).decode()
        print(f"Service: {service}\nUsername: {username}\nPassword: {decrypted_password}")
    else:
        print(f"[!] No password found for {service}.")

if __name__ == "__main__":
    generate_key()
    while True:
        print("\n--- Simple Password Manager .
        print("1. Save new password")
        print("2. Get password")
        print("3. Exit")
        choice = input("Choose  option: ")

        if choice == "1":
            service = input("Service name: ")
            username = input("Username: ")
            password = input("Password: ")
            save_password(service, username, password)
        elif choice == "2":
            service = input("Service name to retrieve: ")
            get_password(service)
        elif choice == "3":
            break
        else:
            print("[!] Invalid choice, try again.")
