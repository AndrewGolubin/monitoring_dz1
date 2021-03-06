# monitoring_dz1

Что необходимо сделать:
1. На виртуальной машине установите любую open source CMS которая включает в себя следующие компоненты: nginx, php-fpm, database (MySQL or Postgresql)
2. На этой же виртуальной машине установите Prometheus exporters для сбора метрик со всех компонентов системы (начиная с VM и заканчивая DB, не забудьте про blackbox exporter который будет проверять доступность вашей CMS)
3. На этой же или дополнительной виртуальной машине установите Prometheus задачей которого будет раз в 5 секунд собирать метрики с экспортеров
4. На этой же или дополнительной виртуальной машине установите Alertmanager и сконфигурируйте его таким образом чтобы в случае недоступности какого либо компонента был отправлен alert с важность Critical в один из каналов оповещений (канал оповещений на выбор: slack or telegram)

Отчет:
1. В среде vmware подняты 2 ВМ: WP-Cloud (192.168.12.168) и Virt2 (192.168.12.179). На обоих хостах установлен docker, docker-compose, и поднят portainer для управления контейнерами. Доступ к общей консоли управления организован на Virt2.
2. На WP-Cloud, в докере, развернута CMS WordPress, орагнизован проброс внешнего трафика, настроен DNS на хосте провайдера, организовано получение и обновление ssl сертификатов. CMS доступна на https://cloud.cardio32.ru. Конфигурационные файлы в каталоге GAP-1/WP-Cloud.
3. На Virt2, в докере, развернуты и настроены prometheus, alermanager, blackbox exporter, node exporter, telegram-bot, настроена передача алертов в телеграмм. Конфигурционные файлы в каталоге GAP-1/Virt2
4. Скрины - ниже.

Консоль управления

![Консоль управления докерами](https://user-images.githubusercontent.com/23739863/169861856-b1c7c3a9-5d4a-4fbb-ab46-d7f39e2964c9.png)

Контейнеры на WP-Cloud

![WP-Cloud](https://user-images.githubusercontent.com/23739863/169865049-33ea30fb-f020-42a6-a197-cffeeb8b1dde.png)

Главная страница CMS

![CMS-Images](https://user-images.githubusercontent.com/23739863/169867665-1c517fe3-9e6b-4376-9131-50894010cef3.png)

Контейнеры на Virt2

![Контейнеры на Virt2](https://user-images.githubusercontent.com/23739863/169869404-b58bc89d-58bb-4220-b684-3ea669aae6ad.png)

Targets-ы prometheus

![targets](https://user-images.githubusercontent.com/23739863/169870335-7c189eb1-ac90-4b54-961b-76493a983df4.png)

Alert-ы prometheus

![alets](https://user-images.githubusercontent.com/23739863/169871066-8972dc00-7dfd-4374-b104-27932c469788.png)

Стоп контейнеров с CMS

![StopCMS](https://user-images.githubusercontent.com/23739863/169969772-22fc7f7a-d19f-49ce-96b6-f14037935406.png)

Активный алерт

![ActivAlert](https://user-images.githubusercontent.com/23739863/169969953-3da4b66e-aaa8-4f50-aecd-ee7ad87ade45.png)

Алерт в alertmanager-е

![Alertmanager](https://user-images.githubusercontent.com/23739863/169970158-d7fd48ca-b37c-4876-b535-8c2cc0121909.png)

Сообщение в телеграмм

![TelegrammMess](https://user-images.githubusercontent.com/23739863/169972465-a5d0fa4c-b57f-4793-8259-b8bcbf29b4f0.png)








