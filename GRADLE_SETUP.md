# Если Android Studio не видит Gradle Wrapper

В архиве нет файла `gradle/wrapper/gradle-wrapper.jar` (это бинарный файл,
который нельзя передать как текст). Android Studio создаст его сама при
первом открытии проекта. Если этого не произошло автоматически —
сделай один из двух вариантов:

## Вариант 1 (проще): через Android Studio

1. Открой проект в Android Studio (File → Open → папка budget-app)
2. Если появится запрос на синхронизацию — нажми "OK" / "Sync Now"
3. Если Studio попросит создать wrapper — согласись

## Вариант 2: вручную через терминал

Если у тебя установлен Gradle глобально на компьютере, выполни в корне
проекта:

```
gradle wrapper --gradle-version 8.4
```

Это создаст `gradle/wrapper/gradle-wrapper.jar` и перезапишет
`gradle-wrapper.properties` (там уже стоит версия 8.4 — то, что нужно).

## Если ошибка "Could not install Gradle distribution" повторяется

Значит дело не в версии, а в сети (таймаут до services.gradle.org).
В Android Studio:

File → Settings → Build, Execution, Deployment → Gradle →
"Use Gradle from" → выбери "'gradle-wrapper.properties' file"
и убедись, что в файле стоит версия 8.4-bin.zip (как у нас).

Если таймаут не уходит — проверь VPN/прокси, либо скачай дистрибутив
gradle-8.4-bin.zip вручную с https://gradle.org/releases/ и укажи
локальный путь к файлу в `distributionUrl` (формат: `file:///C:/.../gradle-8.4-bin.zip`).
