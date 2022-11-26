# Домашнее задание к лекции. «7. Асинхронность» 

## Задача №1. Будильник-колыбельная

Помогите студенту первого курса Васе перестать просыпать пары. 
Для этого нужно написать программу будильник-колыбельную, в которой можно добавлять, удалять, запускать и останавливать звонки.

## Как выполнить задачу

1. Напишите класс *AlarmClock* с методами:

* `constructor` — выделяет память для объекта.
	* Создайте свойство для хранения коллекции звонков `alarmCollection` с начальным значением пустого массива. 
	* Создайте свойство `timerId` для хранения `id` таймера без начального значения.

* `addClock` — добавляет новый звонок в коллекцию существующих.
	* Настройте параметр времени в формате `HH:MM` — время, когда должно запуститься действие.
	* Настройте параметр функции колбека — действие, которое должно запуститься.
	* Настройте параметр идентификатора создаваемого звонка.
	* Проверьте, передан ли параметр `id`. Если параметр не передан, выполните выброс ошибки с помощью `throw new Error('error text')`.
	* Проверьте, есть ли звонок с уже существующим `id`. Если есть, выведите ошибку с помощью `console.error()` и завершите выполнение метода. Программа должна продолжать работать, но звонок не должен быть добавлен.
	* Перед завершением метода добавьте в массив звонков объект со свойствами `id`, `time`, `callback`.

* `removeClock` — удаляет определённый звонок.
	* Настройте приём `id` звонка, который следует удалить.
	* Удалите из массива звонков тот, у которого `id` совпадает с текущим. Например, можно использовать метод `filter`.
	* Верните логическое значение об успешности/провале удаления объекта звонка из общего массива.

* `getCurrentFormattedTime` — возвращает текущее время в строковом формате `HH:MM`.

* `start` — запускает все звонки.
	* Создайте функцию проверки `checkClock`, которая принимает звонок. Если текущее время совпадает со временем звонка, вызывайте колбек.
	* Если значение идентификатора таймера отсутствует, создайте новый интервал.
	* В этом интервале реализуйте функцию, которая будет перебирать все звонки и для каждого вызывать функцию `checkClock`.
	* Результат функции `setInterval` сохраните в свойстве идентификатора текущего таймера.

* `stop` — останавливает выполнение всех звонков.
	* Сделайте проверку существования идентификатора текущего таймера.
	* Если у идентификатора текущего таймера есть значение, вызовите функцию `clearInterval` для удаления интервала. Ещё удалите значение из свойства «идентификатор текущего таймера».

* `printAlarms` — печатает все звонки.
	* С помощью метода `forEach` выведите информацию о каждом звонке (`id` и `time`).

* `clearAlarms` — удаляет все звонки.
	* Настройте вызов метода остановки интервала.
	* Настройте удаление всех звонков.

2. Напишите пример использования класса *AlarmClock*. Реализуйте и запустите функцию `testCase`: 

* создайте объект класса `AlarmClock`;

* добавьте в созданный объект новый звонок с текущим временем и колбеком вывода текста на консоль, чтобы после запуска функция вывода *выполнилась несколько раз*;

* добавьте ещё один звонок со временем +1 минуты от текущего времени и колбеком: вывод текста на консоль и удаление этого звонка. После запуска функция вывода должна *выполниться один раз, а потом удалиться*;

* добавьте ещё один звонок со временем +2 минут от текущего времени и колбеком: вывод текста на консоль, остановка всех звонков, очистка всех звонков и вывод всех звонков. После запуска функция вывода должна *выполниться один раз, потом остановить интервал, очистить все звонки и ничего не выводить*;

* напечатайте все звонки. Должно вывестись 3 звонка;

* запустите выполнение ваших звонков.

Результат работы должен быть примерно таким (код выполнялся по командам из консоли):

![](https://sun1-24.userapi.com/4e78x8Gim59SbBdHgqnEpIbGJiUkjbFP0dhT9A/bLPY-cmewxY.jpg)

### Критерии выполнения

1. Старайтесь избегать циклов. Задание можно реализовать без них. Вместо циклов используйте *функции высшего порядка*, которые мы изучали.
2. Функция `testCase` может отличаться от описания в задании. Главное показать:
	* создание объекта звонков;
	* добавление нескольких звонков;
	* удаление звонков в зависимости от условия;
	* печать звонков перед удалением и после, чтобы проверить, что звонки добавляются и удаляются;
	* запуск звонков и **срабатывание в нужное время**;
	* остановка звонков.

## Требования к домашней работе:

* браузер;
* редактор кода, например [Sublime][1] или [Visual Studio Code][2];
* аккаунт на [GitHub.][0] [Инструкция по регистрации на GitHub][3];
* система контроля версий [Git][4], установленная локально. [Инструкция по установке Git][5];
* запуск всех тестов должен успешно выполнять все тесты:

![графическое представление](../Jasmine/results/sucessed_tasks3_3.png)

## Решение задач

1. Произведите [Fork](https://ru.wikipedia.org/wiki/Форк) репозитория с задачами. Fork нужно делать перед выполнением каждой домашней работы.
2. Перейдите в папку задания `cd ./7.async`.
3. Откройте файл `task.js` в редакторе кода и выполните задание.
4. Самостоятельно вызывать функции не нужно, если в задании этого не просят.
5. Откройте файл `index.html` в браузере и с помощью консоли DevTools убедитесь, что результаты выводятся правильно.
6. Откройте файл `test-runer.html` в вашем браузере и убедитесь, что все тесты выполняются. На вкладке Spec List можно видеть, какие тесты выполнились, а какие нет.
7. Добавить файл `task.js` в индекс git с помощью команды `git add %file-path%`, где `%file-path%` — путь до целевого файла. `git add task.js`.
8. Сделайте коммит, используя команду `git commit -m '%comment%'`, где `%comment%` — это произвольный комментарий к вашему коммиту. `git commit -m 'first commit variables'`.
9. Опубликуйте код в репозиторий `homeworks` с помощью команды `git push -u origin main`.
10. Прикрепите ссылку на репозиторий в личном кабинете на сайте [Нетологии][6].

[0]: https://github.com/
[1]: https://www.sublimetext.com/
[2]: https://code.visualstudio.com/
[3]: https://github.com/netology-code/guides/blob/master/git/github.md
[4]: https://git-scm.com/
[5]: https://github.com/netology-code/guides/blob/master/git/README.md
[6]: https://netology.ru/

*Никаких файлов прикреплять не нужно.*

Выполните все задачи, чтобы получить зачёт. Присылать на проверку можно каждую задачу по отдельности или все задачи вместе. Во время проверки по частям ваша домашняя работа будет со статусом «На доработке».

Любые вопросы по задачам задавайте в чате учебной группы.
