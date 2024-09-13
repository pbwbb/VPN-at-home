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
** nesse caso estou usando um desktop ubuntu
![image](https://github.com/user-attachments/assets/1c6b33ff-9ae8-4df1-9e77-f07145f4ec31)

* Criando o par de chaves do cliente

![image](https://github.com/user-attachments/assets/5a5b87f3-ab58-4c0f-aa44-f5a4976d2afe)

* arquivo de configuração do cliente

![image](https://github.com/user-attachments/assets/cf52d23a-26b5-491a-a744-5924e8ec7777)


[Interface]
PrivateKey = <client-private-key>
Address = 10.66.66.2/24
DNS = <dns-server>   # Optional, but useful for resolving domain names while using the VPN

[Peer]
PublicKey = <server-public-key>
Endpoint = <server-ip>:51820
AllowedIPs = 0.0.0.0/0  # This routes all traffic through the VPN

* Iniciando a interface no cliente
* 



* Adicionando o cliente no servidor

![image](https://github.com/user-attachments/assets/8ffdd9c7-9e09-40d1-b9aa-d1781b75c020)


[Peer]
PublicKey = <client-public-key>
AllowedIPs = 10.66.66.2/32


* Habilitando IP forwarding

/etc/sysctl.conf
![image](https://github.com/user-attachments/assets/c193e43b-7f0d-474f-8582-795b9555ef40)

![image](https://github.com/user-attachments/assets/b6a08249-e65e-42b5-8b5a-8011c8c48ed5)



### testes de conexão

## instalando squid

## teste com servidor apache

