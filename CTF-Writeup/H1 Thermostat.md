Primeiramente, ao entrar no CTF, ele mostra uma página de carregamento que nunca carrega o APK. Porém, ao olhar o código-fonte da página, percebi o request de uma URL para assim montar o APK. Pude baixá-lo e, assim, procurei uma maneira de abri-lo. Fiz isso com o Android Studio, com o qual pude abrir o código-fonte do APK.

![APK aberto](/Images/thermo1.png)

Ao analisar corretamente, decidi verificar a pasta "java", onde encontrei uma subpasta chamada "com.hacker101". Assim que a abri, pude ver um arquivo chamado "PayloadsRequests".

![Caminhos](/Images/thermo2.png)

Quando entrei nesse arquivo e desci um pouco, encontrei uma flag.

![flag0](/Images/thermo3.png)

Logo em seguida, descendo um pouco mais, encontrei outra flag (Kkkkkkkkkkkkkkkkkkkkkk, estou rindo porque não esperava; pensei que estava errado, mas inseri e estava correta).

![flag1](/Images/thermo4.png)
