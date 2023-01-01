# UpdateKernel- OS Centos 7
Проверил какое ядро сейчас установлено - uname –r 3.10.0-1160.el7.x86_64
Импортировал ключ репозитория rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
Установил сам репозиторий yum install https://www.elrepo.org/elrepo-release-7.el7.elrepo.noarch.rpm
Установил ядро - yum --enablerepo=elrepo-kernel install kernel-ml
Проверил есть ли ядро в каталоге - ls /boot/
Перегружаем
Во время загрузки выбираем новое ядро.

Проверяем какое ядро uname –r 6.1.1-1.el7.elrepo.x86_64
Если система работает нормально, то редактируем загрузчик
В загрузчик /etc/default/grub добавим строку «GRUB_DEFAULT=0»
Применим настройки grub2-mkconfig -o /boot/grub2/grub.cfg
Прогрузим систему
Во время загрузки увидим, что система выбрала новое ядро.
uname –r 6.1.1-1.el7.elrepo.x86_64
выводим список ядер rpm -qa | grep kernel-
удаляем старое ядро yum remove kernel-3.10.0-1160.el7.x86_64
