---
creation_time: 2024-01-27 02:54
parents:
  - "[[Remote Access]]"
  - "[[Bash - Unix Shell]]"
  - "[[Communication Protocol]]"
---
[[Secure Shell Protocol (SSH)]] - это тоже сетевой протокол для [[Remote Access|удаленного подключения]] и управления девайсом через командную строку терминала. SSH передаёт данные по [[Transport Control Protocol (TCP). Internet Protocol (IP).|TCP]] в текстовом виде. Передающиеся данные шифруется, предотвращая перехват данных и гарантируя безопасное подключение.

**Authentication** and **Encrypted Connection**
SSH может использовать [[RSA]]-ключи и [[Digital Signature Algorithm (DSA)|DSA]]-подобный алгоритм под капотом для аутентификации пользователя, а установление зашифрованного соединения происходит симметричными алгоритмами по типу [[Advanced Encryption Standard (AES)|AES]] с секретным-ключом обменивающимся между сторонами с помощью [[Diffie-Hellman Key Exchange (DH)|Diffie-Hellman]].

Работа SSH описывается ниже.

---

2024-07-21
Для меня открытие, что RSA ключи используются только для аутентификации через логин/пароль, но сейчас без паролей, в основном просто по типу [[Digital Signature Algorithm (DSA)|DSA]] подписи клиента сгенерированных сервером рандомных байтов (challenge).

Не RSA используется для шифрования данных, а используются симметричные алгоритмы шифрования типа [[Data Encryption Standard (DES)|DES]], [[Advanced Encryption Standard (AES)|AES]] . Они оказывается симметричные.

[[Diffie-Hellman Key Exchange (DH)|Diffie-Hallman]] - это алгоритм вычисления общего секретного ключа, который позже можно использовать в симметричных алгоритмах шифрования типа DES, AES.

---

Также протокол используется для передачи файлов, например в [[SSH File Transfer Protocol (SFTP)]], [[Secure Copy Protocol (SCP)]]. SFTP позволяет безопасно передавать файлы и работать с файловой системой, в то время как SCP прост и позволяет только копировать файлы.

---

See also:
- [[Remote Access]]
- [[Shell Interface]]
- [[Interface]]
- [[Internet]]
- [[Telnet vs. SSH]]
- [[Cryptography]]
- [[SSH Proxy Tunnel]]
- [[Git - SSH to GitHub Remote Repositories]]
