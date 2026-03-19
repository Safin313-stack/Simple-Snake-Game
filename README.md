<div align="center">

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0a,50:0a2a0a,100:1a4a1a&height=200&section=header&text=Simple+Snake+Game&fontSize=52&fontColor=39ff14&fontAlignY=38&desc=A+classic+snake+game+built+with+HTML%2C+CSS+and+JavaScript&descAlignY=60&descSize=15&descColor=7fff7f" width="100%"/>

<br/>

[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![MIT License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](LICENSE)
[![Deployed](https://img.shields.io/badge/Deployed-GitHub%20Pages-0ea5e9?style=flat-square&logo=github)](https://safin313-stack.github.io/Simple-Snake-Game/)
[![Single File](https://img.shields.io/badge/Single-HTML%20File-39ff14?style=flat-square&logoColor=black)]()

<br/>

<a href="https://safin313-stack.github.io/Simple-Snake-Game/">
  <img src="https://img.shields.io/badge/-%F0%9F%90%8D%20%20LIVE%20DEMO%20%20%E2%86%92-0a2a0a?style=for-the-badge&logoColor=39ff14" alt="Live Demo" height="42"/>
</a>

<br/>
<sub>✦ No login &nbsp;·&nbsp; No install &nbsp;·&nbsp; Opens instantly in your browser ✦</sub>

<br/><br/>

</div>

---

<div align="center">

### 🐍 Features

| 🎮 Playable Game | ⬆️ Arrow Controls | 🍎 Food Spawning | 📈 Score Tracker | 💥 Collision Detection | 🔄 Restart |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Fully functional classic snake game | Use arrow keys to control direction | Food spawns at random positions | Score increases with every food eaten | Game ends on wall or self collision | Restart button after game over |

</div>

---

## 🖥️ Game Preview

```
╔══════════════════════════════════════════════════════════╗
║                                                          ║
║   Score: 5                                               ║
║                                                          ║
║  ┌──────────────────────────────────────────────────┐   ║
║  │                                                  │   ║
║  │          🍎                                      │   ║
║  │                                                  │   ║
║  │                ■ ■ ■ ■ ■ ■                       │   ║
║  │                            ■                     │   ║
║  │                            ■  ←  snake           │   ║
║  │                                                  │   ║
║  │                                                  │   ║
║  └──────────────────────────────────────────────────┘   ║
║                                                          ║
║   ↑ ↓ ← →  Arrow keys to move                           ║
╚══════════════════════════════════════════════════════════╝
```

---

## 🧠 How It Works

### Game Loop with setInterval

```js
// Game ticks every 150ms — snake moves each tick
let gameLoop = setInterval(() => {
  update();   // move snake + check collisions
  draw();     // render new frame
}, 150);
```

### Snake Movement Logic

```js
// Snake is an array of {x, y} segments
// New head added in direction · last tail removed
function update() {
  const head = {
    x: snake[0].x + direction.x,
    y: snake[0].y + direction.y
  };
  snake.unshift(head);          // add new head

  if (head.x === food.x && head.y === food.y) {
    score++;                    // ate food → grow
    spawnFood();
  } else {
    snake.pop();                // no food → remove tail
  }
}
```

### Collision Detection

```js
function checkCollision(head) {
  // Wall collision
  if (head.x < 0 || head.x >= cols ||
      head.y < 0 || head.y >= rows) return true;

  // Self collision
  for (let i = 1; i < snake.length; i++) {
    if (snake[i].x === head.x &&
        snake[i].y === head.y) return true;
  }
  return false;
}
```

### Random Food Spawning

```js
function spawnFood() {
  food = {
    x: Math.floor(Math.random() * cols),
    y: Math.floor(Math.random() * rows)
  };
}
```

### Keyboard Controls

```js
document.addEventListener('keydown', (e) => {
  const dirs = {
    ArrowUp:    { x: 0,  y: -1 },
    ArrowDown:  { x: 0,  y:  1 },
    ArrowLeft:  { x: -1, y:  0 },
    ArrowRight: { x:  1, y:  0 }
  };
  if (dirs[e.key]) direction = dirs[e.key];
});
```

---

## 🎮 How to Play

```
1. Open the live demo link
2. Press any Arrow Key to start moving
3. Eat the 🍎 food to grow and score points
4. Avoid hitting the walls or your own tail
5. Game Over? Click Restart to play again!

Controls:
  ↑  →  ↓  ←   Arrow keys
```

---

## 📁 Project Structure

```
Simple-Snake-Game/
│
├── 📄 index.html    ← Complete game: HTML + CSS + JS in one file
└── 📄 README.md     ← Project documentation
```

---

## 🚀 Run It Yourself

**Option 1 — Live (instant, no setup)**

> 🔗 **[https://safin313-stack.github.io/Simple-Snake-Game/](https://safin313-stack.github.io/Simple-Snake-Game/)**

**Option 2 — Clone and open locally**

```bash
git clone https://github.com/Safin313-stack/Simple-Snake-Game.git
open index.html
```

---

## 🛠️ Tech Stack

```
┌──────────────────────────────────────────────────────┐
│           Frontend · Single File · No Framework      │
├─────────────────┬────────────────────────────────────┤
│  HTML5          │  Game canvas and layout            │
│  CSS3           │  Grid styling and dark theme       │
│  JavaScript     │  Game loop · logic · controls      │
│  Technique      │  Array-based snake body segments   │
└─────────────────┴────────────────────────────────────┘
```

---

## 📚 Key Concepts Used

```
setInterval()          → game loop that runs every 150ms
Array unshift/pop      → efficiently add head and remove tail
keydown event          → capture arrow key input for direction
collision detection    → wall bounds check and self-intersection
Math.random()          → random food position spawning
CSS Grid               → rendering the game board cells
modular game state     → score · direction · snake · food · running
```

---

## 💡 Credits & Inspiration

Special thanks to **TCW - AI & coding resources** (Telegram Community)
for ideas, guidance, and coding support throughout this project. 🙏

---

<div align="center">

## 👤 Developer

<br/>

**Saharia Hassan Safin**
Front-end Developer

<br/>

[![GitHub](https://img.shields.io/badge/GitHub-Safin313--stack-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Safin313-stack)
&nbsp;
[![Live Project](https://img.shields.io/badge/Live%20Project-Visit%20Now-0a2a0a?style=for-the-badge&logo=vercel&logoColor=white)](https://safin313-stack.github.io/Simple-Snake-Game/)

<br/>

*"One array, one loop, one classic game"* 🐍

<br/>

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a4a1a,50:0a2a0a,100:0a0a0a&height=120&section=footer" width="100%"/>

<sub>MIT License · © 2025 Saharia Hassan Safin · ⭐ Star this repo if you beat your high score!</sub>

</div>
