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