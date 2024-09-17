# Моя научная работа
имя:ван яо

группа:НПМбд-02-21

билет:1032215430

## цель
 установкa DVWA

### Подготовка перед установкой

1.Обновление системы

- Убедитесь, что ваша система Kali Linux обновлена до последней версии:
sudo apt update && sudo apt upgrade -y
![](https://github.com/wangyao200036/infosec/raw/main/work2_pic/1.png)
2.Проверка веб-сервера

- Убедитесь, что Apache2, PHP и база данных MySQL уже установлены. В Kali Linux эти компоненты обычно уже установлены по умолчанию:
sudo service apache2 status
sudo service mysql status

### Установка DVWA

1.Загрузка DVWA

- Скачайте последнюю версию DVWA с GitHub

cd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git
![](https://github.com/wangyao200036/infosec/raw/main/work2_pic/7.png)
2.Настройка базы данных

- Перейдите в каталог DVWA:
![](https://github.com/wangyao200036/infosec/raw/main/work2_pic/2.png)
cd DVWA
- Создайте базу данных для DVWA:

sudo mysql -u root -p

После ввода пароля пользователя root выполните следующие команды:

CREATE DATABASE dvwa;
GRANT ALL ON dvwa.* TO 'dvwa'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
EXIT;

3.Импорт базы данных DVWA

- Импортируйте SQL файл DVWA:

sudo mysql -u dvwa -p dvwa < dvwa.sql
![](https://github.com/wangyao200036/infosec/raw/main/work2_pic/6.png)
4.Конфигурация DVWA

- Отредактируйте конфигурационный файл DVWA:

sudo nano dvwa/vulnerabilities/config.inc.php

- Измените параметры подключения к базе данных:

$db['host'] = 'localhost';
$db['username'] = 'dvwa';
$db['password'] = 'password';  // Замените на ваш пароль
$db['database'] = 'dvwa';
5.Настройка уровня безопасности

- По умолчанию DVWA устанавливает определенный уровень безопасности. Вы можете изменить его, отредактировав файл security.php:

sudo nano dvwa/hackable/users/admin/config.php

- Измените уровень безопасности:

$DVWA['security'] = 'low';
![](https://github.com/wangyao200036/infosec/raw/main/work2_pic/4.png)
6. Перезапуск Apache

- Перезапустите Apache, чтобы применить изменения:

sudo systemctl restart apache2

### Доступ к DVWA
- Откройте браузер и перейдите по адресу:

http://localhost/DVWA/

- Логин и пароль по умолчанию:
- 
Имя пользователя: admin
Пароль: password
![](https://github.com/wangyao200036/infosec/raw/main/work2_pic/3.png)

