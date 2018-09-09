[![Build Status](https://travis-ci.com/GPGPUCourse2018/Task0EnumDevices.svg?branch=master)](https://travis-ci.com/GPGPUCourse2018/Task0EnumDevices)

Установка OpenCL-драйвера для процессора
========================================

Установить OpenCL-драйвер для процессора полезно даже если у вас есть видеокарта, т.к. на нем удобно тестировать приложение (драйвер видеокарты гораздо чаще может повиснуть вместе с ОС).

Windows
-------

1. Откройте https://software.intel.com/en-us/articles/opencl-drivers#cpu-win64
2. Скачайте ``Windows* OS (64bit)`` -> ``Download / Install Options`` -> ``Download Link``
3. Установите

Linux (Рекомендуется Ubuntu 16.04)
----------------------------------

1. Откройте https://software.intel.com/en-us/articles/opencl-drivers#cpu-lin-u
2. Скачайте ``Linux* OS Ubuntu* (rpm translator)`` -> ``Download / Install Options`` -> ``Download Link``
3. ``apt-get install -yq cpio``
4. ``tar -xzf opencl_runtime_16.1.2_x64_rh_6.4.0.37.tgz``
5. ``sudo ./opencl_runtime_16.1.2_x64_rh_6.4.0.37/install.sh``
6. Проведите установку.

P.S. Если встретите эту ошибку, то я тоже ее наблюдал на Ubuntu 16.04, но в результате все работает:

![OpenCL CPU runtime installation warning](/.figures/intel_cpu_ocl_driver_warning.png)

Если в процессе запуска этого задания процессор не виден как допустимое OpenCL-устройство - создайте **Issue** в этом репозитории с перечислением:

 - Версия OS
 - Вывод команды ``ls /etc/OpenCL/vendors``
 - Если там в т.ч. есть ``intel.icd`` файл - то его содержимое (это маленький текстовый файл)

Установка OpenCL-драйвера для видеокарты
========================================

Windows
-------

Поставьте драйвер стандартным образом - скачав инсталлятор с официального сайта вендора вашей видеокарты и установив.

Linux
-----

NVidia: ``sudo apt install nvidia-384``

AMD: [скачав](https://www.amd.com/en/support) и установив amdgpu-pro драйвер

Проверка окружения и начало выполнения задания
==============================================

Про работу под Windows см. в секции [Как работать под windows](https://github.com/GPGPUCourse2018/Task0EnumDevices#%D0%9A%D0%B0%D0%BA-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%D1%82%D1%8C-%D0%BF%D0%BE%D0%B4-windows).

1. Сделайте fork этого репозитория
2. ``git clone ВАШ_ФОРК_РЕПОЗИТОРИЯ``
3. ``cd Task0EnumDevices``
4. ``mkdir build``
5. ``cd build``
6. ``cmake ..``
7. ``make -j4``
8. ``./enumDevices`` должно увидеть хотя бы одну OpenCL-платформу:

```
Number of OpenCL platforms: 1
Platform #1/1
    Platform name: 
```

Если этого не произошло - создайте **Issue** с перечислением:

 - OS, процессор и видеокарта
 - Успешно ли прошла установка Intel-CPU драйвера
 - Вывод ``./enumDevices``

Задание
=======

0. Сделав fork проекта
1. Вам нужно читать все комментарии подряд и выполнить все **TODO** в файле ``src/main.cpp``. Для разработки под Linux рекомендуется использовать CLion. Под Windows рекомендуется использовать Visual Studio 2017 Community (потребует создать Microsoft аккаунт). Так же под Windows можно использовать CLion+MSVC, но в данный момент в CLion нет поддержки отладчика.
2. Отправить **Pull-request**
3. Убедиться что Travis continuous integration смог скомпилировать ваш код и что все хорошо (если нет - то поправить)
4. Ждать комментарии проверки

**Дедлайн**: начало лекции 17 сентября. Но убедиться что хотя бы одно OpenCL-устройство у вас обнаруживается лучше сделать как можно раньше (см. **Проверка окружения** выше), т.к. если с этим будут проблемы - я могу не успеть вам помочь достаточно быстро.

Как работать под Windows
========================

1. Используйте 64-битный компилятор, т.е. amd64, а не x86. (Если при запуске видите ``Invalid Parameter - 100``, то вы все еще используете 32-битный компилятор)
2. Лучше всего использовать Visual Studio 2017 Community, она поддерживает CMake-проекты (``File`` -> ``Open`` -> ``Cmake...``). Разве что передавать аргументы запускаемой программе [неудобно](https://docs.microsoft.com/en-us/cpp/ide/cmake-tools-for-visual-cpp?view=vs-2017#configure-cmake-debugging-sessions).
3. Можете использовать CLion, но я пробовал только с amd64 MSVC компилятором, и на данный момент в таком варианте нет отладчика.
