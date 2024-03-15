Para este CTF do Petshop Pro, primeiro adicionei um gatinho ao carrinho. Em seguida, inspecionei a página de checkout e encontrei um campo chamado "type=hidden". Ao removê-lo da página, pude trazer um campo de entrada editável para a página. Alterei o preço para $0 e concluí o checkout, obtendo assim a primeira flag.

![flag0](/Images/petshop1.png)

Para encontrar o diretório "/login" necessário para a segunda flag, tive que usar o Kali. Utilizei a ferramenta Gobuster para procurar outros diretórios, usando o seguinte comando:

```
gobuster dir -u https://333941b5e1da213de163456e063d3d1f.ctf.hacker101.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 30
```

![output gobuster](/Images/petshop2.png)

Ao acessar a página, vi que precisava de um nome de usuário e uma senha para fazer login como administrador. Para isso, usei novamente o Kali, com a ferramenta Hydra para usar uma wordlist de nomes de usuário e tentar encontrar a combinação correta, usando o seguinte comando:

```
hydra -L Desktop/usernames.txt -p jinx -t 40 333941b5e1da213de163456e063d3d1f.ctf.hacker101.com https-post-form "/login:username=^USER^&password=^PASS^:Invalid username"
```

![output hydra username](/Images/petshop3.png)

Em seguida, usei um comando quase idêntico, apenas modificando para encontrar a senha:

```
hydra -l christyna -P Desktop/10-million-password-list-top-100000.txt -t 40 333941b5e1da213de163456e063d3d1f.ctf.hacker101.com https-post-form "/login:username=^USER^&password=^PASS^:Invalid password"
```

![output hydra password](/Images/petshop4.png)

Finalmente, ao fazer login com as credenciais corretas, encontrei a flag:

![flag1](/Images/petshop5.png)

Ganhei permissão para editar os itens por causa da conta de administrador. Então, a primeira coisa que fiz foi testar todas as entradas inserindo um pequeno script, "img src=x onerror=alert(1)", em todos os campos. Recebi um erro, então removi um dos scripts de erro de imagem e salvei novamente. Ao salvar, adicionei ao carrinho e obtive a flag.

![flag2](/Images/petshop6.png)
