---
layout: post
title: "Добавить мультиязычность большому самописному интернет-магазину косметики Tiande"
meta_title: "Добавить мультиязычность большому самописному интернет-магазину косметики Tiande"
meta_description: "Для крупного (по крайней мере технически крупного) самописного интернет-магазина была добавлена мультиязычность."
tags:
- мультиязычность
- самопис
- интернет-магазин
- поддержка
- дебаг
- багфиксинг
- php
- sql
- vps
- mvc
- cron
- портфолио
location: "Украина, Харьков"
---

Для крупного (по крайней мере технически крупного) <ins>самописного</ins> интернет-магазина <a href="https://tiande-shop.com.ua/" target="_blank">Tiande</a> была добавлена мультиязычность.

## Дебаг

Проделал большую работe по определнию структуры сайта, определению связей между модулями системы. Сайт не использовал никакой фреймоврк, но следовал MVC.

## О размере проекта

На сайте есть очереди email рассылок, интегрированы смс уведомления, на сайте есть морфологический поиск работающий через Sphinx, все таблицы базы данных не были рассчитаны на мультиязычность, все модели и поля редактирования не были рассчитаны на мультиязычность, фильтры и изображения также не были мультиязычными, в шаблонах был хардкод текст на одном языке, и в конечном итоге даже обьем текста, который необходимо было перевести был огромным.

*P.S. все же начатки мультиязычности были, на что-то можно было опираться.*

## Решение

1. Были переделаны большинство (~80) таблиц базы данных, добавлены таблицы.
2. Добавлен выбор языка на сайте для покупателей, настроено сохранение выбранного языка в сессии.
3. Весь хардкод текст был вынесен в языковые файлы, добавлено авто-встраивание языковых значений в шаблоны.
	1. Повторяющиеся элементы верстки были сделаны компонентами.
4. Переделаны формы просмотра/редактирования многих сущностей в административной панели
5. Так как сайт работал на выделенном сервере и многие службы, такие как cron или Sphinx были запущены в фоне, в автозагрузке и к ним не было никакой документации, то пришлось разобраться со Sphinx и определить нужные процессы.
6. Проделанная работа была протестирована вручную.
7. Все старые товары были продублировны на нужные языки.