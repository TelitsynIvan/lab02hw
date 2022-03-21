## Homework

### Part I

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
3. Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.
4. Добавьте этот файл в локальную копию репозитория.
5. Закоммитьте изменения с *осмысленным* сообщением.
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?
8. Запуште изменения в удалёный репозиторий.
9. Проверьте, что история коммитов доступна в удалёный репозитории.

### Part II

**Note:** *Работать продолжайте с теми же репозиториями, что и в первой части задания.*
1. В локальной копии репозитория создайте локальную ветку `patch1`.
2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.
3. **commit**, **push** локальную ветку в удалённый репозиторий.
4. Проверьте, что ветка `patch1` доступна в удалёный репозитории.
5. Создайте pull-request `patch1 -> master`.
6. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.
7. **commit**, **push**.
8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request
9. В удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.
10. Локально выполните **pull**.
11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.
12. Удалите локальную ветку `patch1`.

### Part III

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. Создайте новую локальную ветку `patch2`.
2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.
3. **commit**, **push**, создайте pull-request `patch2 -> master`.
4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
5. Убедитесь, что в pull-request появились *конфликтны*.
6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.
7. Сделайте *force push* в ветку `patch2`
8. Убедитель, что в pull-request пропали конфликтны. 
9. Вмержите pull-request `patch2 -> master`.

## Links

- [hub](https://hub.github.com/)
- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)



## HOMEWORK REPORT

### PART 1

1. Создаём публичный репозиторий через github.com
2. Создаём первый коммит
```Sh
# переходим в папку TelitsynIvan/workspace/projects
$ cd ~/TelitsynIvan/workspace/projects
# создаём директорию lab02HW
$ mkdir lab02HW
# переходим в нее
$ cd lab02HW
# инициализируем локальный репозиторий
$ git init
# указываем удалённый репозиторий
$ git remote add https://github.com/TelitsynIvan/lab02HW
$ git pull origin master
$ cat .gitignore  <<EOF
*build*/ 
*install*/
*.swp
.idea/
EOF
$ subl
```Shellsession


# отслеживаем все файлы
$ git add .
# коммитим
$ git commit -m "added gitignore"
# пушим коммит на гитхаб
$ git push origin master
```
3. Создадим hello_world .cpp
```c++
$ cat > hello_world.cpp <<EOF
#include <iostream>
#include <string>
using namespace std;

int main(int argc, char* argv){
	string name;
	cout << "Input user_name":
	cin >> name;
	cout << "Hello world from " << name << endl;
	return 0;
}
EOF
```
5. Коммитим файл
``` Sh
$ git add .
$ git commit -m "added hello_world.cpp"
```
6. Изменяем файл
```c++
$ hello_world.cpp <<EOF
  #include <iostream>
  #include <string>
  using namespace std;
  
  int main(int argc, char* argv){
  string name;
  cout << "Input user_name":
  cin >> name;
  cout << "Hello world from " << name << endl;
  return 0;
  }
  EOF
```
7. Коммитим файл
```sh
$ git add .
$ git commit -am "changed hello_world.cpp"
```
8. Заливаем изменения
```sh
$ git push origin master

### PART 2
1. Создаём новую ветку
```sh
# переключаемся на новую ветку
$ git checkout -b "patch1"
```
2. Изменяем hello_world.cpp
```sh
# изменяем hello_world.cpp в субле
$ subl hello_world.cpp
```
```c++
#include <iostream>
#include <string>

int main(int argc, char* argv){
std::string name;
std::cout << "Input user_name":
std::cin >> name;
std::cout << "Hello world from " << name << std::endl;
return 0;
}
```
3. Коммитим и добавляем ветку
```sh
$ git commit -am "fixed using namespace std"
$ git push origin patch1
```
4. Убедился, что  новая ветка доступна в удалённом репозитории
5. Создал пулл-реквест через сайт
6. В субле изменяем hello_world.cpp
``` c++
#include <iostream>
#include <string>

int main(int argc, char* argv){
std::string name; // используем переменную типа string
std::cout << "Input user_name":
std::cin >> name; // вводим своё имя в переменную
std::cout << "Hello world from " << name << std::endl; // выводим приветствие
return 0;
}
```
7. Коммитим и добавляем файлы
``` sh
$ git commit -am "added comments"
$ git push origin patch1
```

8. Делаем слияние и удаляем ветку

9.
``` sh
# переключаемся на ветку master
$ git checkout master
$ git pull origin master
```

10.
``` sh
$ git log
```

11.
```sh
# удаляем ветку
$ git branch -D patch1
```

### PART 3
1. 
```sh
$ git checkout -b patch2
```

2.
``` sh
# форматируем в стиле firefox с заменой файла
$ clang-format -style=Mozilla -i hello_world.cpp

```

3.
```sh
$ git commit -am "Mozilla format"
$ git push origin patch2
```

4. Перевёл комментарии в удалённом репозитории на английский язык 

5. Убедился, конфликты не дают мёржить.

6.
```sh
# переходим на ветку мастер
$ git checkout master
$ git pull origin master
# переходим обратно на pathc2
$ git checkout patch2
# накладываем изменения на ветку, вручную исправляем конфликт
$ git rebase master
$ git add .
$ git rebase --continue
```

7.
```sh
# добавляем изменения
$ git push -f origin patch2
```

8. Убедился, что конфликты действительно пропали

9. Объединил ветку
