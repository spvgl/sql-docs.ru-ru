---
title: Начало работы с SSMA для консоли DB2 (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f245c017-023e-4880-8721-8908d339525e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: fbb0a90d9cfd628e9251a55de3df8b66a22f1ef7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67989654"
---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Начало работы с SSMA для консоли DB2 (DB2ToSQL)
В этом разделе описывается процедура запуска и начала работы с консольным приложением DB2. Здесь также перечислены соглашения, используемые в типичном окне вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>Запуск консоли SSMA  
Чтобы запустить консольное приложение SSMA, выполните следующие действия:  
  
1.  Последовательно выберите пункты **Пуск** и **все программы**.  
  
2.  Щелкните ярлык ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] командной строки помощник по миграции для DB2** .  
  
    В нем отображается меню использования консоли SSMA и `(/? Help)`, которое поможет приступить к работе с консольным приложением.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После успешного запуска консоли в системе Windows для работы с ней можно выполнить следующие действия.  
  
1.  Настройте консоль SSMA с помощью файлов скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40;DB2ToSQL&#41;](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Создание файлов переменных значений &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  Запуск [консоли SSMA &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md) в зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Управление паролями](https://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) и их экспорт и импорт на другие компьютеры Windows  
  
2.  [Создание отчетов](https://msdn.microsoft.com/69ef5fd9-190d-4c58-8199-b3f77d5e1883) для просмотра подробных отчетов с выходом в формате XML для оценки/конверсион и переноса данных. Подробные отчеты об ошибках также могут быть созданы для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команд и параметров сценария SSMA консольная программа отображает результаты и сообщения (сведения, ошибка и т. д.) пользователю на консоли или, если необходимо, перенаправляет в выходной XML-файл. Каждый тип сообщения в выходных данных обозначается уникальным цветом. Например, текстовое сообщение в белом цвете означает команды файла сценария; зеленый цвет представляет собой запрос на ввод пользователя и т. д.  
  
![Вывод консоли SSMA_Oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "Вывод консоли SSMA_Oracle")  
  
Цветовая интерпретация выходных данных консоли в следующей таблице:  
  
|Color|Description|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение пользователю|  
|Белый|Команды файла сценария, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос на ввод данных пользователем|  
|Цвет|Начало, окончание и результат операции|  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для DB2](https://msdn.microsoft.com/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  
