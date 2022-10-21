# SelenidKarta
image: Ubuntu  # образ для сборки

stack: jdk 11  # версия JDK

branches:
  only:
    - master  # ветка git

build: off  # будем использовать свой скрипт сборки

install:
  # запускаем SUT (& означает, что в фоновом режиме не блокируем терминал для запуска тестов)
  - java -jar ./artifacts/app-order.jar -port=9999 &

build_script:
  - chmod +x gradlew
  - ./gradlew test -Dselenide.headless=true --info
[![Build status](https://ci.appveyor.com/api/projects/status/8rrmto7kk63t8385/branch/main?svg=true)](https://ci.appveyor.com/project/UliaF80/selenidkarta/branch/main)
