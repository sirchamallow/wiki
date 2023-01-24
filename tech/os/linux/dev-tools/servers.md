---
description: Outils pour serveurs
---

# 🖥 Serveurs

### Netdata

Si vous gérez votre petit serveur dédié et que pour vous, le suivi des performances en temps réel de celui-ci est important, sachez qu’il existe un outil de monitoring nommé **Netdata** qui permet de surveiller à la seconde près des tas de paramètres. \
\
L'avantage, c’est que Netdata propose des dashboard plutôt jolies 🤩

```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh) all # Download and install Netdata 
systemctl start netdata 				# Start the Netdata service
systemctl enable netdata 				# Now make service enable so that on boot up it start automatically
systemctl status netdata 				# Now check the status
firewall-cmd --permanent --add-port=19999/tcp 		# Allow Netdata default port to pass through firewall
firewall-cmd --reload 					# Reload the firewall
https//server-ip:19999					# Open browser and go to you server ip
```

Source : [https://www.linuxhelp.com/how-to-install-netdata-on-fedora-34](https://www.linuxhelp.com/how-to-install-netdata-on-fedora-34)\
Alternative : [https://learn.netdata.cloud/docs/agent/packaging/installer/methods/kickstart](https://learn.netdata.cloud/docs/agent/packaging/installer/methods/kickstart)
