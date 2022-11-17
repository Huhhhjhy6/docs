---
title: Аварийное восстановление для GitHub Codespaces
intro: 'В этой статье приводятся рекомендации по аварийному восстановлению, при котором из-за масштабного стихийного бедствия или обширного прерывания работы службы весь регион оказывается подвержен сбою.'
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Codespaces
shortTitle: Disaster recovery
redirect_from:
  - /codespaces/codespaces-reference/disaster-recovery-for-codespaces
ms.openlocfilehash: 9b892d6a24332e01174c819e2e88a91d1cdf9d65
ms.sourcegitcommit: e8c012864f13f9146e53fcb0699e2928c949ffa8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2022
ms.locfileid: '148158816'
---
Мы упорно работаем над тем, чтобы служба {% data variables.product.prodname_github_codespaces %} всегда оставалась доступной. Однако иногда по независящим от нас обстоятельствам происходят незапланированные нарушения работы служб.

Хотя сценарии аварийного восстановления являются редкими, мы рекомендуем подготовиться к возможному сбою всего региона. Если весь регион испытывает перебои в работе службы, то локально избыточные копии ваших данных становятся временно недоступными.

В следующем руководстве приведены варианты действий в случае прерывания работы службы во всем регионе, в котором развернуто пространство кода.

{% note %}

**Примечание.** Вы можете уменьшить потенциальное влияние сбоев на уровне службы, выполняя регулярную отправку кода в удаленные репозитории.

{% endnote %}

## Вариант 1. Создание нового пространства кода в другом регионе

В случае регионального сбоя рекомендуется воссоздать пространство кода в другом регионе, который не затронут сбоем, чтобы продолжить работу. Это новое пространство кода будет содержать все изменения на момент последней отправки кода в {% data variables.product.prodname_dotcom %}. Дополнительные сведения о настройке другого региона вручную см. в разделе [Настройка региона по умолчанию для {% data variables.product.prodname_github_codespaces %}](/codespaces/customizing-your-codespace/setting-your-default-region-for-github-codespaces).

Вы можете оптимизировать время восстановления, настроив файл `devcontainer.json` в репозитории проекта. Это позволяет задать инструменты, среды выполнения, платформы, параметры редактора, расширения и другую конфигурацию, необходимую для автоматического восстановления среды разработки. Дополнительные сведения см. в разделе [Общие сведения о контейнерах разработки](/codespaces/setting-up-your-codespace/configuring-codespaces-for-your-project).

## Вариант 2. Ожидание восстановления

В этом случае вам не нужно предпринимать какие-либо действия. Знайте, что мы активно работаем над восстановлением доступности службы. 

Текущее состояние службы можно проверить на [панели мониторинга состояния](https://www.githubstatus.com/).

## Вариант 3. Клонирование репозитория локально или изменение в браузере

Хотя {% data variables.product.prodname_github_codespaces %} предоставляет преимущества предварительно настроенной среды разработчика, исходный код всегда должен быть доступен через репозиторий, размещенный в {% data variables.product.prodname_dotcom_the_website %}. В случае сбоя {% data variables.product.prodname_github_codespaces %} вы по-прежнему можете клонировать репозиторий локально или редактировать файлы в редакторе браузера {% data variables.product.company_short %}. Дополнительные сведения см. в разделе [Редактирование файлов](/repositories/working-with-files/managing-files/editing-files).

Хотя в этом случае у вас нет настроенной среды разработки, вы сможете вносить изменения в исходный код по мере необходимости, пока работа службы не будет восстановлена.

## Вариант 4. Использование расширения Dev Containers и Docker для локальной контейнерной среды

Если в репозитории есть , рассмотрите `devcontainer.json`возможность использования [расширения Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) в {% data variables.product.prodname_vscode %} для сборки локального контейнера разработки для репозитория и присоединения к нему. Время настройки этого варианта зависит от локальных спецификаций и сложности настройки контейнера разработки. Дополнительные сведения см. в разделе [Разработка внутри контейнера](https://code.visualstudio.com/docs/remote/containers#_quick-start-open-a-git-repository-or-github-pr-in-an-isolated-container-volume) в документации по {% data variables.product.prodname_vscode_shortname %}.

{% note %}

**Примечание.** Перед использованием этого варианта убедитесь в том, что локальная конфигурация соответствует [минимальным требованиям](https://code.visualstudio.com/docs/remote/containers#_system-requirements).

{% endnote %}