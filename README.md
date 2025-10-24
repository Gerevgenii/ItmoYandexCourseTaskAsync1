Вот готовый файл `README.md` в виде Markdown-кода (можно просто скопировать и вставить в проект):

````markdown
# 🖋️ Typewriter Effect

## 📋 Задание

Реализовать **эффект постепенного вывода текста**, аналогичный [примеру](https://yastatic.net/s3/taxi-front/tasks/task-matrix.html).

### Требуется реализовать функцию

```ts
function typeWriter(delay: number, outputChar: OutputChar): WriteText;
````

Функция `typeWriter` принимает:

* `delay` — задержку (в миллисекундах) между символами;
* `outputChar` — функцию, вызываемую для каждого символа строки.

Возвращает функцию:

```ts
writeText(text: string): void
```

---

## ⚙️ Поведение функции

Функция `writeText(text)` может вызываться **несколько раз в разные моменты времени**.
Она должна **поочерёдно вызывать `outputChar`** для каждого символа строки `text`
с задержкой `delay` миллисекунд между символами.

### Пример последовательности вызовов

```ts
writeText('ab');
writeText('CD');
writeText('ef');
writeText('xy');
```

### Временная диаграмма

| Время (мс) | 0 | 100 | 200 | 250 | 350 | 450 | 550 | 750 | 850 |
| ---------- | - | --- | --- | --- | --- | --- | --- | --- | --- |
| Символ     | a | b   | C   | D   | e   | f   | x   | y   |     |

Функция `outputChar` вызывается в следующем порядке:

```
outputChar('a')
outputChar('b')
outputChar('C')
outputChar('D')
outputChar('e')
outputChar('f')
outputChar('x')
outputChar('y')
```

---

## 🧠 Типы

```ts
type OutputChar = (char: string) => void;
type WriteText = (text: string) => void;
function typeWriter(delay: number, outputChar: OutputChar): WriteText;
```

---

## 💡 Дополнительные условия

* Решение должно быть **линейным по сложности**.
* Ссылку на строку нужно **«отпускать» сразу после вывода последнего символа**.
* Последний символ строки должен быть выведен корректно, даже при последовательных вызовах `writeText`.

---

## 📘 Пример использования

```ts
const write = typeWriter(100, console.log);

write('ab');
setTimeout(() => write('CD'), 250);
setTimeout(() => write('ef'), 450);
setTimeout(() => write('xy'), 750);
```

```

Хочешь, чтобы я добавил в этот README готовую реализацию функции `typeWriter` для примера (на TypeScript или JavaScript)?
```
