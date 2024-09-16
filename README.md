# VPN-at-home

Nesse laboratório vou configurar um ambiente de VPN na minha rede local, assim como um proxy para acessar conteudo web. O objetivo é criar uma infraestrutura segura para acessar a minha rede local remotamente. Esse lab vai servir de base para projetos futuros

# Configurando o Ambiente

Para esse lab vou usar uma VM rodando ubuntu como servidor de Wireguard e squid

## instalando wireguard
Para a instalação vou seguir o [Quick Start Guide](https://www.wireguard.com/quickstart/) do site oficial da wireguard.

* Instalando

![image](https://github.com/user-attachments/assets/47eda06a-fbbf-40b8-b060-d4257382cfc4)

* Criando a interface de rede wg0
  
![image](https://github.com/user-attachments/assets/9b9fad37-06ab-4ae3-9252-5883cc885c5b)
![image](https://github.com/user-attachments/assets/ce89a3eb-0fe7-49df-beaf-bbfde26ac8bd)

* colocando os IPS

![image](https://github.com/user-attachments/assets/2421581f-6405-420f-b8b9-27350bfea039)

* gerando o par de chaves

![image](https://github.com/user-attachments/assets/6b2f9063-8e62-436a-9070-02c4c6d819f4)


* Criando o arquivo de configuração da interface

![image](https://github.com/user-attachments/assets/5b104998-c8a8-470f-b4bb-c8ecd43ee944)
![image](https://github.com/user-attachments/assets/1b40baeb-ea53-4eb0-a306-18b0120fd5f4)

* Instalando Wireguard no cliente
  
** nesse caso estou usando um laptop windows

![image](https://github.com/user-attachments/assets/da15e68e-9138-4762-8e8e-d10d9cc691aa)


* arquivo de configuração do cliente (add empty tunnel ou ctrl + N)


  ![image](https://github.com/user-attachments/assets/36a49897-65b7-4eb1-a3e8-3e0ef4cec26b)

** o wireguard ja vai criar o par de chaves e completar a chave privada, a chave publica fica disponível acima

![image](https://github.com/user-attachments/assets/8b969f98-e1f5-42f2-9dda-45b2c40c1a7d)

* Iniciando o wiregaurd no cliente

![image](https://github.com/user-attachments/assets/8659798b-d606-4aa6-85f4-40152044f281)
![image](https://github.com/user-attachments/assets/84efa95e-d565-45af-b521-2a4e38c16ad8)


* Adicionando o cliente no servidor

![image](https://github.com/user-attachments/assets/3f3a9ec5-1927-4bdf-b31e-975bd942d48e)


* Habilitando IP forwarding

/etc/sysctl.conf
![image](https://github.com/user-attachments/assets/c193e43b-7f0d-474f-8582-795b9555ef40)

![image](https://github.com/user-attachments/assets/b6a08249-e65e-42b5-8b5a-8011c8c48ed5)


### testes de conexão

# Do cliente, é possível pingar o IP interno do servidor, ou seja, estamos na rede interna da VPN.

![image](https://github.com/user-attachments/assets/e8e369be-fb50-4415-9f51-f9e24d74cae0)


# Também é possível pingar o DNS do Google (8.8.8.8), o que mostra que temos conexão com a internet.

![image](https://github.com/user-attachments/assets/362d8bff-a8aa-4196-85b7-a7c7a6ecf8ec)


# Rodando o tracert para o IP interno do servidor, podemos ver que tivemos apenas um hop, ou seja, o cliente está se conectando diretamente com o servidor do WireGuard, sem rotas intermediárias.

![image](https://github.com/user-attachments/assets/49309645-2deb-4df8-907f-758ccd792c4e)

# rodando um webserver apache podemos acessa-lo pela VPN
![image](https://github.com/user-attachments/assets/eb6f8ad5-c9be-4fc6-8514-429c3a141f2a)
![image](https://github.com/user-attachments/assets/5cfcae5e-5c26-4e67-b553-a9dc8aec75a0)


## instalando squid

## teste com servidor apache

