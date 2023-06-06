# Algorithmic-Tasks

Задача: Поиск и перемещение кролика в норках.
Описание задачи:

[🐇🕳️🕳️🕳️🕳️🕳️🕳️🕳️]

В данной задаче массив это - норки, обозначенные символами "🕳️". В одной из норок находится кролик, обозначенный символом "🐇". Остальные норки пусты. 

Цель задачи состоит в том, чтобы найти норку, в которой находится кролик.

Для решения задачи доступны следующие действия:

1️⃣ Заглянуть внутрь норки: Проверить, есть ли кролик в текущей норке.

2️⃣ Перемещение кролика: Если при заглядывании в норку кролика не обнаружено, кролик перемещается в одну из соседних норок. Он может прыгнуть влево (норка слева от текущей) или вправо (норка справа от текущей).

🔎 Задача состоит в том, чтобы эффективно и точно определить норку, в которой находится кролик, используя минимальное количество заглядываний в норки.

⚠️ Заметка: Исходно неизвестно, в какой конкретной норке находится кролик. Задача заключается в определении этого, выполняя проверки и перемещения по мере необходимости.

🔍💨✨ Решение этой задачи требует использования алгоритма, который позволяет эффективно найти норку с кроликом, учитывая его перемещения и ограничения.
------------------------
const holes = [false, false, false, false, true, false, false];

const moveRabbit = (holes) => {
  const rabbitIndex = holes.findIndex((hole) => hole === true); 

  if (rabbitIndex !== -1) {
    const newIndex = rabbitIndex + (Math.random() < 0.5 ? -1 : 1); 

    if (newIndex >= 0 && newIndex < holes.length) {
      holes[rabbitIndex] = false; 
      holes[newIndex] = true; 
    }
  }

  return holes;
};


const getFindedIndexText = (index) => {
  return`Кролик найден в норке ${index}`
}

const func = (holes, index = 0) => {
  if (holes[index]) {
    return getFindedIndexText(index);
  } else {
    if (holes[index - 1]) {
      return getFindedIndexText(index = 1);
    } else {
      if (holes[index + 1]) {
        return getFindedIndexText(index + 1);
      } else {
        console.log(`Кролик не найден в норке ${index} или её соседних`);
        console.log('Кролик прыгнул в другую норку');
        const newHoles = moveRabbit(holes);
        return func(newHoles, index + 1);
      }
    }
  }
};

const result = func(holes);
console.log(result);
