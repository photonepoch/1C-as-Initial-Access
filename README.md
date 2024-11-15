# 1C-as-Initial-Access
Этот проект показывает PoC как может специалист red team использовать возможности 1С для получение доступа к тестируемой машине.

# PoC Video


## Мануал

Перед тем как мы начнем, опишу используемое ПО:
  - 1C Предприятие 8 - Что бы разработать внешнюю обработку в конфигуратор и запустить её режиме предприятия
  - Wampserver - Сервер который выдаст полезную нагрузку в виде простого MessageBox

Создадим любой проект в режиме Конфигуратора
1) Создадим Внешняю обработку, используя Файл -> Новый -> Внешняя обработка
   ![1](https://github.com/user-attachments/assets/15568b46-99c1-447c-99fc-5debe02918c0)
   
2) Назовем его как хотим и нажмем на "лупу"
   ![2](https://github.com/user-attachments/assets/8fe80fa6-d237-4a55-8264-7bdd05240d42)

3) Нажимаем "Готово"
   ![3](https://github.com/user-attachments/assets/4fa5c302-b2fd-4262-b3a0-b725a680b004)

4) Добавляем команду и переносим её на панель, что бы пользователь нажал на кнопку и запустил нагрузку
   ![4](https://github.com/user-attachments/assets/735a6936-92ee-48c6-b443-c066972e3eb1)
   ![5](https://github.com/user-attachments/assets/ce848886-c45f-4551-b76c-c65e32672478)


5) Добавляем код из файла code.1c и сохраняем файл
   ![7](https://github.com/user-attachments/assets/6ccb35f1-fe44-4282-9e40-402bff40df2d)


6) Теперь мы можем как пример отправить письмо заинтересованому лицу (обычно бухгалтер), с следующим притекстом:
   "Здраствуйте, мы компания которая занимается 1С Разработкой, и у нас появился новый продукт по интеграции ЭДО, Ватсап, чего-либо-еще.
   Мы создали внешнюю обработку, попробуйте запустить её в 1С"

## Заметки
1) Так как это PoC, то функционал предоставленный здесь довольно мал и сегодняшнии технологии защиты быстро отсекут полезную нагрузку.
Можно попытаться сделать запуск полезной нагрузки как fileless вызывая PowerShell. 
2) Прошу заметить что у каждого пользователя 1С стоят очень разные настройки. В видео запуска были видны "предупреждения",
   хотя при тестировании одного и того же кода на другой системе таких же уведомлений не поступало.

# English Speaking Version

## 1C-as-Initial-Access
This project is Proof-of-Concept of using quite popular software called 1C as a means to achieve initial foothold at internal network.

## What is 1C?
1C is complex ecosystem of software products in use in CIS countries (particulary Russia). Most often it is used for internal finance bookeeping.
You can learn more about particular use case related to this manual here: https://v8.1c.ru/buhv8/

## How can I leverage 1C to achieve initial access?

Before we dive in, let us for prepare infrastructure for this PoC:
I use Windows 10 machine with following software:
  - 1C Предприятие 8 - to develop thic PoC
  - Wampserver - to host simple MessageBox PE executable (http://localhost/hello.exe)

First let create any project under 1C and get to Конфигуратор mode
1) We need to create Внешняя обработка, using Файл -> Новый -> Внешняя обработка
   ![1](https://github.com/user-attachments/assets/15568b46-99c1-447c-99fc-5debe02918c0)
   
2) Then we name project whatever we want and click at icon of magnifying glass
   ![2](https://github.com/user-attachments/assets/8fe80fa6-d237-4a55-8264-7bdd05240d42)
   
3) Just click "Готово"
   ![3](https://github.com/user-attachments/assets/4fa5c302-b2fd-4262-b3a0-b725a680b004)

4) We create command and move it to the form so user could click button and launch our payload
   ![4](https://github.com/user-attachments/assets/735a6936-92ee-48c6-b443-c066972e3eb1)
   ![5](https://github.com/user-attachments/assets/ce848886-c45f-4551-b76c-c65e32672478)

6) Insert code from code.1c file
  ![7](https://github.com/user-attachments/assets/6ccb35f1-fe44-4282-9e40-402bff40df2d)

8) After all of this, we could use mail to send phishing message to accountant (much more chance that they use 1C to do everyday tasks) with pretext like this:
   "Hello, We are 1C Software development company and we created new product to integrate your database
   with Jira/Whatsapp whatever. You could try it using out external configuration. Please download it and put it inside
   your active 1C Client instance so you could see how amazing our product is"

## TODO
As 1C language could leverage COM objects and many more features, we can create fileless dropper. 
In video you can see user could be presented with warnings, but keep in mind that security configuration differs between different versions of 1C, different databases in use etc.
I had tested it on two different machines, with different 'Demo database' configurations and language settings yet I wasnt warned as much as in PoC video.
