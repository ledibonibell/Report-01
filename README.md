# Report-01

## 1. Скачайте библиотеку boost с помощью утилиты `wget`
 
```
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```

## 2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0` 

```
$ tar -xvf boost_1_69_0.tar.gz
```

## 3. Подсчитайте количество файлов в директории `~/boost_1_69_0` не включая вложенные директории

```
$ ls -l | grep "^-" | wc -l
```
```
$ find . -maxdepth 1 -type f | wc -l
```

## 4. Подсчитайте количество файлов в директории `~/boost_1_69_0` включая вложенные директории

```
$ ls -l -R | wc -l
```
```
$ find . -type f|wc -l
```

## 5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`)

```
$ ls -l -R | grep -c *.hpp
$ ls -l -R | grep -c *.cpp
$ ls -l -R | grep -v *.hpp | grep -v *.cpp | grep -v 'итого' | wc -l
```
```
$ find . -name “*.hpp” -o -name “*.h” | wc -l
$ find . -name “*.cpp” | wc -l
$ find . -and -type -f -and -not -name “*.cpp” -and -not -name “*.h” -and -not - name “*.hpp” | wc -l
```

## 6. Найдите полный пусть до файла `any.hpp` внутри библиотеки boost

```
$ find $PWD -type f -name any.hpp
```
```
$ find . -name “any.hpp”
```

## 7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`

```
$ grep -Rl "boost::asio"
```

## 8. Скомпилирутйе boost

```
$ ./bootstrap.sh --prefix=boost_output
$ ./b2 install
```

## 9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`

```
$ mv ~/boost_1_69_0/boost_output/lib ~/boost-libs
```

## 10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории

```
$ du -h -a 
```

## 11. Найдите топ 10 самых "тяжёлых"

```
$ du -h -a | sort -r -h | head -n 10
```

## Required libraries

```
$ sudo apt install libicu-dev
$ sudo apt install gcc
$ sudo apt install build-essential
$ sudo apt-get install libboost-all-dev
```

## References used
https://losst.pro/komanda-ls-linux
https://losst.pro/gerp-poisk-vnutri-fajlov-v-linux
https://losst.pro/komanda-wc-v-linux
https://losst.pro/komanda-find-v-linux
https://losst.pro/komanda-pwd-linux
https://codeyarns.com/tech/2017-01-24-how-to-build-boost-on-linux.html#gsc.tab=0
https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html
https://stackoverflow.com/questions/53647596/building-boost-from-sources-on-linux
https://losst.pro/kak-pereimenovat-papku-linux#2_Команда_mv
https://losst.pro/komanda-du-v-linux
https://losst.pro/komanda-sort-v-linux
https://losst.pro/komanda-head-linux
