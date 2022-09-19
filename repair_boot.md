# Forçar fsck na inicialização do sistema  
1 - Crie um arquivo de nome forcefsck na partição raiz do sistema danificado
touch /forcefsck
2 - Reinicie o systema.
reboot

# Segunda opção
1 - Reinicie o servidor e pressione a tecla shift
Durante a inicialização, mantenha pressionada a shifttecla para que o menu grub seja mostrado. Selecione as “ Opções avançadas ”.  
![image](https://user-images.githubusercontent.com/26579714/191116335-4d92a28c-a354-4082-99c7-3ff22b7b3a55.png)  

2 - Em seguida, escolha “ Modo de recuperação ”.  
![image](https://user-images.githubusercontent.com/26579714/191116457-1aa60e1c-8e1a-4f4a-a840-898b6ae1bf67.png)

3 - No próximo menu selecione “ fsck ”.  
![image](https://user-images.githubusercontent.com/26579714/191116616-c7bd83a7-898d-4a64-863c-9de1c4ab39e2.png)

Você será perguntado se deseja que seu sistema de /arquivos seja remontado. Selecione “yes”.  
Confirmar sistema de arquivos raiz  

Você deve ver algo parecido com isso.  
![image](https://user-images.githubusercontent.com/26579714/191116706-a8cd5078-2647-48d3-8860-55d895e15ba7.png)

Você pode então retomar a inicialização normal, selecionando “Resume” .  
![image](https://user-images.githubusercontent.com/26579714/191116742-48de1ac5-b222-47f2-b366-d9c36b9b0440.png)

Selecione a inicialização normal  
Neste tutorial você aprendeu como usar o fsck e executar verificações de consistência em diferentes sistemas de arquivos Linux. 
Se você tiver alguma dúvida sobre o fsck , não hesite em enviá-las na seção de comentários abaixo  
