# lab02_homework
## Далгатов Гитиномагомед, группа ИУ8-22
### Part 1
1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com)(он создан, назывется lab02_homework).
   Это тот репозиторий, на котором мы сейчас находимся.
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
  
   Команды: 
   ```
   $ echo "# lab02_homework" >> README.md
   $ git init
   $ git add README.md
   $ git branch -M main
   $ git remote add origin https://github.com/navckin/lab02new.git
   $ git push -u origin main
   ```
  
3. Создайте файл ```hello_world.cpp``` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку ```using namespace std;```
  
   Команда:  ```$ nano hello_world.cpp```
   Код: 
   ```
   #include <iostream>

   using namespace std;

   int main() 
   { 
      cout << "Hello world!" << endl;
      return 1; 
   }
   ```
  
4. Добавьте этот файл в локальную копию репозитория.

   Команда: ```$ git add hello_world.cpp```
  
5. Закоммитьте изменения с *осмысленным* сообщением.

   Команда: ```git commit -m"Added file .cpp"```
     
   Вывод:
   ```
   [main f1a06cb61] Added file .cpp
   1 file changed, 5 insertions(+), 4 deletions(-)
   ```
  
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение ```Hello world from @name```, где ```@name``` имя пользователя.

   Команда: ```$ nano hello_world.cpp```
  
   Код: 
   ```
   #include <iostream>
   #include <string>
   
   using namespace std;

   int main()
   { 
      string name;
      cin >> name;
      cout << "Hello World from << name << endl;
      return 0;
   }
   ```
   
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно ```git add```?

   Команда: ```$ git commit -a -m "upgrade hello_world.cpp"```
  
   Вывод(фрагмент):
   ```
   ewrite snap/snap-store/common/.cache/gnome-software/fwupd/remotes.d/lvfs/metadata.xml.gz (91%)
   rewrite snap/snap-store/common/.cache/gnome-software/fwupd/remotes.d/lvfs/metadata.xml.gz.asc (86%)
   ```
   Мы не используем ```git add``` второй раз, поскольку ```hello_world.cpp``` уже добавлен, однако для коммита теперь нужно использовать оператор ```-a```.
  
8. Запуште изменения в удалёный репозиторий.

   Команда: ```$ git push origin main```
  
9. Проверьте, что история коммитов доступна в удалёный репозитории.

   Команда: ```$ git log```
  
   Вывод:
   ```
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Mon Apr 19 21:26:22 2021 +0300

    upgrade hello_world.cpp

   commit f1a06cb616ff301689c99a58717fb3087527c4cb
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Mon Apr 19 21:16:29 2021 +0300

    Added file .cpp

   commit 9a04cd984a93ff0fa86956d27681c642d6bc445a
   Author: dgt20u186 <dalgatovgitinomd@gmail.com>
   Date:   Mon Apr 19 21:05:47 2021 +0300

    first commit
   ```
  
### Part 2
1. В локальной копии репозитория создайте локальную ветку ```patch1```.

   Команды: 
   ```
   $ git checkout -b patch1
   ```
   
   Вывод(фрагмент):
   ```
   M	.cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/0ACA9C8486815ABAF991748A4990CB0448F4C3B6
   M	.cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/0DDCED7BD9D8235DE0A1FCCF69235CE8F84669D3
   M	.cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/12C6AB1C64C6E180EE9988497209D0B59C34C8BA
   ```
  
2. Внесите изменения в ветке ```patch1``` по исправлению кода и избавления от ```using namespace std;```.
3. **commit**, **push** локальную ветку в удалённый репозиторий.

   Команды: 
   ```
   $ nano hello_world.cpp
   $ git add hello_world.cpp
   $ $ git commit -m"Changed the mistakes: added std::"
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

   Команда 1: ```$ git commit -m"style=Mozilla" -a```
   
   Вывод:
   ```
   [patch2 ea2870abb] style=Mozilla
   28 files changed, 8 insertions(+), 8 deletions(-)
   rewrite .cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/75C7FF8070DB4ACC8CD59ED913D3BA7AC142E365 (76%)
   rewrite .cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/83A9BA25821651DD88B149D6716D674DB354070A (82%)
   rewrite .cache/mozilla/firefox/q9deefwq.default-release/cache2/entries/FF4FA6D964A9B855A994A2D7E5FCA61ABD42FA09 (78%)
   rewrite .mozilla/firefox/q9deefwq.default-release/datareporting/aborted-session-ping (85%)
   ```
   
   Команда 2: ```$ git push origin patch2```
   
4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

   ---
   
5. Убедитесь, что в pull-request появились *конфликты*.

   ---

6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.

   Команды:
   ```
   $ git checkout master
   $ git rebase master
   $ git checkout patch2
   $ git merge patch2

7. Сделайте *force push* в ветку ```patch2```.

   Команда: ```$ git push --force origin patch2```
   
8. Убедитель, что в pull-request пропали конфликтны.

   ---
   
9. Вмержите pull-request ```patch2 -> master```.

   ---
