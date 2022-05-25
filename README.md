# Opennebula Matryoshka

## Постановка ~~домашки~~ задачи:
Необходимо написать Vagrantfile который по команде vagrant up сделает следующее:

1) Запустит бокс Ubuntu 20.04 (https://app.vagrantup.com/generic/).

2) Внутри ВМ произойдет автоматическая установка docker и docker compose (используя ansible).

3) С помощью docker compose (docker-compose up, сам docker compose стоит дернуть так же через ansible) будет запущен контейнер с opennebula, который будет настроен как front end.

4) ВМ из пункта 1 необходимо настроить как opennebula-node (используя ansible).

5) Добавить ВМ из пункта 1 в front end как вычислительный узел.

6) Контейнер с opennebula должен экспозить 9869 порт в ВМ с убунту.

7) Сама ВМ с убунту должна экспозить 80 порт в хостовую машину.

____

## ToDo List:
:white_check_mark: Vagrant
:black_square_button: test Vagrant
:white_check_mark: Ansible-playbooks
:white_check_mark: test Ansible-playbooks
:black_square_button: Вынести все пароли в файлы, переменные среды, секреты
:white_check_mark: Docker-compose
:white_check_mark: test Docker-compose
:black_square_button: Документация ко всей кодовой базе

____

## Что надо чтобы запустить?
``` bash
$ git clone <thisRepoUrl>
$ # fingers_crossed
$ vagrant up
```

____

### Послесловие

Интернет в моей глуши (в которой я временно пребываю) оставляет желать лучшего и потому, дорогой читатель, я не смог протестировать Vagrant. Однако уверяю тебя, это должно заработать. Со всей отвественностью подходя к этому делу, я просмотрел много документации и выполнял всё строго по инструкциям жителей форумов. И потому прошу, не будь слишком строг ко мне в отношении Vagrant. Ведь легко Ops-ера обидеть, сложнее Ops-ера понять.
Искренне ваш, создатель матрёшки.