# X-UI-English-

# X-UI ENGLISH VERSION 


  ![repo views](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FVehanRajintha%2FX-UI-English-&count_bg=%2379C83D&title_bg=%23555555&icon=gitpod.svg&icon_color=%23E7E7E7&title=Views&edge_flat=false)


![forks](https://img.shields.io/github/forks/VehanRajintha/X-UI-English-?label=Forks&style=social)
![stars](https://img.shields.io/github/stars/VehanRajintha/X-UI-English-?style=social)

![size](https://img.shields.io/github/repo-size/VehanRajintha/X-UI-English-?color=purple&label=Repo%20Size&style=plastic)
![license](https://img.shields.io/github/license/VehanRajintha/X-UI-English-?color=purple&label=License&style=plastic)
![developer](https://img.shields.io/static/v1?label=Author&message=Vehan%20Rajintha&color=purple&style=plastic)


Another Translated-to-English Version of X-UI; with some of more advanced features implemented. 
 

# Features

- Everything is in English (Serverside setup + Serverside UI + Web UI)
- System status monitoring
- Support multi-user multi-protocol, web page visualization operation
- Multi UUIDs can be added as users for Vmess and Vless configurations with separate QR codes
- IP limitation
- Supported protocols: vmess, vless, trojan, shadowsocks, dokodemo-door, socks, http
- Support to configure more transmission configurations
- Traffic statistics, limit traffic, limit expiration time
- Customizable xray configuration templates
- Support https access panel (bring your own domain name + ssl certificate)
- Telegram Bot for basic functions and noticifactions
- Support one-click SSL certificate application and automatic renewal
- Can be securely migrated from v2-ui 
- Can be securely updated from a previous X-UI (CH/EN) version without lossing outbounds
- For more advanced configuration items, see the panel for details


# Preview
![](media/Web.png)
![](media/PostInstallation.png)


# Single Command Install & upgrade

````
bash <(curl -Ls https://raw.githubusercontent.com/VehanRajintha/X-UI-English-/master/install.sh)
````

## Manual install & upgrade

1. First update your system and run the following commands. (Must have root user permissions)
```` 
sudo su
cd
````
2. Then download the latest compressed package from /releases/latest, generally choose `amd64` architecture
3. Run the following commands respectively:

> If your server cpu architecture is not `amd64`, replace `*` in the command with another architecture

````
rm x-ui/ /usr/local/x-ui/ /usr/bin/x-ui -rf
tar zxvf x-ui-linux-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-linux-* x-ui/x-ui.sh
cp x-ui/x-ui.sh /usr/bin/x-ui
cp -f x-ui/x-ui.service /etc/systemd/system/
mv x-ui/ /usr/local/
systemctl daemon-reload
systemctl enable x-ui
systemctl restart x-ui
````

## Install using docker


1. Install docker

```shell
curl -fsSL https://get.docker.com | sh
````

2. Install x-ui

```shell
mkdir x-ui && cd x-ui
docker run -itd --network=host \
    -v $PWD/db/:/etc/x-ui/ \
    -v $PWD/cert/:/root/cert/ \
    --name x-ui --restart=unless-stopped \
    enwaiax/x-ui:latest
````

> Build your own image

```shell
docker build -t x-ui .
````

## SSL certificate application

The script has 3 built-in SSL certificate application functions. Using a sub-domain is recommended.
- ### 1st Method (Recommended. Works for almost any TLD including Freenom free TLDs)
To use this method to apply for a certificate, your server's IP addres being correctly pointed to a domain or subdomain that you own is the only requirement. (Acme.sh script's 3rd option)

- ### 2nd and 3rd Methods (Use if the above one fails. Would not work for Freenom free TLDs)
This is not beginner frienly as much as the first one. To use this method, all of the follwoing prerequisites should be met:
- Knowing the Cloudflare registered email address
- Knowing the Cloudflare Global API Key
- Having domain name has been resolved to the current server through cloudflare

How to get the Cloudflare Global API Key:
1. Visit the link https://dash.cloudflare.com/profile/api-tokens
2. Click on View Global API Key (See the screenshot below)
        ![](media/APIKey1.PNG)
3. You may have to re-authenticate your account. After that, the API Key will be shown (See the screenshot below)\
        ![](media/APIKey2.png)

When using, just enter `domain name`, `email`, `API KEY`, the diagram is as follows:
        ![](media/DetailEnter.png)

Precautions:

- The script uses DNS API for certificate request
- Use Let'sEncrypt as the CA party by default. You can choose between Zerossl.com or Buypass.com
- The certificate installation directory is the /root/ directory
- The certificates applied for by this script are all generic domain name certificates

## IP Limitation and Multi-User on Same Port
There is almost nothing to explain abount Multi-User thing. You will have separate QR codes along with traffic calculation, expiry date setting and stuff. 

**The IP limitation woks as follows:**

**Occasion:**
- There's a client who is using a v2ray config with IP limitation = 1. 
- He is currently connected to the v2ray server from his PC with Wi-Fi 
- Then he is trying connect to the server using the same v2ray config from his mobile with 4G **AT THE SAME TIME** 

**Outcome :**
- There's no impact to his PC's connection
- On his mobile, he will be succesfully connected for about 10 seconds
- Then, his mobile's internet connection through v2ray will be stopped. Returning **ERR_CONNECTION_CLOSED**. 

**Occasion:**
- Afetr some time, the same client, mentioned above, disonnects his PC from v2ray
- But keeps his mobile trying to connect

**Outcome:**
- After about 10 seconds past disconnecting the PC, he will regain the connection for his mobile.

**If it is a fresh installation, these functions, specially IP limiting, will work flowlessly. But if yours is an upgrading, they miight not work while giving XRAY status : not running. In such cases

## Suggested OSs

- CentOS 7+
- Ubuntu 16+
- Debian 8+


**Happy Coding, Beginner Dev!** 



