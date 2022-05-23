# monitoring_dz1

Что необходимо сделать:
1. На виртуальной машине установите любую open source CMS которая включает в себя следующие компоненты: nginx, php-fpm, database (MySQL or Postgresql)
2. На этой же виртуальной машине установите Prometheus exporters для сбора метрик со всех компонентов системы (начиная с VM и заканчивая DB, не забудьте про blackbox exporter который будет проверять доступность вашей CMS)
3. На этой же или дополнительной виртуальной машине установите Prometheus задачей которого будет раз в 5 секунд собирать метрики с экспортеров
4. На этой же или дополнительной виртуальной машине установите Alertmanager и сконфигурируйте его таким образом чтобы в случае недоступности какого либо компонента был отправлен alert с важность Critical в один из каналов оповещений (канал оповещений на выбор: slack or telegram)

Отчет:
1. В среде vmware подняты 2 ВМ: WP-Cloud (192.168.12.168) и Virt2 (192.168.12.179). На обоих хостах установлен docker, docker-compose, и поднят portainer для управления контейнерами. Доступ к общей консоли управления организован на Virt2.
2. На WP-Cloud, в докере, развернута CMS WordPress, орагнизован проброс внешнего трафика, настроен DNS на хосте провайдера, организовано получение и обновление ssl сертификатов. CMS доступна на https://cloud.cardio32.ru. Конфигурационные файлы в каталоге GAP-1/WP-Cloud.
3. На Virt2, в докере, развернуты и настроены prometheus, alermanager, blackbox exporter, node exporter, telegram-bot. Конфигурционные файлы в каталоге GAP-1/Virt2
4. Скрины - ниже.
![ScreenShot](https://cloud.mail.ru/public/YSrk/vrXbnQ4LF)
