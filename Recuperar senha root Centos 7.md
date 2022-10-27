# Recuperar senha root Centos 7
1. Na tela de boot, pressionar a tecla E.
![image](https://user-images.githubusercontent.com/26579714/126210606-1c27c648-a266-4805-9045-7fdaa46bfb99.png)
2. Ir até a linha 16 onde encontra a palavra **ro **e editar conforme a o print abaixo:
![image](https://user-images.githubusercontent.com/26579714/126210764-813f708f-0caf-484b-b34b-0d5227263235.png)
3. Editar a palavra ro para: rw init=/sysroot/bin/sh
![image](https://user-images.githubusercontent.com/26579714/126210840-4f306530-cb48-4090-a980-9aa7fc2e5778.png)
4. Pressione Ctrl + x  
![image](https://user-images.githubusercontent.com/26579714/126210914-53540e7e-eefb-4b7d-80a9-c1e458934557.png)
5. Para acessar o S.O. use o comando abaixo:  
:# chroot /sysroot
6. Resetar a senha:  
:/# ```passwd```
7. Atualizar a informação no selinux:  
:/# touch ./autorelabel
8. Sair do chroot:  
:/# exit
9. Reinicie o S.O.  
:/# reboot  

Logar com a senha definida.
