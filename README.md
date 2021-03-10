# lab02_homework
## Далгатов Гитиномагомед, группа ИУ8-22
### Part 1
1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com)(он создан, назывется lab02_homework).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
  
   Команды: 
   ```
   $ vim README.md
   $ git add README.md
   $ git commit -m"Start doing DZ"
   $ git push origin master
   ```
  
3. Создайте файл ```hello_world.cpp``` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку ```using namespace std;```
  
   Команда:  ```$ vim hello_world.cpp```
   Код: ```#include using namespace std; int main (){ cout << "Hello world\n"; }```
  
4. Добавьте этот файл в локальную копию репозитория.

   Команда: ```$ git add hellow_world.cpp```
  
5. Закоммитьте изменения с *осмысленным* сообщением.

   Команда: ```$ git commit -m "added hello_world.cpp"```
     
   Вывод:
   ```
   [patch1 ee9b3761f] added hello_world.cpp
   1 file changed, 1 insertion(+), 14 deletions(-)
   ```
  
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение ```Hello world from @name```, где ```@name``` имя пользователя.

   Команда: ```$ vim hello_world.cpp```
  
   Код: 
   ```
   #include <iostream>
   #include <string>
 
   int main ()
   { 
       std::string name;
       std::cout << "Input your name: ";
       std::cin >> name;
       std::cout << "Hello world from " << name;
       return 0;
   }
   ```
   
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно ```git add```?

   Команда: ```$ git commit -m"upgrade hello_w0rld.cpp" -a```
  
   Вывод(фрагмент):
   ```
   [patch1 5225767aa] upgrade hello_w0rld.cpp
   3228 files changed, 2320 insertions(+), 677663 deletions(-)
   rewrite .cache/gstreamer-1.0/registry.x86_64.bin (67%)
   ```
   Мы не используем ```git add``` второй раз, поскольку ```hello_world.cpp``` уже добавлен, однако для коммита теперь нужно использовать оператор ```-a```.
  
8. Запуште изменения в удалёный репозиторий.

   Команда: ```$ git push origin master```
  
9. Проверьте, что история коммитов доступна в удалёный репозитории.

   Команда: ```$ git log```
  
   Вывод:
   ```
   commit 5225767aad97828da68c11f4571f8ab434291941 (HEAD -> patch1)
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Wed Mar 10 22:49:44 2021 +0300

       upgrade hello_w0rld.cpp

   commit ee9b3761ffb1d254154a9a4b9208824ed5b8501e
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Wed Mar 10 22:38:35 2021 +0300
 
       added hello_world.cpp

   commit 13da1ec111ddfb9f1c79749c00a7b570a8d5d46a
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Tue Mar 9 10:47:15 2021 +0300

       delete 'using namespace std;'.

   commit edb4a61faaf3d1a3fc2a87c942d4ec96edd24f1b (master)
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Mon Mar 8 12:17:56 2021 +0300

       added hello_world.cpp.
   :
   ```
  
### Part 2
1. В локальной копии репозитория создайте локальную ветку ```patch1```.

   Команды: 
   ```
   $ git branch patch1
   $ git checkout patch1
   ```
   
   Вывод(фрагмент):
   ```
   M	.cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/0ACA9C8486815ABAF991748A4990CB0448F4C3B6
   M	.cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/0DDCED7BD9D8235DE0A1FCCF69235CE8F84669D3
   M	.cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/12C6AB1C64C6E180EE9988497209D0B59C34C8BA
   ```
  
2. Внесите изменения в ветке ```patch1``` по исправлению кода и избавления от ```using namespace std;```.

   Команда: ```$ vim hello_world.cpp```
  
3. **commit**, **push** локальную ветку в удалённый репозиторий.

   Команды: 
   ```
   $ git commit -m"upgrage hello_world.cpp and added RM" -a
   $ git push origin patch1
   ```
    
4. Проверьте, что ветка ```patch1``` доступна в удалёный репозитории.

   ---

5. Создайте pull-request ```patch1 -> master```.

   ---

6. В локальной копии в ветке ```patch1``` добавьте в исходный код комментарии.

   Команда: ```$ vim hello_world.cpp```
  
   Код:
   ```
   #include <iostream>
   #include <string>
 
   int main ()
   { 
      std::string name; //Имя
      std::cout << "Input your name: ";
      std::cin >> name;
      std::cout << "Hello world from " << name;
      return 0;
   }
   ```
  
7. **commit**, **push**.

   Команды: 
   ```
   $ git commit -m"added comment" -a
   $ git push origin patch1 <<<<<<< HEAD
   ```
   
8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request.

   ---

9. В удалённый репозитории выполните слияние ```PR patch1 -> master``` и удалите ветку patch1 в удаленном репозитории.

   ---

10. Локально выполните pull.

    Команда: ```$ git pull origin master```
  
11. С помощью команды ```git log``` просмотрите историю в локальной версии ветки ```master```.

  Команда: ```$ git log```
  
  Вывод:
  ```
  commit cc260faee61518b7034d1a81c08d0545b2cb3d79 (HEAD -> patch1)
  Author: dgt20u186 <dalgatovgitinomd@gmail.com>
  Date:   Wed Mar 10 23:19:21 2021 +0300

      added comment
  ```
  
12. Удалите локальную ветку ```patch1```.

    Команда: ```$ git branch -D patch1```
    
### Part 3
1. Создайте новую локальную ветку ```patch2```.

   Команды:
   ```
   git branch patch2
   git checkout patch2
   ```
   
2. Измените *code style* с помощью утилиты **clang-format**. Например, используя опцию ```-style=Mozilla```.

   Команда: ```$ clang-format -style=Mozilla hello_world.cpp```
   
   Вывод:
   ```
   #include <iostream>
   #include <string>

   int
   main()
   {
     std::string name; //Имя
     std::cout << "Input your name: ";
     std::cin >> name;
     std::cout << "Hello world from " << name;
     return 0;
   }
   ```
   
3. **commit**, **push**, создайте pull-request ```patch2 -> master```.

   Команды:
   ```
   git commit -m"style=Mozilla" -a
   git push origin patch2
   ```
  
4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

   Команды: 
