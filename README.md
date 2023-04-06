# 28-LDAP:
1. Установить FreeIPA;
2. Написать Ansible playbook для конфигурации клиента;
3. Настроить аутентификацию по SSH-ключам*
4. Firewall должен быть включен на сервере и на клиенте*

Настраиваем сервер и 2 клиента с помощью `ansible`. 
Проверяем доступность веб-интерфейса FreeIPA:    
![Image alt](https://github.com/GuliMari/28-LDAP/blob/main/web_ipa.png)
Добавляем пользователя через веб-интерфейс:
![Image alt](https://github.com/GuliMari/28-LDAP/blob/main/user.png)

Проверяем настройки `client1` и `client2`:
```bash
[root@client1 ~]# kinit ouser
Password for ouser@OTUS.LAN: 
Password expired.  You must change it now.
Enter new password: 
Enter it again: 
...

[root@client2 ~]# kinit ouser
Password for ouser@OTUS.LAN: 
[root@client2 ~]# 

```
