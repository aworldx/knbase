---
title: Различия между GET и POST
keywords: http
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: http_get_post_diff.html
folder: knbase
---

## Различия между GET и POST
- GET не должен быть использован для операции с SIDE EFFECTS
- GET может быть тспользован роботами
- GET не должен быть использован для отправки чувствительных данных. Так как параметры кодируются в URI, а URI могут логироваться серверами и прокси, и эти логи могут быть общедоступными.
- Некоторые браузеры (IE) кэшируют GET запросы