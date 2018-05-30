---
description: Система отслеживания ошибок (англ. bug tracking system)
---

# Bug tracking systems

**Система отслеживания ошибок** \(bug tracking system\) — прикладная программа, разработанная с целью помочь разработчикам программного обеспечения \(программистам, тестировщикам и др.\) учитывать и контролировать ошибки и неполадки, найденные в программах, пожелания пользователей, а также следить за процессом устранения этих ошибок и выполнения или невыполнения пожеланий.

* Jira
* TFS
* Redmine
* Bugzilla
* Mantis
* GIT Issues

## Jira 

![&#x41A;&#x43E;&#x43D;&#x446;&#x435;&#x43F;&#x442;&#x443;&#x430;&#x43B;&#x44C;&#x43D;&#x44B;&#x435; &#x43F;&#x43E;&#x43D;&#x44F;&#x442;&#x438;&#x44F; JIRA](../.gitbook/assets/image%20%2822%29.png)

### Задача JIRA {#an-1}

Фактически, все, что можно создать и отслеживать с помощью JIRA, можно назвать задачей:

* Баг
* Проектное задание
* Форма оставленного запроса
* Справочная карточка

Основные атрибуты задачи: 

* Статусы \(указывает ход выполнения проекта\)
*  Решения \(показывают, как можно закрыть задачу\)
* Приоритеты \(определяет важность задачи по отношению к другим\)

**Подзадачи \(Sub-task\)**

Иногда необходимо разбить основную задачу на несколько попроще и поменьше. Вы можете назначать и отслеживать эти задачи отдельно.

### Пример жизненного цикла

![](../.gitbook/assets/snimok%20%282%29.PNG)

### Проект JIRA {#an-3}

**Проект JIRA** — это набор задач. Основными атрибутами проекта являются:

* _**Имя** \(**Name**\)_ выбирается администратором.
* _**Ключ \(Key\)**_ ****— это идентификатор, с которого начинаются все названия задач в рамках проекта.
* _**Компонент проекта \(Project component\)**_ — это логическая группировка задач в рамках проекта.
* Часто необходимо, чтобы конкретная проблема была связана с версией проекта.
* Существует три состояния версий: Выпущенные \(Released\), Невыпущенные \(Unreleased\) или Архивированные \(Archived\).

## TFS

Comparsion with jira [https://rozdoum.com/blog\_articles/items/jira-vs-tfs-synergy-tools-full-integration.html](https://rozdoum.com/blog_articles/items/jira-vs-tfs-synergy-tools-full-integration.html)

{% embed data="{\"url\":\"https://www.youtube.com/watch?v=kh1bxsJL-HE\",\"type\":\"video\",\"title\":\"JIRA vs TFS - a side-by-side comparison, 2016\",\"description\":\"Side by side comparison of JIRA and TFS/VSTS for a Scrum project. High level comparison of the top ALM solutions for modern agile software development.\\n\\nSee also http://www.almbok.com\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.youtube.com/yts/img/favicon\_144-vfliLAfaB.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://i.ytimg.com/vi/kh1bxsJL-HE/maxresdefault.jpg\",\"width\":1280,\"height\":720,\"aspectRatio\":0.5625},\"embed\":{\"type\":\"player\",\"url\":\"https://www.youtube.com/embed/kh1bxsJL-HE?rel=0&showinfo=0\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://www.youtube.com/embed/kh1bxsJL-HE?rel=0&amp;showinfo=0\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

##  Redmine

{% embed data="{\"url\":\"https://www.youtube.com/watch?v=dSUVgrMWSGQ\",\"type\":\"video\",\"title\":\"TechPop: What is Redmine Project Management Software?\",\"description\":\"Redmine is an Open Source Project Management software. For those exploring new software to improve workplace organization and efficiency, we will explore some features found within Redmine.\\n\\nVisit our website: http://technerdservices.com\\nCheck out the printed tutorial: http://bit.ly/1v1315C\\n\\nDo us a favor and hit the LIKE and SUBSCRIBE buttons!\\n\\nConnect with Us! \\nTwitter: http://twitter.com/technerdservice\\nLinkedIN: https://www.linkedin.com/company/tech-nerd-services\\nFacebook: https://www.facebook.com/TechNerdServices\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.youtube.com/yts/img/favicon\_144-vfliLAfaB.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://i.ytimg.com/vi/dSUVgrMWSGQ/maxresdefault.jpg\",\"width\":1280,\"height\":720,\"aspectRatio\":0.5625},\"embed\":{\"type\":\"player\",\"url\":\"https://www.youtube.com/embed/dSUVgrMWSGQ?rel=0&showinfo=0\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 56.2493%;\\\"><iframe src=\\\"https://www.youtube.com/embed/dSUVgrMWSGQ?rel=0&amp;showinfo=0\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.7778}}" %}

##  Bugzilla

Bugzilla — «система контроля ошибок», разработанная «The Mozilla Organization».   
Ключевым понятием системы является баг \(«Bug»\) — некоторое задание, запрос, рекламация по поводу ошибки в системе, или просто сообщение, требующее обратной связи, и назначение системы.   
Сущность Bug имеет набор атрибутов, работа с которыми — редактирование и запросы — является основными сценариями использования Bugzilla.

![](../.gitbook/assets/image%20%286%29.png)

* Структурные:
  * Product - Основной атрибут, задающий структуру. Каждый «Product» состоит из набора компонентов. Можно включить классификацию продуктов — дополнительное подразделение продуктов на группы.
  * Component - Дополнительная структурная классификация. В зависимости от выбранного компонента, баг может иметь разный набор флагов.
* Атрибуты жизненного цикла:
  * Status - Основной атрибут, определяющий текущее состояние бага, то есть меру его активности — от самого «начального» состояния, когда он даже не подтвержден, как баг, до благополучного завершения, когда баг исправлен/решен, что подтверждено Службой Качества. Набор состояний зависит от конкретной инсталляции и настройки Bugzilla, однако, стандартный набор:
    * UNCONFIRMED \(«Не подтвержден»\).
    * NEW \(«Новый»\). Только что зарегистрирован или проверен.
    * ASSIGNED \(«Акцептован»\). Пользователь, указанный в «Assigned-to», подтвердил свою ответственность за этот баг. Баг может быть «перенаправленным» другому лицу, и снова стать «NEW».
    * REOPENED. Баг уже был однажды решен, однако, решение было либо неправильными, либо неокончательным.
  * Resolution — этот атрибут имеет смысл только для багов в состояниях «RESOLVED», «VERIFIED», «CLOSED». Также, набор «резолюций» можно настраивать, но стандартный набор следующий:
    * FIXED \(«Решено»\) — означает, что задание выполнено или баг исправлен.
    * INVALID \(«Некорректно»\) — неправильная или некорректная постановка, не имеющая смысла.
    * WONTFIX \(«Проблема есть, но решать ее не будем»\).
    * DUPLICATE \(«Дубль»\) — описанная проблема уже регистрировалась в определенном баге.
    * WORKSFORME \(«А у меня работает…»\) — не удалось воспроизвести описанную проблему ни эмуляцией сценария, ни анализом кода.
    * MOVED - Проблема перенесена в иную систему- «tracker».
    * LATER - \(Также можно использовать\) Задача зафиксирована, но ее решение откладывается на неопределенный срок.

**Диаграмма**   
Жизненный цикл бага, он же workflow - [http://lib.custis.ru/Bugzilla](http://lib.custis.ru/Bugzilla)  


## Mantis

{% embed data="{\"url\":\"http://ru.qatestlab.com/knowledge-center/qa-testing-materials/for-which-projects-is-mantis-bug-tracker-suitable/\",\"type\":\"link\",\"title\":\"Для каких проектов подходит багтрекер Mantis? – QATestLab \| Компания по тестированию\",\"icon\":{\"type\":\"icon\",\"url\":\"http://ru.qatestlab.com/knowledge-center/qa-testing-materials/for-which-projects-is-mantis-bug-tracker-suitable/favicon.ico\",\"aspectRatio\":0}}" %}

## Git issue

```text
<!--
PLEASE HELP US PROCESS GITHUB ISSUES FASTER BY PROVIDING THE FOLLOWING INFORMATION.

ISSUES MISSING IMPORTANT INFORMATION MAY BE CLOSED WITHOUT INVESTIGATION.
-->

## I'm submitting a...
<!-- Check one of the following options with "x" -->
<pre><code>
[ ] Regression (a behavior that used to work and stopped working in a new release)
[ ] Bug report  <!-- Please search GitHub for a similar issue or PR before submitting -->
[ ] Performance issue
[ ] Feature request
[ ] Documentation issue or request
[ ] Support request => Please do not submit support request here, instead see https://github.com/angular/angular/blob/master/CONTRIBUTING.md#question
[ ] Other... Please describe:
</code></pre>

## Current behavior
<!-- Describe how the issue manifests. -->


## Expected behavior
<!-- Describe what the desired behavior would be. -->


## Minimal reproduction of the problem with instructions
<!--
For bug reports please provide the *STEPS TO REPRODUCE* and if possible a *MINIMAL DEMO* of the problem via
https://stackblitz.com or similar (you can use this template as a starting point: https://stackblitz.com/fork/angular-gitter).
-->

## What is the motivation / use case for changing the behavior?
<!-- Describe the motivation or the concrete use case. -->


## Environment

<pre><code>
Angular version: X.Y.Z
<!-- Check whether this is still an issue in the most recent Angular version -->

Browser:
- [ ] Chrome (desktop) version XX
- [ ] Chrome (Android) version XX
- [ ] Chrome (iOS) version XX
- [ ] Firefox version XX
- [ ] Safari (desktop) version XX
- [ ] Safari (iOS) version XX
- [ ] IE version XX
- [ ] Edge version XX
 
For Tooling issues:
- Node version: XX  <!-- run `node --version` -->
- Platform:  <!-- Mac, Linux, Windows -->

Others:
<!-- Anything else relevant?  Operating system version, IDE, package manager, HTTP server, ... -->
</code></pre>
```



