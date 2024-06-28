
# Installation 

    git clone https://github.com/xiv3r/acunetix_24.4.240514098_x64.git
    cd acunetix_24.4.240514098_x64

1. Before installing the tool, add to your hosts file (usually /etc/hosts) at the end:
```
sudo cd /etc/hosts

127.0.0.1  erp.acunetix.com
127.0.0.1  erp.acunetix.com.
::1  erp.acunetix.com
::1  erp.acunetix.com.

192.178.49.174  telemetry.invicti.com
192.178.49.174  telemetry.invicti.com.
2607:f8b0:402a:80a::200e  telemetry.invicti.com
2607:f8b0:402a:80a::200e  telemetry.invicti.com.
```
2. Now install the tools

  `sudo bash acunetix_24.4.240514098_x64.sh`

3. Once installed let's stop its service

  `sudo systemctl stop acunetix`

4. Let's replace wvsc file:

```
sudo cp wvsc /home/acunetix/.acunetix/v_240514098/scanner/wvsc
sudo chown acunetix:acunetix /home/acunetix/.acunetix/v_240514098/scanner/wvsc
sudo chmod +x /home/acunetix/.acunetix/v_240514098/scanner/wvsc
```

5. Time to add licenses:

```
sudo rm /home/acunetix/.acunetix/data/license/*
sudo cp license_info.json /home/acunetix/.acunetix/data/license/
sudo cp wa_data.dat /home/acunetix/.acunetix/data/license/
sudo chown acunetix:acunetix /home/acunetix/.acunetix/data/license/license_info.json
sudo chown acunetix:acunetix /home/acunetix/.acunetix/data/license/wa_data.dat
sudo chmod 444 /home/acunetix/.acunetix/data/license/license_info.json
sudo chmod 444 /home/acunetix/.acunetix/data/license/wa_data.dat
sudo chattr +i /home/acunetix/.acunetix/data/license/license_info.json (Pay attention to copy and paste right, this can damage your entire  OS!!!)
sudo chattr +i /home/acunetix/.acunetix/data/license/wa_data.dat
```

6. Now let's restart acunetix:

  `sudo systemctl start acunetix`
