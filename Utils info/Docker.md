#### Работа в целом с docker
Чаще всего для операций с docker нужно иметь права администратора, поэтому все команды должны идти после "sudo"
#### Как сделать docker pull?
Очень часто надо делать "docker pull" с источника, где надо проходить процедуру идентификации в системе. Это можно понять по надписям по типу "access denied" или "permition forbidden". На примере исповского gitlab:
1) Находим ссылку на котейнер, который хотим скачать. В нашем примере этой ссылкой будет gitlab.ispras.ru:4567/llvm-powerpc/images/builder
2) выполняем команду `docker login gitlab.ispras.ru:4567/llvm-powerpc/images/builder`. Её скорее всего можно сократить до "docker login gitlab.ispras.ru:4567", но и в первом случае у меня все заработало
3) после этого мы находимся внутри системы, поэтому можем сделать pull с помощью команды `docker pull gitlab.ispras.ru:4567/llvm-powerpc/images/builder`