# Report-01

## Paragraph 1 
#### 1. Скачайте библиотеку boost с помощью утилиты `wget`
 
```
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```

## Paragraph 2 
#### 2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0` 

```
$ tar -xvf boost_1_69_0.tar.gz
```

## Paragraph 3
#### 3. Подсчитайте количество файлов в директории `~/boost_1_69_0` не включая вложенные директории

```
$ ls -l | grep "^-" | wc -l
```
```
$ find . -maxdepth 1 -type f | wc -l
```

## Paragraph 4
#### 4. Подсчитайте количество файлов в директории `~/boost_1_69_0` включая вложенные директории

```
$ ls -l -R | wc -l
```
```
$ find . -type f|wc -l
```

## Paragraph 5
#### 5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`)

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

## Paragraph 6
#### 6. Найдите полный пусть до файла `any.hpp` внутри библиотеки boost

```
$ find $PWD -type f -name any.hpp
```
```
$ find . -name “any.hpp”
```

## Paragraph 7
#### 7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`

```
$ grep -Rl "boost::asio"
```

## Paragraph 8
#### 8. Скомпилирутйе boost

```
$ ./bootstrap.sh --prefix=boost_output
$ ./b2 install
```

## Paragraph 9
#### 9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`

```
$ mv ~/boost_1_69_0/boost_output/lib ~/boost-libs
```

## Paragraph 10
#### 10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории

```
$ du -h -a 
```

## Paragraph 11
#### 11. Найдите топ 10 самых "тяжёлых"

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
