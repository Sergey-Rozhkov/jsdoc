# Code Standards & Review

## Code Standards

Where coding conventions have been specifically designed to produce high-quality code, and have then been formally adopted, they then become coding standards. Specific styles, irrespective of whether they are commonly adopted, do not automatically produce good quality code. It is only if they are designed to produce good quality code that they actually result in good quality code being produced, i.e., they must be very logical in every aspect of their design - every aspect justified and resulting in quality code being produced.

## Code Conventions

**Coding conventions** are a set of guidelines for a specific programming language that recommend programming style, practices, and methods for each aspect of a program written in that language. These conventions usually cover file organization, indentation, comments, declarations, statements, white space, naming conventions, programming practices, programming principles, programming rules of thumb, architectural best practices, etc. These are guidelines for software structural quality. Software programmers are highly recommended to follow these guidelines to help improve the readability of their source code and make software maintenance easier. Coding conventions are only applicable to the human maintainers and peer reviewers of a software project. Conventions may be formalized in a documented set of rules that an entire team or company follows, or may be as informal as the habitual coding practices of an individual. Coding conventions are not enforced by compilers.

## Refactoring

[Refactoring](https://en.wikipedia.org/wiki/Refactoring) refers to a software maintenance activity where [source code](https://en.wikipedia.org/wiki/Source_code) is modified to improve readability or improve its structure. Software is often refactored to bring it into conformance with a team's stated coding standards after its initial release. Any change that does not alter the behavior of the software can be considered refactoring. Common refactoring activities are changing variable names, [renaming methods](https://en.wikipedia.org/wiki/Rename_Method), moving methods or whole classes and [breaking large methods](https://en.wikipedia.org/wiki/Extract_Method) \(or [functions](https://en.wikipedia.org/wiki/Function_%28programming%29)\) into smaller ones.  


## Code smells

Запахи кода — это ключевые признаки необходимости рефакторинга. Существуют запахи, специфичные как для парадигм программирования, так и для конкретных языков. Основной проблемой, с которой сталкиваются разработчики при борьбе с запахами кода, является то, что критерии своевременности рефакторинга невозможно чётко формализовать без апелляции к эстетике и условному чувству прекрасного. Запахи кода это не набор чётких правил, а описание мест, на которые нужно обращать внимание при рефакторинге. Они легко обнаруживаются, но при этом не во всех случаях свидетельствуют о проблемах.

Код с запашком ведёт к распаду кода, разработчики должны стремиться к устранению запашков путём применения однократного или многократного рефакторинга. В процессе рефакторинга происходит избавление от запахов кода, что обеспечивает возможность дальнейшего развития приложения с той же или большей скоростью. Отсутствие регулярного рефакторинга с течением времени способно полностью парализовать проект, поэтому запахи кода необходимо устранять на ранних стадиях.

Виды "запахов" и способы их устранения: [https://refactoring.guru/ru/refactoring/smells](https://refactoring.guru/ru/refactoring/smells)

## Code review

Code review подразумевает, что программисты просматривают код друг друга, и существует некоторая формальная процедура принятия кода — например, «должны посмотреть и одобрить не меньше двух человек, из них один должен быть сеньёр/лид». Примеры: gerrit, Crucible. Если сложность балансирует на грани, то можно попытаться соблюдать соглашение добровольно, обсуждая в комментариях. Но как всё добровольное, за чем не следят роботы, оно иногда будет давать осечки.

