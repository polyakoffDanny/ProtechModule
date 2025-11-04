#### Установка OpenMediaVault.
1. Установил iso OMV, загрузил его в pnet lab, создал qcow2 virtioa, а дальше пошла установка как установка обычного линукс:
![](images/OMV%20и%20Oxidized-25.10.2025-15_10.png)
![](images/OMV%20и%20Oxidized-25.10.2025-15_10-1.png)![](images/OMV%20и%20Oxidized-25.10.2025-15_10-2.png)
![](images/OMV%20и%20Oxidized-25.10.2025-15_10%201.png)
2. Выдал IP интерфейсам, зашел по ip на веб-интерфейс:

![](images/OMV%20и%20Oxidized-25.10.2025-18_10.png)

#### Установка Oxidized.
1. Сначала установил зависимости:
```
sudo apt install-y ruby ruby-dev libsqlite3-dev libssl-dev pkg-config cmake libssh2-1-dev libicu-dev zlib1g-dev g++ libyaml-dev nginx apache2-utils jq gi
sudo gem install oxidized oxidized-web oxidized-script
```

2. Настроил системного пользователя и структуру каталогов, также git-репозиторий для хранения конфигураций:
![](images/OMV%20и%20Oxidized-25.10.2025-19_10-4.png)
3. Далее настроил /opt/oxidized/config/config:
![](images/OMV%20и%20Oxidized-25.10.2025-19_10-5.png)
4. Далее настроил /opt/oxidized/config/node.db:
![](images/OMV%20и%20Oxidized-25.10.2025-19_10-6.png)
5. В конце сервис /etc/systemd/system/oxidized.service:
![](images/OMV%20и%20Oxidized-25.10.2025-20_10.png)

6. Включил службу и зашел на веб-интерфейс
![](images/OMV%20и%20Oxidized-25.10.2025-21_10.png)

![](images/OMV%20и%20Oxidized-25.10.2025-21_10-1.png)
![](images/OMV%20и%20Oxidized-04.11.2025-11_11.png)

![](images/OMV%20и%20Oxidized-04.11.2025-11_11-1.png)
![](images/OMV%20и%20Oxidized-04.11.2025-12_11.png)

![](images/OMV%20и%20Oxidized-04.11.2025-12_11-1.png)
Также можно сделать уведомление в ТГ, которое будет приходить, если конфиг не сохранился: 
![](images/📖%20Установка%20Oxidized.pdf)